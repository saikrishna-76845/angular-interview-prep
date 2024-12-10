### **1. Basic RxJS Concepts**

#### **a. Introduction to RxJS**

1. **What is RxJS and why is it used in modern JavaScript applications?**
   - **Expected Answer:** RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using **Observables**. It allows you to manage asynchronous data streams, such as handling HTTP requests, event handling, and timers, in a more declarative and functional style. RxJS simplifies the management of complex asynchronous workflows, making it easier to compose, handle, and manipulate streams of events or data.

2. **What is the difference between an `Observable` and a `Promise` in RxJS?**
   - **Expected Answer:**
     - **Promise** represents a single value that may be available now or in the future (one-time value).
     - **Observable** represents a stream of multiple values over time (can emit multiple values).
     - Observables are lazy (they don’t emit values until subscribed to) and can be canceled by unsubscribing. Promises, on the other hand, always resolve once and cannot be canceled.

3. **What is the role of the `subscribe()` method in RxJS?**
   - **Expected Answer:** The `subscribe()` method is used to start the execution of an Observable and handle the emitted values, errors, or completion notifications. Without `subscribe()`, an Observable won't do anything (it is lazy). The method allows you to define handlers for the emitted values (using `next`), errors (`error`), and completion (`complete`).

     Example:
     ```typescript
     myObservable.subscribe({
       next: value => console.log(value),
       error: err => console.error(err),
       complete: () => console.log('Observable completed')
     });
     ```

4. **What is the difference between `Observer` and `Observable` in RxJS?**
   - **Expected Answer:**
     - **Observable:** Represents a stream of data that can be subscribed to. It can emit multiple values over time.
     - **Observer:** An object that defines how to handle emitted values from an Observable. It contains `next()`, `error()`, and `complete()` methods that get invoked when the Observable emits a value, encounters an error, or completes.

5. **What is the purpose of the `unsubscribe()` method in RxJS?**
   - **Expected Answer:** The `unsubscribe()` method is used to stop receiving values from an Observable by disposing of the subscription. It is essential to avoid memory leaks, especially in Angular components, where subscriptions need to be cleaned up when a component is destroyed.

---

#### **b. Operators**

6. **What is the difference between `map()` and `flatMap()` (also `mergeMap()`)?**
   - **Expected Answer:**
     - `map()` transforms the values emitted by an Observable by applying a function to each value. It returns a new Observable with the transformed values.
     - `flatMap()` (or `mergeMap()`) flattens the higher-order Observable and subscribes to each inner Observable, potentially executing multiple inner observables concurrently.

     Example:
     ```typescript
     obs$.pipe(
       map(value => value * 2) // Transforms emitted values
     );

     obs$.pipe(
       mergeMap(value => http.get(`api/${value}`)) // Flattening inner Observables
     );
     ```

7. **What is the use of `filter()` in RxJS?**
   - **Expected Answer:** The `filter()` operator allows you to emit values from the source Observable based on a condition (predicate function). It works similarly to the `Array.prototype.filter()` method, but for Observables.

     Example:
     ```typescript
     obs$.pipe(
       filter(value => value > 5) // Only emits values greater than 5
     );
     ```

8. **What is the `debounceTime()` operator in RxJS, and when would you use it?**
   - **Expected Answer:** `debounceTime()` is used to limit the frequency of emitted values by delaying the emission until a specified duration has passed without any new values being emitted. It is commonly used to prevent excessive requests (e.g., in search input fields).

     Example:
     ```typescript
     obs$.pipe(
       debounceTime(300) // Waits 300ms after the last emission before emitting
     );
     ```

9. **What is the `merge()` operator in RxJS?**
   - **Expected Answer:** The `merge()` operator combines multiple Observables into one. It subscribes to each of the input Observables and emits values as they are emitted from any of the source Observables. `merge()` emits values concurrently.

     Example:
     ```typescript
     merge(obs1$, obs2$, obs3$)
       .subscribe(value => console.log(value));
     ```

10. **How does the `distinctUntilChanged()` operator work in RxJS?**
    - **Expected Answer:** `distinctUntilChanged()` ensures that only unique values are emitted consecutively by comparing each emitted value with the previous one. It prevents emitting the same value multiple times in succession.

      Example:
      ```typescript
      obs$.pipe(
        distinctUntilChanged() // Only emits when the value is different from the previous one
      );
      ```

---

### **2. Intermediate RxJS Concepts**

#### **a. Subjects**

