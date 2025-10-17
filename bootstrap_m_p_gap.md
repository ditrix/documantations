## Margin переменные

```scss
// Negative margins
$enable-negative-margins: false;

// Margin utilities
$spacer: 1rem;
$spacers: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
);

// Auto margin
$enable-negative-margins: false;
```

## Padding переменные

```scss
// Padding utilities
$spacer: 1rem;
$spacers: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
);
```

## Grid gutter переменные

```scss
// Grid gutters
$grid-gutter-width: 1.5rem;
$gutters: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
);
```

## Дополнительные переменные

```scss
// Container padding
$container-padding-x: $grid-gutter-width * .5;

// Form control padding
$input-btn-padding-y: .375rem;
$input-btn-padding-x: .75rem;

// Button padding
$btn-padding-y: $input-btn-padding-y;
$btn-padding-x: $input-btn-padding-x;

// Navbar padding
$navbar-padding-y: $spacer * .5;
$navbar-padding-x: $spacer;

// Card padding
$card-spacer-y: $spacer;
$card-spacer-x: $spacer;

// Alert padding
$alert-padding-y: $spacer;
$alert-padding-x: $spacer;
```

## Использование в CSS классах

Эти переменные генерируют следующие утилитарные классы:

- **Margin**: `m-0` до `m-5`, `mt-*`, `mb-*`, `ms-*`, `me-*`, `mx-*`, `my-*`
- **Padding**: `p-0` до `p-5`, `pt-*`, `pb-*`, `ps-*`, `pe-*`, `px-*`, `py-*`
- **Auto margin**: `m-auto`, `mx-auto`, `my-auto`
- **Negative margin**: когда `$enable-negative-margins: true`

Вы можете кастомизировать эти переменные в своем SCSS файле перед импортом Bootstrap.



Bootstrap 5 есть переменные и утилиты для `gap`. 

## Gap переменные

```scss
// Grid gap (для CSS Grid)
$grid-gap: $spacer;

// Gap utilities based on spacers
$spacer: 1rem;
$spacers: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
);
```

## Gap утилиты

Bootstrap 5 предоставляет следующие классы для gap:

### Для CSS Grid
```html
<div class="d-grid gap-0">...</div>
<div class="d-grid gap-1">...</div>
<div class="d-grid gap-2">...</div>
<div class="d-grid gap-3">...</div>
<div class="d-grid gap-4">...</div>
<div class="d-grid gap-5">...</div>
```

### Для Flexbox
```html
<div class="d-flex gap-0">...</div>
<div class="d-flex gap-1">...</div>
<div class="d-flex gap-2">...</div>
<div class="d-flex gap-3">...</div>
<div class="d-flex gap-4">...</div>
<div class="d-flex gap-5">...</div>
```

### Responsive gap утилиты
```html
<div class="d-grid gap-2 gap-md-3 gap-lg-4">...</div>
<div class="d-flex gap-1 gap-sm-2 gap-md-3">...</div>
```

## Column gap и Row gap

Также доступны отдельные утилиты для column и row gaps:

### Column gap
```html
<div class="d-grid column-gap-0">...</div>
<div class="d-grid column-gap-1">...</div>
<div class="d-grid column-gap-2">...</div>
<div class="d-grid column-gap-3">...</div>
<div class="d-grid column-gap-4">...</div>
<div class="d-grid column-gap-5">...</div>
```

### Row gap
```html
<div class="d-grid row-gap-0">...</div>
<div class="d-grid row-gap-1">...</div>
<div class="d-grid row-gap-2">...</div>
<div class="d-grid row-gap-3">...</div>
<div class="d-grid row-gap-4">...</div>
<div class="d-grid row-gap-5">...</div>
```

## Кастомизация gap

Вы можете кастомизировать gap значения в SCSS:

```scss
// Customize gap spacers
$spacers: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
  6: $spacer * 4.5,
  7: $spacer * 6,
);

// Or add custom gaps
$custom-gaps: (
  6: $spacer * 4,
  7: $spacer * 5,
);

// Import Bootstrap after customization
@import "bootstrap/scss/bootstrap";
```

## Пример использования

```html
<!-- CSS Grid с gap -->
<div class="d-grid gap-3">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Flexbox с responsive gap -->
<div class="d-flex flex-wrap gap-2 gap-md-3">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Separate column and row gaps -->
<div class="d-grid column-gap-3 row-gap-2">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <div>Item 4</div>
</div>
```

Gap утилиты особенно полезны для создания равномерных отступов между элементами в grid и flex контейнерах без необходимости использовать margin.
