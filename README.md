# Rollup AST Plugin Template
Use `@babel/core` to parse the AST of Rollup modules and transform code chunks
as needed.

## `rollup.config.js`
```javascript
import astTemplate from 'rollup-plugin-ast-template';
export default {
  ...
  plugins: [
    astTemplate(...args),
  ],
  ...
}
```