# Javascript Primer

## Var vs Let vs Const

- `var` - function scoping
- `let` - block scoping
- `const` - constant, block scoping

```js
// var does not have block scope
var name = 'Ryan'
if (true) {
  var name = 'Michael'
  name // 'Michael'
}
name // 'Michael'

// let has block scope
let name = 'Ryan'
if (true) {
  let name = 'Michael'
  name // 'Michael'
}
name // 'Ryan'

// const has block scope too
const name = 'Ryan'
if (true) {
  const name = 'Michael'
  name // 'Michael'
}
name // 'Ryan'

// let can be reassigned
let isOpen = true
isOpen = false
isOpen // false

// const cannot be reassigned
const isOpen = true
isOpen = false // throws error
```

## Tempalte String


```js
// concat string
const name = 'Net'
const str = 'instead of ' + name + ' !!'

// template string
const str = `you can do ${name} !!`
```

## Function

```js
function add(name) {
  return x + y
}

const add = function(x, y) { return x + y }

// becomes
const add = (x, y) => { return x + y }

// which can be shorter with explicit expression return
const add = (x, y) => x + y

// if we want multiline, we can create an expression with ()
const add = (x, y) => (
  x + y
)
```

## Pure function

- No side effect
- No mutating parameters

```js
// Pure
function add(x, y) {
  return x + y
}
add(1,2) // 3

// Impure
function addItem(arr, item) {
  arr.append(item)
  return arr
}
let numbers = [1,2,3]
addItem(numbers, 4) // 1,2,3,4
number // 1,2,3,4 **Side effect !!**

// Pure
function addItem(arr, item) {
  return arr.concat([item])
}

let numbers = [1,2,3]
addItem(numbers, 4) // 1,2,3,4
number // 1,2,3
```


## Map, Filter, Reduce

```js
const numbers = [ 1, 2, 3, 4, 5 ]

// map converts an array to a new, transformed array
const doubled = numbers.map((number) => {
  return number * 2
})
doubled // [ 2, 4, 6, 8, 10 ]

// filter, return false to remove from an array
const lessThan3 = numbers.filter((n) => {
  return n < 3
})
lessThan3 // [ 1, 2 ]

// remember, that can be super short
const lessThan3 = numbers.filter(n => n < 3)

// reduce, sum of members in array
const sum = numbers.reduce((sum, n) => {
  return sum + n
}, 0)
```

## Call, Apply, Bind

```js
function say(word, toPerson) {
  return `${this.name} says ${sayTo} to ${toPerson}`
}

let person = {
  name: "Net"
}

sayHello("YOLO!!", "Luke") // Throw name of undefined
window.name = "Net"
sayHello("YOLO!!", "Luke") // Net say YOLO!! to Luke


sayHello.call(person, "YOLO!!", "Luke") // Net say YOLO!! to Luke
sayHello.apply(person, ["YOLO!!", "Luke"]) // Net say YOLO!! to Luke
const sayFn = sayHello.bind(person)
sayFn("YOLO!!", "Luke") // Net say YOLO!! to Luke

```

## Destructuring

```js
const obj = { x: 1, y: 2 }

// instead of:
const x = obj.x
const y = obj.y

// we can "destructure" the values off
const { x, y } = obj
x // 1
y // 2

// you can use this all over the place, like function parameters
function add({x, y}) { return x + y}
add({x: 3, y: 4}) // 7
```

## Modules

```js
// instead of cjs
var React = require('react')

// we use ES modules
import React from 'react'
import ReactDOM from 'react-dom'

// and with destructuring to boot!
import { render } from 'react-dom'
```
