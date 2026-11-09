# Type Aliases vs Interfaces in TypeScript

## Introduction
Both `type` and `interface` describe the shape of data in TypeScript, and they overlap heavily. Knowing their differences helps you choose the right one.

## Key Differences
Interfaces describe object shapes and can be extended with `extends`. They also support declaration merging, meaning two interfaces with the same name combine into one.

```ts
interface User {name: string}
interface User {age: number} //merged: {name: string; age: number}
```

Type aliases are more flexible. They can name unions, tuples, primitives and intersections, which interfaces cannot.

```ts
type Id = string | number;
type Point = [number, number];
type Admin = User & {role: string};
```

Unlike interfaces, a type alias canot be reopened, so declaring it twice causes an error.

## When to Choose
Use `interface` for object, class contracts (`implements`) and public APIs that others may extend. Use `type` for unions, tuples, mapped or conditional types, and complex function signatures.

## Conclusion
For plain objects either works, so stay consistent across your codebase. Default to `interface` for objects and switch to `type` when you need its extra power.