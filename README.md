# A real three-dimensional _CSS Grid_ grid-system

Use `css-grid-system.scss` to generate a real three-dimensional **CSS Grid** grid-system.

Notes:

1. Unlike the traditional columnar 12-col grid systems, here **you get to choose** how many columns and rows you need for your layout: 1,2,3,4,5 or 6 (max).
2. You will probably never need to use more than 6 columns or 6 rows (in fact, usually you will use less than 6). But if you do, then change the `$grid--max-cols` variable. [**Warning:** don't go much higher than 6, because this will massively increase your outputted CSS!]
3. Per grid-item justification and alignment.
4. RTL and LTR languages are supported.
5. Three dimensions -- because grid items can overlap.

## Grid system (at all viewport widths)

### Grid Setup Classes

* `.grid`
* `.grid--cols-1` ... `.grid--cols-6` -- choose to have 1,2,3,4,5 or 6 columns.
* `.grid--gap`

### Grid-item Classes

* **Column tracking** -- multiple permutations, e.g.:
	- `.col--1-3` -- starts column track 1 and ends column track 3 = spans columns 1-2.
	- `.col--3-6` -- starts column track 3 and ends column track 6 = spans columns 3-5.


* **Row tracking** -- multiple permutations, e.g.:
	- `.row--1-6` -- starts row track 1 and ends row track 6 = spans rows 1-5.
	- `.row--2-4` -- starts row track 2 and ends row track 4 = spans rows 2-3.

* **Justification (horizontal)** -- within grid area:
	-  `.justify--left`
	-  `.justify--right`
	-  `.justify--center`
	-  `.justify--stretch`

* **Alignment (vertical)** -- within grid area:
	-  `.align--top`
	-  `.align--bottom`
	-  `.align--center`
	-  `.align--stretch`

## Responsive (viewport width) modifiers

### Grid Classes

* `.grid--cols-1` ... `.grid--cols-6` -- all viewport widths
* `.grid-md--cols-1` ... `.grid-md--cols-6` -- 768px width up
* `.grid-lg--cols-1` ... `.grid-lg--cols-6` -- 1024px width up

### Grid-item Classes

* All viewport widths:
	- `col-`
	- `row-`
	- `justify-`
	- `align-`
* Viewport widths 768px up:
	- `col-md-`
	- `row-md-`
	- `justify-md-`
	- `align-md-`
* Viewport widths 1024px up:
	- `col-lg-`
	- `row-lg-`
	- `justify-lg-`
	- `align-lg-`

## Examples

### Simple

This grid will have 3 columns. The 6 grid items will wrap over 2 rows.

```
<div class="grid grid--cols-3">
  <div>First grid item</div>
  <div>Second grid item</div>
  <div>Third grid item</div>
  <div>Fourth grid item</div>
  <div>Fifth grid item</div>
  <div>sixth grid item</div>
</div>
```

### Row spanning

2 columns and 3 rows. The first column will be occupied by the first grid item for its full height (spanning 3 rows). The second grid column will have 3 items on 3 rows.

```
<div class="grid grid--cols-2 grid--gap">
  <div class="col--1-2 row--1-4">First grid item</div>
  <div class="col--2-3 row--1-2">Second grid item</div>
  <div class="col--2-3 row--2-3">Third grid item</div>
  <div class="col--2-3 row--3-4">Fourth grid item</div>
</div>
```

### Easy Layout (all viewport widths)

Full width header and footer. Main section left 2/3 width. Sidebar 1/3 width.

```
<div class="grid grid--cols-3 grid--gap">
  <header class="col--1-4">Header</header>
  <main class="col--1-3">Main article</main>
  <div class="col--3-4">Sidebar</div>
  <footer class="col--1-4">Footer</footer>
</div>
```

### Complex Layout (viewport widths 768px up) -- exemplifying grid nesting, column re-ordering and center-justifying:

* Header full width but centered on small viewports
* Sidebar nav
	- as full width block (below header) on small viewports
	- left 1/4 width on medium viewports
	- right 1/4 width on large viewports
* Main article
	- as full width block on small viewports
	- right 3/4 width on medium viewports
	- left 3/4 width on large viewports
* Three nested items (within main article)
	- stacked on small viewports
	- in a row on medium viewports up
* Footer full width but centered on all viewports

```
<div class="grid grid--cols-1 grid-md--cols-4 grid--gap">
  <header class="col--1-2 col-md--1-5 justify--center justify-md--left row-1-2">Header</header>
  <div class="col--1-2 col-lg--4-5 row-md--2-3">Sidebar nav</div>
  <main class="col--1-2 col-md--2-5 col-lg--1-4 row-md--2-3">
    <h1>Article</h1>
    <section class="grid grid--cols-1 grid-md--cols-3 grid--gap">
      <div class="col-md--1-2">Nested</div>
      <div class="col-md--2-3">Nested</div>
      <div class="col-md--3-4">Nested</div>
    </section>
  </main>
  <footer class="col--1-2 col-md--1-5 justify--center">Footer</footer>
</div>
```
