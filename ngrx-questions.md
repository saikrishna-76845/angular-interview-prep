### **1. Basic NGRX & Store Concepts**

#### **a. Introduction to NGRX**

1. **What is NGRX, and how does it relate to Redux?**
   - Expected answer: NGRX is a reactive state management library for Angular, inspired by Redux. It helps manage state in a predictable manner by using actions, reducers, and a store. Like Redux, NGRX uses a unidirectional data flow where the state is immutable, and the only way to update the state is through actions.

2. **What is the `Store` in NGRX?**
   - Expected answer: The `Store` in NGRX is a global state container that holds the application's state. It provides an observable stream of state, allowing components to subscribe to and dispatch actions to change the state.

3. **What are Actions in NGRX?**
   - Expected answer: Actions in NGRX are events that describe something that has occurred in the application (e.g., user interaction, API response). Actions are dispatched to the store, which triggers the reducers to modify the state accordingly.

4. **What is the role of Reducers in NGRX?**
   - Expected answer: Reducers are pure functions that handle state changes based on actions dispatched to the store. They receive the current state and an action, then return a new state without mutating the old state. Reducers define how the application state transitions in response to actions.

5. **What are Effects in NGRX, and when are they used?**
   - Expected answer: Effects in NGRX handle side effects, such as making HTTP requests, routing, or interacting with external services. Effects listen for specific actions, perform the side effects, and dispatch new actions based on the results. They help decouple side effects from components and reducers.

---

#### **b. Store Setup & Configuration**

6. **How do you configure the NGRX store in an Angular application?**
   - Expected answer: 
     - First, install the required NGRX packages: `@ngrx/store`, `@ngrx/effects`, and `@ngrx/store-devtools`.
     - Define the state interface and create actions, reducers, and selectors.
     - Register the store in the `AppModule` using `StoreModule.forRoot(reducers)` and `EffectsModule.forRoot()` for effects.

     Example:
     ```typescript
     import { StoreModule } from '@ngrx/store';
     import { EffectsModule } from '@ngrx/effects';
     import { rootReducer } from './store/reducers';
     import { AppEffects } from './store/effects';

     @NgModule({
       imports: [
         StoreModule.forRoot(rootReducer),
         EffectsModule.forRoot([AppEffects]),
       ],
     })
     export class AppModule {}
     ```

7. **What is the purpose of `@ngrx/store-devtools`, and how do you configure it?**
   - Expected answer: `@ngrx/store-devtools` is a tool for debugging and visualizing state changes in the NGRX store. It allows developers to inspect actions, view the state history, and perform time-travel debugging. To use it, install the package and configure it in the `AppModule`:
     ```typescript
     import { StoreDevtoolsModule } from '@ngrx/store-devtools';
     
     @NgModule({
       imports: [
         StoreDevtoolsModule.instrument({
           maxAge: 25, // Retains last 25 actions
           logOnly: environment.production, // Disable in production
         }),
       ],
     })
     ```

8. **What is the purpose of `createReducer` and `on` functions in NGRX?**
   - Expected answer: `createReducer` is a helper function to create reducers more concisely, and `on` is used to map specific actions to state changes. It reduces boilerplate code compared to traditional reducers.

     Example:
     ```typescript
     const initialState: State = { count: 0 };

     const counterReducer = createReducer(
       initialState,
       on(increment, state => ({ ...state, count: state.count + 1 })),
       on(decrement, state => ({ ...state, count: state.count - 1 }))
     );
     ```

---

### **2. Intermediate NGRX Concepts**

#### **a. Actions, Reducers, and State**

9. **What are the different types of actions in NGRX, and how do you define them?**
   - Expected answer: Actions in NGRX are classified into:
     - **Simple actions**: Plain actions without any additional payload.
     - **Actions with payload**: Actions that carry additional data (e.g., API response).
     - Actions are defined using the `createAction` function.

     Example:
     ```typescript
     import { createAction, props } from '@ngrx/store';

     export const loadData = createAction('[Data] Load');
     export const loadDataSuccess = createAction(
       '[Data] Load Success',
       props<{ data: any }>()
     );
     ```

