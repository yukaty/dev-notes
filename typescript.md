# TypeScript
- [Getting Started](#getting-started)
- [noEmitOnError option](#noemitonerror-option)
- [tsconfig.json](#tsconfigjson)
- [Define Variables](#define-variables)
- [Accessor](#accessor)
- [Parameter Properties](#parameter-properties)
- [Modules](#modules)
- [OOP](#oop)

TypeScript is a strongly typed programming language that builds on JavaScript.

## Getting Started
1. Create the TypeScript file with the `.ts` extension
2. Convert the TypeScript code to JavaScript code with the `tsc` command
   - Transpiling = Translate + Compile
3. Run the generated `.js` file with the `node` command

## noEmitOnError option
Even though there are errors, the compiler will generates a .js file. The `--noEmitOnError` option can prevent this.
```bash
tsc --noEmitOnError hello.ts
```

## tsconfig.json
tsconfig.json file defines compiler options and project settings.

Generate a tsconfig.json file:
```
tsc --init
```

## Define Variables
Syntax:
```ts
let <variableName>: <type> = <initial value>;
```
Example:
```ts
let isFound: boolean = true;
```

## Accessor
Accessors = Getters and Setters

```ts
class Person {
    private _name: string;

    constructor(name: string) {
        this._name = name;
    }

    // Getter for the name property
    get name(): string {
        return this._name;
    }

    // Setter for the name property
    set name(newName: string) {
         this._name = newName;
    }
}

let person = new Person("Alice");
console.log(person.name); // Alice
person.name = "Bob";
console.log(person.name); // Bob
```

## Parameter Properties

Parameter properties is a short-cut syntax for creating constructors.

Tradisional Approach:
```ts
class Customer {
   private _firstName: string;
   private _lastName: string;

    constructor(theFirst: string, theLast: string) {
        this._firstName = theFirst;
        this._lastName = theLast;
    }
```

The Short Cut:
```ts
class User {
    constructor(private _firstName: string, private _lastName: string){}
}
```

## Modules
- A module can **export** classes, functions, variables etc.
- Another file can **import** them from the module.

Customer.ts
```ts
export class Customer{
   :
}
```

Main.ts
```ts
import { Customer } from './Customer';

let myCustomer = new Customer("John", " Doe")
:
```

## OOP
TypeScript also supports:
- Inheritance
- Abstract Classes
- Interfaces
