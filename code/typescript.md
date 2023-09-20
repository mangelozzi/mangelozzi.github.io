TypeScript
==========

- Summaries from reading: https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html

Typing Simple Variable
----------------------

- Even though we didn’t tell TypeScript that msg had the type string it was able to figure that out. That’s a feature, and it’s best not to add annotations when the type system would end up inferring the same type anyway.

```ts
// not recommended, as the type can be inferred
const myString: string = "Hey there"

const myString = "Hey babe"   // Much better
```

Typing an Object
----------------

- Define the type of the object like this:

```ts
interface User {
    name: string,
    id: number,
}
```

```ts
const user: User = {
    name: "Bob",
    id: 0,
};
```

- Or using classes:
```ts
class UserAccount {
    name: string;
    id: number;
    constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
    }
}
const user:User = new UserAccount("Joe", 1)
```

TYPE ALIAS vs INTERFACE
-----------------------

```ts
interface user {
    name: string,
    id: number,
}
```

or could use a type alias by using the keyword `type`

```ts
type User {
    name: string,
    id: number,
}
```

- Both interface and type can be used to define object types, but they have some differences in their behavior and usage.
- Interfaces can extend other interface with the extends keyword.
- Classes can implement interfaces with the `implements` keyword.
be extended and merged, can't do so with type aliases.
- Conversely, types defined with `type` cannot extend other types or be implemented by classes.
- Aliases support nesting other types to create complex types. Interfaces does not support this.
    - Also support the `|` union operator.
- Interface can define a call signature.
- Interfaces are used to define the shape of an object when view from the outside.
- If defining the shape of an object from the inside, use a type alias.
- A type alias cannot be redefined. An interface can be extended.
- A new alias can be created from an existing alias and expanded upon with new properties by using the `& operator`, e.g.:
    ```ts
    type Animal = { name: string }
    type Bear = Animal & { honey: boolean }
    ```

In summary, type is more flexible and suitable for creating aliases and combining types, while interfaces are more powerful for extending, implementing, and merging declarations. 


FUNCTIONS
---------

```ts
function delUser(user: User) {
    // Typing an arg
}
```

- TS can infer the return type, but it is useful for documentation

```ts
function getMike(): User {
    // Typing the return value
}
```

### Contextual Typing

```ts
const names = ["Alice", "Bob", "Eve"];
// Contextual typing applies to arrow and anonymous functions 
names.forEach((s) => {
  console.log(s.toUpperCase());
});
```


BASICS
------

- When defining a type, prefix it with the `type` keyword.
- Primitive types are `string`, `number`, `boolean`
    - The primitive types are always lowercased
    - The less common `symbol` and `bigint` are also available
- Arrays, `string[]` or `Array<string>`
    - Note `[number]` something different, a tuple
- `any` special value that means don't type check
    - You can access any properties/call of a `any` type, and those properties will also be of type `any`
    - The any type is useful when you don’t want to write out a long type just to convince TS that a particular line of code is okay.


COMPOSING TYPES
---------------

### Unions

- Unions can define a set/enumerated list of string or numbers literals

```ts
type WindowStates = "open" | "closed" | "maximized";
type oddNumbers = 1 | 3 | 5 | 7 | 9;
```

- Unions can also handle different types, e.g. to handle a string or an array of strings:

```ts
function wrapItUpYo(s: string | string[]): string[] {
    if (typeof s === "string") return [s]
    else if (Array.isArray(s)) return s
    else throw "you must be crazy"
}
```

### Generics

- Add variables to types.
- A common example is an array, that without a generic specified it could contain anything

```ts
const stringArray: Array<string>;
const numberArray: Array<number>;
const objArray: Array<{name: string}>;
```

- Can define own types that use generics:

```ts
interface Bag<Type> {
    add: (obj: <Type>) => void,
    get: () => Type,
}

// Tell typescript a variable exists, and not worry about where it came from:
declare const bag: Bag<string>;

// Here TS know things is of type string
const thing = bag.get()

thing.add(123) // Type error
```

STRUCTURAL TYPE SYSTEM
----------------------

- TS uses duck typing to determine if certain types are the same:

