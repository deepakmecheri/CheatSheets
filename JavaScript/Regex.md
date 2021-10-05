# Regular Expressions
[MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)

## Creating a regular expression
This can be acheived in two ways
- Regular expression literal
  ```javascript
  let re = /ab+c/;
  ```
- With `RegExp` constructor
  ```javascript
  let re = new RegExp('ab+c');
  ```
> Note: Use the constructor function when you know the regular expression pattern will be changing, or you don't know the pattern and are getting it from another source, such as user input

