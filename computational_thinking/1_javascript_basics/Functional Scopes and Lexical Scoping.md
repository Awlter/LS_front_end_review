# Functional Scopes and Lexical Scoping

## Function Scope

In JavaScript, every Function creates a new variable scope.

The code within one scope can access any variables in the same scope or **any surrounding scope**. This works no matter how deeply nested a Function is.

## Closures

When we define a Function, it retains access to, or *closes over*, the variable scope currently in effect. We call this *creating a closure*. A closure retains references to everything that is in scope when the closure is created, and retains those references for as long as the closure exists. This means the Function can still access those references wherever we invoke the Function.



The **value** of a variable can change after creating a closure that includes the variable. When this happens, the closure sees the new value; the old value is no longer available

## Lexical Scoping(Static Scoping)

JavaScript uses *Lexical Scoping* to resolve variables; it uses the structure of the source code to determine the variable's scope. That is, **the source code defines the scope**. At any point in a JavaScript program, there is a hierarchy of scopes from the local scope of the code up to the program's global scope.

When JavaScript tries to find a variable, it searches this hierarchy from the bottom to the top. It stops and returns the first variable it finds with a matching name. This means that variables in a lower scope can *shadow*, or hide, a variable with the same name in a higher scope.

Most mainstream programming languages use lexical scoping rules (also called "static scoping"). Some languages use "dynamic scoping" instead, or make dynamic scoping a choice. Dynamic scoping uses the scope of the calling function as the outer scope of a function; we won't get into dynamic scoping here.

## Adding Variables to the Current Scope

These are three ways to create a variable in the current scope. The first uses the `var` keyword; the second uses arguments passed to a Function. The third is the function declaration itself, which creates a variable with the same name as the function (this will be explained in more detail in the next assignment).

## Variable Assignment

Variable scoping rules apply to both assignment and referencing equally. This code:

```
country = 'Liechtenstein';

```

checks the current scope and then each higher scope, looking for a variable with the name `country`. JavaScript sets the first `country`variable it finds to `"Liechtenstein"`.

If JavaScript can't find a matching variable, **it creates a new global variable instead**. This is rarely what you want; it can be the source of subtle bugs.

## Variable Shadowing



To wrap up:

Remember these important variable scoping rules:

- Every Function declaration creates a new variable scope.
- All variables in the same or surrounding scopes are available to your code.