```ts
interface Point {
    x: number,
    y: number,
}

function printPoint(p:Point) {
    console.log(`x: ${p.x}, y:${p.y}`)
}

const duckTypedPoint = {x: 1, y: 2}
printPoint(duckTypedPoint)  // Although not explicitly typed, TS accepts it

const duckTypedPoint2 = {x: 1, y: 2, z:777}
printPoint(duckTypedPoint2)  // Works aswell, because only the required props are checked

```

- There is difference between how classes and objects conform to types:
```ts
class VirtualPoint {
    x: number;
    y: number;
    constructor(x:number, y:number) {
        this.x = x;
        this.y = y;
    }
}
const virtualPoint = new VirtualPoint(4,5);
printPoint(virtualPoint)  // Passes duck typing regardless of the implementation details
```

TSC COMPILER
------------

- By default emits a very old version of the ECMAScript
    - Use `--target es2015` to use the usual ES6
- Use `--noImplicitAny` to make TS raise an error if it can't infer the type. Explicit use of `any` is okay.
- Use `--strictNullChecks` to make TS raises an error if say one expects a `.find()` to always find value, but it might not, and hence one should handle what happens if `undefined` is returned from the `find()`.

INLINE TYPES
------------
- Could create an interface of the type of specify it inline:


```ts
function printPoint(p: {x: number, y:number}) {
    console.log(`x: ${p.x}, y:${p.y}`)
}
```

OPTIONAL PROPERTIES
-------------------

```ts
function printName(obj: {first: string, last?: string}) {
    // Using the optional chaining operator
    console.log(`Hi {obj.first.toUpperCase()} {obj?.last.toUpperCase()}`)
    //...
}
printName({first: "Joe", last: "Soap"})
printName({first: "Bob"})  // OK
```
- When reading an optional parameter, it might be `undefined`, so manually check for this.
    - Optional chaining operator from ES2020 will return undefined instead of continuing the chain.

TYPE ASSERTIONS
---------------

- TypeScript only allows type assertions which convert to a more specific or less specific version of a type. This rule prevents “impossible” coercions like `const x = "hello" as number;`
    - Sometimes this rule can be too conservative and will disallow more complex coercions that might be valid, in which case first assert as `any`, then the type you require, e.g. `cost x = (run() as any) as T`

const a = (expr as any) as T;

- **Type Assertion**:
    - Tells TS that I know the return type, and it will be of this type. Use with caution. Handy when TS can't infer the type.
        ```ts
        const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
        ```

- vs **Type Annotation**:
    - The usual way that allows stronger static typing and allows TS to catch potential type errors during compilation. 
        ```ts
        const myCanvas: HTMLCanvasElement = document.getElementById("main_canvas");
        ```
LITERAL INFERENCE
-----------------

```ts
declare function handleRequest(url: string, method: "GET" | "POST"): void;
 
const req = { url: "https://example.com", method: "GET" };
handleRequest(req.url, req.method);
// Argument of type 'string' is not assignable to parameter of type '"GET" | "POST"'.
```

- Here TS things the type of `req.method` is `string`, which is not `"GET" | "POST"`. I.e. the value could have changed since it was initialised.
- There are two ways of telling TS that the method value is a const here.

