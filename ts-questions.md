### **Basic TypeScript Questions**

1. **What is TypeScript, and how does it differ from JavaScript?**
   - Expected answer: TypeScript is a superset of JavaScript that adds optional static typing, interfaces, and other features. It allows for early detection of errors during development and improves code quality, whereas JavaScript is a dynamic language with no static type checking.

2. **What are the main benefits of using TypeScript over JavaScript?**
   - Expected answer:
     - Static typing helps catch errors at compile-time.
     - Improved tooling and editor support (autocomplete, IntelliSense).
     - Supports modern JavaScript features like ES6+ and compiles down to ES5 or earlier versions.
     - Better support for large-scale application development through interfaces, types, and classes.

3. **What are the basic types in TypeScript?**
   - Expected answer: Some basic types in TypeScript are:
     - `string`: Represents textual data.
     - `number`: Represents numeric values.
     - `boolean`: Represents true/false values.
     - `void`: Represents the absence of a value, often used for functions that don't return anything.
     - `null` and `undefined`: Represent absence of value.
     - `any`: A type that disables type checking (use with caution).
     - `unknown`: Similar to `any`, but safer as it requires type assertion before performing operations.

4. **What is the purpose of the `any` type in TypeScript?**
   - Expected answer: The `any` type disables TypeScript's type checking, allowing any type of value to be assigned to a variable. While it provides flexibility, it also removes the benefits of static typing, so it should be used cautiously.

5. **What is type inference in TypeScript?**
   - Expected answer: Type inference is the ability of TypeScript to automatically infer the type of a variable based on the value assigned to it. For example:
     ```typescript
     let num = 42; // inferred as 'number'
     let name = "John"; // inferred as 'string'
     ```

### **Intermediate TypeScript Questions**

6. **What is an interface in TypeScript, and how is it used?**
   - Expected answer: An interface in TypeScript is a contract for defining the structure of an object, specifying properties and their types. It can also define method signatures. Example:
     ```typescript
     interface Person {
         name: string;
         age: number;
         greet(): void;
     }

     const person: Person = { name: "Alice", age: 25, greet() { console.log("Hello!"); } };
     ```

7. **Explain the difference between `interface` and `type` in TypeScript.**
   - Expected answer:
     - `interface`: Used to define the structure of an object or class. It can be extended and merged with other interfaces.
     - `type`: Can be used to define a type alias, including primitive types, union types, and object shapes. It cannot be merged like an interface.
     Example:
     ```typescript
     interface Person {
         name: string;
         age: number;
     }

     type Car = {
         make: string;
         model: string;
     };
     ```

8. **What is the `readonly` modifier in TypeScript, and how does it work?**
   - Expected answer: The `readonly` modifier is used to define properties in an object or an array that cannot be changed after initialization. Example:
     ```typescript
     interface Person {
         readonly name: string;
         age: number;
     }

     const person: Person = { name: "John", age: 30 };
     person.name = "Alice"; // Error: Cannot assign to 'name' because it is a read-only property.
     ```

9. **What are generics in TypeScript, and how are they useful?**
   - Expected answer: Generics allow you to define reusable and flexible components (functions, classes, interfaces) that work with any type while maintaining type safety. Example:
     ```typescript
     function identity<T>(arg: T): T {
         return arg;
     }

     let result = identity(42);  // inferred type is 'number'
     let stringResult = identity("hello");  // inferred type is 'string'
     ```

10. **How do you create a function with optional parameters in TypeScript?**
    - Expected answer: You can use a `?` to make parameters optional. Example:
      ```typescript
      function greet(name: string, age?: number): string {
          return `Hello ${name}, age: ${age || "unknown"}`;
      }

      greet("Alice"); // Age is optional
      greet("Bob", 30);
      ```

### **Advanced TypeScript Questions**

11. **What is the difference between `unknown` and `any` in TypeScript?**
    - Expected answer:
      - `any`: Allows any value to be assigned, effectively bypassing TypeScript's type system.
      - `unknown`: A safer alternative to `any` because it requires type checking before performing operations. You must assert the type or narrow it down before using it.

12. **What are type guards in TypeScript, and how do they work?**
    - Expected answer: Type guards are mechanisms that narrow down the type of a variable within a conditional block. TypeScript uses type guards to refine types, often using the `typeof` or `instanceof` operators. Example:
      ```typescript
      function isString(value: unknown): value is string {
          return typeof value === 'string';
      }

      const input: unknown = "Hello";
      if (isString(input)) {
          console.log(input.length); // Safe to access length, as TypeScript knows it's a string
      }
      ```

13. **What is `strict` mode in TypeScript?**
    - Expected answer: `strict` mode in TypeScript enables a series of strict type-checking options that make the language more predictable and less error-prone. It includes options like `noImplicitAny`, `strictNullChecks`, `strictFunctionTypes`, etc.

14. **What is the `never` type in TypeScript, and when would you use it?**
    - Expected answer: The `never` type represents values that will never occur, such as functions that always throw an error or never return (e.g., infinite loops). Example:
      ```typescript
      function throwError(message: string): never {
          throw new Error(message);
      }
      ```

15. **Explain the concept of `Declaration Merging` in TypeScript.**
    - Expected answer: Declaration merging in TypeScript occurs when multiple declarations of the same name are combined into a single entity. This happens primarily with interfaces and can be useful for augmenting existing types or libraries. Example:
      ```typescript
      interface Person {
          name: string;
      }

      interface Person {
          age: number;
      }

      const person: Person = { name: "Alice", age: 25 };
      ```