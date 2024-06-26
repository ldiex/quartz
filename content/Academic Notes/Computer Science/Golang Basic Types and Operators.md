# Basic Types
`bool`, `byte (uint8)`, `int (64bit)`, `uint64`
## array
`[N]int`,`[N]bool` etc.

## slice
Dynamic Array
`[]int`,`[]bool` etc.
## bool
values: `true` or `false`

## string
A string in Golang is a collection of bytes representing a sequence of characters. Each character might be encoded using a single byte (for ASCII characters) or multiple bytes (for characters outside the ASCII range).

For example, if you define `s := "Alan"`, then the type of `s[1]` is `byte`; but if you're working with Unicode characters, especially non-ASCII ones, you might want to convert the string to a slice of runes first. For example:
``` go
r := []rune(s)
```
Then `r[1]` would give you the second Unicode code point (of type `rune`, which is an alias for `int32`).
# Basic Operators
`++`, `--` (only `i++`, no `++i`)
`>>`, `<<`
bit operator `&(and)`, `|(or)`, `^(xor)`
logical operator `&&`, `||`, `!`



