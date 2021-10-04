- [Bootstrap Theme Files](#bootstrap-theme-files)
- [Overriding Bootstrap 4 Theme.](#overriding-bootstrap-4-theme)

## Bootstrap Theme Files

In this article, I will show you how to override the default Bootstrap theme with your own custom theme variables.

First, we need to understand how **Bootstrap 4 theme** files work.

So, after installing Bootstrap 4 via [NPM](https://www.npmjs.com/package/bootstrap)

```
npm i bootstrap@4
```

Navigate to **node_modules/bootstrap/scss/\_variables.scss** file.

> We will not make our modifications inside this file we will just take a quick look to understand how Bootstrap works and then we will make our modification in a proper way.

In this file, you will find every variable used in Bootstrap.
Scrolling down we will see some pre-defined color variables:

\_variables.scss

```scss
$blue: #007bff !default;
$indigo: #6610f2 !default;
$purple: #6f42c1 !default;
$pink: #e83e8c !default;
$red: #dc3545 !default;
$orange: #fd7e14 !default;
$yellow: #ffc107 !default;
$green: #28a745 !default;
$teal: #20c997 !default;
$cyan: #17a2b8 !default;
```

And then it uses these variable with its theme variables:

```scss
$primary: $blue !default;
$secondary: $gray-600 !default;
$success: $green !default;
$info: $cyan !default;
$warning: $yellow !default;
$danger: $red !default;
$light: $gray-100 !default;
$dark: $gray-800 !default;
```

After that, it creates an [SCSS Map](https://sass-lang.com/documentation/values/maps):

```scss
$theme-colors: () !default;
$theme-colors: map-merge(
  (
    "primary": $primary,
    "secondary": $secondary,
    "success": $success,
    "info": $info,
    "warning": $warning,
    "danger": $danger,
    "light": $light,
    "dark": $dark,
  ),
  $theme-colors
);
```

## Overriding Bootstrap 4 Theme.

```scss
// Required
@import "node_modules/bootstrap/scss/functions";
@import "node_modules/bootstrap/scss/variables";

// Adding/Overriding Colors
$theme-colors: map-merge(
  $theme-colors,
  (
    "secondary": #ddc22b,
    "tertiary": #e059c3,
    "quaternary": #25a1a1,
  )
);

// Overriding/Adding Spacers
$spacers: map-merge(
  $spacers,
  (
    10: $spacer * 10,
  )
);
$sizes: map-merge(
  $sizes,
  (
    10: 10%,
    90: 90%,
  )
);

// Bootstrap and its default variables
@import "node_modules/bootstrap/scss/bootstrap";
```
