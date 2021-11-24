# Klippa Responsive SCSS

This is the SCSS library used for [@klippa/ngx-grid](https://github.com/klippa-app/ngx-grid) and for other
responsive design in Klippa projects.

## How to use

First install it:

```
$ yarn add @klippa/responsive-scss
```

Then include it where you need it with @use.

```scss
@use "~@klippa/responsive-scss";

$default-color: red;
$small-color: green;
$large-color: blue;

.my-awesome-container {
  color: $default-color;
  
  // for all screen widths >= sm.
  @include responsive-scss.responsive(sm) {
    color: $small-color; 
  }
  
  // for all screen widths >= lg.
  @include responsive-scss.responsive(lg) {
    color: $large-color;
  }
}

@mixin set-content($breakpoint, $min-width) {
    content: "Screen is currently #{$breakpoint} and has a minimum width of #{$min-width}";
}

h1 {
  // create @media blocks for all breakpoints and @include set-content in each one.
  @include responsive-scss.allBreakpoints using ($breakpoint, $min-width) {
    @include set-content($breakpoint, $min-width);
  }
}
```

The default breakpoints can be overwritten or extended like so:

```scss
// only create breakpoints xs, sm, md, and over-9000
@use "~@klippa/responsive-scss" with (
  $breakpoints: (
    xs: 0px,
    sm: 200px,
    md: 300px,
    over-9000: 9001px,
  )
);
```


The default breakpoints are:

```scss
$breakpoints: (
        xs: 0px,
        sm: 576px,
        md: 768px,
        lg: 992px,
        xl: 1200px,
        xxl: 1440px,
) !default;
```
