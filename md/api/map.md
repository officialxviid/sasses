<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    Map Module
</h1>

<p align="center">
    Makes it possible to look up the value associated with a key in advanced map.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/map"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="">Functions</a>
            <ul>
                <li><a href="">Deep Merge</a></li>
                <li><a href="">Deep Remove</a></li>
                <li><a href="">Get</a></li>
                <li><a href="">Has Key</a></li>
                <li><a href="">Keys</a></li>
                <li><a href="">Merge</a></li>
                <li><a href="">Remove</a></li>
                <li><a href="">Set</a></li>
                <li><a href="">Values</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Functions</h2>

<h3>deep-merge</h3>

```sass
map.deep-merge($map1, $map2)  //=> map
```

<p>Identical to <a href="#merge"><code>map.merge()</code></a>, except that nested map values are <i>also</i> recursively merged.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $helvetica-light: ("weights": ("lightest": 100, "light": 300))
> $helvetica-heavy: ("weights": ("medium": 500, "bold": 700))
>
> @debug map.deep-merge($helvetica-light, $helvetica-heavy)
> // (
> //   "weights": (
> //     "lightest": 100,
> //     "light": 300,
> //     "medium": 500,
> //     "bold": 700
> //   )
> // )
> @debug map.merge($helvetica-light, $helvetica-heavy);
> // (
> //   "weights": (
> //     "medium: 500,
> //     "bold": 700
> //   )
> // )
> ```

<h3>deep-remove</h3>

```sass
map.deep-remove($map, $key, $keys...)  //=> map
```

<p>If <code>$keys</code> is empty, returns a copy of <code>$map</code> without a value associated with <code>$key</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.deep-remove($font-weights, "regular")  //=> ("medium": 500, "bold": 700)
> ```

<p>If <code>$keys</code> is not empty, follows the set of keys including <code>$key</code> and excluding the last key in <code>$keys</code>, from left to right, to find the nested map targeted for updating.</p>
<p>Returns a copy of <code>$map</code> where the targeted map does not have a value associated with the last key in <code>$keys</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $fonts: ("Helvetica": ("weights": ("regular": 400, "medium": 500, "bold": 700)))
>
> @debug map.deep-remove($fonts, "Helvetica", "weights", "regular")
> // (
> //   "Helvetica": (
> //     "weights: (
> //       "medium": 500,
> //       "bold": 700
> //     )
> //   )
> // )
> ```

<h3>get</h3>

```sass
map.get($map, $key, $keys...)
```

<p>If <code>$keys</code> is empty, returns the value in <code>$map</code> associated with <code>$key</code>.</p>
<p>If <code>$map</code> doesn’t have a value associated with <code>$key</code>, returns <a target="_blank" href="https://sass-lang.com/documentation/values/null/">null</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.get($font-weights, "medium")  //=> 500
> @debug map.get($font-weights, "extra-bold")  //=> null
> ```

<p>If <code>$keys</code> is not empty, follows the set of keys including <code>$key</code> and excluding the last key in <code>$keys</code>, from left to right, to find the nested map targeted for searching.</p>
<p>Returns the value in the targeted map associated with the last key in <code>$keys</code>.</p>
<p>Returns <a target="_blank" href="https://sass-lang.com/documentation/values/null/">null</a> if the map does not have a value associated with the key, or if any key in <code>$keys</code> is missing from a map or references a value that is not a map.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $fonts: ("Helvetica": ("weights": ("regular": 400, "medium": 500, "bold": 700)))
>
> @debug map.get($fonts, "Helvetica", "weights", "regular")  //=> 400
> @debug map.get($fonts, "Helvetica", "colors")  //=> null
> ```

<h3>has-key</h3>

```sass
map.has-key($map, $key, $keys...)  //=> boolean
```

<p>If <code>$keys</code> is empty, returns whether <code>$map</code> contains a value associated with <code>$key</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.has-key($font-weights, "regular")  //=> true
> @debug map.has-key($font-weights, "bolder")  //=> false
> ```

