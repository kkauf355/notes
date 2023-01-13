# TypeScript Basics
TypeScript is JavaScript with syntax for types. TypeScript uses a converter (tsc) to convert a TypeScript file to JavaScript. That means TypeScript's type system only helps you during development (i.e. before the code gets compiled.)

The key difference is: JavaScript uses "dynamic types" (resolved at runtime), TypeScript uses "static types" (set during development)

```bash
npm install -g typescript
```

```bash
tsc app.ts
```

### Core Types
number: 1, 5.3, -10, etc.   - All numbers, no differentiation between integers and floats
string: 'Hi', "Hi", `Hi`    - All text values
boolean: true, false        - Just these two, no "truthy" or "falsy" values

```ts
function add(n1: number, n2: number) {
    return n1 + n2
}

const number1 = 5
const number2 = 2.8

const result = add(number1, number2)
console.log(result)
```

# Compiler & Configuration


# Working with Next-gen JS Code


# Classes and Interfaces


# Advanced Types & TypeScript Features


# Generics


# Decorators


# Full Project


# Working with Namespaces & Modules


# Webpack & Typescript


# Third-Party Libraries & TypeScript


# React + TypeScript & NodeJS + TypeScript


