+++
date = '2025-09-12T13:46:00-06:00'
title = 'Radio Buttons'
+++

# Radio Buttons

Radio buttons should be used when a user needs to select one option from among a group of related options. See [Bootstrap's documentation](https://getbootstrap.com/docs/5.3/forms/checks-radios/#radios) for their radio button styles.

Semantically, there is no difference between a set of radio buttons and a `<select>`; however, with radio buttons, the alternative choices are always visible, whereas the options of a `<select>` are not. When choosing between a set of radio buttons and a `<select>`, consider how many options the user must choose from and how much space those options will take up, as well as if you want the user to be aware of what options they are *not* choosing.

If your set of radio buttons only has two options, consider using a toggle switch (checkbox) instead.

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

