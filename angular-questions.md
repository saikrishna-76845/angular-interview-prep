### **1. Basic Concepts in Angular**

#### **a. Angular Overview & Architecture**

1. **What is Angular, and what are its key features?**
   - Expected answer: Angular is a platform and framework for building single-page applications (SPAs). Key features include two-way data binding, component-based architecture, dependency injection, routing, and support for building modular and scalable applications.

2. **What is the difference between Angular and AngularJS?**
   - Expected answer: AngularJS is the 1.x version of the framework, which was based on JavaScript. Angular (2+) is a complete rewrite of AngularJS using TypeScript, offering better performance, a modular architecture, and improved tooling.

3. **What are components in Angular, and why are they important?**
   - Expected answer: Components are the fundamental building blocks of an Angular application. Each component controls a part of the UI and is composed of an HTML template, a CSS style, and a TypeScript class. Components are important because they enable reusability and separation of concerns.

4. **What is the role of the `@NgModule` decorator in Angular?**
   - Expected answer: `@NgModule` is a decorator used to define Angular modules. It provides metadata about the module, including declarations (components, directives, pipes), imports (other modules), providers (services), and the root component.

5. **Explain the term "dependency injection" in Angular.**
   - Expected answer: Dependency Injection (DI) is a design pattern where a class’s dependencies (services, etc.) are injected into it rather than the class creating them. Angular’s DI system provides an efficient and modular way to manage dependencies.

---

#### **b. Data Binding**

1. **What are the different types of data binding in Angular?**
   - Expected answer: There are four main types of data binding in Angular:
     - **Interpolation**: `{{ expression }}`
     - **Property Binding**: `[property]="expression"`
     - **Event Binding**: `(event)="handler"`
     - **Two-way Binding**: `[(ngModel)]="property"`

2. **Explain how two-way data binding works in Angular.**
   - Expected answer: Two-way data binding in Angular allows synchronization of data between a component’s property and an input element (or any DOM element). It uses the `[(ngModel)]` directive, which combines property binding and event binding.

3. **What is property binding, and how is it different from interpolation?**
   - Expected answer: Property binding is used to bind data to an element's property, e.g., `[src]="imageUrl"`. Interpolation binds data to an element's text content, e.g., `{{title}}`.

4. **What is event binding, and when would you use it?**
   - Expected answer: Event binding is used to listen for events (like clicks, keypresses, etc.) and execute methods in response. Example: `(click)="onClick()"`.

5. **What is the purpose of the `ngModel` directive in Angular?**
   - Expected answer: The `ngModel` directive is used for two-way data binding. It synchronizes the value of form elements like input fields with the component class property.

---

#### **c. Directives**

1. **What is the difference between structural and attribute directives in Angular?**
   - Expected answer: 
     - Structural directives change the structure of the DOM (e.g., `*ngIf`, `*ngFor`).
     - Attribute directives change the appearance or behavior of an element (e.g., `ngClass`, `ngStyle`).

2. **How does `*ngIf` work in Angular?**
   - Expected answer: `*ngIf` is a structural directive that conditionally includes or removes an element from the DOM based on a boolean expression.

3. **What is `ngFor` and how is it used?**
   - Expected answer: `ngFor` is a structural directive used to iterate over an array and render a template for each element. Example: 
     ```html
     <div *ngFor="let item of items">
       {{ item }}
     </div>
     ```

4. **Explain how `ngClass` works in Angular.**
   - Expected answer: `ngClass` is an attribute directive that dynamically adds or removes CSS classes based on the evaluation of an expression. Example: `<div [ngClass]="{ 'active': isActive }"></div>`.

5. **What is the `ngStyle` directive, and how is it used?**
   - Expected answer: `ngStyle` is an attribute directive used to dynamically set inline styles on an element. Example:
     ```html
     <div [ngStyle]="{ 'background-color': color }"></div>
     ```

---

### **2. Intermediate Concepts in Angular**

#### **a. Routing**

1. **What is Angular Router, and how does it work?**
   - Expected answer: Angular Router is used to navigate between views or components in a single-page application. It provides features like route parameters, lazy loading, guards, and more. Routes are defined in the `AppRoutingModule` using the `RouterModule.forRoot()` method.

2. **What are route guards, and how are they used in Angular?**
   - Expected answer: Route guards are interfaces that control access to routes. They can be used to prevent unauthorized access or to check if data is ready before navigation occurs. Examples include `CanActivate`, `CanDeactivate`, `CanLoad`, etc.

3. **What is the difference between `routerLink` and `routerLinkActive`?**
   - Expected answer:
     - `routerLink`: A directive that binds a link to a route. It navigates to a route when clicked.
     - `routerLinkActive`: A directive that adds a class to the link when the route is active.

4. **What is lazy loading in Angular, and how is it implemented?**
   - Expected answer: Lazy loading allows Angular to load modules only when they are needed, rather than at the initial load. It is implemented using the `loadChildren` property in route configuration:
     ```typescript
     { path: 'feature', loadChildren: () => import('./feature/feature.module').then(m => m.FeatureModule) }
     ```

5. **What are path parameters and query parameters in Angular routes?**
   - Expected answer: 
     - **Path parameters** are dynamic values in the route URL (e.g., `/users/:id`).
     - **Query parameters** are optional parameters appended to the URL (e.g., `/users?id=1`).

---

#### **b. Services & Dependency Injection**

1. **What is a service in Angular, and why are they used?**
   - Expected answer: Services are classes that provide specific functionality or business logic and can be injected into components, other services, or directives. They promote code reusability and separation of concerns.

2. **How does Angular’s Dependency Injection (DI) system work?**
   - Expected answer: Angular’s DI system allows services and other dependencies to be injected into components and classes instead of having to manually create instances. Services are provided in an Angular module, component, or service.

3. **What are the different ways to provide services in Angular?**
   - Expected answer: Services can be provided in:
     - The root injector using `providedIn: 'root'`.
     - Specific modules, components, or directives by using the `providers` array.

4. **What is the role of the `@Injectable` decorator in Angular?**
   - Expected answer: The `@Injectable` decorator marks a class as a service that can be injected into other components or services. It also allows the service to participate in Angular’s dependency injection system.

5. **Explain the difference between `@Injectable` and `@Component` decorators.**
   - Expected answer: 
     - `@Injectable` is used for services to indicate that the class can be injected into other parts of the application.
     - `@Component` is used to define a component and attach metadata about the component’s template, style, and selector.

---

#### **c. Forms in Angular**

1. **What is the difference between template-driven forms and reactive forms in Angular?**
   - Expected answer:
     - **Template-driven forms** are simple forms where the form controls are defined in the template and Angular binds them automatically.
     - **Reactive forms** provide more control and flexibility, defining the form model in the component class using `FormGroup`, `FormControl`, etc.

2. **How do you create a reactive form in Angular?**
   - Expected answer: To create a reactive form, import `ReactiveFormsModule`, define a form model in the component using `FormGroup` and `FormControl`, and bind the form to the template using `formControlName`.

3. **What are form validators in Angular, and how do you use them?**
   - Expected answer: Validators are functions that check if the form controls meet certain criteria (e.g., required, min length). They are used with both template-driven and reactive forms, e.g., `Validators.required`, `Validators.minLength(3)`.

4. **How do you handle form submission in Angular?**
   - Expected answer: In template-driven forms, use `ngSubmit` with the form element. In reactive forms, use the `submit()` method after validating the form.

5. **What is the purpose of `ngModel` in template-driven forms?**
   - Expected answer: `ngModel` is used to bind form inputs to component properties, enabling two-way data binding and form control. It helps in creating template-driven forms with less boilerplate code.