1. Change the inference by adding a type assertion in either location:
    ```ts
    // Change 1:
    const req = { url: "https://example.com", method: "GET" as "GET" };  // Mike: I think this makes the most sense in this example
    // ...or Change 2
    handleRequest(req.url, req.method as "GET");```
    ```
2. Convert the entire object to a constant with `as const`:
    ```ts
    const req = { url: "https://example.com", method: "GET" } as const;
    handleRequest(req.url, req.method);
    ```

NON-NULL ASSERTION OPERATOR 
---------------------------
- The TS `!` operator can be used tell TS the expression's value is not `null` not `undefined`

```ts
this.getElementById("selectorId")!.toogleAttriubte('marked', true)
```

ENUMS
-----

- Not a typing features.
- A TS addition to that result in run time changes.
- Know they exist, but avoid for now.

NARROWING
---------

- The process of refining types to more specific types than declared is called narrowing.

### Type Guards

- TS understands code like `typeof x === "number"`

- Note there is no "null" return value from the `typeof` operator.

Type        | Predicate
------------|----------------------
bigint  	| typeof x === "bigint"
boolean	    | typeof x === "boolean"
function	| typeof x === "function"
number	    | typeof x === "number"
object  	| typeof x === "object"
string	    | typeof x === "string"
symbol      | typeof x === "symbol"
undefined	| typeof x === "undefined"
array	    | Array.isArray(a)

- In JS the `typeof null` is actually `null`! ... an unfortunate accident of history.
    - Say you have a function that takes in a param with type: `strs: string | string[] | null`
    - And then one checks: `(typeof strs === "object")` ... the type of `str` at this point has been narrowed down to `string[] | null`

### Truthiness narrowing

The following values are considered falsey, all other values are truthy:
- `0`
- `NaN`
- `""`      (the empty string)
- `0n`      (the bigint version of zero)
- `null`
- `undefined`

To coerce a boolean value, can use `Boolean()` or `!!`, they have different implications in TS:
```ts
Boolean("hello"); // type: boolean, value: true
!!"world";        // type: true,    value: true
```

In this example:
```ts
function multiplyAll(
  nums: number[] | undefined,
  factor: number
): number[] | undefined {
  if (!nums) {  // <-- this predicate will filter out all falsey values nums could be, i.e. undefined in this case
    return nums;
  } else {
    return nums.map((x) => x * factor);
  }
}
```

### Equality narrowing

```ts
function example(x: string | number, y: string | boolean) {
  if (x === y) {
    // We can now call any 'string' method on 'x' or 'y'.
    // Since the only common type between them is string
    x.toUpperCase();
    y.toLowerCase();
  }
```

- TS understands the narrowing effects of `==` vs `===`
    - Note: The less strict equality check `==` which make `null` equal to `undefined`

### The in operator narrowing

- In JavaScript there is an operator for checking if an object (or it's prototype chain) has a certain property, it's called in `in` operator.

```ts
type bird = { fly: () => void}
type fish = { swim: () => void}
function doSomething(animal: bird | fish) {
    if ('fly' in animal) {
        // type is bird
    }
}
```

### `instanceof` narrowing

- `instanceof Foo` checks whether an object has `Foo.prototype` in it's prototype chain. Useful for objects constructed with `new`.

```ts
function logValue(x: Date | string) {
  if (x instanceof Date) {
    // x: Date
  } else {
    // x: string
  }
}
```

### Equality narrowing

```ts
let x = Math.random() < 0.5 ? 10 : "hello world!";` // here `x` is of type `string | number`
x = 123; // TS know its type is now Number
```

### Control flow analysis

- If you return early from a function due to variable being of a certain type, TS know from there on the type will not be of that type.

```ts
function run(foo: string | number) {
    if (typeof foo === "number") return
    return foo.toUpperCase();
}
```

### Using type predicates

- To define a user-defined type guard, we simply need to define a function whose return type is a type predicate:
- Predicate type syntax is `Name is Type`

```
function isFish(obj: fish | bird): obj is fish {
    return 'swim' in fish;
}

let pet = getSmallPet();
if (isFish(pet)) {
  pet.swim();  // TS knows here it is of type fish
}
```

### Assertion Functions

Can be narrowed using assertion function e.g. `assert(typeof x === "number");`

### Discriminated unions

- When every type in a union contains a common property with literal types, TypeScript considers that to be a discriminated union, and can narrow out the members of the union.
- E.g. 
    ```
    interface Circle {
        kind: "circle";
        radius: number;
    }
    
    interface Square {
        kind: "square";
        sideLength: number;
    }
    
    type Shape = Circle | Square;
    ```
- Here the `discriminant property` of `Shape` is `kind`.
- This way if `kind === circle`, TS knows it will have a `radius`

### The `never` type 

When narrowing, you can reduce the options of a union to a point where you have removed all possibilities and have nothing left. In those cases, TS will use a never type to represent a state which shouldn't exist.
- The never type is assignable to every type; however, no type is assignable to never (except never itself).
    - This means you can use narrowing and rely on never turning up to do exhaustive checking in a switch statement.

MORE ON FUNCTIONS
-----------------

### Function Type Expressions

- Format `(a: string) => void` means “a function with one parameter, named a, of type string, that doesn't have a return value".
    - Just like with function declarations, if a parameter type isn't specified, it’s implicitly `any`.
    - `(string) => void` mean a function that tags a parameter of `any` type and return no value.

```ts
function testGreeter(func: (str: string) => void) {
    func('Test greeter')
}

function greet(s: string): void {
    console.log(string)
}
```

### Optional Parameters

```ts
function f(x?: number) {
    // ...
}
f(); // OK, same as f(undefined);
f(10);
```
