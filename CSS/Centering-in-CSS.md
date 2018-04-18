## Horizontally

### inline or inline-* elements
 within a block-level parent element
```CSS
.center-children {
  text-align: center;
}
```

### block-level element

- a block-level element in a row (it should be set a width)
```CSS
.center-me {
  margin: 0 auto;
}
```

- block-level elements in a row
```CSS
/* inline-block */
.inline-block-center {
  text-align: center;
}

/* divs are the children of .inline-block-center */
.inline-block-center div {
  display: inline-block;
}
```

```CSS
/* flex */
.flex-center {
  display: flex;
  justify-content: center;
}
```

## Vertically

### inline or inline-* element
- line-height
```CSS
main div {
  height: 100px;
  line-height: 100px;
  white-space: nowrap;
}
```

- table
```CSS
/* table */
table td {
  vertical-align: middle;
}

/* or */
.center-table {
  display: table;
  height: 250px;
  width: 240px;
}
.center-table p {
  display: table-cell;
  vertical-align: middle;
}
```

- pseudo element
  a full-height pseudo element is placed inside the container and the text is vertically aligned with that
```CSS
.ghost-center {
  position: relative;
}
.ghost-center::before {
  content: " ";
  display: inline-block;
  height: 100%;
  width: 1px;
  vertical-align: middle;
}
.ghost-center p {
  display: inline-block;
  vertical-align: middle;
}
```

### block-level element
- absolute
```CSS
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
```

- flex box
```CSS
.parent {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

## Both Horizontally and Vertically

### absolute
```CSS
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

### flex box
```CSS
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### grid
```CSS
.parent {
  display: grid;
  height: 200px;
}
p {
  margin: auto;
}
```