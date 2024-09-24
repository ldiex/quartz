*UTF-8* is a variable-length character encoding standard used for electronic communication. Defined by the [[Unicode|Unicode Standard]], the name is derived from *Unicode Transformation Format – 8-bit*
# Encoding
The first 128 characters of Unicode, which correspond one-to-one with [[Data Representation#ASCII Table|ASCII]] are encoded using a single byte with the same binary value as ASCII, so that valid ASCII text is valid UTF-8-encoded Unicode as well.

| Unicode Points   | UTF-8 Encoding                                         | Bytes |
| ---------------- | ------------------------------------------------------ | ----- |
| 0000~007F        | `0xxxxxxx`                                             | 1     |
| 0080~07FF        | `110xxxxx 10xxxxxx`                                    | 2     |
| 0800~FFFF        | `1110xxxx 10xxxxxx 10xxxxxx`                           | 3     |
| 10000~1FFFFF     | `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx`                  | 4     |
| 200000~3FFFFFF   | `111110xx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx`         | 5     |
| 4000000~7FFFFFFF | `111110x 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx` | 6     |
Where `x` represents the bits of the corresponding Unicode point