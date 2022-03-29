# Introduction

**KON** (Kumiko Obejct Notation) is a JSON-based file format and data interchange format. It supports very limitied data types from **python** in order to be compatible with JSON.

Similar to JSON, whitespace is allowed and ignored around or between syntactic elements (values and punctuation, but not within a str value). Four specific characters are considered whitespace for this purpose: space, horizontal tab, line feed, and carriage return.

In addition, KON defines a custom type, `ano` , to indicate what type of data the value assigned with `ano` should further be allowed to set.

# Data Types

| KON  |   python   |  JSON   |
| :--: | :--------: | :-----: |
| num  | int, float | Number  |
| str  |    str     | String  |
| bul  |    bool    | Boolean |
| lst  |    list    |  Array  |
| obj  |    dict    | Object  |
| non  |  NoneType  |  null   |
| ano  |     -      |    -    |

# Basic Unit

`key-value pair` is the basic unit of KON which is formed by a n-tuple, where n is greater than or equal to 2, of which the key is at index 0 and the value is at index 1. The rest of the elements in the tuple must be `str` and will be considered as comments.

Notice that the key can only be `str` .

For example:

```
("foo", 0, "This is a comment.", "This is another comment.")
```

# lst

`lst` is formed by a tuple, in which every element is a 2-tuple, of which the index of item is at index 0 and the item itself is at index 1.

Arranging items in order is recommended but not required.

For example:

```
(
    (0, "foo"),
    (1, "bar"),
    (2, "baz")
)
```

In addition, `(0,)` indicates an empty `lst` .

# obj

`obj` is formed by a tuple, in which every element is a `key-value pair` .

For example:

```
(
    ("foo", 0),
    ("bar", "Hello World"),
    ("baz", None)
)
```

In addition, `()` indicates an empty `obj` .

# ano

`ano` is formed by a 1-tuple, in which the element is a case-insensitive str.

Valid `ano` values:
- `("num",)`
- `("int",)` : accept integer only
- `("flt",)` : accept float only
- `("str",)`
- `("bul",)`
- `("lst",)`
- `("obj",)`
- `("non",)`
- `("ano",)`
- `("any",)` : accept any kind of types

If a value is supposed to be one of several types (for example, `num` , `str` and `lst`) in the future, use comma seperator `,` to concatenate their values as follow:

```
("num,str,lst",)
```

The order is not required and no whitespace should be in the string.
