# c14n

Haskell bindings for the c14n implementation in libxml (XML canonicalisation). Unfortunately there is (at the time of writing) no pure Haskell implementation, so this seems like the best option.

## Requirements

You need to have `libxml2` installed, including on macOS (with `brew install libxml2`). Then build with `stack build`. 

## Usage

The `Text.XML.C14N` module exports a function named `c14n` which provides a mid-level interface to the canonicalisation function from `libxml2`. It will handle most of the marshalling, but not much more. For example:

```haskell
> c14n [] c14n_1_1 [] False Nothing "<root>foo<!-- comment -->bar</root>" 
"<root>foobar</root>"
```

The arguments, in order, are:

* Parser options, see the module documentation or the [libxml2 documentation](http://xmlsoft.org/html/libxml-parser.html)
* The canonicalisation specification to use (`c14n_1_0`, `c14n_exclusive_1_0`, or `c14n_1_1`).
* A list of 
* A boolean value indicating whether to keep comments in the output or not.
* A thing