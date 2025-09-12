+++
date = '2025-09-12T13:46:23-06:00'
title = 'Accordion'
+++

# Accordion
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
