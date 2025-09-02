+++
date = '2025-08-19T13:44:53-06:00'
title = 'PHP'
+++

# PHP Coding Conventions

Please keep the following coding conventions in mind when writing PHP.

{{< h2 title="Naming" >}}

Use `snake_case` for identifiers. If a variable is declared but not used, prefix its name with an underscore to indicate that it is a placeholder. Boolean variables and functions that return boolean values should start with `is_` or `has_`.

```php
// good
function is_valid() {
	$foo_bar = "baz";
	return $foo_bar === "baz";
}

// bad
function Validate() {
	$fooBar = "baz";
	return $fooBar === "baz";
}
```

{{< h2 title="Literals" >}}

Use uppercase `TRUE`, `FALSE`, and `NULL` to remain consistent with inline SQL.

```php
// good
$foo = TRUE == FALSE;
$bar = NULL;

// bad
$baz = true == false;
$quux = null;
```

{{< h2 title="Brace Style" >}}

Use “egyptian braces”. Do not omit braces for single-statement blocks. Single-statement blocks that fit on a single line may be formatted as a single line.

```php
function good_example() {
	$x = 5;
	while ($x < 10) { $x++; }
	if ($x == 10) {
		echo("x is 10");
	} else {
		echo("x is not 10");
		echo($x);
	}
}

function bad_example()
{
	$x = 5;
	while ($x < 10)
		x++;
	if ($x == 10)
		echo("x is 10");
	else
	{
		echo("x is not 10");
		echo($x);
	}
}
```

{{< h2 title="Spacing" >}}

Use hard tabs for indentation. Use Unix-style line endings (LF) rather than Windows-style (CRLF). Add spaces between control flow keywords and their conditions, and do not add extra spaces within control flow conditions. Put a space between operators and their operands, including the `!` (not) operator and its operand. Lines must not have unnecessary trailing whitespace.

```php
// good
if (! FALSE === TRUE) {
	echo("cool and good");
}

// bad
if( FALSE===TRUE ) {     // trailing whitespace
   echo("not cool or good");
}
```

{{< h2 title="Strings" >}}

Use double quotes for strings.

```php
$bad = 'do not do this';
$good = "please do this";
```

{{< h2 title="Arrays" >}}

Declare arrays using square brackets. Use single quotes for string
array keys.

```php
// good
$foo = [
	'bar' => 1,
	'baz' => [
		'quux' => "corge",
	],
];

// bad
$grault = array(
	"garply" => -1,
	"waldo" => array(
		"fred" => "plugh"
	)
);
```

{{< h2 title="HTTP Status Codes" >}}

When responding to HTTP requests, use an HTTP status code that best reflects that response. You may see legacy code that always responds with `200`, and uses some permutation of `result: "error"` in the response body to indicate failure. Do not do this. If you copy old code, you are responsible for updating your copy to use HTTP status codes properly.
Here are the three most common status codes:
- `200`: Use this if everything worked properly
- `400`: Use this if something failed and it’s the user’s fault
- `500`: Use this if something that should not ever fail does fail (it’s our fault)

There are many other status codes beyond those three. [They can be viewed here](https://www.rfc-editor.org/rfc/rfc9110.html#name-status-codes).

```php
// good
function very_real_endpoint_good() {
	$post_data = $this->request->post();
	if (strlen($post_data['some_user_input']) > 10) {
		throw new HTTP_Exception_400("User input must be 10 characters or less");
	}
	// 200 status returned implicitly
}

// bad
function very_real_endpoint_bad() {
	$post_data = $this->request->post();
	$response = ['success' => TRUE];
	if (strlen($post_data['some_user_input']) > 10) {
		$response['success'] = FALSE;
		$response['error'] = "User input must be 10 characters or less";
	}
	$this->response->body(json_encode($response));
}

// other illegal versions you may see:
$response['status'] = "success";
$response['success'] = "failure";
$response['ok'] = "1";
// et cetera
```

{{< h2 title="Type Declarations" >}}

You may optionally declare function return types, function parameter types, and class member types. If a function is not intended to return a value, declare its return type to be `void`. View [PHP's documentation for type declarations](https://www.php.net/manual/en/language.types.declarations.php).

PHP supports disjoint normal form for type declarations as of PHP 8.2 (see the [RFC](https://wiki.php.net/rfc/dnf_types) for details).

Type annotations are a form of enforcable documentation and are highly valuable. In the future, `declare(strict_types=1)` may be used, which will enforce these type hints and treat violations as errors.

```php
// good
class Thing {
	public string $fearsome_title;
	public int $power;
	public function is_powerful(): bool {
		return $this->power > 9000; 
	}
	public function say(?string $message): string {
		return ""$fearsome_title says: "" . $message ?? "hello there";
	}
}

// bad
class Thing {
	public $fearsome_title;
	public $power;
	public function is_powerful() {
		return $this->power > 9000; 
	}
	public function say($message) {
		return ""$fearsome_title says: "" . $message ?? "hello there";
	}
}
```

{{< h2 title="Boolean Zen" >}}

Do not compare boolean values to `TRUE` or `FALSE`, use the value directly (or its negation through the `!` operator) instead. Ternary expressions must not have boolean literals in either branch. If a value’s intended type is not always a boolean, strict comparisons (`===`) to `TRUE` or `FALSE` are acceptable.

```php
function good_function(int $x) {
	return $x == 3;
}

// $y could be a string (or even a falsy string). This checks
// specifically for when $y is a bool with a value of FALSE.
function acceptable_function(bool | string $y) {
	return $y === FALSE;
}

function bad_function(int $x) {
	$pointless_intermediate_value = FALSE;
	if ($x == 3) {
		$pointless_intermediate_value = TRUE;
	}
	if ($pointless_intermediate_value == FALSE) {
		return TRUE;
	} else {
		return FALSE;
	}
}
```
