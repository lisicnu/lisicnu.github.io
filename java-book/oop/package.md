## Package
- 解决命名冲突
  - 如果小明写了一个`Person`类，小红也写了一个`Person`类，现在，小白既想用小明的`Person`，也想用小红的`Person`, 怎么办？

- 每个`class` 都应该有一个 `package`，没有虽然不会错误，但是会加大发生冲突的可能性。
- 位于同一个包的类，可以访问包作用域的字段和方法。不用`public`、`protected`、`private`修饰的字段和方法就是包作用域。
  - 即通常看到的 一个 `package` 下可以直接使用， 而不需要单独的 `import`
- 要使用不同 `package` 下的 `class` 需要单独的 `import`
  - e.g.  import xx.xx.x.x