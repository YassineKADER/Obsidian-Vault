## container

```CSS
.container{
    min-height: 100px;
    width: 100%;
    font-size: 100px;
    background-color: lightgray;

    display: grid;
    grid-template-columns: 100px 100px 100px;/* creating a 3 columns each column has 100px*/
    grid-template-rows: 150px 200px;/*create two rows that had 100px in height*/
}
```

![[Untitled 53.png|Untitled 53.png]]

### output:

![[Untitled 1 29.png|Untitled 1 29.png]]

### columns size:

![[Untitled 2 27.png|Untitled 2 27.png]]

### add gap between columns and rows:

```CSS
grid-column-gap: 20px;
grid-row-gap:20px;
```

  

or use:

```CSS
grid-gap:20px 20px;/*first value gap between rows and last one gap between columns*/
```

  

  

![[Untitled 3 27.png|Untitled 3 27.png]]

use grid-column to control spacing:

```CSS
grid-column:2/4;/*strat from line 2 to 4*/
```

![[Untitled 4 25.png|Untitled 4 25.png]]

we can do the same things with rows also:

```CSS
grid-column: 2/4;
grid-row: 2/4;
```

![[Untitled 5 22.png|Untitled 5 22.png]]

we can combine the `grid-column` and `grid-row` using `gred-area` :

```CSS
grid-area:row-start/column-start/row-end/column-end;
```

to get the same output above:

```CSS
grid-area:2/2/4/4;
```

If grid items aren't explicitly placed with `grid-area` , `grid-column`, `grid-row`, etc., they are automatically placed according to their order in the source code. We can override this using the `order` property, which is one of the advantages of grid over table-based layout.

By default, all grid items have an `order` of 0, but this can be set to any positive or negative value, similar to `z-index`.

```CSS
.d5{
order:-1;
}
```

![[Untitled 6 19.png|Untitled 6 19.png]]

```CSS
.d1{
order:1;
}
```

![[Untitled 7 17.png|Untitled 7 17.png]]

for `grid-template-columns:` we can use `repeat(5,1fr)` inseade of `grid-template-columns:1fr 1fr 1fr 1fr 1fr;`

```CSS
grid-template-columns:repeat(5, 1fr);
```

`**grid-template**`:

`grid-template` is a shorthand property that combines `grid-template-rows` and `grid-template-columns`.

For example, `grid-template: 50% 50% / 200px;` will create a grid with two rows that are 50% each, and one column that is 200 pixels wide.

Try using `grid-template` to water an area that includes the top 60% and left 200 pixels of your garden.

**Align an item Horizontally using** `**justify-self**`**:**

```CSS
.d2{
    justify-self: center;
    background-color: green;
}
```

![[Untitled 8 14.png|Untitled 8 14.png]]

**Align an item Vertically using** `**align-self**`**:**

```CSS
.d2{
    align-self: end;
    background-color: green;
}
```

![[Untitled 9 11.png|Untitled 9 11.png]]

**Align All Items Horizontally using** `**justify-items**`**:**

```CSS
justify-items: center;/*place it on the container*/
```

![[Untitled 10 10.png|Untitled 10 10.png]]

**Divide the grid into an area template:**

```CSS
/*place it on the container*/
grid-template-areas:
    "header header header"
    "advert content advert"
    "footer footer footer";
```

**Place Items in Grid Areas Using the** `**grid-area**` **Property:**

```CSS
grid-area: advert;/*place an area from the areas templates*/
```