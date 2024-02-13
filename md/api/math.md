<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    Math Module
</h1>

<p align="center">
    Provides functions that operate on advanced numbers.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/math"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="#variables">Variables</a>
            <ul>
                <li><a href="#e"><i>e</i></a></li>
                <li><a href="#epsilon">Epsilon</a></li>
                <li><a href="#max-number">Max Number</a></li>
                <li><a href="#max-safe-integer">Max Safe Integer</a></li>
                <li><a href="#min-number">Min Number</a></li>
                <li><a href="#min-safe-integer">Min Safe Integer</a></li>
                <li><a href="#pi">Pi</a></li>
            </ul>
        </li>
        <li>
            <a href="#functions">Functions</a>
            <ul>
                <li><a href="#ceil">Ceil</a></li>
                <li><a href="#clamp">Clamp</a></li>
                <li><a href="#floor">Floor</a></li>
                <li><a href="#max">Max</a></li>
                <li><a href="#min">Min</a></li>
                <li><a href="#round">Round</a></li>
                <li><a href="#absolute">Absolute</a></li>
                <li><a href="#hypot">Hypot</a></li>
                <li><a href="#logarithm">Logarithm</a></li>
                <li><a href="#power">Power</a></li>
                <li><a href="#square-root">Square Root</a></li>
                <li><a href="#cosine">Cosine</a></li>
                <li><a href="#sine">Sine</a></li>
                <li><a href="#tangent">Tangent</a></li>
                <li><a href="#arccosine">Arccosine</a></li>
                <li><a href="#arcsine">Arcsine</a></li>
                <li><a href="#arctangent">Arctangent</a></li>
                <li><a href="#2-argument-arctangent">2-Argument Arctangent</a></li>
                <li><a href="#compatible">Compatible</a></li>
                <li><a href="#is-unitless">Is Unitless</a></li>
                <li><a href="#unit">Unit</a></li>
                <li><a href="#dividing">Dividing</a></li>
                <li><a href="#percentage">Percentage</a></li>
                <li><a href="#random">Random</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Variables</h2>

<h3><i>e</i></h3>

```sass
math.$e
```

<p>The closest 64-bit floating point approximation of the <a target="_blank" href="https://en.wikipedia.org/wiki/E_(mathematical_constant)">mathematical constant <i>e</i></a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$e  //=> 2.7182818285
> ```

<h3>Epsilon</h3>

```sass
math.$epsilon
```

<p>The difference between 1 and the smallest 64-bit floating point number greater than 1 according to floating-point comparisons. Because of Sass numbers’ <a target="_blank" href="https://sass-lang.com/documentation/values/numbers/">10 digits of precision</a>, in many cases this will appear to be 0.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$epsilon  //=> 0
> ```

<h3>Max Number</h3>

```sass
math.$max-number
```

<p>The maximum finite number that can be represented as a 64-bit floating point number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$max-number
> //=> 179769313486231570000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
> ```

<h3>Max Safe Integer</h3>

```sass
math.$max-safe-integer
```

<p>The maximum integer n such that both n and n + 1 can be precisely represented as a 64-bit floating-point number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$max-safe-integer  //=> 9007199254740991
> ```

<h3>Min Number</h3>

```sass
math.$min-number
```

<p>The smallest positive number that can be represented as a 64-bit floating point number. Because of Sass numbers’ <a target="_blank" href="https://sass-lang.com/documentation/values/numbers/">10 digits of precision</a>, in many cases this will appear to be 0.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$min-number  //=> 0
> ```

<h3>Min Safe Integer</h3>

```sass
math.$min-safe-integer
```

<p>The minimum integer n such that both n and n - 1 can be precisely represented as a 64-bit floating-point number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$min-safe-integer  //=> -9007199254740991
> ```

<h3>Pi</h3>

```sass
math.$pi
```

<p>The closest 64-bit floating point approximation of the <a target="_blank" href="https://en.wikipedia.org/wiki/Pi">mathematical constant π</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.$pi  //=> 3.1415926536
> ```

<h2>Functions</h2>

<h3>Ceil</h3>

```sass
math.ceil($number)  //=> number

// or

ceil($number)  //=> number
```

<p>Rounds <code>$number</code> up to the next highest whole number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.ceil(4)  //=> 4
> @debug math.ceil(4.2)  //=> 5
> @debug math.ceil(4.9)  //=> 5
> ```

<h3>Clamp</h3>

```sass
math.clamp($min, $number, $max)  //=> number
```

<p>Restricts <code>$number</code> to the range between <code>$min</code> and <code>$max</code>. If <code>$number</code> is less than <code>$min</code> this returns <code>$min</code>, and if it’s greater than <code>$max</code> this returns <code>$max</code>.</p>
<p><code>$min</code>, <code>$number</code>, and <code>$max</code> must have compatible units, or all be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.clamp(-1, 0, 1)  //=> 0
> @debug math.clamp(1px, -1px, 10px)  //=> 1px
> @debug math.clamp(-1in, 1cm, 10mm)  //=> 10mm
> ```

<h3>Floor</h3>

```sass
math.floor($number)  //=> number

