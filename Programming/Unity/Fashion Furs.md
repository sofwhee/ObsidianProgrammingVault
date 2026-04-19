[[Raycast]]

Ideas for UI drag and Drop:

Raycast
Detect UI objects
Drag
While Dragging, Raycast from Dragged object's collider
If dragged object detects something underneath
then, when released
do something
else
do something else

## Drag and Drop Inventory UI

InventoryController.cs

```C#
// Psuedocode
void Start()
{
	for 40 loops
		instantiate a slot prefab at this location
		if we have another item to instantiate in the slot
			instantiate item with the slot as a parent
			get the item's recttransform's anchored position variable and set it to 0
			set the slot's current item variable to this item
}
```

```C#
public GameObject inventoryPanel;
public GameObject slotPrefab;
public int slotCount;
public GameObject itemPrefabs;

void Start()
{
	// for however many slots you want
	for(int i = 0; i < slotCount; i++)
	{
		// make a slot prefab
		// set the variable to a Slot class by getting component Slot
		Slot slot = Instantiate(slotPrefab, inventoryPanel.transform).GetComponent<Slot>();
		// use the loop number to see if we have items left to fill slots with
		if(i < itemPrefabs.Length)
		{
			// make an item prefab with the slot as its parent
			// turn the item's recttransform's anchoredPosition to 0
			// this will center it within the slot
			GameObject item = Instantiate(itemPrefabs[i], slot.transform);
			item.GetComponent<RectTransform>().anchoredPosition = vector2.zero;
			slot.currentItem = item;
		}
	}
}
```

UI Image item prefab object
- give it canvas group
	- interactable
- give it a drag handler

```C#
public class ItemDragHandler : MonoBehaviour, IBeginDragHandler, IDragHandler, IEndDragHandler
{
	// This is the slot we pulled it from
	// It allows us to snap it back in place if we let go.
	Transform originalParent;
	CanvasGroup canvasGroup;
	
	void Start()
	{
		canvasGroup = GetComponent<CanvasGroup>();
	}
	
	public void OnBeginDrag(PoinerEventData eventData)
	{
		originalParent = transform.parent; // Save OG parent
		transform.SetParent(transform.root); // Above other canvas
		// prevents dragged object getting in the way of raycasts
		// (way more elegant solution than the RaycastAll I was doing)
		canvasGroup.blocksRaycasts = false;
		canvasGroup.alpha = 0.6f; //semi-transparent during drag
	}
	
	public void OnDrag(PointerEventData eventData)
	{
		transform.position = eventData.position; //Follow the mouse
	}
	
	public void OnEndDrag(PointerEventData eventData)
	{
		// raycast detects this object again
		canvasGroup.blocksRaycasts = true;
		canvasGroup.alpha = 1f; // transparent'nt
		// Slot you dropped the item at, if any
		Slot dropSlot = eventData.pointerEnter?.GetComponent<Slot>();
		Slot originalSlot = originalParent.GetComponent<Slot>();
		
		// item swapping within slot inventory
		if (dropSlot != null)
		{
			if (dropSlot.currentItem != null)
			{
				// Slot has an item - move that item to our orignal slot
				dropSlot.currentItem.transform.SetParent(originalSlot.transform);
				originalSlot.currentItem = dropSlot.currentItem;
				dropSlot.currentItem.GetComponent<RectTransform>().anchoredPosition = Vector2.zero;
			}
			else
			{
				// New slot had no item - make original slot empty
				originalSlot.currentItem = null;
			}
			
			// Move item into drop slot
			transform.SetParent(dropSlot.transform);
			dropSlot.currentItem = gameObject;
		}
		else // if there's no slot under the mouse
		{
			transform.SetParent(originalParent);
		}
		
		// Center this item in its slot, wherever it landed
		GetComponent<RectTransform>.anchoredPosition = Vector2.zero
		
	}
	
}
```
## Snapping objects


```C#
For each snapPoint
if the distance between this snapPoint and this object is within 0.5f
object.position = point.position

public list<Transform> snapPoints;
public float snapRange - 0.5f;
...

public void SnapObject(Transform obj)
{
	foreach (Transform point in snapPoints)
	{
		if (Vector2.distance(point.position, obj.position) <= snapRange)
		{
			object.position = point.position;
			return;
		}
	}
}
```