---
title: JavaScript 和 TypeScript 的语法及使用区别
published: 2025-03-11
description: 'JavaScript 和 TypeScript 的语法及使用区别'
image: './js-vs-ts.png'
tags: [javascript, typescript, frontend]
category: 'Cheatsheets'
draft: false 
lang: ''
---

### 1. 类型声明
#### JavaScript
JavaScript 是动态类型语言，变量在声明时不需要指定类型，类型在运行时确定。
```javascript
// 声明变量
let num = 10;
let str = "hello";
let bool = true;

// 可以随时改变变量的类型
num = "not a number";
```

#### TypeScript
TypeScript 是静态类型语言，变量在声明时可以指定类型，编译器会在编译阶段进行类型检查。
```typescript
// 声明变量并指定类型
let num: number = 10;
let str: string = "hello";
let bool: boolean = true;

// 以下代码会报错，因为类型不匹配
// num = "not a number"; 
```

### 2. 函数参数和返回值类型
#### JavaScript
函数参数和返回值不需要指定类型。
```javascript
function add(a, b) {
    return a + b;
}

// 可以传入任意类型的参数
const result = add(1, 2);
const wrongResult = add("1", "2"); 
```

#### TypeScript
函数参数和返回值可以指定类型，增强代码的可读性和安全性。
```typescript
function add(a: number, b: number): number {
    return a + b;
}

// 正确调用
const result = add(1, 2);

// 以下代码会报错，因为参数类型不匹配
// const wrongResult = add("1", "2"); 
```

### 3. 接口（Interfaces）
#### JavaScript
JavaScript 没有接口的概念，通常使用对象字面量来模拟类似的功能。
```javascript
function printPerson(person) {
    console.log(`${person.name} is ${person.age} years old.`);
}

const person = {
    name: "John",
    age: 30
};

printPerson(person);
```

#### TypeScript
TypeScript 提供了接口来定义对象的结构，用于类型检查。
```typescript
interface Person {
    name: string;
    age: number;
}

function printPerson(person: Person) {
    console.log(`${person.name} is ${person.age} years old.`);
}

const person: Person = {
    name: "John",
    age: 30
};

printPerson(person);
```

### 4. 类（Classes）
#### JavaScript
ES6 引入了类的语法，但类的属性和方法没有类型声明。
```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a noise.`);
    }
}

const dog = new Animal("Dog");
dog.speak();
```

#### TypeScript
TypeScript 中的类可以有类型声明，并且支持访问修饰符（如 `public`、`private`、`protected`）。
```typescript
class Animal {
    // 声明属性类型
    name: string;

    constructor(name: string) {
        this.name = name;
    }

    speak(): void {
        console.log(`${this.name} makes a noise.`);
    }
}

const dog: Animal = new Animal("Dog");
dog.speak();
```

### 5. 枚举（Enums）
#### JavaScript
JavaScript 没有内置的枚举类型，通常使用对象字面量来模拟。
```javascript
const Direction = {
    NORTH: 0,
    EAST: 1,
    SOUTH: 2,
    WEST: 3
};

const currentDirection = Direction.NORTH;
```

#### TypeScript
TypeScript 提供了枚举类型，方便定义一组命名的常量。
```typescript
enum Direction {
    NORTH,
    EAST,
    SOUTH,
    WEST
}

const currentDirection: Direction = Direction.NORTH;
```

### 6. 类型断言
#### JavaScript
JavaScript 没有类型断言的概念。

#### TypeScript
TypeScript 允许开发者手动指定一个值的类型，有两种语法：尖括号语法和 `as` 语法。
```typescript
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;

// 或者使用 as 语法
let strLength2: number = (someValue as string).length;
```

### 7. 可选参数和默认参数
#### JavaScript
JavaScript 函数的参数都是可选的，默认值可以通过逻辑或运算符 `||` 来设置。
```javascript
function greet(name) {
    name = name || "Guest";
    console.log(`Hello, ${name}!`);
}

greet(); 
greet("John"); 
```

#### TypeScript
TypeScript 可以明确指定可选参数和默认参数。
```typescript
function greet(name?: string) {
    name = name || "Guest";
    console.log(`Hello, ${name}!`);
}

greet(); 
greet("John"); 

// 使用默认参数
function greetWithDefault(name: string = "Guest") {
    console.log(`Hello, ${name}!`);
}

greetWithDefault(); 
greetWithDefault("John"); 
```
