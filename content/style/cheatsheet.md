+++
date = '2025-08-19T13:45:16-06:00'
title = 'Cheatsheet'
+++

# Style Guide Cheatsheet

Below are examples of common utilities and components as reference for your convenience.

{{< h2 title="Action Bar" >}}

Pages occasionally have a row of buttons for common actions near the top.

<div class="example">
	<div class="action_bar">
		<button type="button" class="btn btn-primary">Button A</button>
		<button type="button" class="btn btn-primary">Button B</button>
		<button type="button" class="btn btn-warning ms-auto">Button C</button>
	</div>
</div>

```html
<div class="action_bar">
	<button type="button" class="btn btn-primary">Button A</button>
	<button type="button" class="btn btn-primary">Button B</button>
	<!-- If you need to align an item to the right, use .ms-auto -->
	<button type="button" class="btn btn-warning ms-auto">Button C</button>
</div>
```

{{< h2 title="Stacks" >}}

Bootstrap has utility classes for flexbox layouts called ["stacks"](https://getbootstrap.com/docs/5.3/helpers/stacks), which are simpler than and often preferable to Bootstrap's traditional grid.

{{< h3 title="Horizontal Stack" >}}

See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/helpers/stacks/#horizontal) for horizontal stacks.

<div class="example">
	<div class="hstack gap-3 border" style="padding: 1px">
		<div class="p-2 border">First item</div>
		<div class="p-2 border">Second item</div>
		<div class="p-2 border">Third item</div>
	</div>
</div>

```html
<!-- .gap-3 defines the gutter between items; different gap values can be used. -->
<div class="hstack gap-3">
	<div>First item</div>
	<div>Second item</div>
	<div>Third item</div>
</div>
```

{{< h3 title="Vertical Stack" >}}

See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/helpers/stacks/#vertical) for vertical stacks.

<div class="example">
	<div class="vstack gap-3 border" style="padding: 1px">
		<div class="p-2 border">First item</div>
		<div class="p-2 border">Second item</div>
		<div class="p-2 border">Third item</div>
	</div>
</div>

```html
<!-- .gap-3 defines the gutter between items; different gap values can be used. -->
<div class="vstack gap-3">
	<div>First item</div>
	<div>Second item</div>
	<div>Third item</div>
</div>
```

{{< h2 title="Checkboxes" >}}

Checkboxes should be used when a user needs to select one or more from among a group of related options. Lone checkboxes should be styled as toggle switches instead. See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/forms/checks-radios/#checks) for their checkbox styles.

Note that it is necessary to give each checkbox an `id` attribute, and give their labels `for` attributes with corresponding values.

<div class="example">
	<div class="form-check">
		<input class="form-check-input" type="checkbox" id="checkbox_default">
		<label class="form-check-label" for="checkbox_default">Default checkbox</label>
	</div>
	<div class="form-check">
		<input class="form-check-input" type="checkbox" id="checkbox_checked" checked>
		<label class="form-check-label" for="checkbox_checked">Checked checkbox</label>
	</div>
</div>

```html
<div class="form-check">
	<input class="form-check-input" type="checkbox" id="checkbox_default">
	<label class="form-check-label" for="checkbox_default">Default checkbox</label>
</div>
<div class="form-check">
	<input class="form-check-input" type="checkbox" id="checkbox_checked" checked>
	<label class="form-check-label" for="checkbox_checked">Checked checkbox</label>
</div>
```

{{< h3 title="Indeterminate Checkboxes" >}}

Checkboxes with hierarchy should use apply the [`indeterminate`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/indeterminate) property when their children are not all the same value.

<script type="text/javascript">
	addEventListener("DOMContentLoaded", _ => {
		const check_parent = document.getElementById("checkbox_parent");
		const check_children = document.querySelectorAll("[id*=checkbox_child_]");

		function update_parent(child_checked) {
			check_parent.indeterminate = ![...check_children]
				.every((v, _, arr) => !v.indeterminate && v.checked === arr[0].checked);
			check_parent.checked = !check_parent.indeterminate && child_checked;
		}

		check_children.forEach(el => el.addEventListener("change", _ => update_parent(el.checked)));

		check_parent.addEventListener("change", _ => {
			check_parent.indeterminate = false;
			check_children.forEach(el => el.checked = check_parent.checked);
		});

		update_parent(check_parent.checked);
	});
</script>
<div class="example">
	<div class="form-check">
		<input class="form-check-input" type="checkbox" id="checkbox_parent">
		<label class="form-check-label" for="checkbox_parent">Parent</label>
	</div>
	<ul style="list-style-type: none; margin-bottom: 0">
		<li class="form-check">
			<input class="form-check-input" type="checkbox" id="checkbox_child_a">
			<label class="form-check-label" for="checkbox_child_a">Child A</label>
		</li>
		<li class="form-check">
			<input class="form-check-input" type="checkbox" id="checkbox_child_b" checked>
			<label class="form-check-label" for="checkbox_child_b">Child B</label>
		</li>
		<li class="form-check">
			<input class="form-check-input" type="checkbox" id="checkbox_child_c">
			<label class="form-check-label" for="checkbox_child_c">Child C</label>
		</li>
	</ul>
</div>

```html
<div class="form-check">
	<input class="form-check-input" type="checkbox" id="checkbox_parent">
	<label class="form-check-label" for="checkbox_parent">Parent</label>
</div>
<ul style="list-style-type: none; margin-bottom: 0">
	<li class="form-check">
		<input class="form-check-input" type="checkbox" id="checkbox_child_a">
		<label class="form-check-label" for="checkbox_child_a">Child A</label>
	</li>
	<li class="form-check">
		<input class="form-check-input" type="checkbox" id="checkbox_child_b" checked>
		<label class="form-check-label" for="checkbox_child_b">Child B</label>
	</li>
	<li class="form-check">
		<input class="form-check-input" type="checkbox" id="checkbox_child_c">
		<label class="form-check-label" for="checkbox_child_c">Child C</label>
	</li>
</ul>
```

```js
const parent = document.getElementById("checkbox_parent");
const children = document.querySelectorAll("[id*=checkbox_child_]");

function update_parent(child_checked) {
	parent.indeterminate = ![...children]
		.every((v, _, arr) => !v.indeterminate && v.checked === arr[0].checked);
	parent.checked = !parent.indeterminate && child_checked;
}

children.forEach(el => el.addEventListener("change", _ => update_parent(el.checked)));

parent.addEventListener("change", _ => {
	parent.indeterminate = false;
	children.forEach(el => el.checked = parent.checked);
});

update_parent(parent.checked);
```

{{< h3 title="Toggle Switches" >}}

For individual checkboxes not part of a set, use a toggle switch. See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/forms/checks-radios/#native-switches) for toggle switches.

<div class="example">
	<div class="form-check form-switch">
		<input class="form-check-input" type="checkbox" id="toggle_switch_1" switch>
		<label class="form-check-label" for="toggle_switch_1">Enable refrigerator</label>
	</div>
	<div class="form-check form-switch">
		<input class="form-check-input" type="checkbox" id="toggle_switch_2" switch checked>
		<label class="form-check-label" for="toggle_switch_2">Self-destruct on incorrect password</label>
	</div>
</div>

```html
<div class="form-check form-switch">
	<input class="form-check-input" type="checkbox" id="toggle_switch_1" switch>
	<label class="form-check-label" for="toggle_switch_1">Enable refrigerator</label>
</div>
<div class="form-check form-switch">
	<input class="form-check-input" type="checkbox" id="toggle_switch_2" switch checked>
	<label class="form-check-label" for="toggle_switch_2">Self-destruct on incorrect password</label>
</div>
```

{{< h2 title="Radio Buttons" >}}

Radio buttons should be used when a user needs to select one option from among a group of related options. See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/forms/checks-radios/#radios) for their radio button styles.

Semantically, there is no difference between a set of radio buttons and a `<select>`; however, with radio buttons, the alternative choices are always visible, whereas the options of a `<select>` are not. When choosing between a set of radio buttons and a `<select>`, consider how many options the user must choose from and how much space those options will take up, as well as if you want the user to be aware of what options they are *not* choosing.

If your set of radio buttons only has two options, consider using a toggle switch instead.

Note that it is necessary to give each radio button an `id` attribute, and give their labels `for` attributes with corresponding values.

<div class="example">
	<div class="form-check">
		<input class="form-check-input" type="radio" id="radio_1" name="radio_set">
		<label class="form-check-label" for="radio_1">Red</label>
	</div>
	<div class="form-check">
		<input class="form-check-input" type="radio" id="radio_2" name="radio_set" checked>
		<label class="form-check-label" for="radio_2">Yellow</label>
	</div>
	<div class="form-check">
		<input class="form-check-input" type="radio" id="radio_3" name="radio_set">
		<label class="form-check-label" for="radio_3">Blue</label>
	</div>
</div>

```html
<div class="form-check">
	<input class="form-check-input" type="radio" id="radio_1" name="radio_set">
	<label class="form-check-label" for="radio_1">Red</label>
</div>
<div class="form-check">
	<input class="form-check-input" type="radio" id="radio_2" name="radio_set" checked>
	<label class="form-check-label" for="radio_2">Yellow</label>
</div>
<div class="form-check">
	<input class="form-check-input" type="radio" id="radio_3" name="radio_set">
	<label class="form-check-label" for="radio_3">Blue</label>
</div>
```

{{< h2 title="Dropdown Menus" >}}

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

{{< h2 title="Accordion" >}}
<!-- https://css-tricks.com/how-to-animate-the-details-element-using-waapi -->

Use the [`<details>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/details) element.

To make accordions mutually exclusive, give them the same `name` attribute.

<div class="example">
	<details name="color">
		<summary>Red summary</summary>
		<p>Red is the color of a yummy strawberry!</p>
	</details>
	<details name="color">
		<summary>Yellow summary</summary>
		<p>Yellow is the color of a yummy banana!</p>
	</details>
	<details name="color">
		<summary>Blue summary</summary>
		<p>Blueberries are not blue. Have you actually looked at a blueberry? Their insides are a dark reddish-purple. The skin doesn't even contain any blue pigments. Who named these things?</p>
	</details>
</div>

```html
<details name="color">
	<summary>Red summary</summary>
	<p>Red is the color of a yummy strawberry!</p>
</details>
<details name="color">
	<summary>Yellow summary</summary>
	<p>Yellow is the color of a yummy banana!</p>
</details>
<details name="color">
	<summary>Blue summary</summary>
	<p>Blueberries are not blue. Have you actually looked at a blueberry? Their insides are a weird light color like a grape. It's the skins that contain all the pigment, and they're a much darker violet color. If you've ever blended blueberries in a blender, you'd know they're quite purple.</p>
</details>
```
