---
layout: post
title:      "Overview of Variables, Hoisting, and Scope"
date:       2019-08-14 10:01:17 -0400
permalink:  overview_of_variables_hoisting_and_scope
---


What is a variable? According to Eloquent JavaScript, a binding or a **variable** is used by JavaScript to catch or hold *values*. Before the implemetation of ES6, `var` was the only key word that was used to declare variables. ES6 added two new key words for variable declaration; `let` & `const`. Each variable has a **scope**, which is the part of the program where the variable is visible. Variables can either have *global* or *local* scope. *Global* variables are variables that exist only once in a script, and are visible in every function. *Local* variables exist only in the block in which they are declared in. **Hoisting** in JavaScript is where variables and *function declarations* are moved to the top of their scope before code execution. Functions and variables are moved to the top of their scope when they are declared, regardless of whether their scope is global or local. This blog will discuss the differences between `var`, `let`, and  `const` in regards to **Scope**, and **Hoisting**.



**`var`**

`var` declarations can be globally and locally scoped; `var` is globally scoped when declared outside a function and locally scoped when it is declared within a function. For example:
```
var a = "nike"

function shoes() {
   var b = "adidas"
}

console.log(b) // error: b not defined
```
`a` is globally scoped because it exists outside a function while `b` is locally scoped and can only be accessed in the shoes function. `console.log(adidas)` will return an error because it is not available outside the function.

`var` can be reassigned and redeclared.  This means that there won't be an error when it is reassigned or redeclared:
```
    var color = "blue";
    color = "red"; // returns "red"
```



**`let`**

`let` declarations are *block scoped*. A block is code wrapped in curly braces. This means that a `let` variable declared in a block is only available in that block. This example will return an error because 'a' is used outside its block:

```
function pokemon() {
	if (true) {
	let a = "bulbasaur" 
	}
}
console.log(a) // a is not defined
```

`let` variables can be reassigned within its scope. However, unlike `var`, it cannot be redeclared.
This code works:
```
let pokemon = "charmander"
pokemon = "squirtle" // returns "squirtle"
```

while this will return an error:
```
let pokemon = "charmander"
let pokemon = "squirtle" // error, identifier pokemon has already been declared
```

Also, if the same `let` variable is defined in different scopes, there will not be an error since both variables were declared in different scopes:
```
let pokemon = "mew"
if(true) {
  let pokemon = "mewtwo"
  console.log(pokemon) // returns "mewtwo"
}
console.log(pokemon) // returns "mew"
```



**`const`**

`const` declarations maintain constant values. Just like `let`, variables declared with `const` are block scoped. Unlike `let` however, `const`variables cannot be reassigned or redeclared. For example:
```
const designer = "helmut lang"
const designer = "dries van noten" // error, identifier designer has already been declared
```
and
```
const designer = "helmut lang"
designer = "dries van noten" // error, assignment to constant variable
```
both return errors. `const` variables must be initialized at the time of declaration.



**Hoisting of `var` , `let` , and `const` **

`var`variables are hoisted to the top of its scope and is initialized. Here's an example of hoisting with `var`:

```
function singer(){
  console.log('My favorite singer is', singer)

  var singer = "Britney Spears"
}

singer() // returns "My favorite singer is undefined"
```


`let` and `const` variables are also hoisted to the top of their scopes but *are not* initialized. Here's an example:

```
function singer(){
  console.log('My favorite singer is', singer)

  let singer = "Britney Spears"
}

singer() // error, cannot access 'singer' before initialization
```

For the code to work, the declaration has to occur before the console.log:
```
function singer(){
  let singer = "Britney Spears"
  console.log('My favorite singer is', singer)
}

singer() // returns "My favorite singer is Britney Spears"
```

To highlight the main differences of the three keywords:
* `let`and `const`declarations are both block scoped while `var` declarations are function or globally scoped.
* `var` variables can be reassigned and redeclared, `let` variables can be reassigned but not redeclared, `const` variables cannot be updated nor redeclared.
* `var` and `let` can be declared without being initialized while `const` must be initialized when declared.
* `var`, `let`, and `const` are all hoisted to the top of their scope. `var` variables are initialized with undefined while `let` and `const` variables are not initialized.

Thank you!
