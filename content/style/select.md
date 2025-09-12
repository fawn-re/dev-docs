+++
date = '2025-09-12T13:46:14-06:00'
title = 'Select'
+++

# Select

Dropdown menus should be used when a user needs to select one option from among a group of related options. See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/forms/select) for their dropdown menu styles.

Dropdown menus containing a default "Please choose an option" `<option>` must give the `disabled` attribute to that `<option>` in order to prevent the user from choosing it, and that `<option>` should have a `value=""` attribute (its value must be the empty string). It may also be helpful to include the `required` attribute on the `<select>`, since this also prevents the user from submitting a form if they have selected an `<option value="">`.

If your dropdown menu does not have a corresponding `<label>`, it must have an `aria-label` attribute. Dedicated `<label>`s are preferred, since they also contextualize the selected option, which may be unclear otherwise.

Semantically, there is no difference between a set of radio buttons and a `<select>`; however, with radio buttons, the alternative choices are always visible, whereas the options of a `<select>` are not. When choosing between a set of radio buttons and a `<select>`, consider how many options the user must choose from and how much space those options will take up, as well as if you want the user to be aware of what options they are *not* choosing.

If your `<select>` only has two options, consider using a toggle switch instead.

<div class="example">
	<label class="form-label" for="select_example">Choose an ink</label>
	<select id="select-example" class="form-select" required>
		<option value="" disabled selected>—</option>
		<option value="1">Cyan</option>
		<option value="2">Magenta</option>
		<option value="3">Yellow</option>
		<option value="4">Black</option>
	</select>
</div>

```html
<label class="form-label" for="select_example">Choose an ink</label>
<select id="select-example" class="form-select" required>
	<option value="" disabled selected>—</option>
	<option value="1">Cyan</option>
	<option value="2">Magenta</option>
	<option value="3">Yellow</option>
	<option value="4">Black</option>
</select>
```
