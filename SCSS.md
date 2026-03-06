# SCSS Note

- [Setup](#Setup)
- [Variables](#Variables)
- [Nesting](#Nesting)
- [Selector](#Selector)
- [Mixin](#Mixin)
- [Flow Control](#Flow-Control)
- [Partial and Import](#Partial-and-Import)
- [Functions](#Functions)
- [Math Operations](#Math-Operations)
- [Learn more](#Learn-more)

## Setup
- Install Node.js: https://nodejs.org/en/download/
- Install Sass: `npm install -g sass`
- Compile SCSS to CSS: `sass input.scss output.css`
- Watch for changes: `sass --watch input.scss:output.css`
- Compile entire folder: `sass --watch src/scss:src/css`

```cmd
# Install Sass globally
npm install -g sass

# Compile SCSS to CSS
sass --watch input.scss:output.css

# Compile scss from src/scss to css in src/css
sass --watch src/scss:src/css
```

-----------
<br/>


## Variables
- Normal variable: `$variable-name`: `value;`
- Map variable: `$variable-name`: `(key: value, key: value, ...);`
- Get variable from map: `map-get($variable-name, key);`

```scss
$primary-color: #333; #define variable
$secondary-color: #666;

$front-weights: ( #define map variable
  light: 300,
  normal: 400,
  bold: 700
);


body{
    color: $primary-color;
    font-weight: map-get($font-weights, normal); #Get Variable from map
    
}
```

-----------------------
<br/>

## Nesting
- Nesting allows you to write CSS in a nested structure, which can make it more organized
- However, be careful not to overuse nesting, as it can lead to overly specific selectors and make your CSS harder to maintain. It's generally recommended to keep nesting to a maximum of 3 levels deep.

```scc
.nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  li { display: inline-block; }
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```


-----------------------
<br/>

## Selector
- `&`: Parent selector
- `#{}`: Interpolation
- `#{$variable-name}`: Get variable value and use it as selector
- `@at-root`: Remove parent selector

### Parent selector(&)
```scss
.card {
  &__title {
    color: red;
  }
}
```

```css
#& = .card
.card__title {
  color: red;
}
```

### Interpolation(#{}, #{$variable-name})
```scss
$name: 'button';

.#{$name}{
 color:blue;
}


.button{
 #{&}{
   color:red;
 }
}

.button{
 #{&}__ỉtem{
   color:red;
 }
}
```

```css

.button {
 color: blue;
}


.button .button {
 color: red;
}


.button .button__ỉtem {
 color: red;
}
```

-----------------------
<br/>

## Mixin
- A mixin is a reusable block of code that can be included in other selectors. It can contain any CSS properties and can also accept arguments to make it more flexible.
- To define a mixin, you use the `@mixin` directive followed by the name of the mixin and its content. To include a mixin in a selector, you use the `@include` directive followed by the name of the mixin.
- Reuse code and avoid repetition
- Define: `@mixin mixin-name { ... }`
- use: `@include mixin-name;`
```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}   

.button {
    @include border-radius(5px);
}
```

```css
.button {
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
}
```

-----------------------
<br/>

## Flow Control
- SCSS supports flow control directives such as `@if`, `@else if`, `@else`, `@for`, `@each`, and `@while` to allow for more complex logic in your stylesheets.

### @if
```scss
$theme: dark;

.button {
  @if $theme == dark {
    background: black;
    color: white;
  } @else {
    background: white;
    color: black;
  }
}
```

```css
.button {
  background: black;
  color: white;
}
```

#
### @for
```scss
@for $i from 1 through 3 {
    .item-#{$i} {
        width: 2em * $i;
    }
}
```
```css
.item-1 {
    width: 2em;
}
.item-2 {
    width: 4em;
}
.item-3 {
    width: 6em;
}
```

#
### @each
```scss
$colors: (primary: #333, secondary: #666);
@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;
  }
}
```

```css
.text-primary {
  color: #333;
}   
.text-secondary {
  color: #666;
}
```

#
### @while
```scss
$i: 1;

@while $i <= 3 {
  .m-#{$i} {
    margin: $i * 10px;
  }
  $i: $i + 1;
}
```
```css
.m-1 { margin: 10px; }
.m-2 { margin: 20px; }
.m-3 { margin: 30px; }
```

-----------------------
<br/>

## Partial and Import
- Partials are SCSS files that start with an underscore (`_`) and are meant to be imported into other SCSS files. They are not compiled into CSS on their own.
- To import a partial, you use the `@import` directive followed by the name of the partial without the underscore and file extension.
- SCSS partials is files that start with an underscore (`_`) (`_variables`, `_mixin`).

- Why use partials?
  - Because In css have a lot of code, and it's hard to maintain and organize. 
  - So we can use partials to split the code into smaller files and import them into a main file.


```scss
_variables.scss
_mixins.scss
_header.scss
_buttons.scss
```

### Structure
```scss
scss/
│
├── main.scss
├── _variables.scss
├── _mixins.scss
├── _header.scss
└── _footer.scss


or
scss/
│
├── main.scss
├── _variables.scss
├── _mixins.scss


modules/
│
├── _header.scss
└── _footer.scss
```

### main.scss
- Just compile main.scss to css, and it will import all the partials and compile them together. This way, you can keep your code organized and maintainable.


```scss
@import 'variables';
@import 'mixins';
@import 'header';
@import 'footer';

or 

@import 'variables';
@import 'mixins';
@import 'modules/header';
@import 'modules/footer';
```

#### Note
- New versions use `@use` instead of `@import`.
```scss
@use 'variables';
@use 'mixins';
@use 'modules/header';
@use 'modules/footer';
```

------------
<br/>

## Functions
- SCSS allows you to define your own functions using the `@function` directive.
- Functions can take arguments and return a value, which can then be used in your stylesheets.

```scss
@function function-name($param) {
  // logic
  @return value;
}
```

```scss
@function double($number) {
  @return $number * 2;
}

.box {
  width: double(10px);
}
```

```css
.box {
  width: 20px;
}
```

#

- Some Example of function:
```scss
@function text-color($background) {
  @if $background == black {
    @return white;
  } @else {
    @return black;
  }
}

.box {
  color: text-color(black);
}


#css
.box {
  color: white;
} 
```

#

- Map function example:
```scss
$weights: (
  regular: 400,
  medium: 500,
  bold: 700
);

@function weight($name) {
  @return map-get($weights, $name);
}

.text {
  font-weight: weight(bold);
}

#css
.text {
  font-weight: 700;
}
```

-----------
<br/>

## Math Operations
- SCSS supports basic math operations such as addition (`+`), subtraction (`-`), multiplication (`*`), and division (`/`) on numeric values.

- Reference: https://sass-lang.com/documentation/modules/math


## Learn more
- Home page : https://sass-lang.com/documentation/syntax/
