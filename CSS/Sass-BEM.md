## BEM

块（block）、元素（element）、修饰符（modifier）

## Example

**Scss**
```scss
.menu {
 list-style: none;
  
 &__item {
   font-weight: bold;
  
   &--selected {
     color: red;
   }
 }
}
```

**CSS**
```
.menu {
  list-style: none;
}

list__item {
  font-weight: bold;
}

list__item--selected {
  color: red;
}
```