+++
date = '2025-09-12T13:45:49-06:00'
title = 'Bootstrap Grid'
weight = 2
+++

# Bootstrap Grid

You probably don't need Bootstrap's grid utilities. Most HTML elements are by default either [block elements or inline elements](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_display/Block_and_inline_layout_in_normal_flow), and their defaults are chosen carefully. Default behavior is often sufficient.

When default behavior is not enough, many layouts can be achieved using [flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox) layout. Bootstrap 5 has some convenient flex utility classes called ["stacks"](https://getbootstrap.com/docs/5.3/helpers/stacks) (`.hstack` and `.vstack`) that are more than sufficient in most situations.

If you truly need a layout that is a grid, consider using [CSS's native grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout) layout instead, which is superior to Bootstrap's grid solution. Bootstrap grid existed before CSS grid was formalized, and continues to exist for backwards compatibility. In fact, Bootstrap is experimenting with a new [opt-in grid](https://getbootstrap.com/docs/5.3/layout/css-grid) built on CSS's native grid layout.

If using Bootstrap grid is absolutely necessary, follow these guidelines:

- Do not put non-column elements directly inside rows.
- Do not put column elements outside of a containing row.
- Do not use rows if they would have less than two columns.
- Do not use rows if all of their columns have 'auto' width (`.col-auto`). Use an [`.hstack`](https://getbootstrap.com/docs/5.3/helpers/stacks/#horizontal) instead.
- Do not use grid offsets on non-column elements. (In fact, avoid using grid offsets in general.)
- Avoid using full-width column classes (`.col-12`, `.col-sm-12`, `.col-md-12`, `.col-lg-12`, `.col-xl-12`, `.col-xxl-12`), as this often indicates that no grid is necessary at all.

Unnecessary `.row > .col` wrappers should be removed as they are found.

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
