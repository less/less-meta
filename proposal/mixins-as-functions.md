> Return variables from mixins

By default, mixins return rulesets (a set of property/value declarations), and in 3.0, variables and mixins defined within a mixin are not visible to the caller's scope. As of Less 3.0, you can, however, specify a return variable in a mixin definition to use the mixin like a function.

Example:

```less
.average(@x, @y): @average {
  @average: ((@x + @y) / 2);
}

div {
  padding: .average(16px, 50px);    // use its return value
}
```

Results in:

```css
div {
  padding: 33px;
}
```

