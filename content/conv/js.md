+++
date = '2025-08-19T13:44:46-06:00'
title = 'JavaScript'
+++

# JavaScript Conventions

Please keep the following coding conventions in mind when writing JavaScript.

{{< h2 title="Naming" >}}

Use `snake_case` for identifiers. URLs must use hyphens rather than underscores. Custom CSS IDs and classes must use underscores rather than hyphens. If a variable is declared but not used, prefix its name with an underscore to indicate that it is a placeholder. Boolean variables and functions that return boolean values should start with `is_` or `has_`.

Always declare variables before using them. Declare variables with `const` by default; only declare a variable with `let` if it is intended to be mutable. Do not declare variables with `var` when writing new code, but avoid changing existing `var` declarations. `var` is a footgun with some error-prone behaviors that existing code may rely upon, but are generally undesirable for all new code:

- Declaring a variable using `var` succeeds even if there is already a variable or function with the same name. Doing so is not an error, nor is it a warning, unless the other name was declared using `const`.
- Variables declared with `var` are scoped to the entire containing function, or if outside a function, scoped globally (commonly known as [“hoisting”](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#hoisting)).

```js
function good_example() {
	const ajax_url = $("#ajax-url").val() + "endpoint-name";
	const input_el = $("#the-input-element");
	let is_okay = false;
	$.post(ajax_url, input_el.val()).done((_res) => {
		input_el.addClass("#is-valid")
			.removeClass("#is-invalid");
		is_okay = true;
	}).fail((_rej) => {
		input_el.addClass("#is-invalid")
			.removeClass("#is-valid");
	});
	return is_okay;
}

function BadExample() {
	const ajaxURL = $("#ajax_url").val() + "endpoint_name";
	let InputEl = $("#theInputElement");
	var okay = false;
	$.post(ajaxURL, InputEl.val()).done((res) => {
		InputEl.addClass("#is-valid")
			.removeClass("#is-invalid");
		okay = true;
	}).fail((rej) => {
		InputEl.addClass("#is-invalid")
			.removeClass("#is-valid");
	});
	return okay;
}
```

{{< h2 title="Brace Style" >}}

Use “egyptian braces”. Do not omit braces for single-statement blocks. Single-statement blocks that fit on a single line may be formatted as a single line.

```js
function good_example() {
	let x = 5;
	while (x < 10) { x++; }
	if (x == 10) {
		console.log("x is 10");
	} else {
		console.log("x is not 10");
		console.log(x);
	}
}

function bad_example()
{
	let x = 5;
	while (x < 10)
		x++;
	if (x == 10)
		console.log("x is 10");
	else
	{
		console.log("x is not 10");
		console.log(x);
	}
}
```

{{< h2 title="Spacing" >}}

Use hard tabs for indentation. Use Unix-style line endings (LF) rather than Windows-style (CRLF). Add spaces between control flow keywords and their conditions, and do not add extra spaces within control flow conditions. Put a space between operators and their operands, including the `!` (not) operator and its operand. Lines must not have unnecessary trailing whitespace.

```js
// good
if (! 1 < 2) {
	console.log("cool and good");
}

// bad
if( !1<2 ) {  // trailing whitespace
	console.log("not cool or good");
}
```

{{< h2 title="Strings" >}}

Use double quotes for strings. When combining more than three values together into a string, use string templates.

```js
const qty = 100;
const thing = "mandarin oranges";

// good
const good1 = `i would like ${qty} of ${thing}`
const good2 = "i would like two " + thing;

// bad
const bad = 'i would like ' + qty + ' of ' + thing;
```

{{< h2 title="Boolean Zen" >}}

Do not compare values to `true` or `false`, use the value directly (or its negation through the `!` operator) instead. Ternary expressions must not have boolean literals in either branch. If a value’s intended type is not always a boolean, strict comparisons (`===`) to `true` or `false` are acceptable.

```js
function good_function(x) {
	return x !== 3;
}

// y could be any type, thanks JavaScript! This checks
// specifically for when y is a boolean with a value of false.
function acceptable_function(y) {
	return y === false;
}

function bad_function(x) {
	let pointless_intermediate_value = false;
	if (x === 3) {
		pointless_intermediate_value = true;
	}
	if (pointless_intermediate_value == false) {
		return true;
	} else {
		return false;
	}
}
```
