# Compile class fields to `get` methods
Uses Babel to transpile public class fields to `get` methods for compilation by
Closure Compiler, which currently does [not support them](https://github.com/google/closure-compiler/issues/2731).

## `rollup.config.js`
```javascript
import classFieldsToGetters from 'rollup-plugin-class-fields-to-getters';
export default {
  ...
  plugins: [
    ...
    classFieldsToGetters(),
    ...
  ],
  ...
}
```

## Input
```javascript
class MyTestClass {
  static myStaticProp1 = 'staticProp';
  static myStaticProp2 = 'staticProp';
  static myStaticProp3 = 'staticProp';
  myProp1 = 'instanceProp';
  myProp2 = 'instanceProp';
  myProp3 = 'instanceProp';
}
```

## Output
```javascript
class MyTestClass {
  static get myStaticProp1() {
    return 'staticProp';
  }

  static get myStaticProp2() {
    return 'staticProp';
  }

  static get myStaticProp3() {
    return 'staticProp';
  }

  get myProp1() {
    return 'instanceProp';
  }

  get myProp2() {
    return 'instanceProp';
  }

  get myProp3() {
    return 'instanceProp';
  }

}
```