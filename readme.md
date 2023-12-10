# Lumen

Lumen is a simple user-friendly configuration format.

## Assignments

Assign values using the `key = value` format. Values can be reassigned. 
Semicolons are optional.

```lumen
key = "value"
key = 42;
```

## Keys

Keys should start with either a letter or an underscore, and then they may also
contain digits and hyphens. Lumen is case-sensitive.

```lumen
_This-Key_IsAllowed1 = true
```

Keys may be enclosed in `` ` `` and are parsed exactly like strings:

```lumen
`123` = 123
`A Key ` = "A key with spaces"
`\n` = "Newline character"
`!*&([{}++-...\`.` = true
```

## Comments

Comments start with a `#`. 

```lumen
# A comment
```

## Types

There are 6 data types:

- `int`
- `bool`
- `float`
- `string`
- `array`
- `object`

## Numbers

Positive numbers may be optionally prefixed with a plus sign. Negative numbers
are prefixed with a minus sign.

```lumen
int = +42
int = 42
int = -42

float = +0.42
float = 0.42
float = -0.42
```

Underscores between digits are allowed.

```lumen
long-number = 123456789
long-number = 123_456_789

long-number = 12345.6789
long-number = 12_345.6_789
```

Unsigned integers may also be expressed in HEX, OCT or BIN.

```lumen
hex = 0xFF
hex = 0xF_F

oct = 0o77
oct = 0o7_7

bin = 0b11
bin = 0b1_1
```

Scientific notation is supported.

```lumen
float = 314e-2
float = 0.314e+1
float = 0.314e1
```

## Booleans

Booleans can be either true or false. 

```lumen
boolean = true
boolean = false
```

## Strings

Strings are enclosed in either `"` or `'`. Escape sequences are allowed. 

```lumen
string = "This is a \t 'string'. \n"
```

Strings can last multiple lines. 

```lumen
message = "
A
Long
Message
"
```

## Arrays

Arrays are defined using `[]`. Values of different types can be used. Commas are
optional. Trailing commas are allowed.

```lumen
fruits = [ "apple", "orange" ]
fruits = [
    "apple"
    "orange",
]
```

## Objects

Objects are defined using `{}`. Commas are optional. Trailing commas are 
allowed.

```lumen
user = { name = "John", active = true }
user = {
    name = "John",
    active = true,
}
```

## Key Paths

A key path is a sequence of keys split with a `.`. 

```lumen
# This
settings.search-engine = "google"

# Is an equivalent of this
settings = {
    search-engine = "google"
}
```

```lumen
websites.`www.google.com` = true
```

Key paths are scoped when assigning values inside of an object.

```lumen
# This
user = {
    address.city = "City"
    address.street = "Street"
}

# Is the same as this
user = {
    address = { city = "City", street = "Street" }
}
```

## Referencing Previous Values

You can reference previously defined values using key paths. 

```lumen
colors.red = "#ff0000"
colors.green = "#00ff00"
colors.blue = "#0000ff"

background-color = colors.red
foreground-color = colors.green
```

When referencing values, key paths are globally scoped.

```lumen
colors.red = "#ff0000"
colors.green = "#00ff00"
colors.blue = "#0000ff"

colorscheme = {
    background = colors.red
    foreground = colors.green
}
```

## File Extensions

Lumen files should use the `.lu` file extension.
