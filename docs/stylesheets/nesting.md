# Nesting

---
Your plain `.css` files automatically support SASS-style nesting:

```scss
.someClass {
  h1 {
    color: green;
  }
  .someOtherClass {
    color: red;
  }
}
```

This is achieved via [postcss-nested](https://github.com/postcss/postcss-nested) and means that, if you only want to do SASS-style nesting, you can avoid the additional overhead of a SASS or LESS parser.

> `node-sass`, the SASS parser, is written in C and is extremely fast.  If you want to use other SASS functionality besides nesting, use it!
