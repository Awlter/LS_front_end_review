# Function Declarations and Function Expressions

Declaration:

```
function foo() {}
```

Expression:

```
var foo = function() {}
```



## Function Declarations

Function declarations are similar to variable declarations. Just as variable declarations must start with `var`, function declarations must start with `function`.



This "functional variable" obeys general scoping rules, and we can use it exactly like other JavaScript variables.

## Function Expressions

A function expression defines a function as part of a larger expression syntax (typically a variable assignment).

```ruby
var hello = function () {
  return 'hello';
};

console.log(typeof hello);    // function
console.log(hello());         // hello
```

In this code, we define an anonymous function (one without a name) and assign it to the variable `hello`. We then use the variable to invoke the function.

```ruby
var foo = function () {
  return function () {   // function expression as return value
    return 1;
  };
};

var bar = foo();         // bar is assigned to the returned function

bar();                   // 1
```

Here, the function `foo` returns an anonymous function. On line 7, we call `foo` and assign the returned function expression to `bar`. We can then call `bar` to get the return value `1` of the anonymous function.

## Named Function Expressions

We can also name function expressions, like this:

```
var hello = function foo() {
  console.log(typeof foo);   // function
};

hello();

foo();                       // Uncaught ReferenceError: foo is not defined

```

However, the name is only available inside the function (i.e., it can only be referenced from within the function's local scope). Though most function expressions use anonymous functions, named function expressions are useful for debugging. The debugger can show the function's name in the call stack, providing a valuable clue. Named function expressions can also be useful for recursive functions.

Named function expressions can look very similar to function declarations, but there is an easy way to differentiate between the two: if a *statement* begins with the `function` keyword, then it is a function declaration; otherwise, it is a function expression. In the following code, we can see that even a minor change (adding parentheses) is enough to turn a function declaration into a function expression:

```
function foo() {
  console.log('function declaration');
}

(function bar() {
  console.log('function expression');
});

foo();    // function declaration
bar(); 
```