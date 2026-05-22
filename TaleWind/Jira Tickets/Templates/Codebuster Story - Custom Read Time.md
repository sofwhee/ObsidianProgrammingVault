
**User Story:**

Currently, the media platform automatically calculates and displays the estimated “read time” for articles based on system logic. While this works for standard text-based articles, some clients include attachments or supplementary materials that significantly impact the actual time required to consume the content.  
  
An option that allows a user to manually override the system-calculated read time and set a custom value when necessary must be introduced due to:

- Attachment inclusions that increase the time required to review the document.
- Clients may want more accurate or intentional control over the displayed read time.
- Enhances client satisfaction by allowing content-specific adjustments.

**Proposed Solution:**

- Add an optional **Custom Read Time** field in the article Create and Edit pages
- If a Custom Read Time is **provided**, override the system-calculated value.
- If Custom Read Time is **blank**, the system continues to display the auto-calculated read time.
    

**Acceptance Criteria:**

- Users can enter a custom read time on the backend when creating or editing an article.
- If a custom read time is entered, it is displayed in place of the system-calculated value.
- If no custom read time is entered, the system calculated read time is displayed. _(existing behaviour)_
- Users can edit or remove the custom read time.
- Proper validation of form field input: **Positive integers only**
- Does not impact existing articles unless a custom value is manually added.

(attachment)
![[Pasted image 20260506141217.png]]