# [Nix Language](https://nixos.org/manual/nix/unstable/language/#nix-language)

The Nix language is designed for conveniently creating and composing _derivations_ – precise descriptions of how contents of existing files are used to derive new files. It is:

- _domain-specific_
    
    It comes with [built-in functions](https://nixos.org/manual/nix/unstable/language/builtins) to integrate with the Nix store, which manages files and performs the derivations declared in the Nix language.
    
- _declarative_
    
    There is no notion of executing sequential steps. Dependencies between operations are established only through data.
    
- _pure_
    
    Values cannot change during computation. Functions always produce the same output if their input does not change.
    
- _functional_
    
    Functions are like any other value. Functions can be assigned to names, taken as arguments, or returned by functions.
    
- _lazy_
    
    Values are only computed when they are needed.
    
- _dynamically typed_
    
    Type errors are only detected when expressions are evaluated.
    

## [Overview](https://nixos.org/manual/nix/unstable/language/#overview)

This is an incomplete overview of language features, by example.

|Example|Description|
|---|---|
|_Basic values_||
|`"hello world"`|A string|
|`''   multi    line     string ''`|A multi-line string. Strips common prefixed whitespace. Evaluates to `"multi\n line\n  string"`.|
|`"hello ${ { a = "world"; }.a }"`<br><br>`"1 2 ${toString 3}"`<br><br>`"${pkgs.bash}/bin/sh"`|String interpolation (expands to `"hello world"`, `"1 2 3"`, `"/nix/store/<hash>-bash-<version>/bin/sh"`)|
|`true`, `false`|Booleans|
|`null`|Null value|
|`123`|An integer|
|`3.141`|A floating point number|
|`/etc`|An absolute path|
|`./foo.png`|A path relative to the file containing this Nix expression|
|`~/.config`|A home path. Evaluates to the `"<user's home directory>/.config"`.|
|`<nixpkgs>`|Search path for Nix files. Value determined by [`$NIX_PATH` environment variable](https://nixos.org/manual/nix/unstable/command-ref/env-common#env-NIX_PATH).|
|_Compound values_||
|`{ x = 1; y = 2; }`|A set with attributes named `x` and `y`|
|`{ foo.bar = 1; }`|A nested set, equivalent to `{ foo = { bar = 1; }; }`|
|`rec { x = "foo"; y = x + "bar"; }`|A recursive set, equivalent to `{ x = "foo"; y = "foobar"; }`|
|`[ "foo" "bar" "baz" ]`<br><br>`[ 1 2 3 ]`<br><br>`[ (f 1) { a = 1; b = 2; } [ "c" ] ]`|Lists with three elements.|
|_Operators_||
|`"foo" + "bar"`|String concatenation|
|`1 + 2`|Integer addition|
|`"foo" == "f" + "oo"`|Equality test (evaluates to `true`)|
|`"foo" != "bar"`|Inequality test (evaluates to `true`)|
|`!true`|Boolean negation|
|`{ x = 1; y = 2; }.x`|Attribute selection (evaluates to `1`)|
|`{ x = 1; y = 2; }.z or 3`|Attribute selection with default (evaluates to `3`)|
|`{ x = 1; y = 2; } // { z = 3; }`|Merge two sets (attributes in the right-hand set taking precedence)|
|_Control structures_||
|`if 1 + 1 == 2 then "yes!" else "no!"`|Conditional expression|
|`assert 1 + 1 == 2; "yes!"`|Assertion check (evaluates to `"yes!"`).|
|`let x = "foo"; y = "bar"; in x + y`|Variable definition|
|`with builtins; head [ 1 2 3 ]`|Add all attributes from the given set to the scope (evaluates to `1`)|
|_Functions (lambdas)_||
|`x: x + 1`|A function that expects an integer and returns it increased by 1|
|`x: y: x + y`|Curried function, equivalent to `x: (y: x + y)`. Can be used like a function that takes two arguments and returns their sum.|
|`(x: x + 1) 100`|A function call (evaluates to 101)|
|`let inc = x: x + 1; in inc (inc (inc 100))`|A function bound to a variable and subsequently called by name (evaluates to 103)|
|`{ x, y }: x + y`|A function that expects a set with required attributes `x` and `y` and concatenates them|
|`{ x, y ? "bar" }: x + y`|A function that expects a set with required attribute `x` and optional `y`, using `"bar"` as default value for `y`|
|`{ x, y, ... }: x + y`|A function that expects a set with required attributes `x` and `y` and ignores any other attributes|
|`{ x, y } @ args: x + y`<br><br>`args @ { x, y }: x + y`|A function that expects a set with required attributes `x` and `y`, and binds the whole set to `args`|
|_Built-in functions_||
|`import ./foo.nix`|Load and return Nix expression in given file|
|`map (x: x + x) [ 1 2 3 ]`|Apply a function to every element of a list (evaluates to `[ 2 4 6 ]`)|
# [Data Types](https://nixos.org/manual/nix/unstable/language/values#data-types)

## [Primitives](https://nixos.org/manual/nix/unstable/language/values#primitives)

- [String](https://nixos.org/manual/nix/unstable/language/values#type-string)
    
    _Strings_ can be written in three ways.
    
    The most common way is to enclose the string between double quotes, e.g., `"foo bar"`. Strings can span multiple lines. The special characters `"` and `\` and the character sequence `${` must be escaped by prefixing them with a backslash (`\`). Newlines, carriage returns and tabs can be written as `\n`, `\r` and `\t`, respectively.
    
    You can include the results of other expressions into a string by enclosing them in `${ }`, a feature known as [string interpolation](https://nixos.org/manual/nix/unstable/language/string-interpolation).
    
    The second way to write string literals is as an _indented string_, which is enclosed between pairs of _double single-quotes_, like so:
    
    ```nix
    ''   
		This is the first line.   
		This is the second line.     
		This is the third line. 
	''
    ```
    
    This kind of string literal intelligently strips indentation from the start of each line. To be precise, it strips from each line a number of spaces equal to the minimal indentation of the string as a whole (disregarding the indentation of empty lines). For instance, the first and second line are indented two spaces, while the third line is indented four spaces. Thus, two spaces are stripped from each line, so the resulting string is
    
    ```nix
    "This is the first line.\nThis is the second line.\n  This is the third line.\n"
    ```
    
    Note that the whitespace and newline following the opening `''` is ignored if there is no non-whitespace text on the initial line.
    
    Indented strings support [string interpolation](https://nixos.org/manual/nix/unstable/language/string-interpolation).
    
    Since `${` and `''` have special meaning in indented strings, you need a way to quote them. `$` can be escaped by prefixing it with `''` (that is, two single quotes), i.e., `''$`. `''` can be escaped by prefixing it with `'`, i.e., `'''`. `$` removes any special meaning from the following `$`. Linefeed, carriage-return and tab characters can be written as `''\n`, `''\r`, `''\t`, and `''\` escapes any other character.
    
    Indented strings are primarily useful in that they allow multi-line string literals to follow the indentation of the enclosing Nix expression, and that less escaping is typically necessary for strings representing languages such as shell scripts and configuration files because `''` is much less common than `"`. Example:
    
    ```nix
    stdenv.mkDerivation {   
	    ...   
	    postInstall =     
	    ''       
		    mkdir $out/bin $out/etc       
		    cp foo $out/bin       
		    echo "Hello World" > $out/etc/foo.conf       
		    ${if enableBar then "cp bar $out/bin" else ""}     
		'';   
		... 
	}
    ```
    
    Finally, as a convenience, _URIs_ as defined in appendix B of [RFC 2396](http://www.ietf.org/rfc/rfc2396.txt) can be written _as is_, without quotes. For instance, the string `"http://example.org/foo.tar.bz2"` can also be written as `http://example.org/foo.tar.bz2`.
    
- [Number](https://nixos.org/manual/nix/unstable/language/values#type-number)
    
    Numbers, which can be _integers_ (like `123`) or _floating point_ (like `123.43` or `.27e13`).
    
    See [arithmetic](https://nixos.org/manual/nix/unstable/language/operators#arithmetic) and [comparison](https://nixos.org/manual/nix/unstable/language/operators#comparison) operators for semantics.
    
- [Path](https://nixos.org/manual/nix/unstable/language/values#type-path)
    
    _Paths_, e.g., `/bin/sh` or `./builder.sh`. A path must contain at least one slash to be recognised as such. For instance, `builder.sh` is not a path: it's parsed as an expression that selects the attribute `sh` from the variable `builder`. If the file name is relative, i.e., if it does not begin with a slash, it is made absolute at parse time relative to the directory of the Nix expression that contained it. For instance, if a Nix expression in `/foo/bar/bla.nix` refers to `../xyzzy/fnord.nix`, the absolute path is `/foo/xyzzy/fnord.nix`.
    
    If the first component of a path is a `~`, it is interpreted as if the rest of the path were relative to the user's home directory. e.g. `~/foo` would be equivalent to `/home/edolstra/foo` for a user whose home directory is `/home/edolstra`.
    
    For instance, evaluating `"${./foo.txt}"` will cause `foo.txt` in the current directory to be copied into the Nix store and result in the string `"/nix/store/<hash>-foo.txt"`.
    
    Note that the Nix language assumes that all input files will remain _unchanged_ while evaluating a Nix expression. For example, assume you used a file path in an interpolated string during a `nix repl` session. Later in the same session, after having changed the file contents, evaluating the interpolated string with the file path again might not return a new [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path), since Nix might not re-read the file contents.
    
    Paths can include [string interpolation](https://nixos.org/manual/nix/unstable/language/string-interpolation) and can themselves be [interpolated in other expressions]. [interpolated in other expressions]: ./string-interpolation.md#interpolated-expressions
    
    At least one slash (`/`) must appear _before_ any interpolated expression for the result to be recognized as a path.
    
    `a.${foo}/b.${bar}` is a syntactically valid division operation. `./a.${foo}/b.${bar}` is a path.
    
    [Lookup paths](https://nixos.org/manual/nix/unstable/language/constructs/lookup-path) such as `<nixpkgs>` resolve to path values.
    
- [Boolean](https://nixos.org/manual/nix/unstable/language/values#type-boolean)
    
    _Booleans_ with values `true` and `false`.
    
- [Null](https://nixos.org/manual/nix/unstable/language/values#type-null)
    
    The null value, denoted as `null`.
    

## [List](https://nixos.org/manual/nix/unstable/language/values#list)

Lists are formed by enclosing a whitespace-separated list of values between square brackets. For example,

```nix
[ 123 ./foo.nix "abc" (f { x = y; }) ]
```

defines a list of four elements, the last being the result of a call to the function `f`. Note that function calls have to be enclosed in parentheses. If they had been omitted, e.g.,

```nix
[ 123 ./foo.nix "abc" f { x = y; } ]
```

the result would be a list of five elements, the fourth one being a function and the fifth being a set.

Note that lists are only lazy in values, and they are strict in length.

## [Attribute Set](https://nixos.org/manual/nix/unstable/language/values#attribute-set)

An attribute set is a collection of name-value-pairs (called _attributes_) enclosed in curly brackets (`{ }`).

An attribute name can be an identifier or a [string](https://nixos.org/manual/nix/unstable/language/values#string). An identifier must start with a letter (`a-z`, `A-Z`) or underscore (`_`), and can otherwise contain letters (`a-z`, `A-Z`), numbers (`0-9`), underscores (`_`), apostrophes (`'`), or dashes (`-`).

> **Syntax**
> 
> _name_ = _identifier_ | _string_  
> _identifier_ ~ `[a-zA-Z_][a-zA-Z0-9_'-]*`

Names and values are separated by an equal sign (`=`). Each value is an arbitrary expression terminated by a semicolon (`;`).

> **Syntax**
> 
> _attrset_ = `{` [ _name_ `=` _expr_ `;` ]... `}`

Attributes can appear in any order. An attribute name may only occur once.

Example:

```nix
{   x = 123;   text = "Hello";   y = f { bla = 456; }; }
```

This defines a set with attributes named `x`, `text`, `y`.

Attributes can be accessed with the [. operator](https://nixos.org/manual/nix/unstable/language/operators#attribute-selection).

Example:

```nix
{ a = "Foo"; b = "Bar"; }.a
```

This evaluates to `"Foo"`.

It is possible to provide a default value in an attribute selection using the `or` keyword.

Example:

```nix
{ a = "Foo"; b = "Bar"; }.c or "Xyzzy"`
```

```nix
{ a = "Foo"; b = "Bar"; }.c.d.e.f.g or "Xyzzy"
```

will both evaluate to `"Xyzzy"` because there is no `c` attribute in the set.

You can use arbitrary double-quoted strings as attribute names:

```nix
{ "$!@#?" = 123; }."$!@#?"
```

```nix
let bar = "bar"; in 
{ "foo ${bar}" = 123; }."foo ${bar}"
```

Both will evaluate to `123`.

Attribute names support [string interpolation](https://nixos.org/manual/nix/unstable/language/string-interpolation):

```nix
let bar = "foo"; in 
{ foo = 123; }.${bar}
```

```nix
let bar = "foo"; in 
{ ${bar} = 123; }.foo
```

Both will evaluate to `123`.

In the special case where an attribute name inside of a set declaration evaluates to `null` (which is normally an error, as `null` cannot be coerced to a string), that attribute is simply not added to the set:

```nix
{ ${if foo then "bar" else null} = true; }
```

This will evaluate to `{}` if `foo` evaluates to `false`.

A set that has a `__functor` attribute whose value is callable (i.e. is itself a function or a set with a `__functor` attribute whose value is callable) can be applied as if it were a function, with the set itself passed in first , e.g.,

```nix
let add = { __functor = self: x: x + self.x; };     
	inc = add // { x = 1; }; 
in inc 1
```

evaluates to `2`. This can be used to attach metadata to a function without the caller needing to treat it specially, or to implement a form of object-oriented programming, for example.

# [Language Constructs](https://nixos.org/manual/nix/unstable/language/constructs#language-constructs)

## [Recursive sets](https://nixos.org/manual/nix/unstable/language/constructs#recursive-sets)

Recursive sets are like normal [attribute sets](https://nixos.org/manual/nix/unstable/language/values#attribute-set), but the attributes can refer to each other.

> _rec-attrset_ = `rec { [ _name_ = _expr_ ; ]... }`

Example:

```nix
rec {   
	x = y;   
	y = 123; 
}.x
```

This evaluates to `123`.

Note that without `rec` the binding `x = y;` would refer to the variable `y` in the surrounding scope, if one exists, and would be invalid if no such variable exists. That is, in a normal (non-recursive) set, attributes are not added to the lexical scope; in a recursive set, they are.

Recursive sets of course introduce the danger of infinite recursion. For example, the expression

```nix
rec {   
	x = y;   
	y = x; 
}.x
```

will crash with an `infinite recursion encountered` error message.

## [Let-expressions](https://nixos.org/manual/nix/unstable/language/constructs#let-expressions)

A let-expression allows you to define local variables for an expression.

> _let-in_ = `let` [ _identifier_ = _expr_ ]... `in` _expr_

Example:

```nix
let   
	x = "foo";   
	y = "bar"; 
in x + y
```

This evaluates to `"foobar"`.

## [Inheriting attributes](https://nixos.org/manual/nix/unstable/language/constructs#inheriting-attributes)

When defining an [attribute set](https://nixos.org/manual/nix/unstable/language/values#attribute-set) or in a [let-expression](https://nixos.org/manual/nix/unstable/language/constructs#let-expressions) it is often convenient to copy variables from the surrounding lexical scope (e.g., when you want to propagate attributes). This can be shortened using the `inherit` keyword.

Example:

```nix
let x = 123; 
in {   
	inherit x;   
	y = 456; 
}
```

is equivalent to

```nix
let x = 123; 
in {   
	x = x;   
	y = 456; 
}
```

and both evaluate to `{ x = 123; y = 456; }`.

> **Note**
> 
> This works because `x` is added to the lexical scope by the `let` construct.

It is also possible to inherit attributes from another attribute set.

Example:

In this fragment from `all-packages.nix`,

```nix
graphviz = (import ../tools/graphics/graphviz) {   
	inherit fetchurl stdenv libpng libjpeg expat x11 yacc;   
	inherit (xorg) libXaw; 
};  
	
xorg = {   
	libX11 = ...;   
	libXaw = ...;   
	... 
}  
	
libpng = ...; 
libjpg = ...; 
...
```

the set used in the function call to the function defined in `../tools/graphics/graphviz` inherits a number of variables from the surrounding scope (`fetchurl` ... `yacc`), but also inherits `libXaw` (the X Athena Widgets) from the `xorg` set.

Summarizing the fragment

```nix
... 
inherit x y z; 
inherit (src-set) a b c; 
...
```
is equivalent to

```nix
... 
x = x; y = y; z = z; 
a = src-set.a; b = src-set.b; c = src-set.c; 
...
```

when used while defining local variables in a let-expression or while defining a set.

## [Functions](https://nixos.org/manual/nix/unstable/language/constructs#functions)

Functions have the following form:

```nix
pattern: body
```

The pattern specifies what the argument of the function must look like, and binds variables in the body to (parts of) the argument. There are three kinds of patterns:

- If a pattern is a single identifier, then the function matches any argument. Example:
    
    ```nix
    let negate = x: !x;     
	    concat = x: y: x + y; 
    in if negate true then concat "foo" "bar" else ""
    ```
    
    Note that `concat` is a function that takes one argument and returns a function that takes another argument. This allows partial parameterisation (i.e., only filling some of the arguments of a function); e.g.,
    
    ```nix
    map (concat "foo") [ "bar" "bla" "abc" ]
    ```
    
    evaluates to `[ "foobar" "foobla" "fooabc" ]`.
    
- A _set pattern_ of the form `{ name1, name2, …, nameN }` matches a set containing the listed attributes, and binds the values of those attributes to variables in the function body. For example, the function
    
    ```nix
    { x, y, z }: z + y + x
    ```
    
    can only be called with a set containing exactly the attributes `x`, `y` and `z`. No other attributes are allowed. If you want to allow additional arguments, you can use an ellipsis (`...`):
    
    ```nix
    { x, y, z, ... }: z + y + x
    ```
    
    This works on any set that contains at least the three named attributes.
    
    It is possible to provide _default values_ for attributes, in which case they are allowed to be missing. A default value is specified by writing `name ? e`, where _e_ is an arbitrary expression. For example,
    
    ```nix
    { x, y ? "foo", z ? "bar" }: z + y + x
    ```
    
    specifies a function that only requires an attribute named `x`, but optionally accepts `y` and `z`.
    
- An `@`-pattern provides a means of referring to the whole value being matched:
    
    ```nix
    args@{ x, y, z, ... }: z + y + x + args.a
    ```
    
    but can also be written as:
    
    ```nix
    { x, y, z, ... } @ args: z + y + x + args.a
    ```
    
    Here `args` is bound to the argument _as passed_, which is further matched against the pattern `{ x, y, z, ... }`. The `@`-pattern makes mainly sense with an ellipsis(`...`) as you can access attribute names as `a`, using `args.a`, which was given as an additional attribute to the function.
    
    > **Warning**
    > 
    > `args@` binds the name `args` to the attribute set that is passed to the function. In particular, `args` does _not_ include any default values specified with `?` in the function's set pattern.
    > 
    > For instance
    > 
    > `let   f = args@{ a ? 23, ... }: [ a args ]; in   f {}`
    > 
    > is equivalent to
    > 
    > `let   f = args @ { ... }: [ (args.a or 23) args ]; in   f {}`
    > 
    > and both expressions will evaluate to:
    > 
    > `[ 23 {} ]`
    

Note that functions do not have names. If you want to give them a name, you can bind them to an attribute, e.g.,

```nix
let concat = { x, y }: x + y; 
in concat { x = "foo"; y = "bar"; }
```

## [Conditionals](https://nixos.org/manual/nix/unstable/language/constructs#conditionals)

Conditionals look like this:

```nix
if e1 then e2 else e3
```

where _e1_ is an expression that should evaluate to a Boolean value (`true` or `false`).

## [Assertions](https://nixos.org/manual/nix/unstable/language/constructs#assertions)

Assertions are generally used to check that certain requirements on or between features and dependencies hold. They look like this:

```nix
assert e1; e2
```

where _e1_ is an expression that should evaluate to a Boolean value. If it evaluates to `true`, _e2_ is returned; otherwise expression evaluation is aborted and a backtrace is printed.

Here is a Nix expression for the Subversion package that shows how assertions can be used:.

```nix
{ localServer ? false 
, httpServer ? false 
, sslSupport ? false 
, pythonBindings ? false 
, javaSwigBindings ? false 
, javahlBindings ? false 
, stdenv, fetchurl 
, openssl ? null, httpd ? null, db4 ? null, expat, swig ? null, j2sdk ? null }:

assert localServer -> db4 != null; ① 
assert httpServer -> httpd != null && httpd.expat == expat; ② 
assert sslSupport -> openssl != null && (httpServer -> httpd.openssl == openssl); ③ 
assert pythonBindings -> swig != null && swig.pythonSupport; 
assert javaSwigBindings -> swig != null && swig.javaSupport; 
assert javahlBindings -> j2sdk != null;  

stdenv.mkDerivation {   
	name = "subversion-1.1.1";   
	...   
	openssl = if sslSupport then openssl else null; ④   
	... 
}
```

The points of interest are:

1. This assertion states that if Subversion is to have support for local repositories, then Berkeley DB is needed. So if the Subversion function is called with the `localServer` argument set to `true` but the `db4` argument set to `null`, then the evaluation fails.
    
    Note that `->` is the [logical implication](https://en.wikipedia.org/wiki/Truth_table#Logical_implication) Boolean operation.
    
2. This is a more subtle condition: if Subversion is built with Apache (`httpServer`) support, then the Expat library (an XML library) used by Subversion should be same as the one used by Apache. This is because in this configuration Subversion code ends up being linked with Apache code, and if the Expat libraries do not match, a build- or runtime link error or incompatibility might occur.
    
3. This assertion says that in order for Subversion to have SSL support (so that it can access `https` URLs), an OpenSSL library must be passed. Additionally, it says that _if_ Apache support is enabled, then Apache's OpenSSL should match Subversion's. (Note that if Apache support is not enabled, we don't care about Apache's OpenSSL.)
    
4. The conditional here is not really related to assertions, but is worth pointing out: it ensures that if SSL support is disabled, then the Subversion derivation is not dependent on OpenSSL, even if a non-`null` value was passed. This prevents an unnecessary rebuild of Subversion if OpenSSL changes.
    

## [With-expressions](https://nixos.org/manual/nix/unstable/language/constructs#with-expressions)

A _with-expression_,

```nix
with e1; e2
```

introduces the set _e1_ into the lexical scope of the expression _e2_. For instance,

```nix
let as = { x = "foo"; y = "bar"; }; 
in with as; x + y
```

evaluates to `"foobar"` since the `with` adds the `x` and `y` attributes of `as` to the lexical scope in the expression `x + y`. The most common use of `with` is in conjunction with the `import` function. E.g.,

```nix
with (import ./definitions.nix); ...
```

makes all attributes defined in the file `definitions.nix` available as if they were defined locally in a `let`-expression.

The bindings introduced by `with` do not shadow bindings introduced by other means, e.g.

```nix
let a = 3; in with { a = 1; }; let a = 4; in with { a = 2; }; ...
```

establishes the same scope as

```nix
let a = 1; in let a = 2; in let a = 3; in let a = 4; in ...
```

## [Comments](https://nixos.org/manual/nix/unstable/language/constructs#comments)

Comments can be single-line, started with a `#` character, or inline/multi-line, enclosed within `/* ... */`.

## [String interpolation](https://nixos.org/manual/nix/unstable/language/string-interpolation#string-interpolation)

String interpolation is a language feature where a [string](https://nixos.org/manual/nix/unstable/language/values#type-string), [path](https://nixos.org/manual/nix/unstable/language/values#type-path), or [attribute name](https://nixos.org/manual/nix/unstable/language/values#attribute-set) can contain expressions enclosed in `${ }` (dollar-sign with curly brackets).

Such a construct is called _interpolated string_, and the expression inside is an [interpolated expression](https://nixos.org/manual/nix/unstable/language/string-interpolation#interpolated-expression).

### [Examples](https://nixos.org/manual/nix/unstable/language/string-interpolation#examples)

#### [String](https://nixos.org/manual/nix/unstable/language/string-interpolation#string)

Rather than writing

```nix
"--with-freetype2-library=" + freetype + "/lib"
```

(where `freetype` is a [derivation]), you can instead write

```nix
"--with-freetype2-library=${freetype}/lib"
```

The latter is automatically translated to the former.

A more complicated example (from the Nix expression for [Qt](http://www.trolltech.com/products/qt)):

```nix
configureFlags = "   
	-system-zlib -system-libpng -system-libjpeg   
	${if openglSupport then "-dlopen-opengl     
		-L${mesa}/lib -I${mesa}/include     
		-L${libXmu}/lib -I${libXmu}/include" else ""}   
	${if threadSupport then "-thread" else "-no-thread"} 
";
```

Note that Nix expressions and strings can be arbitrarily nested; in this case the outer string contains various interpolated expressions that themselves contain strings (e.g., `"-thread"`), some of which in turn contain interpolated expressions (e.g., `${mesa}`).

#### [Path](https://nixos.org/manual/nix/unstable/language/string-interpolation#path)

Rather than writing

```nix
./. + "/" + foo + "-" + bar + ".nix"
```

or

```nix
./. + "/${foo}-${bar}.nix"
```

you can instead write

```nix
./${foo}-${bar}.nix
```

#### [Attribute name](https://nixos.org/manual/nix/unstable/language/string-interpolation#attribute-name)

Attribute names can be interpolated strings.

> **Example**
> 
> `let name = "foo"; in { ${name} = 123; }`
> 
> `{ foo = 123; }`

Attributes can be selected with interpolated strings.

> **Example**
> 
> `let name = "foo"; in { foo = 123; }.${name}`
> 
> `123`

## [Interpolated expression](https://nixos.org/manual/nix/unstable/language/string-interpolation#interpolated-expression)

An expression that is interpolated must evaluate to one of the following:

- a [string](https://nixos.org/manual/nix/unstable/language/values#type-string)
    
- a [path](https://nixos.org/manual/nix/unstable/language/values#type-path)
    
- an [attribute set](https://nixos.org/manual/nix/unstable/language/values#attribute-set) that has a `__toString` attribute or an `outPath` attribute
    
    - `__toString` must be a function that takes the attribute set itself and returns a string
    - `outPath` must be a string
    
    This includes [derivations](https://nixos.org/manual/nix/unstable/language/derivations) or [flake inputs](https://nixos.org/manual/nix/unstable/command-ref/new-cli/nix3-flake#flake-inputs) (experimental).
    

A string interpolates to itself.

A path in an interpolated expression is first copied into the Nix store, and the resulting string is the [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) of the newly created [store object](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object).

> **Example**
> 
> `$ mkdir foo`
> 
> Reference the empty directory in an interpolated expression:
> 
> `"${./foo}"`
> 
> `"/nix/store/2hhl2nz5v0khbn06ys82nrk99aa1xxdw-foo"`

A derivation interpolates to the [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) of its first [output](https://nixos.org/manual/nix/unstable/language/derivations#attr-outputs).

> **Example**
> 
> `let   pkgs = import <nixpkgs> {}; in "${pkgs.hello}"`
> 
> `"/nix/store/4xpfqf29z4m8vbhrqcz064wfmb46w5r7-hello-2.12.1"`

An attribute set interpolates to the return value of the function in the `__toString` applied to the attribute set itself.

> **Example**
> 
> `let   a = {     value = 1;     __toString = self: toString (self.value + 1);   }; in "${a}"`
> 
> `"2"`

An attribute set also interpolates to the value of its `outPath` attribute.

> **Example**
> 
> `let   a = { outPath = "foo"; }; in "${a}"`
> 
> `"foo"`

If both `__toString` and `outPath` are present in an attribute set, `__toString` takes precedence.

> **Example**
> 
> `let   a = { __toString = _: "yes"; outPath = throw "no"; }; in "${a}"`
> 
> `"yes"`

If neither is present, an error is thrown.

> **Example**
> 
> `let   a = {}; in "${a}"`
> 
> `error: cannot coerce a set to a string         at «string»:4:2:              3| in             4| "${a}"              |  ^`
## [Lookup path](https://nixos.org/manual/nix/unstable/language/constructs/lookup-path#lookup-path)

> **Syntax**
> 
> _lookup-path_ = `<` _identifier_ [ `/` _identifier_ ]... `>`

A lookup path is an identifier with an optional path suffix that resolves to a [path value](https://nixos.org/manual/nix/unstable/language/values#type-path) if the identifier matches a search path entry.

The value of a lookup path is determined by [`builtins.nixPath`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-nixPath).

See [`builtins.findFile`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-findFile) for details on lookup path resolution.

> **Example**
> 
> `<nixpkgs>`
> 
> `/nix/var/nix/profiles/per-user/root/channels/nixpkgs`

> **Example**
> 
> `<nixpkgs/nixos>`
> 
> `/nix/var/nix/profiles/per-user/root/channels/nixpkgs/nixos`
# [Operators](https://nixos.org/manual/nix/unstable/language/operators#operators)

|Name|Syntax|Associativity|Precedence|
|---|---|---|---|
|[Attribute selection](https://nixos.org/manual/nix/unstable/language/operators#attribute-selection)|_attrset_ `.` _attrpath_ [ `or` _expr_ ]|none|1|
|Function application|_func_ _expr_|left|2|
|[Arithmetic negation](https://nixos.org/manual/nix/unstable/language/operators#arithmetic)|`-` _number_|none|3|
|[Has attribute](https://nixos.org/manual/nix/unstable/language/operators#has-attribute)|_attrset_ `?` _attrpath_|none|4|
|List concatenation|_list_ `++` _list_|right|5|
|[Multiplication](https://nixos.org/manual/nix/unstable/language/operators#arithmetic)|_number_ `*` _number_|left|6|
|[Division](https://nixos.org/manual/nix/unstable/language/operators#arithmetic)|_number_ `/` _number_|left|6|
|[Subtraction](https://nixos.org/manual/nix/unstable/language/operators#arithmetic)|_number_ `-` _number_|left|7|
|[Addition](https://nixos.org/manual/nix/unstable/language/operators#arithmetic)|_number_ `+` _number_|left|7|
|[String concatenation](https://nixos.org/manual/nix/unstable/language/operators#string-concatenation)|_string_ `+` _string_|left|7|
|[Path concatenation](https://nixos.org/manual/nix/unstable/language/operators#path-concatenation)|_path_ `+` _path_|left|7|
|[Path and string concatenation](https://nixos.org/manual/nix/unstable/language/operators#path-and-string-concatenation)|_path_ `+` _string_|left|7|
|[String and path concatenation](https://nixos.org/manual/nix/unstable/language/operators#string-and-path-concatenation)|_string_ `+` _path_|left|7|
|Logical negation (`NOT`)|`!` _bool_|none|8|
|[Update](https://nixos.org/manual/nix/unstable/language/operators#update)|_attrset_ `//` _attrset_|right|9|
|[Less than](https://nixos.org/manual/nix/unstable/language/operators#comparison-operators)|_expr_ `<` _expr_|none|10|
|[Less than or equal to](https://nixos.org/manual/nix/unstable/language/operators#comparison-operators)|_expr_ `<=` _expr_|none|10|
|[Greater than](https://nixos.org/manual/nix/unstable/language/operators#comparison-operators)|_expr_ `>` _expr_|none|10|
|[Greater than or equal to](https://nixos.org/manual/nix/unstable/language/operators#comparison-operators)|_expr_ `>=` _expr_|none|10|
|[Equality](https://nixos.org/manual/nix/unstable/language/operators#equality)|_expr_ `==` _expr_|none|11|
|Inequality|_expr_ `!=` _expr_|none|11|
|Logical conjunction (`AND`)|_bool_ `&&` _bool_|left|12|
|Logical disjunction (`OR`)|_bool_ `\|` _bool_|left|13|
|[Logical implication](https://nixos.org/manual/nix/unstable/language/operators#logical-implication)|_bool_ `->` _bool_|none|14|

## [Attribute selection](https://nixos.org/manual/nix/unstable/language/operators#attribute-selection)

> **Syntax**
> 
> _attrset_ `.` _attrpath_ [ `or` _expr_ ]

Select the attribute denoted by attribute path _attrpath_ from [attribute set](https://nixos.org/manual/nix/unstable/language/values#attribute-set) _attrset_. If the attribute doesn’t exist, return the _expr_ after `or` if provided, otherwise abort evaluation.

An attribute path is a dot-separated list of [attribute names](https://nixos.org/manual/nix/unstable/language/values#attribute-set).

> **Syntax**
> 
> _attrpath_ = _name_ [ `.` _name_ ]...

## [Has attribute](https://nixos.org/manual/nix/unstable/language/operators#has-attribute)

> **Syntax**
> 
> _attrset_ `?` _attrpath_

Test whether [attribute set](https://nixos.org/manual/nix/unstable/language/values#attribute-set) _attrset_ contains the attribute denoted by _attrpath_. The result is a [Boolean](https://nixos.org/manual/nix/unstable/language/values#type-boolean) value.

## [Arithmetic](https://nixos.org/manual/nix/unstable/language/operators#arithmetic)

Numbers are type-compatible: Pure integer operations will always return integers, whereas any operation involving at least one floating point number return a floating point number.

See also [Comparison](https://nixos.org/manual/nix/unstable/language/operators#comparison-operators) and [Equality](https://nixos.org/manual/nix/unstable/language/operators#equality).

The `+` operator is overloaded to also work on strings and paths.

## [String concatenation](https://nixos.org/manual/nix/unstable/language/operators#string-concatenation)

> **Syntax**
> 
> _string_ `+` _string_

Concatenate two [string](https://nixos.org/manual/nix/unstable/language/values#type-string)s and merge their string contexts.

## [Path concatenation](https://nixos.org/manual/nix/unstable/language/operators#path-concatenation)

> **Syntax**
> 
> _path_ `+` _path_

Concatenate two [path](https://nixos.org/manual/nix/unstable/language/values#type-path)s. The result is a path.

## [Path and string concatenation](https://nixos.org/manual/nix/unstable/language/operators#path-and-string-concatenation)

> **Syntax**
> 
> _path_ + _string_

Concatenate _[path](https://nixos.org/manual/nix/unstable/language/values#type-path)_ with _[string](https://nixos.org/manual/nix/unstable/language/values#type-string)_. The result is a path.

> **Note**
> 
> The string must not have a string context that refers to a [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path).

## [String and path concatenation](https://nixos.org/manual/nix/unstable/language/operators#string-and-path-concatenation)

> **Syntax**
> 
> _string_ + _path_

Concatenate _[string](https://nixos.org/manual/nix/unstable/language/values#type-string)_ with _[path](https://nixos.org/manual/nix/unstable/language/values#type-path)_. The result is a string.

> **Important**
> 
> The file or directory at _path_ must exist and is copied to the [store](https://nixos.org/manual/nix/unstable/glossary#gloss-store). The path appears in the result as the corresponding [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path).

## [Update](https://nixos.org/manual/nix/unstable/language/operators#update)

> **Syntax**
> 
> _attrset1_ // _attrset2_

Update [attribute set](https://nixos.org/manual/nix/unstable/language/values#attribute-set) _attrset1_ with names and values from _attrset2_.

The returned attribute set will have of all the attributes in _attrset1_ and _attrset2_. If an attribute name is present in both, the attribute value from the latter is taken.

## [Comparison](https://nixos.org/manual/nix/unstable/language/operators#comparison)

Comparison is

- [arithmetic](https://nixos.org/manual/nix/unstable/language/operators#arithmetic) for [number](https://nixos.org/manual/nix/unstable/language/values#type-number)s
- lexicographic for [string](https://nixos.org/manual/nix/unstable/language/values#type-string)s and [path](https://nixos.org/manual/nix/unstable/language/values#type-path)s
- item-wise lexicographic for [list](https://nixos.org/manual/nix/unstable/language/values#list)s: elements at the same index in both lists are compared according to their type and skipped if they are equal.

All comparison operators are implemented in terms of `<`, and the following equivalencies hold:

|comparison|implementation|
|---|---|
|_a_ `<=` _b_|`! (` _b_ `<` _a_ `)`|
|_a_ `>` _b_|_b_ `<` _a_|
|_a_ `>=` _b_|`! (` _a_ `<` _b_ `)`|

## [Equality](https://nixos.org/manual/nix/unstable/language/operators#equality)

- [Attribute sets](https://nixos.org/manual/nix/unstable/language/values#attribute-set) and [list](https://nixos.org/manual/nix/unstable/language/values#list)s are compared recursively, and therefore are fully evaluated.
- Comparison of [function](https://nixos.org/manual/nix/unstable/language/constructs#functions)s always returns `false`.
- Numbers are type-compatible, see [arithmetic](https://nixos.org/manual/nix/unstable/language/operators#arithmetic) operators.
- Floating point numbers only differ up to a limited precision.

## [Logical implication](https://nixos.org/manual/nix/unstable/language/operators#logical-implication)

Equivalent to `!`_b1_ `||` _b2_.
# [Derivations](https://nixos.org/manual/nix/unstable/language/derivations#derivations)

The most important built-in function is `derivation`, which is used to describe a single derivation: a specification for running an executable on precisely defined input files to repeatably produce output files at uniquely determined file system paths.

It takes as input an attribute set, the attributes of which specify the inputs to the process. It outputs an attribute set, and produces a [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation) as a side effect of evaluation.

## [Input attributes](https://nixos.org/manual/nix/unstable/language/derivations#input-attributes)

### [Required](https://nixos.org/manual/nix/unstable/language/derivations#required)

- [`name`](https://nixos.org/manual/nix/unstable/language/derivations#attr-name) ([String](https://nixos.org/manual/nix/unstable/language/values#type-string))
    
    A symbolic name for the derivation. It is added to the [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)'s [path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) and its [output paths](https://nixos.org/manual/nix/unstable/glossary#gloss-output-path).
    
    Example: `name = "hello";`
    
    The store derivation's path will be `/nix/store/<hash>-hello.drv`, and the output paths will be of the form `/nix/store/<hash>-hello[-<output>]`
    
- [`system`](https://nixos.org/manual/nix/unstable/language/derivations#attr-system) ([String](https://nixos.org/manual/nix/unstable/language/values#type-string))
    
    The system type on which the [`builder`](https://nixos.org/manual/nix/unstable/language/derivations#attr-builder) executable is meant to be run.
    
    A necessary condition for Nix to build derivations locally is that the `system` attribute matches the current [`system` configuration option](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-system). It can automatically [build on other platforms](https://nixos.org/manual/nix/unstable/advanced-topics/distributed-builds) by forwarding build requests to other machines.
    
    Examples:
    
    `system = "x86_64-linux";`
    
    `system = builtins.currentSystem;`
    
    [`builtins.currentSystem`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-currentSystem) has the value of the [`system` configuration option](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-system), and defaults to the system type of the current Nix installation.
    
- [`builder`](https://nixos.org/manual/nix/unstable/language/derivations#attr-builder) ([Path](https://nixos.org/manual/nix/unstable/language/values#type-path) | [String](https://nixos.org/manual/nix/unstable/language/values#type-string))
    
    Path to an executable that will perform the build.
    
    Examples:
    
    `builder = "/bin/bash";`
    
    `builder = ./builder.sh;`
    
    `builder = "${pkgs.python}/bin/python";`
    

### [Optional](https://nixos.org/manual/nix/unstable/language/derivations#optional)

- [`args`](https://nixos.org/manual/nix/unstable/language/derivations#attr-args) ([List](https://nixos.org/manual/nix/unstable/language/values#list) of [String](https://nixos.org/manual/nix/unstable/language/values#type-string)) Default: `[ ]`
    
    Command-line arguments to be passed to the [`builder`](https://nixos.org/manual/nix/unstable/language/derivations#attr-builder) executable.
    
    Example: `args = [ "-c" "echo hello world > $out" ];`
    
- [`outputs`](https://nixos.org/manual/nix/unstable/language/derivations#attr-outputs) ([List](https://nixos.org/manual/nix/unstable/language/values#list) of [String](https://nixos.org/manual/nix/unstable/language/values#type-string)) Default: `[ "out" ]`
    
    Symbolic outputs of the derivation. Each output name is passed to the [`builder`](https://nixos.org/manual/nix/unstable/language/derivations#attr-builder) executable as an environment variable with its value set to the corresponding [output path](https://nixos.org/manual/nix/unstable/glossary#gloss-output-path).
    
    By default, a derivation produces a single output path called `out`. However, derivations can produce multiple output paths. This allows the associated [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object) and their [closures](https://nixos.org/manual/nix/unstable/glossary#gloss-closure) to be copied or garbage-collected separately.
    
    Examples:
    
    Imagine a library package that provides a dynamic library, header files, and documentation. A program that links against such a library doesn’t need the header files and documentation at runtime, and it doesn’t need the documentation at build time. Thus, the library package could specify:
    
    ```nix
    derivation {   
	    # ...   
	    outputs = [ "lib" "dev" "doc" ];   
	    # ... 
	}
    ```
    
    This will cause Nix to pass environment variables `lib`, `dev`, and `doc` to the builder containing the intended store paths of each output. The builder would typically do something like
    
    ```nix
    ./configure \   
    --libdir=$lib/lib \   
    --includedir=$dev/include \   
    --docdir=$doc/share/doc
    ```
    
    for an Autoconf-style package.
    
    You can refer to each output of a derivation by selecting it as an attribute, e.g. `myPackage.lib` or `myPackage.doc`.
    
    The first element of `outputs` determines the _default output_. Therefore, in the given example, `myPackage` is equivalent to `myPackage.lib`.
    
- See [Advanced Attributes](https://nixos.org/manual/nix/unstable/language/advanced-attributes) for more, infrequently used, optional attributes.
    
- Every other attribute is passed as an environment variable to the builder. Attribute values are translated to environment variables as follows:
    
    - Strings are passed unchanged.
        
    - Integral numbers are converted to decimal notation.
        
    - Floating point numbers are converted to simple decimal or scientific notation with a preset precision.
        
    - A _path_ (e.g., `../foo/sources.tar`) causes the referenced file to be copied to the store; its location in the store is put in the environment variable. The idea is that all sources should reside in the Nix store, since all inputs to a derivation should reside in the Nix store.
        
    - A _derivation_ causes that derivation to be built prior to the present derivation; its default output path is put in the environment variable.
        
    - Lists of the previous types are also allowed. They are simply concatenated, separated by spaces.
        
    - `true` is passed as the string `1`, `false` and `null` are passed as an empty string.
        

## [Builder execution](https://nixos.org/manual/nix/unstable/language/derivations#builder-execution)

The [`builder`](https://nixos.org/manual/nix/unstable/language/derivations#attr-builder) is executed as follows:

- A temporary directory is created under the directory specified by `TMPDIR` (default `/tmp`) where the build will take place. The current directory is changed to this directory.
    
- The environment is cleared and set to the derivation attributes, as specified above.
    
- In addition, the following variables are set:
    
    - `NIX_BUILD_TOP` contains the path of the temporary directory for this build.
        
    - Also, `TMPDIR`, `TEMPDIR`, `TMP`, `TEMP` are set to point to the temporary directory. This is to prevent the builder from accidentally writing temporary files anywhere else. Doing so might cause interference by other processes.
        
    - `PATH` is set to `/path-not-set` to prevent shells from initialising it to their built-in default value.
        
    - `HOME` is set to `/homeless-shelter` to prevent programs from using `/etc/passwd` or the like to find the user's home directory, which could cause impurity. Usually, when `HOME` is set, it is used as the location of the home directory, even if it points to a non-existent path.
        
    - `NIX_STORE` is set to the path of the top-level Nix store directory (typically, `/nix/store`).
        
    - `NIX_ATTRS_JSON_FILE` & `NIX_ATTRS_SH_FILE` if `__structuredAttrs` is set to `true` for the dervation. A detailed explanation of this behavior can be found in the [section about structured attrs](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-structuredAttrs).
        
    - For each output declared in `outputs`, the corresponding environment variable is set to point to the intended path in the Nix store for that output. Each output path is a concatenation of the cryptographic hash of all build inputs, the `name` attribute and the output name. (The output name is omitted if it’s `out`.)
        
- If an output path already exists, it is removed. Also, locks are acquired to prevent multiple Nix instances from performing the same build at the same time.
    
- A log of the combined standard output and error is written to `/nix/var/log/nix`.
    
- The builder is executed with the arguments specified by the attribute `args`. If it exits with exit code 0, it is considered to have succeeded.
    
- The temporary directory is removed (unless the `-K` option was specified).
    
- If the build was successful, Nix scans each output path for references to input paths by looking for the hash parts of the input paths. Since these are potential runtime dependencies, Nix registers them as dependencies of the output paths.
    
- After the build, Nix sets the last-modified timestamp on all files in the build result to 1 (00:00:01 1/1/1970 UTC), sets the group to the default group, and sets the mode of the file to 0444 or 0555 (i.e., read-only, with execute permission enabled if the file was originally executable). Note that possible `setuid` and `setgid` bits are cleared. Setuid and setgid programs are not currently supported by Nix. This is because the Nix archives used in deployment have no concept of ownership information, and because it makes the build result dependent on the user performing the build.
## [Advanced Attributes](https://nixos.org/manual/nix/unstable/language/advanced-attributes#advanced-attributes)

Derivations can declare some infrequently used optional attributes.

- [`allowedReferences`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-allowedReferences)  
    The optional attribute `allowedReferences` specifies a list of legal references (dependencies) of the output of the builder. For example,
    
    ```nix
    allowedReferences = [];
    ```
    
    enforces that the output of a derivation cannot have any runtime dependencies on its inputs. To allow an output to have a runtime dependency on itself, use `"out"` as a list item. This is used in NixOS to check that generated files such as initial ramdisks for booting Linux don’t have accidental dependencies on other paths in the Nix store.
    
- [`allowedRequisites`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-allowedRequisites)  
    This attribute is similar to `allowedReferences`, but it specifies the legal requisites of the whole closure, so all the dependencies recursively. For example,
    
    ```nix
    allowedRequisites = [ foobar ];
    ```
    
    enforces that the output of a derivation cannot have any other runtime dependency than `foobar`, and in addition it enforces that `foobar` itself doesn't introduce any other dependency itself.
    
- [`disallowedReferences`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-disallowedReferences)  
    The optional attribute `disallowedReferences` specifies a list of illegal references (dependencies) of the output of the builder. For example,
    
    ```nix
    disallowedReferences = [ foo ];
    ```
    
    enforces that the output of a derivation cannot have a direct runtime dependencies on the derivation `foo`.
    
- [`disallowedRequisites`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-disallowedRequisites)  
    This attribute is similar to `disallowedReferences`, but it specifies illegal requisites for the whole closure, so all the dependencies recursively. For example,
    
    ```nix
    disallowedRequisites = [ foobar ];
    ```
    
    enforces that the output of a derivation cannot have any runtime dependency on `foobar` or any other derivation depending recursively on `foobar`.
    
- [`exportReferencesGraph`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-exportReferencesGraph)  
    This attribute allows builders access to the references graph of their inputs. The attribute is a list of inputs in the Nix store whose references graph the builder needs to know. The value of this attribute should be a list of pairs `[ name1 path1 name2 path2 ... ]`. The references graph of each _pathN_ will be stored in a text file _nameN_ in the temporary build directory. The text files have the format used by `nix-store --register-validity` (with the deriver fields left empty). For example, when the following derivation is built:
    
    ```nix
    derivation {   
	    ...   
	    exportReferencesGraph = [ "libfoo-graph" libfoo ]; 
	};
    ```
    
    the references graph of `libfoo` is placed in the file `libfoo-graph` in the temporary build directory.
    
    `exportReferencesGraph` is useful for builders that want to do something with the closure of a store path. Examples include the builders in NixOS that generate the initial ramdisk for booting Linux (a `cpio` archive containing the closure of the boot script) and the ISO-9660 image for the installation CD (which is populated with a Nix store containing the closure of a bootable NixOS configuration).
    
- [`impureEnvVars`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-impureEnvVars)  
    This attribute allows you to specify a list of environment variables that should be passed from the environment of the calling user to the builder. Usually, the environment is cleared completely when the builder is executed, but with this attribute you can allow specific environment variables to be passed unmodified. For example, `fetchurl` in Nixpkgs has the line
    
    ```nix
    impureEnvVars = [ "http_proxy" "https_proxy" ... ];
    ```
    
    to make it use the proxy server configuration specified by the user in the environment variables `http_proxy` and friends.
    
    This attribute is only allowed in _fixed-output derivations_ (see below), where impurities such as these are okay since (the hash of) the output is known in advance. It is ignored for all other derivations.
    
    > **Warning**
    > 
    > `impureEnvVars` implementation takes environment variables from the current builder process. When a daemon is building its environmental variables are used. Without the daemon, the environmental variables come from the environment of the `nix-build`.
    
    If the [`configurable-impure-env` experimental feature](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-configurable-impure-env) is enabled, these environment variables can also be controlled through the [`impure-env`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-impure-env) configuration setting.
    
- [`outputHash`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputHash); [`outputHashAlgo`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputHashAlgo); [`outputHashMode`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputHashMode)  
    These attributes declare that the derivation is a so-called _fixed-output derivation_, which means that a cryptographic hash of the output is already known in advance. When the build of a fixed-output derivation finishes, Nix computes the cryptographic hash of the output and compares it to the hash declared with these attributes. If there is a mismatch, the build fails.
    
    The rationale for fixed-output derivations is derivations such as those produced by the `fetchurl` function. This function downloads a file from a given URL. To ensure that the downloaded file has not been modified, the caller must also specify a cryptographic hash of the file. For example,
    
    ```nix
    fetchurl {   
	    url = "http://ftp.gnu.org/pub/gnu/hello/hello-2.1.1.tar.gz";   
	    sha256 = "1md7jsfd8pa45z73bz1kszpp01yw6x5ljkjk2hx7wl800any6465"; 
	}
    ```
    
    It sometimes happens that the URL of the file changes, e.g., because servers are reorganised or no longer available. We then must update the call to `fetchurl`, e.g.,
    
    ```nix
    fetchurl {   
	    url = "ftp://ftp.nluug.nl/pub/gnu/hello/hello-2.1.1.tar.gz";   
		sha256 = "1md7jsfd8pa45z73bz1kszpp01yw6x5ljkjk2hx7wl800any6465"; 
	}
    ```
    
    If a `fetchurl` derivation was treated like a normal derivation, the output paths of the derivation and _all derivations depending on it_ would change. For instance, if we were to change the URL of the Glibc source distribution in Nixpkgs (a package on which almost all other packages depend) massive rebuilds would be needed. This is unfortunate for a change which we know cannot have a real effect as it propagates upwards through the dependency graph.
    
    For fixed-output derivations, on the other hand, the name of the output path only depends on the `outputHash*` and `name` attributes, while all other attributes are ignored for the purpose of computing the output path. (The `name` attribute is included because it is part of the path.)
    
    As an example, here is the (simplified) Nix expression for `fetchurl`:
    
    ```nix
    { stdenv, curl }: # The curl program is used for downloading.  
    
    { url, sha256 }:  
    
    stdenv.mkDerivation {   
	    name = baseNameOf (toString url);   
	    builder = ./builder.sh;   
	    buildInputs = [ curl ];    
	    
	    # This is a fixed-output derivation; the output must be a regular   
	    # file with SHA256 hash sha256.   
	    outputHashMode = "flat";   
	    outputHashAlgo = "sha256";   
	    outputHash = sha256;    
		
		inherit url; 
	}
    ```
    
    The `outputHashAlgo` attribute specifies the hash algorithm used to compute the hash. It can currently be `"sha1"`, `"sha256"` or `"sha512"`.
    
    The `outputHashMode` attribute determines how the hash is computed. It must be one of the following two values:
    
    - `"flat"`  
        The output must be a non-executable regular file. If it isn’t, the build fails. The hash is simply computed over the contents of that file (so it’s equal to what Unix commands like `sha256sum` or `sha1sum` produce).
        
        This is the default.
        
    - `"recursive"`  
        The hash is computed over the NAR archive dump of the output (i.e., the result of [`nix-store --dump`](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump)). In this case, the output can be anything, including a directory tree.
        
    
    The `outputHash` attribute, finally, must be a string containing the hash in either hexadecimal or base-32 notation. (See the [`nix-hash` command](https://nixos.org/manual/nix/unstable/command-ref/nix-hash) for information about converting to and from base-32 notation.)
    
- [`__contentAddressed`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-__contentAddressed)
    
    > **Warning** This attribute is part of an [experimental feature](https://nixos.org/manual/nix/unstable/contributing/experimental-features).
    > 
    > To use this attribute, you must enable the [`ca-derivations`](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-ca-derivations) experimental feature. For example, in [nix.conf](https://nixos.org/manual/nix/unstable/command-ref/conf-file) you could add:
    > 
    > `extra-experimental-features = ca-derivations`
    
    If this attribute is set to `true`, then the derivation outputs will be stored in a content-addressed location rather than the traditional input-addressed one.
    
    Setting this attribute also requires setting [`outputHashMode`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputHashMode) and [`outputHashAlgo`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputHashAlgo) like for _fixed-output derivations_ (see above).
    
    It also implicitly requires that the machine to build the derivation must have the `ca-derivations` [system feature](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-system-features).
    
- [`passAsFile`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-passAsFile)  
    A list of names of attributes that should be passed via files rather than environment variables. For example, if you have
    
    ```nix
    passAsFile = ["big"]; 
    big = "a very long string";
    ```
    
    then when the builder runs, the environment variable `bigPath` will contain the absolute path to a temporary file containing `a very long string`. That is, for any attribute _x_ listed in `passAsFile`, Nix will pass an environment variable `xPath` holding the path of the file containing the value of attribute _x_. This is useful when you need to pass large strings to a builder, since most operating systems impose a limit on the size of the environment (typically, a few hundred kilobyte).
    
- [`preferLocalBuild`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-preferLocalBuild)  
    If this attribute is set to `true` and [distributed building is enabled](https://nixos.org/manual/nix/unstable/advanced-topics/distributed-builds), then, if possible, the derivation will be built locally instead of forwarded to a remote machine. This is appropriate for trivial builders where the cost of doing a download or remote build would exceed the cost of building locally.
    
- [`allowSubstitutes`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-allowSubstitutes)  
    If this attribute is set to `false`, then Nix will always build this derivation; it will not try to substitute its outputs. This is useful for very trivial derivations (such as `writeText` in Nixpkgs) that are cheaper to build than to substitute from a binary cache.
    
    > **Note**
    > 
    > You need to have a builder configured which satisfies the derivation’s `system` attribute, since the derivation cannot be substituted. Thus it is usually a good idea to align `system` with `builtins.currentSystem` when setting `allowSubstitutes` to `false`. For most trivial derivations this should be the case.
    
- [`__structuredAttrs`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-structuredAttrs)  
    If the special attribute `__structuredAttrs` is set to `true`, the other derivation attributes are serialised into a file in JSON format. The environment variable `NIX_ATTRS_JSON_FILE` points to the exact location of that file both in a build and a [`nix-shell`](https://nixos.org/manual/nix/unstable/command-ref/nix-shell). This obviates the need for [`passAsFile`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-passAsFile) since JSON files have no size restrictions, unlike process environments.
    
    It also makes it possible to tweak derivation settings in a structured way; see [`outputChecks`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputChecks) for example.
    
    As a convenience to Bash builders, Nix writes a script that initialises shell variables corresponding to all attributes that are representable in Bash. The environment variable `NIX_ATTRS_SH_FILE` points to the exact location of the script, both in a build and a [`nix-shell`](https://nixos.org/manual/nix/unstable/command-ref/nix-shell). This includes non-nested (associative) arrays. For example, the attribute `hardening.format = true` ends up as the Bash associative array element `${hardening[format]}`.
    
- [`outputChecks`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-outputChecks)  
    When using [structured attributes](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-structuredAttrs), the `outputChecks` attribute allows defining checks per-output.
    
    In addition to [`allowedReferences`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-allowedReferences), [`allowedRequisites`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-allowedRequisites), [`disallowedReferences`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-disallowedReferences) and [`disallowedRequisites`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-disallowedRequisites), the following attributes are available:
    
    - `maxSize` defines the maximum size of the resulting [store object](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object).
    - `maxClosureSize` defines the maximum size of the output's closure.
    - `ignoreSelfRefs` controls whether self-references should be considered when checking for allowed references/requisites.
    
    Example:
    
    ```nix
    __structuredAttrs = true;  
    
    outputChecks.out = {   
	    # The closure of 'out' must not be larger than 256 MiB.   
	    maxClosureSize = 256 * 1024 * 1024;    
	    
	    # It must not refer to the C compiler or to the 'dev' output.   
	    disallowedRequisites = [ stdenv.cc "dev" ]; 
	};  
	
	outputChecks.dev = {   
		# The 'dev' output must not be larger than 128 KiB.   
		maxSize = 128 * 1024; 
	};
	```
    
- [`unsafeDiscardReferences`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-unsafeDiscardReferences)
    
    When using [structured attributes](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-structuredAttrs), the attribute `unsafeDiscardReferences` is an attribute set with a boolean value for each output name. If set to `true`, it disables scanning the output for runtime dependencies.
    
    Example:
    
    ```nix
    __structuredAttrs = true; 
    unsafeDiscardReferences.out = true;
    ```
    
    This is useful, for example, when generating self-contained filesystem images with their own embedded Nix store: hashes found inside such an image refer to the embedded store and not to the host's Nix store.
    
- [`requiredSystemFeatures`](https://nixos.org/manual/nix/unstable/language/advanced-attributes#adv-attr-requiredSystemFeatures)
    
    If a derivation has the `requiredSystemFeatures` attribute, then Nix will only build it on a machine that has the corresponding features set in its [`system-features` configuration](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-system-features).
    
    For example, setting
    
    ```nix
    requiredSystemFeatures = [ "kvm" ];
    ```
    
    ensures that the derivation can only be built on a machine with the `kvm` feature.
## [Import From Derivation](https://nixos.org/manual/nix/unstable/language/import-from-derivation#import-from-derivation)

The value of a Nix expression can depend on the contents of a [store object](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object).

Passing an expression `expr` that evaluates to a [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) to any built-in function which reads from the filesystem constitutes Import From Derivation (IFD):

- [`import`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-import) `expr`
- [`builtins.readFile`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readFile) `expr`
- [`builtins.readFileType`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readFileType) `expr`
- [`builtins.readDir`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readDir) `expr`
- [`builtins.pathExists`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-pathExists) `expr`
- [`builtins.filterSource`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-filterSource) `f expr`
- [`builtins.path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-path) `{ path = expr; }`
- [`builtins.hashFile`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-hashFile) `t expr`
- `builtins.scopedImport x drv`

When the store path needs to be accessed, evaluation will be paused, the corresponding store object [realised](https://nixos.org/manual/nix/unstable/glossary#gloss-realise), and then evaluation resumed.

This has performance implications: Evaluation can only finish when all required store objects are realised. Since the Nix language evaluator is sequential, it only finds store paths to read from one at a time. While realisation is always parallel, in this case it cannot be done for all required store paths at once, and is therefore much slower than otherwise.

Realising store objects during evaluation can be disabled by setting [`allow-import-from-derivation`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-allow-import-from-derivation) to `false`. Without IFD it is ensured that evaluation is complete and Nix can produce a build plan before starting any realisation.

## [Example](https://nixos.org/manual/nix/unstable/language/import-from-derivation#example)

In the following Nix expression, the inner derivation `drv` produces a file with contents `hello`.

```nix
# IFD.nix 
let   
	drv = derivation {     
		name = "hello";     
		builder = "/bin/sh";     
		args = [ "-c" "echo -n hello > $out" ];     
		system = builtins.currentSystem;   
	}; 
in "${builtins.readFile drv} world"
```

```nix
nix-instantiate IFD.nix --eval --read-write-mode
```

```nix
building '/nix/store/348q1cal6sdgfxs8zqi9v8llrsn4kqkq-hello.drv'... 
"hello world"
```

The contents of the derivation's output have to be [realised](https://nixos.org/manual/nix/unstable/glossary#gloss-realise) before they can be read with [`readFile`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readFile). Only then evaluation can continue to produce the final result.

## [Illustration](https://nixos.org/manual/nix/unstable/language/import-from-derivation#illustration)

As a first approximation, the following data flow graph shows how evaluation and building are interleaved, if the value of a Nix expression depends on realising a [store object]. Boxes are data structures, arrow labels are transformations.

```
+----------------------+             +------------------------+ 
| Nix evaluator        |             | Nix store              | 
|  .----------------.  |             |                        | 
|  | Nix expression |  |             |                        | 
|  '----------------'  |             |                        | 
|          |           |             |                        | 
|       evaluate       |             |                        | 
|          |           |             |                        | 
|          V           |             |                        | 
|    .------------.    |             |  .------------------.  | 
|    | derivation |----|-instantiate-|->| store derivation |  | 
|    '------------'    |             |  '------------------'  | 
|                      |             |           |            | 
|                      |             |        realise         | 
|                      |             |           |            | 
|                      |             |           V            | 
|  .----------------.  |             |    .--------------.    | 
|  | Nix expression |<-|----read-----|----| store object |    | 
|  '----------------'  |             |    '--------------'    | 
|          |           |             |                        | 
|       evaluate       |             |                        | 
|          |           |             |                        | 
|          V           |             |                        | 
|    .------------.    |             |                        | 
|    |   value    |    |             |                        | 
|    '------------'    |             |                        | 
+----------------------+             +------------------------+
```

In more detail, the following sequence diagram shows how the expression is evaluated step by step, and where evaluation is blocked to wait for the build output to appear.

```
.-------.     .-------------.                        .---------. 
|Nix CLI|     |Nix evaluator|                        |Nix store| 
'-------'     '-------------'                        '---------'
	|                |                                    |     
	|evaluate IFD.nix|                                    |     
	|--------------->|                                    |     
	|                |                                    |     
	|  evaluate `"${readFile drv} world"`                 |     
	|                |                                    |     
	|    evaluate `readFile drv`                          |     
	|                |                                    |     
	|   evaluate `drv` as string                          |     
	|                |                                    |     
	|                |instantiate /nix/store/...-hello.drv|     
	|                |----------------------------------->|     
	|                :                                    |     
	|                :  realise /nix/store/...-hello.drv  |     
	|                :----------------------------------->|     
	|                :                                    |     
	|                                                     |--------.     
	|                :                                    |        |     
	|      (evaluation blocked)                           |  echo hello > $out     
	|                :                                    |        |     
	|                                                     |<-------'     
	|                :        /nix/store/...-hello        |     
	|                |<-----------------------------------|     
	|                |                                    |     
	|  resume `readFile /nix/store/...-hello`             |     
	|                |                                    |     
	|                |   readFile /nix/store/...-hello    |     
	|                |----------------------------------->|     
	|                |                                    |     
	|                |               hello                |     
	|                |<-----------------------------------|     
	|                |                                    |     
	|      resume `"${"hello"} world"`                    |     
	|                |                                    |     
	|        resume `"hello world"`                       |     
	|                |                                    |     
	| "hello world"  |                                    |     
	|<---------------|                                    | 
.-------.     .-------------.                        .---------. 
|Nix CLI|     |Nix evaluator|                        |Nix store| 
'-------'     '-------------'                        '---------'
```
# [Built-in Constants](https://nixos.org/manual/nix/unstable/language/builtin-constants#built-in-constants)

These constants are built into the Nix language evaluator:

[`builtins`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-builtins) (set)

Contains all the [built-in functions](https://nixos.org/manual/nix/unstable/language/builtins) and values.

Since built-in functions were added over time, [testing for attributes](https://nixos.org/manual/nix/unstable/language/operators#has-attribute) in `builtins` can be used for graceful fallback on older Nix installations:

```nix
# if hasContext is not available, we assume `s` has a context 
if builtins ? hasContext then builtins.hasContext s else true
```

[`currentSystem`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-currentSystem) (string)

The value of the [`system` configuration option](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-pure-eval).

It can be used to set the `system` attribute for [`builtins.derivation`](https://nixos.org/manual/nix/unstable/language/derivations) such that the resulting derivation can be built on the same system that evaluates the Nix expression:

 ```nix
 builtins.derivation {    
	 # ...    
	 system = builtins.currentSystem; 
}
 ```

It can be overridden in order to create derivations for different system than the current one:

```bash
$ nix-instantiate --system "mips64-linux" --eval --expr 'builtins.currentSystem' "mips64-linux"
```

> **Note**
> 
> Not available in [pure evaluation mode](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-pure-eval).

[`currentTime`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-currentTime) (integer)

Return the [Unix time](https://en.wikipedia.org/wiki/Unix_time) at first evaluation. Repeated references to that name will re-use the initially obtained value.

Example:

```bash
$ nix repl 
Welcome to Nix 2.15.1 Type :? for help. 

nix-repl> builtins.currentTime 
1683705525 

nix-repl> builtins.currentTime 
1683705525
```

The [store path](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) of a derivation depending on `currentTime` will differ for each evaluation, unless both evaluate `builtins.currentTime` in the same second.

> **Note**
> 
> Not available in [pure evaluation mode](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-pure-eval).

[`false`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-false) (Boolean)

Primitive value.

It can be returned by [comparison operators](https://nixos.org/manual/nix/unstable/language/operators#Comparison) and used in [conditional expressions](https://nixos.org/manual/nix/unstable/language/constructs#Conditionals).

The name `false` is not special, and can be shadowed:

```bash
nix-repl> let false = 1; in false 
1
```

[`langVersion`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-langVersion) (integer)

The current version of the Nix language.

[`nixPath`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-nixPath) (list)

List of search path entries used to resolve [lookup paths](https://nixos.org/manual/nix/unstable/language/constructs/lookup-path).

Lookup path expressions can be [desugared](https://en.wikipedia.org/wiki/Syntactic_sugar) using this and [`builtins.findFile`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-findFile):

```nix
<nixpkgs>
```

is equivalent to:

```nix
builtins.findFile builtins.nixPath "nixpkgs"
```

[`nixVersion`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-nixVersion) (string)

The version of Nix.

For example, where the command line returns the current Nix version,

```bash
$ nix --version nix (Nix) 
2.16.0
```

the Nix language evaluator returns the same value:

```bash
nix-repl> builtins.nixVersion 
"2.16.0"
```

[`null`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-null) (null)

Primitive value.

The name `null` is not special, and can be shadowed:

```bash
nix-repl> let null = 1; in null 
1
```

[`storeDir`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-storeDir) (string)

Logical file system location of the [Nix store](https://nixos.org/manual/nix/unstable/glossary#gloss-store) currently in use.

This value is determined by the `store` parameter in [Store URLs](https://nixos.org/manual/nix/unstable/command-ref/new-cli/nix3-help-stores):

```bash
$ nix-instantiate --store 'dummy://?store=/blah' --eval --expr builtins.storeDir "/blah"
```

[`true`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-true) (Boolean)

Primitive value.

It can be returned by [comparison operators](https://nixos.org/manual/nix/unstable/language/operators#Comparison) and used in [conditional expressions](https://nixos.org/manual/nix/unstable/language/constructs#Conditionals).

The name `true` is not special, and can be shadowed:

```bash
nix-repl> let true = 1; in true 
1
```
# [Built-in Functions](https://nixos.org/manual/nix/unstable/language/builtins#built-in-functions)

This section lists the functions built into the Nix language evaluator. All built-in functions are available through the global [`builtins`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-builtins) constant.

For convenience, some built-ins can be accessed directly:

- [`derivation`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-derivation)
- [`import`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-import)
- [`abort`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-abort)
- [`throw`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-throw)

[`derivation attrs`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-derivation)

derivation is described in [its own section](https://nixos.org/manual/nix/unstable/language/derivations).

[`abort s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-abort)

Abort Nix expression evaluation and print the error message _s_.

[`add e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-add)

Return the sum of the numbers _e1_ and _e2_.

[`all pred list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-all)

Return `true` if the function _pred_ returns `true` for all elements of _list_, and `false` otherwise.

[`any pred list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-any)

Return `true` if the function _pred_ returns `true` for at least one element of _list_, and `false` otherwise.

[`attrNames set`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-attrNames)

Return the names of the attributes in the set _set_ in an alphabetically sorted list. For instance, `builtins.attrNames { y = 1; x = "foo"; }` evaluates to `[ "x" "y" ]`.

[`attrValues set`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-attrValues)

Return the values of the attributes in the set _set_ in the order corresponding to the sorted attribute names.

[`baseNameOf s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-baseNameOf)

Return the _base name_ of the string _s_, that is, everything following the final slash in the string. This is similar to the GNU `basename` command.

[`bitAnd e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-bitAnd)

Return the bitwise AND of the integers _e1_ and _e2_.

[`bitOr e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-bitOr)

Return the bitwise OR of the integers _e1_ and _e2_.

[`bitXor e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-bitXor)

Return the bitwise XOR of the integers _e1_ and _e2_.

[`break v`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-break)

In debug mode (enabled using `--debugger`), pause Nix expression evaluation and enter the REPL. Otherwise, return the argument `v`.

[`catAttrs attr list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-catAttrs)

Collect each attribute named _attr_ from a list of attribute sets. Attrsets that don't contain the named attribute are ignored. For example,

```nix
builtins.catAttrs "a" [{a = 1;} {b = 0;} {a = 2;}]
```

evaluates to `[1 2]`.

[`ceil double`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-ceil)

Converts an IEEE-754 double-precision floating-point number (_double_) to the next higher integer.

If the datatype is neither an integer nor a "float", an evaluation error will be thrown.

[`compareVersions s1 s2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-compareVersions)

Compare two strings representing versions and return `-1` if version _s1_ is older than version _s2_, `0` if they are the same, and `1` if _s1_ is newer than _s2_. The version comparison algorithm is the same as the one used by [`nix-env -u`](https://nixos.org/manual/nix/unstable/command-ref/nix-env#operation---upgrade).

[`concatLists lists`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-concatLists)

Concatenate a list of lists into a single list.

[`concatMap f list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-concatMap)

This function is equivalent to `builtins.concatLists (map f list)` but is more efficient.

[`concatStringsSep separator list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-concatStringsSep)

Concatenate a list of strings with a separator between each element, e.g. `concatStringsSep "/" ["usr" "local" "bin"] == "usr/local/bin"`.

[`deepSeq e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-deepSeq)

This is like `seq e1 e2`, except that _e1_ is evaluated _deeply_: if it’s a list or set, its elements or attributes are also evaluated recursively.

[`dirOf s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-dirOf)

Return the directory part of the string _s_, that is, everything before the final slash in the string. This is similar to the GNU `dirname` command.

[`div e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-div)

Return the quotient of the numbers _e1_ and _e2_.

[`elem x xs`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-elem)

Return `true` if a value equal to _x_ occurs in the list _xs_, and `false` otherwise.

[`elemAt xs n`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-elemAt)

Return element _n_ from the list _xs_. Elements are counted starting from 0. A fatal error occurs if the index is out of bounds.

[`fetchClosure args`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchClosure)

Fetch a store path [closure](https://nixos.org/manual/nix/unstable/glossary#gloss-closure) from a binary cache, and return the store path as a string with context.

This function can be invoked in three ways, that we will discuss in order of preference.

**Fetch a content-addressed store path**

Example:

```nix
builtins.fetchClosure {   
	fromStore = "https://cache.nixos.org";   
	fromPath = /nix/store/ldbhlwhh39wha58rm61bkiiwm6j7211j-git-2.33.1; 
}
```

This is the simplest invocation, and it does not require the user of the expression to configure [`trusted-public-keys`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-trusted-public-keys) to ensure their authenticity.

If your store path is [input addressed](https://nixos.org/manual/nix/unstable/glossary#gloss-input-addressed-store-object) instead of content addressed, consider the other two invocations.

**Fetch any store path and rewrite it to a fully content-addressed store path**

Example:

```nix
builtins.fetchClosure {   
	fromStore = "https://cache.nixos.org";   
	fromPath = /nix/store/r2jd6ygnmirm2g803mksqqjm4y39yi6i-git-2.33.1;   
	toPath = /nix/store/ldbhlwhh39wha58rm61bkiiwm6j7211j-git-2.33.1; 
}
```

This example fetches `/nix/store/r2jd...` from the specified binary cache, and rewrites it into the content-addressed store path `/nix/store/ldbh...`.

Like the previous example, no extra configuration or privileges are required.

To find out the correct value for `toPath` given a `fromPath`, use [`nix store make-content-addressed`](https://nixos.org/manual/nix/unstable/command-ref/new-cli/nix3-store-make-content-addressed):

```nix
# nix store make-content-addressed --from https://cache.nixos.org /nix/store/r2jd6ygnmirm2g803mksqqjm4y39yi6i-git-2.33.1 
rewrote '/nix/store/r2jd6ygnmirm2g803mksqqjm4y39yi6i-git-2.33.1' to '/nix/store/ldbhlwhh39wha58rm61bkiiwm6j7211j-git-2.33.1'
```

Alternatively, set `toPath = ""` and find the correct `toPath` in the error message.

**Fetch an input-addressed store path as is**

Example:

```nix
builtins.fetchClosure {   
	fromStore = "https://cache.nixos.org";   
	fromPath = /nix/store/r2jd6ygnmirm2g803mksqqjm4y39yi6i-git-2.33.1;   
	inputAddressed = true; 
}
```

It is possible to fetch an [input-addressed store path](https://nixos.org/manual/nix/unstable/glossary#gloss-input-addressed-store-object) and return it as is. However, this is the least preferred way of invoking `fetchClosure`, because it requires that the input-addressed paths are trusted by the Nix configuration.

**`builtins.storePath`**

`fetchClosure` is similar to [`builtins.storePath`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-storePath) in that it allows you to use a previously built store path in a Nix expression. However, `fetchClosure` is more reproducible because it specifies a binary cache from which the path can be fetched. Also, using content-addressed store paths does not require users to configure [`trusted-public-keys`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-trusted-public-keys) to ensure their authenticity.

This function is only available if the [fetch-closure](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-fetch-closure) experimental feature is enabled.

[`fetchGit args`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchGit)

Fetch a path from git. _args_ can be a URL, in which case the HEAD of the repo at that URL is fetched. Otherwise, it can be an attribute with the following attributes (all except `url` optional):

- `url`
    
    The URL of the repo.
    
- `name` (default: _basename of the URL_)
    
    The name of the directory the repo should be exported to in the store.
    
- `rev` (default: _the tip of `ref`_)
    
    The [Git revision](https://git-scm.com/docs/git-rev-parse#_specifying_revisions) to fetch. This is typically a commit hash.
    
- `ref` (default: `HEAD`)
    
    The [Git reference](https://git-scm.com/book/en/v2/Git-Internals-Git-References) under which to look for the requested revision. This is often a branch or tag name.
    
    By default, the `ref` value is prefixed with `refs/heads/`. As of 2.3.0, Nix will not prefix `refs/heads/` if `ref` starts with `refs/`.
    
- `submodules` (default: `false`)
    
    A Boolean parameter that specifies whether submodules should be checked out.
    
- `shallow` (default: `false`)
    
    A Boolean parameter that specifies whether fetching a shallow clone is allowed.
    
- `allRefs`
    
    Whether to fetch all references of the repository. With this argument being true, it's possible to load a `rev` from _any_ `ref` (by default only `rev`s from the specified `ref` are supported).
    

Here are some examples of how to use `fetchGit`.

- To fetch a private repository over SSH:
    
    ```nix
    builtins.fetchGit {   
	    url = "git@github.com:my-secret/repository.git";   
	    ref = "master";   
	    rev = "adab8b916a45068c044658c4158d81878f9ed1c3"; 
	}
    ```
    
- To fetch an arbitrary reference:
    
    ```nix
    builtins.fetchGit {   
	    url = "https://github.com/NixOS/nix.git";   
		ref = "refs/heads/0.5-release"; 
	}
    ```
    
- If the revision you're looking for is in the default branch of the git repository you don't strictly need to specify the branch name in the `ref` attribute.
    
    However, if the revision you're looking for is in a future branch for the non-default branch you will need to specify the the `ref` attribute as well.
    
    ```nix
    builtins.fetchGit {   
	    url = "https://github.com/nixos/nix.git";   
	    rev = "841fcbd04755c7a2865c51c1e2d3b045976b7452";   
	    ref = "1.11-maintenance"; 
	}
    ```
    
    > **Note**
    > 
    > It is nice to always specify the branch which a revision belongs to. Without the branch being specified, the fetcher might fail if the default branch changes. Additionally, it can be confusing to try a commit from a non-default branch and see the fetch fail. If the branch is specified the fault is much more obvious.
    
- If the revision you're looking for is in the default branch of the git repository you may omit the `ref` attribute.
    
    ```nix
    builtins.fetchGit {   
	    url = "https://github.com/nixos/nix.git";   
	    rev = "841fcbd04755c7a2865c51c1e2d3b045976b7452"; 
	}
    ```
    
- To fetch a specific tag:
    
    ```nix
    builtins.fetchGit {   
	    url = "https://github.com/nixos/nix.git";   
	    ref = "refs/tags/1.9"; 
	}
    ```
    
- To fetch the latest version of a remote branch:
    
    ```nix
    builtins.fetchGit {   
	    url = "ssh://git@github.com/nixos/nix.git";   
	    ref = "master"; 
	}
    ```
    
    Nix will refetch the branch according to the [`tarball-ttl`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-tarball-ttl) setting.
    
    This behavior is disabled in [pure evaluation mode](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-pure-eval).
    
- To fetch the content of a checked-out work directory:
    
    ```nix
    builtins.fetchGit ./work-dir
    ```
    

If the URL points to a local directory, and no `ref` or `rev` is given, `fetchGit` will use the current content of the checked-out files, even if they are not committed or added to Git's index. It will only consider files added to the Git repository, as listed by `git ls-files`.

[`fetchTarball args`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchTarball)

Download the specified URL, unpack it and return the path of the unpacked tree. The file must be a tape archive (`.tar`) compressed with `gzip`, `bzip2` or `xz`. The top-level path component of the files in the tarball is removed, so it is best if the tarball contains a single directory at top level. The typical use of the function is to obtain external Nix expression dependencies, such as a particular version of Nixpkgs, e.g.

```nix
with import (fetchTarball https://github.com/NixOS/nixpkgs/archive/nixos-14.12.tar.gz) {};  

stdenv.mkDerivation { … }
```

The fetched tarball is cached for a certain amount of time (1 hour by default) in `~/.cache/nix/tarballs/`. You can change the cache timeout either on the command line with `--tarball-ttl` _number-of-seconds_ or in the Nix configuration file by adding the line `tarball-ttl =` _number-of-seconds_.

Note that when obtaining the hash with `nix-prefetch-url` the option `--unpack` is required.

This function can also verify the contents against a hash. In that case, the function takes a set instead of a URL. The set requires the attribute `url` and the attribute `sha256`, e.g.

```nix
with import (fetchTarball {   
	url = "https://github.com/NixOS/nixpkgs/archive/nixos-14.12.tar.gz";   
	sha256 = "1jppksrfvbk5ypiqdz4cddxdl8z6zyzdb2srq8fcffr327ld5jj2"; }) {}; 

stdenv.mkDerivation { … }
```

Not available in [restricted evaluation mode](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-restrict-eval).

[`fetchTree input`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchTree)

Fetch a source tree or a plain file using one of the supported backends. _input_ can be an attribute set representation of [flake reference](https://nixos.org/manual/nix/unstable/command-ref/new-cli/nix3-flake#flake-references) or a URL. The input should be "locked", that is, it should contain a commit hash or content hash unless impure evaluation (`--impure`) is allowed.

Here are some examples of how to use `fetchTree`:

- Fetch a GitHub repository:
    
    ```nix
    builtins.fetchTree {   
	    type = "github";   
	    owner = "NixOS";   
	    repo = "nixpkgs";   
	    rev = "ae2e6b3958682513d28f7d633734571fb18285dd"; 
	}
    ```
    
    This evaluates to attribute set:
    
    ```nix
    {   
	    lastModified = 1686503798;   
	    lastModifiedDate = "20230611171638";   
	    narHash = "sha256-rA9RqKP9OlBrgGCPvfd5HVAXDOy8k2SmPtB/ijShNXc=";   
	    outPath = "/nix/store/l5m6qlvfs9sdw14ja3qbzpglcjlb6j1x-source";   
	    rev = "ae2e6b3958682513d28f7d633734571fb18285dd";   
	    shortRev = "ae2e6b3"; 
	}
    ```
    
- Fetch a single file from a URL:
    
    ```nix
    builtins.fetchTree "https://example.com/"
    ```
    

This function is only available if the [flakes](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-flakes) experimental feature is enabled.

[`fetchurl url`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchurl)

Download the specified URL and return the path of the downloaded file.

Not available in [restricted evaluation mode](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-restrict-eval).

[`filter f list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-filter)

Return a list consisting of the elements of _list_ for which the function _f_ returns `true`.

[`filterSource e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-filterSource)

> **Warning**
> 
> `filterSource` should not be used to filter store paths. Since `filterSource` uses the name of the input directory while naming the output directory, doing so will produce a directory name in the form of `<hash2>-<hash>-<name>`, where `<hash>-<name>` is the name of the input directory. Since `<hash>` depends on the unfiltered directory, the name of the output directory will indirectly depend on files that are filtered out by the function. This will trigger a rebuild even when a filtered out file is changed. Use `builtins.path` instead, which allows specifying the name of the output directory.

This function allows you to copy sources into the Nix store while filtering certain files. For instance, suppose that you want to use the directory `source-dir` as an input to a Nix expression, e.g.

```nix
stdenv.mkDerivation {   
	...   
	src = ./source-dir; 
}
```

However, if `source-dir` is a Subversion working copy, then all those annoying `.svn` subdirectories will also be copied to the store. Worse, the contents of those directories may change a lot, causing lots of spurious rebuilds. With `filterSource` you can filter out the `.svn` directories:

```nix
src = builtins.filterSource   
(path: type: type != "directory" || baseNameOf path != ".svn")   
./source-dir;
```

Thus, the first argument _e1_ must be a predicate function that is called for each regular file, directory or symlink in the source tree _e2_. If the function returns `true`, the file is copied to the Nix store, otherwise it is omitted. The function is called with two arguments. The first is the full path of the file. The second is a string that identifies the type of the file, which is either `"regular"`, `"directory"`, `"symlink"` or `"unknown"` (for other kinds of files such as device nodes or fifos — but note that those cannot be copied to the Nix store, so if the predicate returns `true` for them, the copy will fail). If you exclude a directory, the entire corresponding subtree of _e2_ will be excluded.

[`findFile search-path lookup-path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-findFile)

Find _lookup-path_ in _search-path_.

A search path is represented list of [attribute sets](https://nixos.org/manual/nix/unstable/language/values#attribute-set) with two attributes:

- `prefix` is a relative path.
- `path` denotes a file system location The exact syntax depends on the command line interface.

Examples of search path attribute sets:

- 1
	```nix
	{   
		prefix = "nixos-config";   
		path = "/etc/nixos/configuration.nix"; 
	}
	```
    
- 2
	```nix
	{   
		prefix = "";   
		path = "/nix/var/nix/profiles/per-user/root/channels"; 
	}
	```
    

The lookup algorithm checks each entry until a match is found, returning a [path value](https://nixos.org/manual/nix/unstable/language/values#type-path) of the match:

- If _lookup-path_ matches `prefix`, then the remainder of _lookup-path_ (the "suffix") is searched for within the directory denoted by `path`. Note that the `path` may need to be downloaded at this point to look inside.
- If the suffix is found inside that directory, then the entry is a match. The combined absolute path of the directory (now downloaded if need be) and the suffix is returned.

[Lookup path](https://nixos.org/manual/nix/unstable/language/constructs/lookup-path) expressions can be [desugared](https://en.wikipedia.org/wiki/Syntactic_sugar) using this and [`builtins.nixPath`](https://nixos.org/manual/nix/unstable/language/builtin-constants#builtins-nixPath):

```nix
<nixpkgs>
```

is equivalent to:

```nix
builtins.findFile builtins.nixPath "nixpkgs"
```

[`flakeRefToString attrs`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-flakeRefToString)

Convert a flake reference from attribute set format to URL format.

For example:

```nix
builtins.flakeRefToString {   
	dir = "lib"; owner = "NixOS"; ref = "23.05"; repo = "nixpkgs"; type = "github"; 
	}
```

evaluates to

```
"github:NixOS/nixpkgs/23.05?dir=lib"
```

This function is only available if the [flakes](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-flakes) experimental feature is enabled.

[`floor double`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-floor)

Converts an IEEE-754 double-precision floating-point number (_double_) to the next lower integer.

If the datatype is neither an integer nor a "float", an evaluation error will be thrown.

[`foldl' op nul list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-foldl')

Reduce a list by applying a binary operator, from left to right, e.g. `foldl' op nul [x0 x1 x2 ...] = op (op (op nul x0) x1) x2) ...`. For example, `foldl' (x: y: x + y) 0 [1 2 3]` evaluates to 6. The return value of each application of `op` is evaluated immediately, even for intermediate values.

[`fromJSON e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fromJSON)

Convert a JSON string to a Nix value. For example,

```nix
builtins.fromJSON ''{"x": [1, 2, 3], "y": null}''
```

returns the value `{ x = [ 1 2 3 ]; y = null; }`.

[`fromTOML e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fromTOML)

Convert a TOML string to a Nix value. For example,

```nix
builtins.fromTOML ''   
	x=1   
	s="a"   
	[table]   
	y=2 
''
```

returns the value `{ s = "a"; table = { y = 2; }; x = 1; }`.

[`functionArgs f`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-functionArgs)

Return a set containing the names of the formal arguments expected by the function _f_. The value of each attribute is a Boolean denoting whether the corresponding argument has a default value. For instance, `functionArgs ({ x, y ? 123}: ...) = { x = false; y = true; }`.

"Formal argument" here refers to the attributes pattern-matched by the function. Plain lambdas are not included, e.g. `functionArgs (x: ...) = { }`.

[`genList generator length`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-genList)

Generate list of size _length_, with each element _i_ equal to the value returned by _generator_ `i`. For example,

```nix
builtins.genList (x: x * x) 5
```

returns the list `[ 0 1 4 9 16 ]`.

[`genericClosure attrset`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-genericClosure)

Take an _attrset_ with values named `startSet` and `operator` in order to return a _list of attrsets_ by starting with the `startSet` and recursively applying the `operator` function to each `item`. The _attrsets_ in the `startSet` and the _attrsets_ produced by `operator` must contain a value named `key` which is comparable. The result is produced by calling `operator` for each `item` with a value for `key` that has not been called yet including newly produced `item`s. The function terminates when no new `item`s are produced. The resulting _list of attrsets_ contains only _attrsets_ with a unique key. For example,

```nix
builtins.genericClosure {   
	startSet = [ {key = 5;} ];   
	operator = item: [{     
		key = if (item.key / 2 ) * 2 == item.key          
			then item.key / 2          
			else 3 * item.key + 1;  
	}]; 
}
```

evaluates to

```nix
[ { key = 5; } { key = 16; } { key = 8; } { key = 4; } { key = 2; } { key = 1; } ]
```

[`getAttr s set`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-getAttr)

`getAttr` returns the attribute named _s_ from _set_. Evaluation aborts if the attribute doesn’t exist. This is a dynamic version of the `.` operator, since _s_ is an expression rather than an identifier.

[`getContext s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-getContext)

Return the string context of _s_.

The string context tracks references to derivations within a string. It is represented as an attribute set of [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation) paths mapping to output names.

Using [string interpolation](https://nixos.org/manual/nix/unstable/language/string-interpolation) on a derivation will add that derivation to the string context. For example,

```nix
builtins.getContext "${derivation { name = "a"; builder = "b"; system = "c"; }}"
```

evaluates to

```nix
{ "/nix/store/arhvjaf6zmlyn8vh8fgn55rpwnxq0n7l-a.drv" = { outputs = [ "out" ]; }; }
```

[`getEnv s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-getEnv)

`getEnv` returns the value of the environment variable _s_, or an empty string if the variable doesn’t exist. This function should be used with care, as it can introduce all sorts of nasty environment dependencies in your Nix expression.

`getEnv` is used in Nix Packages to locate the file `~/.nixpkgs/config.nix`, which contains user-local settings for Nix Packages. (That is, it does a `getEnv "HOME"` to locate the user’s home directory.)

[`getFlake args`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-getFlake)

Fetch a flake from a flake reference, and return its output attributes and some metadata. For example:

```nix
(builtins.getFlake "nix/55bc52401966fbffa525c574c14f67b00bc4fb3a").packages.x86_64-linux.nix
```

Unless impure evaluation is allowed (`--impure`), the flake reference must be "locked", e.g. contain a Git revision or content hash. An example of an unlocked usage is:

```nix
(builtins.getFlake "github:edolstra/dwarffs").rev
```

This function is only available if the [flakes](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-flakes) experimental feature is enabled.

[`groupBy f list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-groupBy)

Groups elements of _list_ together by the string returned from the function _f_ called on each element. It returns an attribute set where each attribute value contains the elements of _list_ that are mapped to the same corresponding attribute name returned by _f_.

For example,

```nix
builtins.groupBy (builtins.substring 0 1) ["foo" "bar" "baz"]
```

evaluates to

```
{ b = [ "bar" "baz" ]; f = [ "foo" ]; }
```

[`hasAttr s set`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-hasAttr)

`hasAttr` returns `true` if _set_ has an attribute named _s_, and `false` otherwise. This is a dynamic version of the `?` operator, since _s_ is an expression rather than an identifier.

[`hasContext s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-hasContext)

Return `true` if string _s_ has a non-empty context. The context can be obtained with [`getContext`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-getContext).

[`hashFile type p`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-hashFile)

Return a base-16 representation of the cryptographic hash of the file at path _p_. The hash algorithm specified by _type_ must be one of `"md5"`, `"sha1"`, `"sha256"` or `"sha512"`.

[`hashString type s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-hashString)

Return a base-16 representation of the cryptographic hash of string _s_. The hash algorithm specified by _type_ must be one of `"md5"`, `"sha1"`, `"sha256"` or `"sha512"`.

[`head list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-head)

Return the first element of a list; abort evaluation if the argument isn’t a list or is an empty list. You can test whether a list is empty by comparing it with `[]`.

[`import path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-import)

Load, parse, and return the Nix expression in the file _path_.

> **Note**
> 
> Unlike some languages, `import` is a regular function in Nix.

The _path_ argument must meet the same criteria as an [interpolated expression](https://nixos.org/manual/nix/unstable/language/string-interpolation#interpolated-expression).

If _path_ is a directory, the file `default.nix` in that directory is used if it exists.

> **Example**
> 
> `$ echo 123 > default.nix`
> 
> Import `default.nix` from the current directory.
> 
> `import ./.`
> 
> `123`

Evaluation aborts if the file doesn’t exist or contains an invalid Nix expression.

A Nix expression loaded by `import` must not contain any _free variables_, that is, identifiers that are not defined in the Nix expression itself and are not built-in. Therefore, it cannot refer to variables that are in scope at the call site.

> **Example**
> 
> If you have a calling expression
> 
> `rec {   x = 123;   y = import ./foo.nix; }`
> 
> then the following `foo.nix` will give an error:
> 
> `# foo.nix x + 456`
> 
> since `x` is not in scope in `foo.nix`. If you want `x` to be available in `foo.nix`, pass it as a function argument:
> 
> `rec {   x = 123;   y = import ./foo.nix x; }`
> 
> and
> 
> `# foo.nix x: x + 456`
> 
> The function argument doesn’t have to be called `x` in `foo.nix`; any name would work.

[`intersectAttrs e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-intersectAttrs)

Return a set consisting of the attributes in the set _e2_ which have the same name as some attribute in _e1_.

Performs in O(_n_ log _m_) where _n_ is the size of the smaller set and _m_ the larger set's size.

[`isAttrs e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isAttrs)

Return `true` if _e_ evaluates to a set, and `false` otherwise.

[`isBool e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isBool)

Return `true` if _e_ evaluates to a bool, and `false` otherwise.

[`isFloat e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isFloat)

Return `true` if _e_ evaluates to a float, and `false` otherwise.

[`isFunction e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isFunction)

Return `true` if _e_ evaluates to a function, and `false` otherwise.

[`isInt e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isInt)

Return `true` if _e_ evaluates to an integer, and `false` otherwise.

[`isList e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isList)

Return `true` if _e_ evaluates to a list, and `false` otherwise.

[`isNull e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isNull)

Return `true` if _e_ evaluates to `null`, and `false` otherwise.

> **Warning**
> 
> This function is _deprecated_; just write `e == null` instead.

[`isPath e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isPath)

Return `true` if _e_ evaluates to a path, and `false` otherwise.

[`isString e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-isString)

Return `true` if _e_ evaluates to a string, and `false` otherwise.

[`length e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-length)

Return the length of the list _e_.

[`lessThan e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-lessThan)

Return `true` if the number _e1_ is less than the number _e2_, and `false` otherwise. Evaluation aborts if either _e1_ or _e2_ does not evaluate to a number.

[`listToAttrs e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-listToAttrs)

Construct a set from a list specifying the names and values of each attribute. Each element of the list should be a set consisting of a string-valued attribute `name` specifying the name of the attribute, and an attribute `value` specifying its value.

In case of duplicate occurrences of the same name, the first takes precedence.

Example:

```nix
builtins.listToAttrs   
	[ { name = "foo"; value = 123; }     
	  { name = "bar"; value = 456; }     
	  { name = "bar"; value = 420; }   
	]
```

evaluates to

```nix
{ foo = 123; bar = 456; }
```

[`map f list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-map)

Apply the function _f_ to each element in the list _list_. For example,

```nix
map (x: "foo" + x) [ "bar" "bla" "abc" ]
```

evaluates to `[ "foobar" "foobla" "fooabc" ]`.

[`mapAttrs f attrset`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-mapAttrs)

Apply function _f_ to every element of _attrset_. For example,

```nix
builtins.mapAttrs (name: value: value * 10) { a = 1; b = 2; }
```

evaluates to `{ a = 10; b = 20; }`.

[`match regex str`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-match)

Returns a list if the [extended POSIX regular expression](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap09.html#tag_09_04) _regex_ matches _str_ precisely, otherwise returns `null`. Each item in the list is a regex group.

```nix
builtins.match "ab" "abc"
```

Evaluates to `null`.

```nix
builtins.match "abc" "abc"
```

Evaluates to `[ ]`.

```nix
builtins.match "a(b)(c)" "abc"
```

Evaluates to `[ "b" "c" ]`.

```nix
builtins.match "[[:space:]]+([[:upper:]]+)[[:space:]]+" "  FOO   "
```

Evaluates to `[ "FOO" ]`.

[`mul e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-mul)

Return the product of the numbers _e1_ and _e2_.

[`outputOf derivation-reference output-name`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-outputOf)

Return the output path of a derivation, literally or using a placeholder if needed.

If the derivation has a statically-known output path (i.e. the derivation output is input-addressed, or fixed content-addresed), the output path will just be returned. But if the derivation is content-addressed or if the derivation is itself not-statically produced (i.e. is the output of another derivation), a placeholder will be returned instead.

_`derivation reference`_ must be a string that may contain a regular store path to a derivation, or may be a placeholder reference. If the derivation is produced by a derivation, you must explicitly select `drv.outPath`. This primop can be chained arbitrarily deeply. For instance,

```nix
builtins.outputOf   
	(builtins.outputOf myDrv "out)   
	"out"
```

will return a placeholder for the output of the output of `myDrv`.

This primop corresponds to the `^` sigil for derivable paths, e.g. as part of installable syntax on the command line.

This function is only available if the [dynamic-derivations](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-dynamic-derivations) experimental feature is enabled.

[`parseDrvName s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-parseDrvName)

Split the string _s_ into a package name and version. The package name is everything up to but not including the first dash not followed by a letter, and the version is everything following that dash. The result is returned in a set `{ name, version }`. Thus, `builtins.parseDrvName "nix-0.12pre12876"` returns `{ name = "nix"; version = "0.12pre12876"; }`.

[`parseFlakeRef flake-ref`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-parseFlakeRef)

Parse a flake reference, and return its exploded form.

For example:

```nix
builtins.parseFlakeRef "github:NixOS/nixpkgs/23.05?dir=lib"
```

evaluates to:

```nix
{ dir = "lib"; owner = "NixOS"; ref = "23.05"; repo = "nixpkgs"; type = "github"; }
```

This function is only available if the [flakes](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-flakes) experimental feature is enabled.

[`partition pred list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-partition)

Given a predicate function _pred_, this function returns an attrset containing a list named `right`, containing the elements in _list_ for which _pred_ returned `true`, and a list named `wrong`, containing the elements for which it returned `false`. For example,

```nix
builtins.partition (x: x > 10) [1 23 9 3 42]
```

evaluates to

```nix
{ right = [ 23 42 ]; wrong = [ 1 9 3 ]; }
```

[`path args`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-path)

An enrichment of the built-in path type, based on the attributes present in _args_. All are optional except `path`:

- path  
    The underlying path.
    
- name  
    The name of the path when added to the store. This can used to reference paths that have nix-illegal characters in their names, like `@`.
    
- filter  
    A function of the type expected by `builtins.filterSource`, with the same semantics.
    
- recursive  
    When `false`, when `path` is added to the store it is with a flat hash, rather than a hash of the NAR serialization of the file. Thus, `path` must refer to a regular file, not a directory. This allows similar behavior to `fetchurl`. Defaults to `true`.
    
- sha256  
    When provided, this is the expected hash of the file at the path. Evaluation will fail if the hash is incorrect, and providing a hash allows `builtins.path` to be used even when the `pure-eval` nix config option is on.
    

[`pathExists path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-pathExists)

Return `true` if the path _path_ exists at evaluation time, and `false` otherwise.

[`placeholder output`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-placeholder)

Return a placeholder string for the specified _output_ that will be substituted by the corresponding output path at build time. Typical outputs would be `"out"`, `"bin"` or `"dev"`.

[`readDir path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readDir)

Return the contents of the directory _path_ as a set mapping directory entries to the corresponding file type. For instance, if directory `A` contains a regular file `B` and another directory `C`, then `builtins.readDir ./A` will return the set

```nix
{ B = "regular"; C = "directory"; }
```

The possible values for the file type are `"regular"`, `"directory"`, `"symlink"` and `"unknown"`.

[`readFile path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readFile)

Return the contents of the file _path_ as a string.

[`readFileType p`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-readFileType)

Determine the directory entry type of a filesystem node, being one of "directory", "regular", "symlink", or "unknown".

[`removeAttrs set list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-removeAttrs)

Remove the attributes listed in _list_ from _set_. The attributes don’t have to exist in _set_. For instance,

```nix
removeAttrs { x = 1; y = 2; z = 3; } [ "a" "x" "z" ]
```

evaluates to `{ y = 2; }`.

[`replaceStrings from to s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-replaceStrings)

Given string _s_, replace every occurrence of the strings in _from_ with the corresponding string in _to_.

The argument _to_ is lazy, that is, it is only evaluated when its corresponding pattern in _from_ is matched in the string _s_

Example:

```nix
builtins.replaceStrings ["oo" "a"] ["a" "i"] "foobar"
```

evaluates to `"fabir"`.

[`seq e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-seq)

Evaluate _e1_, then evaluate and return _e2_. This ensures that a computation is strict in the value of _e1_.

[`sort comparator list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-sort)

Return _list_ in sorted order. It repeatedly calls the function _comparator_ with two elements. The comparator should return `true` if the first element is less than the second, and `false` otherwise. For example,

```nix
builtins.sort builtins.lessThan [ 483 249 526 147 42 77 ]
```

produces the list `[ 42 77 147 249 483 526 ]`.

This is a stable sort: it preserves the relative order of elements deemed equal by the comparator.

[`split regex str`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-split)

Returns a list composed of non matched strings interleaved with the lists of the [extended POSIX regular expression](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap09.html#tag_09_04) _regex_ matches of _str_. Each item in the lists of matched sequences is a regex group.

```nix
builtins.split "(a)b" "abc"
```

Evaluates to `[ "" [ "a" ] "c" ]`.

```nix
builtins.split "([ac])" "abc"
```

Evaluates to `[ "" [ "a" ] "b" [ "c" ] "" ]`.

```nix
builtins.split "(a)|(c)" "abc"
```

Evaluates to `[ "" [ "a" null ] "b" [ null "c" ] "" ]`.

```nix
builtins.split "([[:upper:]]+)" " FOO "
```

Evaluates to `[ " " [ "FOO" ] " " ]`.

[`splitVersion s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-splitVersion)

Split a string representing a version into its components, by the same version splitting logic underlying the version comparison in [`nix-env -u`](https://nixos.org/manual/nix/unstable/command-ref/nix-env#operation---upgrade).

[`storePath path`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-storePath)

This function allows you to define a dependency on an already existing store path. For example, the derivation attribute `src = builtins.storePath /nix/store/f1d18v1y…-source` causes the derivation to depend on the specified path, which must exist or be substitutable. Note that this differs from a plain path (e.g. `src = /nix/store/f1d18v1y…-source`) in that the latter causes the path to be _copied_ again to the Nix store, resulting in a new path (e.g. `/nix/store/ld01dnzc…-source-source`).

Not available in [pure evaluation mode](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-pure-eval).

See also [`builtins.fetchClosure`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchClosure).

[`stringLength e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-stringLength)

Return the length of the string _e_. If _e_ is not a string, evaluation is aborted.

[`sub e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-sub)

Return the difference between the numbers _e1_ and _e2_.

[`substring start len s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-substring)

Return the substring of _s_ from character position _start_ (zero-based) up to but not including _start + len_. If _start_ is greater than the length of the string, an empty string is returned, and if _start + len_ lies beyond the end of the string, only the substring up to the end of the string is returned. _start_ must be non-negative. For example,

```nix
builtins.substring 0 3 "nixos"
```

evaluates to `"nix"`.

[`tail list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-tail)

Return the list without its first item; abort evaluation if the argument isn’t a list or is an empty list.

> **Warning**
> 
> This function should generally be avoided since it's inefficient: unlike Haskell's `tail`, it takes O(n) time, so recursing over a list by repeatedly calling `tail` takes O(n^2) time.

[`throw s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-throw)

Throw an error message _s_. This usually aborts Nix expression evaluation, but in `nix-env -qa` and other commands that try to evaluate a set of derivations to get information about those derivations, a derivation that throws an error is silently skipped (which is not the case for `abort`).

[`toFile name s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-toFile)

Store the string _s_ in a file in the Nix store and return its path. The file has suffix _name_. This file can be used as an input to derivations. One application is to write builders “inline”. For instance, the following Nix expression combines the Nix expression for GNU Hello and its build script into one file:

```nix
{ stdenv, fetchurl, perl }:  

stdenv.mkDerivation {   
	name = "hello-2.1.1";    
	
	builder = builtins.toFile "builder.sh" "     
		source $stdenv/setup      
		
		PATH=$perl/bin:$PATH      
		
		tar xvfz $src     
		cd hello-*     
		./configure --prefix=$out     
		make     
		make install   
	";    
	
	src = fetchurl {     
		url = "http://ftp.nluug.nl/pub/gnu/hello/hello-2.1.1.tar.gz";     
		sha256 = "1md7jsfd8pa45z73bz1kszpp01yw6x5ljkjk2hx7wl800any6465";   
	};   
	inherit perl; 
}
```

It is even possible for one file to refer to another, e.g.,

```nix
builder = let   
	configFile = builtins.toFile "foo.conf" "     
		# This is some dummy configuration file.     
		...   
	"; 
in builtins.toFile "builder.sh" "   
	source $stdenv/setup   
	...   
	cp ${configFile} $out/etc/foo.conf 
";
```

Note that `${configFile}` is a [string interpolation](https://nixos.org/manual/nix/unstable/language/values#type-string), so the result of the expression `configFile` (i.e., a path like `/nix/store/m7p7jfny445k...-foo.conf`) will be spliced into the resulting string.

It is however _not_ allowed to have files mutually referring to each other, like so:

```nix
let   
	foo = builtins.toFile "foo" "...${bar}...";   
	bar = builtins.toFile "bar" "...${foo}..."; 
in foo
```

This is not allowed because it would cause a cyclic dependency in the computation of the cryptographic hashes for `foo` and `bar`.

It is also not possible to reference the result of a derivation. If you are using Nixpkgs, the `writeTextFile` function is able to do that.

[`toJSON e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-toJSON)

Return a string containing a JSON representation of _e_. Strings, integers, floats, booleans, nulls and lists are mapped to their JSON equivalents. Sets (except derivations) are represented as objects. Derivations are translated to a JSON string containing the derivation’s output path. Paths are copied to the store and represented as a JSON string of the resulting store path.

[`toPath s`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-toPath)

**DEPRECATED.** Use `/. + "/path"` to convert a string into an absolute path. For relative paths, use `./. + "/path"`.

[`toString e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-toString)

Convert the expression _e_ to a string. _e_ can be:

- A string (in which case the string is returned unmodified).
    
- A path (e.g., `toString /foo/bar` yields `"/foo/bar"`.
    
- A set containing `{ __toString = self: ...; }` or `{ outPath = ...; }`.
    
- An integer.
    
- A list, in which case the string representations of its elements are joined with spaces.
    
- A Boolean (`false` yields `""`, `true` yields `"1"`).
    
- `null`, which yields the empty string.
    

[`toXML e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-toXML)

Return a string containing an XML representation of _e_. The main application for `toXML` is to communicate information with the builder in a more structured format than plain environment variables.

Here is an example where this is the case:

```nix
{ stdenv, fetchurl, libxslt, jira, uberwiki }:  

stdenv.mkDerivation (rec {   
	name = "web-server";    
	
	buildInputs = [ libxslt ];    
	
	builder = builtins.toFile "builder.sh" "     
		source $stdenv/setup     
		mkdir $out     
		echo "$servlets" | xsltproc ${stylesheet} - > $out/server-conf.xml ①   
	";    
	
	stylesheet = builtins.toFile "stylesheet.xsl" ②    
		"<?xml version='1.0' encoding='UTF-8'?>     
			<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>       
				<xsl:template match='/'>         
					<Configure>           
						<xsl:for-each select='/expr/list/attrs'>             
							<Call name='addWebApplication'>               
								<Arg><xsl:value-of select=\"attr[@name = 'path']/string/@value\" /></Arg>               
								<Arg><xsl:value-of select=\"attr[@name = 'war']/path/@value\" /></Arg>             
							</Call>           
						</xsl:for-each>         
					</Configure>       
				</xsl:template>     
			</xsl:stylesheet>   
		";    
		
		servlets = builtins.toXML [ ③     
			{ path = "/bugtracker"; war = jira + "/lib/atlassian-jira.war"; }     
			{ path = "/wiki"; war = uberwiki + "/uberwiki.war"; }   
		]; 
})
```

The builder is supposed to generate the configuration file for a [Jetty servlet container](http://jetty.mortbay.org/). A servlet container contains a number of servlets (`*.war` files) each exported under a specific URI prefix. So the servlet configuration is a list of sets containing the `path` and `war` of the servlet (①). This kind of information is difficult to communicate with the normal method of passing information through an environment variable, which just concatenates everything together into a string (which might just work in this case, but wouldn’t work if fields are optional or contain lists themselves). Instead the Nix expression is converted to an XML representation with `toXML`, which is unambiguous and can easily be processed with the appropriate tools. For instance, in the example an XSLT stylesheet (at point ②) is applied to it (at point ①) to generate the XML configuration file for the Jetty server. The XML representation produced at point ③ by `toXML` is as follows:

```nix
<?xml version='1.0' encoding='utf-8'?> 
	<expr>   
		<list>     
			<attrs>       
				<attr name="path">         
					<string value="/bugtracker" />       
				</attr>       
				<attr name="war">         
					<path value="/nix/store/d1jh9pasa7k2...-jira/lib/atlassian-jira.war" />       
				</attr>     
			</attrs>     
			<attrs>       
				<attr name="path">         
					<string value="/wiki" />       
				</attr>       
				<attr name="war">         
					<path value="/nix/store/y6423b1yi4sx...-uberwiki/uberwiki.war" />       
				</attr>     
			</attrs>   
		</list> 
	</expr>
```

Note that we used the `toFile` built-in to write the builder and the stylesheet “inline” in the Nix expression. The path of the stylesheet is spliced into the builder using the syntax `xsltproc ${stylesheet}`.

[`trace e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-trace)

Evaluate _e1_ and print its abstract syntax representation on standard error. Then return _e2_. This function is useful for debugging.

[`traceVerbose e1 e2`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-traceVerbose)

Evaluate _e1_ and print its abstract syntax representation on standard error if `--trace-verbose` is enabled. Then return _e2_. This function is useful for debugging.

[`tryEval e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-tryEval)

Try to shallowly evaluate _e_. Return a set containing the attributes `success` (`true` if _e_ evaluated successfully, `false` if an error was thrown) and `value`, equalling _e_ if successful and `false` otherwise. `tryEval` will only prevent errors created by `throw` or `assert` from being thrown. Errors `tryEval` will not catch are for example those created by `abort` and type errors generated by builtins. Also note that this doesn't evaluate _e_ deeply, so `let e = { x = throw ""; }; in (builtins.tryEval e).success` will be `true`. Using `builtins.deepSeq` one can get the expected result: `let e = { x = throw ""; }; in (builtins.tryEval (builtins.deepSeq e e)).success` will be `false`.

[`typeOf e`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-typeOf)

Return a string representing the type of the value _e_, namely `"int"`, `"bool"`, `"string"`, `"path"`, `"null"`, `"set"`, `"list"`, `"lambda"` or `"float"`.

[`zipAttrsWith f list`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-zipAttrsWith)

Transpose a list of attribute sets into an attribute set of lists, then apply `mapAttrs`.

`f` receives two arguments: the attribute name and a non-empty list of all values encountered for that attribute name.

The result is an attribute set where the attribute names are the union of the attribute names in each element of `list`. The attribute values are the return values of `f`.

```nix
builtins.zipAttrsWith   
	(name: values: { inherit name values; })   
	[ { a = "x"; } { a = "y"; b = "z"; } ]
```

evaluates to

```nix
{   
	a = { name = "a"; values = [ "x" "y" ]; };   
	b = { name = "b"; values = [ "z" ]; }; 
}
```