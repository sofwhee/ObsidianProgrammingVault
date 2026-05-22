[[Raycast]]

[[DragAndDrop]]
[[Clothing Character]]
[[Save And Load]]
[[2d Animation Puppet Workflow]]
[[The Observer Pattern in Unity]]

## Current notes

I wanted to modularize all the code, but I'm wondering if it's all too hard to read and understand. I also wonder what the point of modularizing the code is, since this is such a simple game. I feel like I'm optimizing too early.

I'm now thinking I want to organize the logic of the project with as little code as possible, so it's easier to work with.

I wanted to reduce dependencies, I think...

But why did I put in dependencies in the first place?
I suppose it's an easy way to code things initially.
But it becomes harder to change things when everything expects everything else to stay unchanging.
Maybe modularity is a good idea.

I wanted to remove the vestigial swappable aspects of the drag and drop system i implemented. Maybe I need to rethink the slot system. Or maybe it will be reused for a shop. I don't really know. 

I think I'd like to make everything modular because I can do test driven development.

I am making self contained classes that interface with each other using a controller


Dropping on character box

When player places a clothing item on the character box,
The game will place the clothing at the appropriate places on the body

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
- Pos Z = 1
- Width + Height = 100 x 100 or whatever
- set RectTransform anchor point to "center" on slot and item prefab

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
		
		// Slot where item dropped
		Slot dropSlot = eventData.pointerEnter?.GetComponent<Slot>();
		
		if(dropSlot == null)
		{
			// Grab the game object we're dropping onto
			GameObject dropItem = eventData.pointerEnter;
			if (dropItem != null)
			{
				dropSlot = dropItem.GetComponentInParent<Slot>();
			}
		}
		
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

## 2D Puppet Animation

1. PackageManager
	1. 2D Animation
	2. 2D IK
	3. 2D PSDImporter
2. Make a Photoshop PSD with different layers for each body part
	1. Unity will automatically separate each layer into body parts
3. Skinning Editor (go into sprite editor and change to Skinning)
	1. Create Bone on top left
	2. click to make a bone
	3.  click again to make another connected bone
	4. right click to stop
	5.  you can click a bone, which will then connect the next bone to it even if it's separated by space
	6. Reparent Bone to see the bone heirarchy
	7. Hit preview Pose to move bones around
4. Auto Geometry
	1. Hitting auto geometry will allow you to generate sprits
	2. Outline detail - The bigger it is, the more vertices along the edge of your character (it's fine to leave it at a low num)
	3. Subdivide creates more vertices

### Serialized Dict

```C#
// For serializable dictionaries. Nobody knows why it's in Rendering...

using UnityEngine.Rendering;
    public SerializedDictionary<GameObject, GameObject> itemPrefabsDict;
    
    foreach (var itemPrefab in itemPrefabsDict)
    {
	    GameObject itemKey = itemPrefab.Key;
	    GameObject itemValue = itemPrefab.Value;
    }

```