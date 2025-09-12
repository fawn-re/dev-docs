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
