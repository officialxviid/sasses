<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    List Module
</h1>

<p align="center">
    Lets you access and modify values in lists.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/list"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="">Functions</a>
            <ul>
                <li><a href="">append</a></li>
                <li><a href="">index</a></li>
                <li><a href="">is bracketed</a></li>
                <li><a href="">join</a></li>
                <li><a href="">length</a></li>
                <li><a href="">separator</a></li>
                <li><a href="">nth</a></li>
                <li><a href="">set nth</a></li>
                <li><a href="">slash</a></li>
                <li><a href="">zip</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Functions</h2>

<h3>append</h3>

```sass
list.append($list, $val, $separator: auto) //=> list
```

<p>Returns a copy of <code>$list</code> with <code>$val</code> added to the end.</p>
<p>If <code>$separator</code> is comma, space, or slash, the returned list is comma-separated, space-separated, or slash-separated, respectively. If it’s auto (the default), the returned list will use the same separator as <code>$list</code> (or space if <code>$list</code> doesn’t have a separator). Other values aren’t allowed.</p>
<p>Note that unlike <a href="#join"><code>list.join()</code></a>, if <code>$val</code> is a list it’s nested within the returned list rather than having all its elements added to the returned list.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.append(10px 20px, 30px)  //=> 10px 20px 30px
> @debug list.append((blue, red), green)  //=> blue, red, green
> @debug list.append(10px 20px, 30px 40px)  //=> 10px 20px (30px 40px)
> @debug list.append(10px, 20px, $separator: comma)  //=> 10px, 20px
> @debug list.append((blue, red), green, $separator: space)  //=> blue red green
> ```

<h3>index</h3>

```sass
list.index($list, $value) //=> number | null
```

<p>Returns the index of <code>$value</code> in <code>$list</code>.</p>
<p>If <code>$value</code> doesn’t appear in <code>$list</code>, this returns <a target="_blank" href=""><code>null</code></a>. If <code>$value</code> appears multiple times in <code>$list</code>, this returns the index of its first appearance.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.index(1px solid red, 1px)  //=> 1
> @debug list.index(1px solid red, solid)  //=> 2
> @debug list.index(1px solid red, dashed)  //=> null
> ```

<h3>is-bracketed</h3>

```sass
list.is-bracketed($list) //=> boolean
```

<p>Returns whether <code>$list</code> has square brackets.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.is-bracketed(1px 2px 3px)  //=> false
> @debug list.is-bracketed([1px, 2px, 3px])  //=> true
> ```

<h3>join</h3>

```sass
list.join($list1, $list2, $separator: auto, $bracketed: auto) //=> list
```

<p>Returns a new list containing the elements of <code>$list1</code> followed by the elements of <code>$list2</code>.</p>
<p>If $separator is <code>comma</code>, <code>space</code>, or <code>slash</code>, the returned list is comma-separated, space-separated, or slash-separated, respectively. If it’s auto (the default), the returned list will use the same separator as <code>$list1</code> if it has a separator, or else <code>$list2</code> if it has a separator, or else space. Other values aren’t allowed.</p>
<p>If <code>$bracketed</code> is auto (the default), the returned list will be bracketed if <code>$list1</code> is. Otherwise, the returned list will have square brackets if <code>$bracketed</code> is truthy and no brackets if <code>$bracketed</code> is falsey.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.join(10px 20px, 30px 40px)  //=> 10px 20px 30px 40px
> @debug list.join((blue, red), (#abc, #def))  //=> blue, red, #abc, #def
> @debug list.join(10px, 20px)  //=> 10px 20px
> @debug list.join(10px, 20px, comma)  //=> 10px, 20px
> @debug list.join((blue, red), (#abc, #def), space)  //=> blue red #abc #def
> @debug list.join([10px], 20px)  //=> [10px 20px]
> @debug list.join(10px, 20px, $bracketed: true)  //=> [10px 20px]
> ```

<h3>length</h3>

```sass
list.length($list) //=> number
```

<p>Returns the length of <code>$list</code>.</p>
<p>This can also return the number of pairs in a map.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.length(10px)  //=> 1
> @debug list.length(10px 20px 30px)  //=> 3
> @debug list.length((width: 10px, height: 20px))  //=> 2
> ```

<h3>separator</h3>

```sass
list.separator($list) //=> unquoted string
```

<p>Returns the name of the separator used by <code>$list</code>, either <code>comma</code>, <code>space</code>, or <code>slash</code>.</p>
<p>If <code>$list</code> doesn’t have a separator, returns space.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.separator(1px 2px 3px)  //=> space
> @debug list.separator((1px, 2px, 3px))  //=> comma
> @debug list.separator('Helvetica')  //=> space
> @debug list.separator(())  //=> space
> ```

<h3>nth</h3>

```sass
list.nth($list, $n)
```

<p>Returns the element of <code>$list</code> at index <code>$n</code>.</p>
<p>If <code>$n</code> is negative, it counts from the end of <code>$list</code>. Throws an error if there is no element at index <code>$n</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.nth(10px 12px 16px, 2)  // 12px
> @debug list.nth([line1, line2, line3], -1)  // line3
> ```

<h3>set-nth</h3>

```sass
list.set-nth($list, $n, $value)  //=> list
```

<p>Returns a copy of <code>$list</code> with the element at <a target="_blank" href="https://sass-lang.com/documentation/values/lists/#indexes">index</a> <code>$n</code> replaced with $value.</p>
<p>If <code>$n</code> is negative, it counts from the end of <code>$list</code>. Throws an error if there is no existing element at index <code>$n</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.set-nth(10px 20px 30px, 1, 2em);  //=> 2em 20px 30px
> @debug list.set-nth(10px 20px 30px, -1, 8em);  //=> 10px, 20px, 8em
> @debug list.set-nth((Helvetica, Arial, sans-serif), 3, Roboto);  //=> Helvetica, Arial, Roboto
> ```

<h3>slash</h3>

```sass
list.slash($elements...)  //=> list
```

<p>Returns a slash-separated list that contains <code>$elements</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.slash(1px, 50px, 100px)  //=> 1px / 50px / 100px
> ```

<h3>zip</h3>

```sass
list.zip($lists...)  //=> list
```

<p>Combines every list in <code>$lists</code> into a single list of sub-lists.</p>
<p>Each element in the returned list contains all the elements at that position in <code>$lists</code>. The returned list is as long as the shortest list in <code>$lists</code>.</p>
<p>The returned list is always comma-separated and the sub-lists are always space-separated.</p>

> **Sass**
>
> ```sass
> @use "sasses/list"
>
> @debug list.zip(10px 50px 100px, short mid long)  //=> 10px short, 50px mid, 100px long
> @debug list.zip(10px 50px 100px, short mid)  //=> 10px short, 50px mid
> ```
