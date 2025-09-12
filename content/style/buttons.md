+++
date = '2025-09-12T13:46:36-06:00'
title = 'Buttons'
+++

# Buttons

Bootstrap has several <a href="https://getbootstrap.com/docs/5.3/customize/color" target="_blank">predefined classes</a> that apply colors in order to communicate functionality. These options are <strong class=text-primary-emphasis>primary</strong>, <strong class=text-secondary-emphasis>secondary</strong>, <strong class=text-success-emphasis>success</strong>, <strong class=text-danger-emphasis>danger</strong>, <strong class=text-warning-emphasis>warning</strong>, and <strong class=text-info-emphasis>info</strong>.

Button colors should use the following classes, depending on that button's role:

- <strong class="text-primary-emphasis">Primary</strong>: The default button color. Use this if none of the other roles fit.
- <strong class="text-secondary-emphasis">Secondary</strong>: Use this for buttons that are uncommonly used, and for the 'Close' buttons in the footers of modals where closing the modal cannot result in a loss of information (that is to say, modals where changes are saved automatically).
- <strong class="text-success-emphasis">Success</strong>: Use this for buttons that complete an action, such as submitting a form, creating a resource, downloading a file, and so on. Common buttons that use this role have text such as 'Save', 'Submit', 'Confirm', or 'Download'.
- <strong class="text-danger-emphasis">Danger</strong>: Use this for buttons that a user should not click by accident, such as buttons that delete a resource, buttons that close a modal with unsaved changes, and so on. If clicking the button by mistake would make the user sad or upset, use this role.
- <strong class="text-warning-emphasis">Warning</strong>: Use this for buttons that a user should not click by accident, but that don't have severe consequences if they do. Such cases are pretty rare; examples include buttons that edit important information. Use this role for buttons that a user should not click lightly, but that don't warrant the use of the <strong class="text-danger-emphasis">danger</strong> role.
- <strong class="text-info-emphasis">Info</strong>: Use this for buttons whose action is idempotent (clicking it multiple times is no different than clicking it once, as far as the backend is concerned). Examples of this are buttons that show reports and graphs.

The exact colors of these different classes depends on site-specific styles; it is important to choose the class based off the intended role of the button, not the resulting color. The function of any button should be clear without color or icon, and both colors and icons merely augment the communication of a button's role.

<div class="example hstack gap-2">
	<button type="button" class="btn btn-primary">Settings</button>
	<button type="button" class="btn btn-secondary">Close</button>
	<button type="button" class="btn btn-success">Save</button>
	<button type="button" class="btn btn-danger">Delete</button>
	<button type="button" class="btn btn-warning">Edit</button>
	<button type="button" class="btn btn-info">Stats</button>
</div>

```html
<button type="button" class="btn btn-primary">Settings</button>
<button type="button" class="btn btn-secondary">Close</button>
<button type="button" class="btn btn-success">Save</button>
<button type="button" class="btn btn-danger">Delete</button>
<button type="button" class="btn btn-warning">Edit</button>
<button type="button" class="btn btn-info">Stats</button>
```

{{< h2 title="Button Icons" >}}

<!-- This requires https://redmine.raceentry.com/issues/6711 in order to function. -->
Adding icons to buttons can help communicate their function. To add an icon to a button, just add the appropriate Font Awesome CSS class to the `<button>` itself.

For the following common buttons, prefer using these standard icons (and roles):

- "Save" buttons must use `fa-floppy-disk` and must be `btn-success`.
- "Delete" buttons must use `fa-trash` and must be `btn-danger`.
- "Enable" or "Show" buttons must use `fa-eye` and must be `btn-success`.
- "Disable" or "Hide" buttons must use `fa-eye-slash` and must be `btn-warning`. 
- "Settings" buttons must use `fa-gear`, and depending on context, must be either `btn-primary` or `btn-warning`. Settings buttons that open a modal **must not** be labelled "Advanced" unless there are non-trivial settings present outside of the modal.
- "Dismiss" or "Close" buttons in modals may use `fa-square-xmark` if there are multiple adjacent buttons, otherwise these buttons should use no icon. If closing the modal would forfeit unsaved changes, the button must be `btn-danger`. If closing the modal has no effect on unsaved changes, or if changes in the modal are saved automatically, the button must be `btn-secondary`.
- "Add" buttons, which add an item to a list or create a new row in a table, must use `fa-circle-plus` and be `btn-success`.
- "Remove" buttons, which remove an item from a list or delete a row from a table, must use `fa-circle-minus` and be `btn-danger`.
- "Upload" buttons must use `fa-upload`. If that same button submits the file to the server after a file has been selected, it must be `btn-success`, otherwise it must be `btn-primary`.
- "Download" buttons must use `fa-download` and should be `btn-success`.

<div class="example hstack flex-wrap gap-2">
	<button type="button" class="btn btn-success fa-floppy-disk">Save</button>
	<button type="button" class="btn btn-danger fa-trash">Delete</button>
	<button type="button" class="btn btn-success fa-eye">Enable</button>
	<button type="button" class="btn btn-warning fa-eye-slash">Disable</button>
	<button type="button" class="btn btn-primary fa-gear">Settings</button>
	<button type="button" class="btn btn-secondary fa-square-xmark">Dismiss</button>
	<button type="button" class="btn btn-success fa-circle-plus">Add</button>
	<button type="button" class="btn btn-danger fa-circle-minus">Remove</button>
	<button type="button" class="btn btn-primary fa-upload">Upload</button>
	<button type="button" class="btn btn-success fa-download">Download</button>
</div>

```html
<button type="button" class="btn btn-success fa-floppy-disk">Save</button>
<button type="button" class="btn btn-danger fa-trash">Delete</button>
<button type="button" class="btn btn-success fa-eye">Enable</button>
<button type="button" class="btn btn-warning fa-eye-slash">Disable</button>
<button type="button" class="btn btn-primary fa-gear">Settings</button>
<button type="button" class="btn btn-secondary fa-square-xmark">Dismiss</button>
<button type="button" class="btn btn-success fa-circle-plus">Add</button>
<button type="button" class="btn btn-danger fa-circle-minus">Remove</button>
<button type="button" class="btn btn-primary fa-upload">Upload</button>
<button type="button" class="btn btn-success fa-download">Download</button>
```
