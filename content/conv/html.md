+++
date = '2025-08-21T14:55:07-06:00'
title = 'HTML'
+++

# HTML Conventions

Please keep the following coding conventions in mind when writing HTML.

{{< h2 title="Attributes" >}}

Attributes must appear in the following order, when present: `id`, `class`, `type`, any attributes with string values such as `inputmode`, then any attributes without explicit values such as `disabled`.

Attributes must be surrounded by double quotes.

```html
<!-- good -->
<input id="some_id" class="some_class" type="number" inputmode="numeric" disabled>

<!-- bad -->
<input disabled class=some_class id=some_id inputmode=numeric type=number>
```

{{< h2 title="Spacing" >}}

Use hard tabs for indentation. Use Unix-style line endings (LF) rather than Windows-style (CRLF). Lines must not have unnecessary trailing whitespace.
```html
<!-- good -->
<div>
	<h1>Hello there!</h1>
</div>

<!-- bad -->
<div>
  <h1>Hello there!</h1>      <!-- trailing whitespace -->
</div>
```
