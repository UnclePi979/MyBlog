---
title: TypeScript Cheatsheet
published: 2025-03-11
description: 'A Cheatsheet for TypeScript'
image: './ts-logo-128.svg'
tags: ['typescript', '前端']
category: '备忘录'
draft: false 
lang: ''
---

## 基础类型
```typescript
// 基本类型
let booleanValue: boolean = true;
let numberValue: number = 42;
let stringValue: string = "Hello, TypeScript!";

// 数组
let array1: number[] = [1, 2, 3];
let array2: Array<string> = ["a", "b", "c"];

// 元组
let tuple: [string, number] = ["item", 10];

// 枚举
enum Color { Red, Green, Blue }
let color: Color = Color.Red; // 0

// 特殊类型
let anyValue: any = "dynamic";
let unknownValue: unknown = "safe";
let voidValue: void = undefined;
let neverValue: never = (() => { throw new Error() })();
```

## 高级类型
```typescript
// 联合类型
let union: string | number = "text";
union = 123;

// 交叉类型
type Admin = { name: string } & { role: string };

// 类型别名
type ID = string | number;

// 字面量类型
type Direction = "up" | "down" | "left" | "right";

// 可选类型
interface User {
  name: string;
  age?: number; // 可选属性
}

// 函数类型
type AddFunction = (a: number, b: number) => number;
const add: AddFunction = (x, y) => x + y;
```

## 函数与类
```typescript
// 函数参数与返回类型
function greet(name: string): void {
  console.log(`Hello, ${name}!`);
}

// 可选参数与默认值
function multiply(a: number, b: number = 1): number {
  return a * b;
}

// 类
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`${this.name}, ${this.age}岁`);
  }
}

// 继承
class Student extends Person {
  major: string;
  constructor(name: string, age: number, major: string) {
    super(name, age);
    this.major = major;
  }
}
```

## 接口与泛型
```typescript
// 接口
interface Shape {
  area(): number;
}

class Circle implements Shape {
  radius: number;
  constructor(radius: number) { this.radius = radius; }
  area() { return Math.PI * this.radius ** 2; }
}

// 泛型
function identity<T>(arg: T): T {
  return arg;
}
let output = identity<string>("myString");
```

## 模块与装饰器
```typescript
// ES模块
export const PI = 3.14159;
import { PI } from "./math";

// 装饰器
function Logger(target: any) {
  console.log("Class created:", target.name);
}

@Logger
class MyClass {}
```

## 类型断言
```typescript
let value: unknown = "some string";
let length: number = (value as string).length;
// 或
let length: number = (<string>value).length;
```

## 常见错误与最佳实践
1. **避免使用`any`类型**：尽可能使用更具体的类型
2. **启用严格模式**：`"strict": true` 在tsconfig.json中
3. **使用类型别名**：提高代码可读性
4. **检查null/undefined**：使用`!`非空断言运算符需谨慎
5. **利用类型推断**：减少冗余类型声明

> 提示：使用 `tsc --init` 生成配置文件，根据项目需求调整 `tsconfig.json` 中的编译选项。