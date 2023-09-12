### Tutorial 

Link : https://auth0.com/blog/node-js-and-typescript-tutorial-build-a-crud-api/

express: Fast, unopinionated, minimalist web framework for Node.js.

dotenv: Zero-dependency module that loads environment variables from a .env file into process.env.

cors: Express middleware to enable CORS with various options.

helmet: Express middleware to secure your apps by setting various HTTP headers, which mitigate common attack vectors.

## Notes

### Built in Types
When a package doesn't have built-in types, you can get its type definitions through the @types npm namespace, which hosts TypeScript type definitions from the DefinitelyTyped project. Once you install the packages, the TypeScript compiler automatically includes the types, and your IDE can use them to provide you with code assistance.

### ts-node-dev
 `ts-node-dev` is a tweaked version of node-dev that uses ts-node under the hood, some of its options are the combined options of those two packages. 

## Steps to Bootstrap Nodejs, Expressjs, and Typescript

### Bootstrap application 
```
mkdir menu-api
cd menu-api
```

### Install Project Dependencies
`npm i express dotenv cors helmet`

### Install Typescript
`npm i -D typescript`

### Install Type Definitions for dependencies
`npm i -D @types/node @types/express @types/dotenv @types/cors @types/helmet`

### Initialize Typescript using tsconfig.json file. 
`npx tsc --init`

### Use Environment file
`touch .env`

Populate file with config: `PORT=7000`

### Create an Express app with Typescript
`mkdir src`
`touch src/index.ts`

### Setup index.ts
See `index.ts`

### Hot Reload
`npm i -D ts-node-dev` 

### Run Project
`npm run dev`

## Typescript

#### How to write a function
```
function functionName(parameter1: type1, parameter2: type2, ...): returnType {
    // Function body
    // You can use parameters and perform operations here
    // Optionally, return a value of returnType
}
```

#### How to write a function with Function Type Alias:
```
type BinaryOperation = (a: number, b: number) => number;

const subtract: BinaryOperation = function (a, b) {
    return a - b;
};
```

#### Function with Default Parameter Value: 
```
function greet(name: string = "Anonymous"): string {
    return `Hello, ${name}!`;
}
```

#### Function with variable number of parameters
```
function sum(...numbers: number[]): number {
```

#### Function with optional parameters
```
function greetWithAge(name: string, age?: number): string {
    if (age === undefined) {
        return `Hello, ${name}!`;
    } else {
        return `Hello, ${name}, you are ${age} years old!`;
    }
}
```

#### Function with Rest Parameters
A variable number of arguments, all of which should be of the same type. This is known as a rest parameter. Here. we're defining an anonymous function inline, and the parameters are provided by the callback definition signature are all optional, but match by order. So in this case, total and num match by order the reduce call's first argument, which happens to be a callback that has 4 arguments. Since its by order, we may need to use placeholders in case we dont care about a specific parameter. 
```
function sum(...numbers: number[]): number {
    return numbers.reduce((total, num) => total + num, 0);
}
```

e.g. placeholder
function sum(...numbers: number[]): number {
    return numbers.reduce((total, unusedNum, currentIndex) => total + currentIndex, 0);
}


#### How to write an anonymous function
Anonymous functions are often used when you need a function temporarily or as a callback. 
```
const add = function (a: number, b: number): number {
    return a + b;
};
```

#### How to write an anonymous Arrow function
Arrow functions provide a concise way to write anonymous functions: 
```
const multiply = (x: number, y: number): number => x * y;
```

#### Anonymous Functions as Callbacks
Anonymous functions are often used as callback functions, especially in asynchronous code or when passing functions as arguments to other functions:
```
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(function (num) {
    return num * 2;
});
```

#### Function Inline
You can create and execute an anonymous function immediately after defining it. This is useful for encapsulating code and preventing variable scope pollution:
```
(function () {
    // Your code here
})();
```


#### Strongly Typing your functions
```
class Foo {
    save(callback: (n: number) => any) : void {
        callback(42);
    }
}
var foo = new Foo();
var numCallback = (result: number) : void => {
    alert(result.toString());
}
foo.save(numCallback); // OK
```

A type alias 
```
type NumberCallback = (n: number) => any;

class Foo {
    // Equivalent
    save(callback: NumberCallback) : void {
        callback(42);
    }
}
```

#### Generics - Matching Input to Output 
```
function identity<T>(value: T): T {
    return value;
}
```
The purpose of this identity function is to act as a passthrough or an identity operation. It doesn't perform any operations or transformations on the input value; it simply returns the input value unchanged. The generic type parameter T allows you to use this function with various data types while maintaining type safety. For example:
```
const numberIdentity = identity(42); // Returns 42 (number)
const stringIdentity = identity("Hello, world!"); // Returns "Hello, world!" (string)
const booleanIdentity = identity(true); // Returns true (boolean)
```
In each case, the identity function preserves the type of the input value and returns it as-is. This can be useful in situations where you want to ensure that the output type matches the input type, even when using a generic function.