// or

floor($number)  //=> number
```

<p>Rounds <code>$number</code> down to the next lowest whole number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.floor(4)  //=> 4
> @debug math.floor(4.2)  //=> 4
> @debug math.floor(4.9)  //=> 4
> ```

<h3>Max</h3>

```sass
math.max($number...)  //=> number

// or

max($number...)  //=> number
```

<p>Returns the highest of one or more numbers.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.max(1px, 4px)  //=> 4px
>
> $widths: 50px, 30px, 100px
> @debug math.max($widths...)  //=> 100px
> ```

<h3>Min</h3>

```sass
math.min($number...)  //=> number

//or

min($number...)  //=> number
```

<p>Returns the lowest of one or more numbers.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.min(1px, 4px)  //=> 1px
>
> $widths: 50px, 30px, 100px
> @debug math.min($widths...)  //=> 30px
> ```

<h3>Round</h3>

```sass
math.round($number)  //=> number

// or

round($number)  //=> number
```

<p>Rounds <code>$number</code> to the nearest whole number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.round(4)  //=> 4
> @debug math.round(4.2)  //=> 4
> @debug math.round(4.9)  //=> 5
> ```

<h3>Absolute</h3>

```sass
math.abs($number)  //=> number

// or

abs($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Absolute_value">absolute value</a> of <code>$number</code>. If <code>$number</code> is negative, this returns -<code>$number</code>, and if <code>$number</code> is positive, it returns <code>$number</code> as-is.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.abs(10px)  //=> 10px
> @debug math.abs(-10px)  //=> 10px
> ```

<h3>Hypot</h3>

```sass
math.hypot($number...) //=> number
```

<p>Returns the length of the <i>n</i>-dimensional vector that has components equal to each <code>$number</code>. For example, for three numbers <i>a</i>, <i>b</i>, and <i>c</i>, this returns the square root of <i>a² + b² + c²</i>.</p>
<p>The numbers must either all have compatible units, or all be unitless. And since the numbers’ units may differ, the output takes the unit of the first number.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.hypot(3, 4)  //=> 5
>
> $lengths: 1in, 10cm, 50px
> @debug math.hypot($lengths...)  //=> 4.0952775683in
> ```

<h3>Logarithm</h3>

```sass
math.log($number, $base: null) //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Logarithm">logarithm</a> of <code>$number</code> with respect to <code>$base</code>. If <code>$base</code> is null, the <a target="_blank" href="https://en.wikipedia.org/wiki/Natural_logarithm">natural log</a> is calculated.</p>
<p><code>$number</code> and <code>$base</code> must be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.log(10);  //=> 2.302585093
> @debug math.log(10, 10);  //=> 1
> ```

<h3>Power</h3>

```sass
math.pow($base, $exponent)  //=> number
```

<p>Raises <code>$base</code> <a target="_blank" href="https://en.wikipedia.org/wiki/Exponentiation">to the power</a> of <code>$exponent</code>.</p>
<p><code>$base</code> and <code>$exponent</code> must be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.pow(10, 2)  //=> 100
> @debug math.pow(100, math.div(1, 3))  //=> 4.6415888336
> @debug math.pow(5, -2)  //=> 0.04
> ```

<h3>Square Root</h3>

```sass
math.sqrt($number)  //=> number
```

<p>Returns the <a target="_blank" href="">square root</a> of <code>$number</code>.</p>
<p><code>$number</code> must be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.sqrt(100)  //=> 10
> @debug math.sqrt(math.div(1, 3))  //=> 0.5773502692
> @debug math.sqrt(-1)  //=> NaN
> ```

<h3>Cosine</h3>

```sass
math.cos($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Trigonometric_functions#Right-angled_triangle_definitions">cosine</a> of <code>$number</code>.</p>
<p><code>$number</code> must be an angle (its units must be compatible with <code>deg</code>) or unitless. If <code>$number</code> has no units, it is assumed to be in <code>rad</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.cos(100deg)  //=> -0.1736481777
> @debug math.cos(1rad)  //=> 0.5403023059
> @debug math.cos(1)  //=> 0.5403023059
> ```

<h3>Sine</h3>

```sass
math.sin($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Trigonometric_functions#Right-angled_triangle_definitions">sine</a> of <code>$number</code>.</p>
<p><code>$number</code> must be an angle (its units must be compatible with <code>deg</code>) or unitless. If <code>$number</code> has no units, it is assumed to be in <code>rad</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.sin(100deg)  //=> 0.984807753
> @debug math.sin(1rad)  //=> 0.8414709848
> @debug math.sin(1)  //=> 0.8414709848
> ```

<h3>Tangent</h3>

```sass
math.tan($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Trigonometric_functions#Right-angled_triangle_definitions">tangent</a> of <code>$number</code>.</p>
<p><code>$number</code> must be an angle (its units must be compatible with <code>deg</code>) or unitless. If <code>$number</code> has no units, it is assumed to be in <code>rad</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.tan(100deg)  //=> -5.6712818196
> @debug math.tan(1rad)  //=> 1.5574077247
> @debug math.tan(1)  //=> 1.5574077247
> ```

<h3>Arccosine</h3>

```sass
math.acos($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Inverse_trigonometric_functions#Basic_properties">arccosine</a> of <code>$number</code> in <code>deg</code>.</p>
<p><code>$number</code> must be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.acos(0.5)  //=> 60deg
> @debug math.acos(2)  //=> NaNdeg
> ```

<h3>Arcsine</h3>

```sass
math.asin($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Inverse_trigonometric_functions#Basic_properties">arcsine</a> of <code>$number</code> in <code>deg</code>.</p>
<p><code>$number</code> must be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.asin(0.5)  //=> 30deg
> @debug math.asin(2)  //=> NaNdeg
> ```

<h3>Arctangent</h3>

```sass
math.atan($number)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Inverse_trigonometric_functions#Basic_properties">arctangent</a> of <code>$number</code> in <code>deg</code>.</p>
<p><code>$number</code> must be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.atan(10)  //=> 84.2894068625deg
> ```

<h3>2-Argument Arctangent</h3>

```sass
math.atan2($y, $x)  //=> number
```

<p>Returns the <a target="_blank" href="https://en.wikipedia.org/wiki/Atan2">2-argument arctangent</a> of <code>$y</code> and <code>$x</code> in deg.</p>
<p><code>$y</code> and <code>$x</code> must have compatible units or be unitless.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.atan2(-1, 1)  //=> 135deg
> ```

<h3>Compatible</h3>

```sass
math.compatible($number1, $number2)  //=> boolean

// or

comparable($number1, $number2)  //=> boolean
```

<p>Returns whether <code>$number1</code> and <code>$number2</code> have compatible units.</p>
<p>If this returns true, <code>$number1</code> and <code>$number2</code> can safely be added, subtracted, and compared. Otherwise, doing so will produce errors.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.compatible(2px, 1px)  //=> true
> @debug math.compatible(100px, 3em)  //=> false
> @debug math.compatible(10cm, 3mm)  //=> true
> ```

<h3>Is Unitless</h3>

```sass
math.is-unitless($number)  //=> boolean

// or

unitless($number)  //=> boolean
```

<p>Returns whether <code>$number</code> has no units.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.is-unitless(100)  //=> true
> @debug math.is-unitless(100px)  //=> false
> ```

<h3>Unit</h3>

```sass
math.unit($number)  //=> quoted string

// or

unit($number)  //=> quoted string
```

<p>Returns a string representation of <code>$number</code>’s units.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.unit(100)  //=> ""
> @debug math.unit(100px)  //=> "px"
> @debug math.unit(5px * 10px)  //=> "px*px"
> @debug math.unit(math.div(5px, 1s))  //=> "px/s"
> ```

<h3>Dividing</h3>

```sass
math.div($number1, $number2)  //=> number
```

<p>Returns the result of dividing <code>$number1</code> by <code>$number2</code>.</p>
<p>Any units shared by both numbers will be canceled out. Units in <code>$number1</code> that aren’t in <code>$number2</code> will end up in the return value’s numerator, and units in <code>$number2</code> that aren’t in <code>$number1</code> will end up in its denominator.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.div(1, 2)  //=> 0.5
> @debug math.div(100px, 5px)  //=> 20
> @debug math.div(100px, 5)  //=> 20px
> @debug math.div(100px, 5s)  //=> 20px/s
> ```

<h3>Percentage</h3>

```sass
math.percentage($number)  //=> number

// or

percentage($number)  //=> number
```

<p>Converts a unitless <code>$number</code> (usually a decimal between 0 and 1) to a percentage.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.percentage(0.2)  //=> 20%
> @debug math.percentage(math.div(100px, 50px))  //=> 200%
> ```

<h3>Random</h3>

```sass
math.random($limit: null)  //=> number

// or

random($limit: null)  //=> number
```

<p>If <code>$limit</code> is <code>null</code>, returns a random decimal number between 0 and 1.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.random()  //=> 0.2821251858
> @debug math.random()  //=> 0.6221325814
> ```

<p>If <code>$limit</code> is a number greater than or equal to 1, returns a random whole number between 1 and <code>$limit</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/math"
>
> @debug math.random(10)  //=> 4
> @debug math.random(10000)  //=> 5373
> ```
