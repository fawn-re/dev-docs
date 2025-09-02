+++
date = '2025-08-19T13:45:00-06:00'
title = 'Principles'
weight = 1
+++

# Style Guide Principles

Follow these principles when designing or enhancing user interfaces.

{{< h2 title="Read Documentation" >}}

Familiarize yourself with the documentation for the tools we use. This will help you make more informed decisions.

- [CSS documentation from MDN](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [HTML documentation from MDN](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [JavaScript documentation from MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Bootstrap 5.2 documentation](https://getbootstrap.com/docs/5.3/getting-started/introduction)
- [Font Awesome 4.7 documentation](https://fontawesome.com/v4/icons)

Consult the documentation before inventing something new; it may already exist.

{{< h2 title="Model Inputs After Data" >}}

Inputs should model the data they represent. This can be done by selecting the proper attributes, such as [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#input_types) and [`inputmode`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode#values):

- Boolean or binary values ⟶ [`<input type=checkbox>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)
- One of an enumeration ⟶ [`<input type=radio>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/radio) or [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/select)
- Number ⟶ [`<input type=number>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/number)
	- For integers, use [`inputmode=numeric`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode#numeric).
	- For decimals, use [`inputmode=decimal`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode#decimal).
	- Include [`min`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/number#min), [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/number#max), and [`step`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/number#step) attributes where it is useful to do so.
- Email address ⟶ [`<input type=email inputmode=email>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/email)
- Telephone number ⟶ [`<input type=tel inputmode=tel>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/tel)
- URL ⟶ [`<input type=url inputmode=url>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/url)

These are just some of the most common examples. See the many options available for the [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#input_types) and [`inputmode`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode#values) attributes to find what input best fits your data.

{{< h2 title="Style Conservatively" >}}

Be conservative with custom CSS styles. Prioritize using Bootstrap components and styles instead. Be very careful adding styles that are inconsistent with the style guide (or the rest of the site, if not addressed here), even if ticket spec or anybody else asks for it. Always ask yourself, "what problem does this solve?" If you don't understand why you are making a change, it is likely unwise to do so.

{{< h2 title="Use Elements Properly" >}}

HTML elements should be used for their intended purpose, and the most appropriate HTML element should be used.

{{< h3 title="Do Not Use Anchor Tags as Buttons" >}}

One of the most common violations of this is the use of `<a>` elements as buttons through the use of the `onclick` attribute. [MDN advises against this](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/a#onclick_events) for very good reason:

> Anchor elements are often abused as fake buttons by setting their href to `#` or `javascript:void(0)` to prevent the page from refreshing, then listening for their click events.
> These bogus `href` values cause unexpected behavior when copying/dragging links, opening links in a new tab/window, bookmarking, or when JavaScript is loading, errors, or is disabled. They also convey incorrect semantics to assistive technologies, like screen readers.
> Use a `<button>` instead. In general, **you should only use a hyperlink for navigation to a real URL.**

It is okay to style an `<a>` element like a button, but it must have an `href` attribute and must not have an `onclick` attribute.

{{< h2 title="Bootstrap" >}}

Follow these principles when utilizing Bootstrap's components and utilities.

{{< h3 title="Grid Mindfulness" >}}

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

{{< h3 title="Button Classes" >}}

Bootstrap has several <a href="https://getbootstrap.com/docs/5.3/customize/color" target="_blank">predefined classes</a> that apply colors in order to communicate functionality. These options are <strong class=text-primary-emphasis>primary</strong>, <strong class=text-secondary-emphasis>secondary</strong>, <strong class=text-success-emphasis>success</strong>, <strong class=text-danger-emphasis>danger</strong>, <strong class=text-warning-emphasis>warning</strong>, and <strong class=text-info-emphasis>info</strong>.

Button colors should use the following classes, depending on that button's role:

- <strong class="text-primary-emphasis">Primary</strong>: The default button color. Use this if none of the other roles fit.
- <strong class="text-secondary-emphasis">Secondary</strong>: Use this for buttons that are uncommonly used, and for the 'Close' buttons in the footers of modals where closing the modal cannot result in a loss of information (that is to say, modals where changes are saved automatically).
- <strong class="text-success-emphasis">Success</strong>: Use this for buttons that complete an action, such as submitting a form, creating a resource, downloading a file, and so on. Common buttons that use this role have text such as 'Save', 'Submit', 'Confirm', or 'Download'.
- <strong class="text-danger-emphasis">Danger</strong>: Use this for buttons that a user should not click by accident, such as buttons that delete a resource, buttons that close a modal with unsaved changes, and so on. If clicking the button by mistake would make the user sad or upset, use this role.
- <strong class="text-warning-emphasis">Warning</strong>: Use this for buttons that a user should not click by accident, but that don't have severe consequences if they do. Such cases are pretty rare; examples include buttons that edit important information. Use this role for buttons that a user should not click lightly, but that don't warrant the use of the <strong class="text-danger-emphasis">danger</strong> role.
- <strong class="text-info-emphasis">Info</strong>: Use this for buttons whose action is idempotent (clicking it multiple times is no different than clicking it once, as far as the backend is concerned). Examples of this are buttons that show reports and graphs.

The exact colors of these different classes depends on site-specific styles; it is important to choose the class based off the intended role of the button, not the resulting color.

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
	
