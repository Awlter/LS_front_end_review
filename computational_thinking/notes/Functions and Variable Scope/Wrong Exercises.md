Wrong Exercises:

- ```
  function say() {
    if (false) {
      var a = 'hello from inside a block';
    }

    console.log(a);
  }

  say();
  ```

  Scoping in JavaScript is function-level, not block-level. Therefore, after hoisting, this code becomes:

- ```
  var a = 'outer';

  console.log(a);
  setScope();
  console.log(a);

  var setScope = function () {
    a = 'inner';
  };
  ```

  ```
  outer
  Uncaught TypeError: setScope is not a function(…)
  ```

- ```
  var a = [1, 2, 3];

  function myValue(b) {
    b[2] += 7;
  }

  myValue(a);
  console.log(a);
  ```

  Recall that JavaScript is pass-by-value. In this exercise, the tricky part is understanding exactly *what* "value" is being passed. In JavaScript, when passing objects (e.g., arrays), *the value is the reference to the object*.

  When `a` is passed to the function on line 7, a local variable `b` is initialized (on line 3) to the same value that `a` is referencing: the array object in the global scope. Therefore, when the program executes the statement `b[2] += 7` on line 4, it is actually being executed on the array object referenced by `a`, mutating that object. Consequently, when the value of `a` is logged on line 8, we can see the result of this mutation: `[1, 2, 10]`.

- ```
  var qux = 2;
  function foo() {
    var qux = 1;
    bar();
  }

  function bar() {
    console.log(qux);
  }

  foo(); 
  ```

- ​