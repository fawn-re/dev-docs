+++
date = '2025-09-12T13:46:00-06:00'
title = 'Checkboxes'
+++

# Checkboxes

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

{{< h2 title="Indeterminate Checkboxes" >}}

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

{{< h2 title="Toggle Switches" >}}

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