10. **How do you use selectors in NGRX, and what are their benefits?**
    - Expected answer: Selectors are functions used to select slices of the state from the store. They are memoized for performance optimization and help avoid unnecessary re-renders of components.

    Example:
    ```typescript
    import { createSelector } from '@ngrx/store';

    export const selectCount = createSelector(
      (state: AppState) => state.counter,
      (counter) => counter.count
    );
    ```

    Benefits:
    - **Performance optimization**: Memoized selectors prevent redundant recalculations.
    - **Encapsulation**: Selectors help abstract and encapsulate state logic.

11. **How does NGRX handle state immutability in reducers?**
    - Expected answer: NGRX enforces state immutability by requiring reducers to return new state objects instead of modifying the current state directly. The spread operator (`{ ...state }`) or libraries like `immer` can be used to ensure that the state remains immutable.

12. **Explain the concept of "action creators" in NGRX.**
    - Expected answer: Action creators are functions that simplify the creation of actions. Instead of manually creating action objects, action creators (e.g., `createAction`) generate actions with consistent types and payloads.

    Example:
    ```typescript
    export const loadData = createAction('[Data] Load');
    export const loadDataSuccess = createAction(
      '[Data] Load Success',
      props<{ data: any }>()
    );
    ```

---

#### **b. Effects**

13. **What are NGRX Effects, and how do they help in managing side effects?**
    - Expected answer: Effects are used to manage side effects (e.g., HTTP requests, logging, routing) in NGRX. They listen to specific actions, perform asynchronous operations, and dispatch new actions based on the results. Effects help keep the application logic separate from the component and reducer code.

    Example:
    ```typescript
    @Injectable()
    export class DataEffects {
      loadData$ = createEffect(() =>
        this.actions$.pipe(
          ofType(loadData),
          mergeMap(() =>
            this.dataService.getData().pipe(
              map((data) => loadDataSuccess({ data })),
              catchError((error) => of(loadDataFailure({ error })))
            )
          )
        )
      );

      constructor(private actions$: Actions, private dataService: DataService) {}
    }
    ```

14. **How do you handle HTTP requests using NGRX Effects?**
    - Expected answer: NGRX Effects are often used to handle HTTP requests by dispatching actions before and after the request. When an action is dispatched (e.g., `loadData`), the effect triggers an HTTP call and dispatches success or failure actions based on the result.

    Example:
    ```typescript
    loadData$ = createEffect(() =>
      this.actions$.pipe(
        ofType(loadData),
        mergeMap(() =>
          this.http.get('api/data').pipe(
            map(data => loadDataSuccess({ data })),
            catchError(error => of(loadDataFailure({ error })))
          )
        )
      )
    );
    ```

15. **What are the differences between `createEffect` and `Effects` in NGRX?**
    - Expected answer: `createEffect` is a function used to define side effects in NGRX 8+ while `Effects` (in the older versions) was a class-based approach to manage side effects. `createEffect` is simpler and more declarative, while `Effects` required more boilerplate code.

---

### **3. Advanced NGRX Concepts**

#### **a. Entity Store**

16. **What is the purpose of `@ngrx/entity`, and how does it simplify state management?**
    - Expected answer: `@ngrx/entity` provides utilities for managing collections of entities in the store. It simplifies the process of handling CRUD operations on arrays of entities by providing pre-built reducers and selectors for managing entity state.

    Example:
    ```typescript
    import { createEntityAdapter, EntityState } from '@ngrx/entity';

    interface Item {
      id: number;
      name: string;
    }

    const adapter = createEntityAdapter<Item>();

    const initialState: EntityState<Item> = adapter.getInitialState({
      selectedItemId: null,
    });

    const itemReducer = createReducer(
      initialState,
     

 on(addItem, (state, { item }) => adapter.addOne(item, state)),
      on(removeItem, (state, { id }) => adapter.removeOne(id, state))
    );
    ```

17. **What are memoized selectors in NGRX, and why are they important?**
    - Expected answer: Memoized selectors in NGRX are selectors that cache the result of a function call based on the input arguments. They are important because they prevent unnecessary recalculations when the state has not changed, improving performance.

    Example:
    ```typescript
    const selectAllItems = createSelector(
      state => state.items,
      items => items.filter(item => item.active)
    );
    ```