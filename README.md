# Humble grid

A modern and minimal grid system built on top of CSS grid.

Main features:

📦 Modular

🎈 Lightweight (minified and gzipped core module is just 353 bytes)

⚡ Powerful

🎨 Very customizable

⏱️ Set up in less than no time

## Demo

Demo is coming soon.


## Getting started

1. Install humble grid

```
npm install humble-grid

or

yarn add humble-grid
```

2. Import the grid into your SCSS file

```scss
@import 'path/to/your/node/modules/humble-grid/humble-grid.scss';
```

3. Customise it!


## Core

The core module provides minimal amount of settings needed for creating a fully working grid system.

It contains of: container, columns and breakpoints.

### Default variables

#### Columns

By default `humble grid` relies on 12 column system, but it can be easily overriden by in your custom config.

Example:

```scss
$grid-columns: 6;
```

#### Container

Default container max-size is 1200px. If you want to adjust it simply override the default value:

Example:

```scss
$grid-container: 1120px;
```

#### Breakpoints

Not every project needs many breakpoints. Some of them don't.
To keep `humble grid` as flexible as it's possible you start with only 1 predefined breakpoint:

```scss
$grid-breakpoints: (
  medium: 64em,
);
```

...that you can extend it as you wish:

```scss
$grid-breakpoints: (
  medium: 64em,
  large: 90em,
);
```

Output code will include set of `@${breakpoint}` classes that you can later use in your project:

```html
<div class="grid grid__container">
  <div class="grid__cell grid__cell--4@medium grid__cell--6@large"></div>
  <div class="grid__cell grid__cell--6@medium grid__cell--6@large"></div>
</div>
```

Naming convention is up to you. The breakpoints `@handle` can be customised too. So:

```scss
$grid-breakpoints: (
  m: 64em,
  xl: 90em,
);
```

Will turn into:

```html
<div class="grid grid__container">
  <div class="grid__cell grid__cell--4@m grid__cell--6@xl"></div>
  <div class="grid__cell grid__cell--6@m grid__cell--6@xl"></div>
</div>
```

You can add as many breakpoints as you need for the specific project. There's no limitation.
Example setup for a complex project could look like this:

```scss
$grid-breakpoints: (
  tiny: 35.5em, // ~ 568px
    small: 48em, // ~ 768px
    medium: 64em, // ~ 1024px
    large: 80em, // ~ 1280px
    huge: 90em, // ~ 1440px
);
```

## Extensions

The core module includes only minimal amount of code needed for setting up a fully working grid.
Although it's a great solution for many projects it may not be enough for all of them.
At some point you may need a bit more complex structure and this is where `humble grid`'s extensions come handy.

To extend your grid with extra functionality just add modules you need to the `$grid-extensions` array.

This is what you would do if you wanted to use all of them:

```scss
$grid-extensions('offset', 'grid-gap', 'auto-fit');
```

### offset

You can include it in your project like so:

```scss
$grid-extensions('offset');
```

Above code will enable a set of offset classes starting with: `grid__cell--start` and `grid__cell--end` that you can use to position your grid cells.

Use `grid__cell--start-${track}@${breakpoint}` classes to define a cell starting position.

Example:
```html
<div class="grid">
  <div class="grid__cell grid__cell--4@medium grid__cell--start-3@medium"></div>
</div>
```

or `grid__cell--end${track}@${breakpoint}` classes to define grid end position:

```html
<div class="grid">
  <div class="grid__cell grid__cell--4@medium grid__cell--end-11@medium"></div>
</div>
```

### grid gap

By default there is no space between the columns. Enabling `grid gap` extension makes it easy to create gutters in your layout:

You can enable it like so:

```scss
$grid-extensions('grid-gap');
```

Customise it by providing custom values for `$grid-gaps` map.

```scss
$grid-gaps: (
  tiny: 1rem,
  huge: 3rem,
);
```

The example above would create a set of `grid gap` related classes for each of declared breakpoint [`.grid--gap-${key}@${breakpoint}`]:

```css
grid--gap-tiny, grid--gap-huge
grid--gap-tiny@medium, grid--gap-huge@medium [for default breakpoint values]
```

### auto-fit

Add any number of columns to your container and grid will figure out how to place them in a best possible way.

Enable `auto-width` columns in your project like so:

```scss
$grid-extensions('auto-fit');
```

You can setup minimal size for a column by providing its sizes in the config:

```scss
$grid-auto-fit-cols: (
  xs: 1rem,
  s: 2rem,
);
```

Above sample will create set of classes that you can use on various breakpoints: `grid--auto-fit-#{$name}` and `.grid--auto-fit-#{$name}\@#{$breakpoint}`

Example:

```html
<div class="grid grid--auto-fit-xs grid--auto-fit-xs@medium">
  <div class="grid__cell"></div>
  <div class="grid__cell"></div>
  <div class="grid__cell"></div>
  <div class="grid__cell"></div>
</div>
```