11. **What is a `Subject` in RxJS, and how does it differ from an Observable?**
    - **Expected Answer:** A `Subject` is both an **Observable** and an **Observer**. It allows values to be multicasted to many Observers. Unlike regular Observables, which only emit values to their subscribers, Subjects can also emit values using `next()`, making them useful for multicast or event broadcasting scenarios.

    Example:
    ```typescript
    const subject = new Subject();
    subject.next('Hello');
    subject.subscribe(val => console.log(val)); // Will log 'Hello'
    ```

12. **What is a `BehaviorSubject` in RxJS?**
    - **Expected Answer:** A `BehaviorSubject` is a type of Subject that stores the **latest value** and emits that value to any new subscribers immediately upon subscription. It requires an initial value when created and is useful for cases where you always want the latest value to be emitted, like managing shared state.

    Example:
    ```typescript
    const behaviorSubject = new BehaviorSubject('Initial value');
    behaviorSubject.subscribe(val => console.log(val)); // Will emit 'Initial value'
    behaviorSubject.next('Updated value');
    ```

13. **What is the difference between `ReplaySubject` and `BehaviorSubject`?**
    - **Expected Answer:** 
      - **`ReplaySubject`**: Stores a **history of values** and emits those values to new subscribers, based on the number of values you specify when creating the subject.
      - **`BehaviorSubject`**: Stores the **latest value** only and emits it to any new subscriber.

    Example:
    ```typescript
    const replaySubject = new ReplaySubject(2);
    replaySubject.next(1);
    replaySubject.next(2);
    replaySubject.next(3);
    replaySubject.subscribe(val => console.log(val)); // Will emit 2, 3
    ```

14. **What is an `AsyncSubject` in RxJS, and when would you use it?**
    - **Expected Answer:** An `AsyncSubject` only emits the **last value** from an Observable **when it completes**. It is useful when you want to ensure that only the final result of an Observable is important (e.g., the final outcome of an API call or a calculation).

    Example:
    ```typescript
    const asyncSubject = new AsyncSubject();
    asyncSubject.subscribe(val => console.log(val)); // Will emit only the last value
    asyncSubject.next(1);
    asyncSubject.next(2);
    asyncSubject.complete(); // Will emit 2
    ```

---

#### **b. Higher-Order Observables**

15. **What is a higher-order Observable in RxJS?**
    - **Expected Answer:** A higher-order Observable is an Observable that emits other Observables, meaning it emits inner Observables. These can be processed using operators like `mergeMap()`, `switchMap()`, `concatMap()`, etc., which flatten the inner Observables into a single stream.

16. **What is the `concatMap()` operator in RxJS?**
    - **Expected Answer:** `concatMap()` is a mapping operator that maps each emitted value to an inner Observable, but unlike `mergeMap()`, it subscribes to each inner Observable **sequentially** (one after the other). It ensures that the next Observable is only subscribed to after the previous one completes.

    Example:
    ```typescript
    obs$.pipe(
      concatMap(id => this.http.get(`api/user/${id}`)) // Sequential requests
    ).subscribe();
    ```

17. **How does `switchMap()` differ from `mergeMap()`?**
    - **Expected Answer:** 
      - `switchMap()` is used when you want to **switch to a new inner Observable** every time the source Observable emits a new value. It cancels the previous inner Observable and subscribes to the new one.
      - `mergeMap()` processes all inner Observables **concurrently**, and does not cancel any of them.

    Example:
    ```typescript
    obs$.pipe(
      switchMap(value => this.http.get(`api/user/${value}`)) //

 Cancels previous requests if a new value comes in
    );
    ```

18. **What is the `forkJoin()` operator in RxJS, and when would you use it?**
    - **Expected Answer:** `forkJoin()` is used to **combine multiple Observables** and wait for all of them to complete. It emits the last emitted value from each Observable in an array, once all Observables have completed. It is useful when you need to wait for multiple independent async operations to finish before continuing.

    Example:
    ```typescript
    forkJoin(
      this.http.get('api/user'),
      this.http.get('api/posts')
    ).subscribe(([user, posts]) => {
      console.log(user, posts);
    });
    ```

19. **What is the purpose of `combineLatest()` in RxJS?**
    - **Expected Answer:** `combineLatest()` combines the latest values from multiple Observables, emitting an array of the latest values each time any of the Observables emits a new value. It is useful when you need to react to changes in multiple sources.

    Example:
    ```typescript
    combineLatest([
      this.http.get('api/user'),
      this.http.get('api/posts')
    ]).subscribe(([user, posts]) => {
      console.log(user, posts);
    });
    ```