<p>If <code>$keys</code> is not empty, follows the set of keys including <code>$key</code> and excluding the last key in <code>$keys</code>, from left to right, to find the nested map targeted for searching.</p>
<p>Returns true if the targeted map contains a value associated with the last key in <code>$keys</code>.</p>
<p>Returns false if it does not, or if any key in <code>$keys</code> is missing from a map or references a value that is not a map.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $fonts: ("Helvetica": ("weights": ("regular": 400, "medium": 500, "bold": 700)))
>
> @debug map.has-key($fonts, "Helvetica", "weights", "regular")  //=> true
> @debug map.has-key($fonts, "Helvetica", "colors")  //=> false
> ```

<h3>keys</h3>

```sass
map.keys($map)  //=> list
```

<p>Returns a comma-separated list of all the keys in <code>$map</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.keys($font-weights)  //=> "regular", "medium", "bold"
> ```

<h3>merge</h3>

```sass
map.merge($map1, $map2)  //=> map

// or

map.merge($map1, $keys..., $map2)  //=> map
```

<p>If no <code>$keys</code> are passed, returns a new map with all the keys and values from both <code>$map1</code> and <code>$map2</code>.</p>
<p>If both <code>$map1</code> and <code>$map2</code> have the same key, <code>$map2</code>’s value takes precedence.</p>
<p>All keys in the returned map that also appear in <code>$map1</code> have the same order as in <code>$map1</code>. New keys from <code>$map2</code> appear at the end of the map.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $light-weights: ("lightest": 100, "light": 300)
> $heavy-weights: ("medium": 500, "bold": 700)
>
> @debug map.merge($light-weights, $heavy-weights)
> //=> ("lightest": 100, "light": 300, "medium": 500, "bold": 700)
> ```

<p>If <code>$keys</code> is not empty, follows the <code>$keys</code> to find the nested map targeted for merging. If any key in <code>$keys</code> is missing from a map or references a value that is not a map, sets the value at that key to an empty map.</p>
<p>Returns a copy of <code>$map1</code> where the targeted map is replaced by a new map that contains all the keys and values from both the targeted map and <code>$map2</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $fonts: ("Helvetica": ("weights": ("lightest": 100, "light": 300)))
> $heavy-weights: ("medium": 500, "bold": 700)
>
> @debug map.merge($fonts, "Helvetica", "weights", $heavy-weights)
> // (
> //   "Helvetica": (
> //     "weights": (
> //       "lightest": 100,
> //       "light": 300,
> //       "medium": 500,
> //       "bold": 700
> //     )
> //   )
> // )
> ```

<h3>remove</h3>

```sass
map.remove($map, $keys...)  //=> map
```

<p>Returns a copy of $map without any values associated with <code>$keys</code>.</p>
<p>If a key in <code>$keys</code> doesn’t have an associated value in <code>$map</code>, it’s ignored.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.remove($font-weights, "regular")  //=> ("medium": 500, "bold": 700)
> @debug map.remove($font-weights, "regular", "bold")  //=> ("medium": 500)
> @debug map.remove($font-weights, "bolder")  //=> ("regular": 400, "medium": 500, "bold": 700)
> ```

<h3>set</h3>

```sass
map.set($map, $key, $value)  //=> map

// or

map.set($map, $keys..., $key, $value)  //=> map
```

<p>If <code>$keys</code> are not passed, returns a copy of <code>$map</code> with the value at <code>$key</code> set to <code>$value</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.set($font-weights, "regular", 300)
> //=> ("regular": 300, "medium": 500, "bold": 700)
> ```

<p>If <code>$keys</code> are passed, follows the <code>$keys</code> to find the nested map targeted for updating. If any key in <code>$keys</code> is missing from a map or references a value that is not a map, sets the value at that key to an empty map.</p>
<p>Returns a copy of <code>$map</code> with the targeted map’s value at <code>$key</code> set to <code>$value</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $fonts: ("Helvetica": ("weights": ("regular": 400, "medium": 500, "bold": 700)))
>
> @debug map.set($fonts, "Helvetica", "weights", "regular", 300)
> // (
> //   "Helvetica": (
> //     "weights": (
> //       "regular": 300,
> //       "medium": 500,
> //       "bold": 700
> //     )
> //   )
> // )
> ```

<h3>values</h3>

```sass
map.values($map)  //=> list
```

<p>Returns a comma-separated list of all the values in <code>$map</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/map"
>
> $font-weights: ("regular": 400, "medium": 500, "bold": 700)
>
> @debug map.values($font-weights)  //=> 400, 500, 700
> ```
