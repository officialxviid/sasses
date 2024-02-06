<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    String Module
</h1>

<p align="center">
    Provides more advanced string functions for Sass.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/string"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="">Functions</a>
            <ul>
                <li><a href="">quote</a></li>
                <li><a href="">index</a></li>
                <li><a href="">insert</a></li>
                <li><a href="">length</a></li>
                <li><a href="">slice</a></li>
                <li><a href="">split</a></li>
                <li><a href="">to upper case</a></li>
                <li><a href="">to lower case</a></li>
                <li><a href="">unique id</a></li>
                <li><a href="">unquote</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Functions</h2>

<h3>quote</h3>

```sass
string.quote($string)  //=> string

// or

quote($string)  //=> string
```

<p>Returns <code>$string</code> as a quoted string.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.quote(Helvetica)  //=> "Helvetica"
> @debug string.quote("Helvetica")  //=> "Helvetica"
> ```

<h3>index</h3>

```sass
string.index($string, $substring)  //=> number
str-index($string, $substring)  //=> number
```

<p>Returns the first <a target="_blank" href="https://sass-lang.com/documentation/values/strings/#string-indexes">index</a> of <code>$substring</code> in <code>$string</code>, or <code>null</code> if <code>$string</code> doesn’t contain <code>$substring</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.index("Helvetica Neue", "Helvetica")  //=> 1
> @debug string.index("Helvetica Neue", "Neue")  //=> 11
> @debug string.index("I love you", "o")  //=> 4
> ```

<h3>insert</h3>

```sass
string.insert($string, $insert, $index)  //=> string

// or

str-insert($string, $insert, $index)  //=> string
```

<p>Returns a copy of <code>$string</code> with <code>$insert</code> inserted at <a target="_blank" href="https://sass-lang.com/documentation/values/strings/#string-indexes"><code>$index</code></a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.insert("Roboto Bold", " Mono", 7)  //=> "Roboto Mono Bold"
> @debug string.insert("Roboto Bold", " Mono", -6)  //=> "Roboto Mono Bold"
> ```

<p>If <code>$index</code> is higher than the length of <code>$string</code>, <code>$insert</code> is added to the end. If <code>$index</code> is smaller than the negative length of the string, <code>$insert</code> is added to the beginning.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.insert("Roboto", " Bold", 100)  //=> "Roboto Bold"
> @debug string.insert("Bold", "Roboto ", -100)  //=> "Roboto Bold"
> ```

<h3>length</h3>

```sass
string.length($string)  //=> number

// or

str-length($string)  //=> number
```

<p>Returns the number of characters in <code>$string</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.length("Helvetica Neue")  //=> 14
> @debug string.length(bold)  //=> 4
> @debug string.length("")  //=> 0
> ```

<h3>slice</h3>

```sass
string.slice($string, $start-at, $end-at: -1)  //=> string

// or

str-slice($string, $start-at, $end-at: -1)  //=> string
```

<p>Returns the slice of $string starting at <a target="_blank" href="https://sass-lang.com/documentation/values/strings/#string-indexes">index</a> <code>$start-at</code> and ending at index <code>$end-at</code> (both inclusive).</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.slice("Helvetica Neue", 11)  //=> "Neue"
> @debug string.slice("Helvetica Neue", 1, 3)  //=> "Hel"
> @debug string.slice("Helvetica Neue", 1, -6)  //=> "Helvetica"
> ```

<h3>split</h3>

```sass
string.split($string, $separator, $limit: null)  //=> list
```

<p>Returns a bracketed, comma-separated list of substrings of <code>$string</code> that are separated by <code>$separator</code>. The <code>$separators</code> aren’t included in these substrings.</p>
<p>If <code>$limit</code> is a number 1 or higher, this splits on at most that many <code>$separators</code> (and so returns at most <code>$limit</code> + 1 strings). The last substring contains the rest of the string, including any remaining <code>$separators</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.split("Segoe UI Emoji", " ")  // ["Segoe", "UI", "Emoji"]
> @debug string.split("Segoe UI Emoji", " ", $limit: 1)  // ["Segoe", "UI Emoji"]
> ```

<h3>to-upper-case</h3>

```sass
string.to-upper-case($string)  //=> string

// or

to-upper-case($string)  //=> string
```

<p>Returns a copy of <code>$string</code> with the <a targe="_blank" href="https://en.wikipedia.org/wiki/ASCII"><code>ASCII</code></a> letters converted to upper case.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.to-upper-case("Bold")  //=> "BOLD"
> @debug string.to-upper-case(sans-serif)  //=> SANS-SERIF
> ```

<h3>to-lower-case</h3>

```sass
string.to-lower-case($string)  //=> string

// or

to-lower-case($string)  //=> string
```

<p>Returns a copy of <code>$string</code> with the <a targe="_blank" href="https://en.wikipedia.org/wiki/ASCII"><code>ASCII</code></a> letters converted to lower case.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.to-lower-case("Bold")  //=> "bold"
> @debug string.to-lower-case(SANS-SERIF)  //=> sans-serif
> ```

<h3>unique-id</h3>

```sass
string.unique-id()  //=> string

// or

unique-id()  //=> string
```

<p>Returns a randomly-generated unquoted string that’s guaranteed to be a valid CSS identifier and to be unique within the current Sass compilation.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.unique-id()  //=> uabtrnzug
> @debug string.unique-id()  //=> u6w1b1def
> ```

<h3>unquote</h3>

```sass
string.unquote($string)  //=> string

// or

unquote($string)  //=> string
```

<p>Returns <code>$string</code> as an unquoted string. This can produce strings that aren’t valid CSS, so use with caution.</p>

> **Sass**
>
> ```sass
> @use "sasses/string"
>
> @debug string.unquote("Helvetica")  //=> Helvetica
> @debug string.unquote(".widget:hover")  //=> .widget:hover
> ```
