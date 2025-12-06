# Angular

## Angular Directives
Directives in Angular are classes that add extra behaviors to HTML elements (DOMs)

1. Component Directives 
  - Component name as Directive 
  - Ex. <app-component> </app-component>
  
2. Structural Directives
  - *ngIf
  - *ngFor
  - *ngSwitch
  - ng-template

3. Attribute Directives 
  - ngStyle
  - ngClass

4. Custom Directives
  - User Defined


## Component Lifecycle

In Shortway
  - OnChanges → OnInit → DoCheck → AfterContent → AfterView → OnDestroy
  - Changes   → Init   → Check   → Content      → View      → Destroy (CICCVD)

1. ngOnChanges()
Triggered when input (@Input) properties change. Fires before ngOnInit.

2. ngOnInit()
Runs once after first ngOnChanges. Best place for initialization logic.

3. ngDoCheck()
Called during every change detection cycle. Used for custom change detection logic.

4. ngAfterContentInit()
Runs once after content (projected via <ng-content>) is inserted.

5. ngAfterContentChecked()
Called after Angular checks the content for changes.

6. ngAfterViewInit()
Runs once after component’s view (and child views) are fully initialized.

7. ngAfterViewChecked()
Called after Angular checks the component’s views for changes.

8. ngOnDestroy()
Cleanup hook — unsubscribe, detach events, stop timers, etc.

## Pure Pipes Vs Impure Pipes

Pure Pipes 
  - Triggered only when the input value (reference) changes (Default)
  - No re-run for: internal mutations (e.g., pushing to the same array) , frequent events or change detection cycles

Async Pipe
  - The async pipe is an Angular built-in pipe that automatically subscribes to an *Observable* or *Promise* and renders the latest emitted value in the template.

Impure Pure Pipes 
  - Run on every change detection cycle.
  - Triggered even when: input value changed in place (e.g., arr.push(1)), async data is coming in repeatedly

## Standalone Components
  - Standalone components are Angular components that do not require NgModules. They can import dependencies directly inside the component itself.

  - standalone: true → NgModule is not required
  - Can import other standalone components, pipes, directives
  - Can be used in lazy loading easily
  - Reduces boilerplate and improves tree-shaking

## Cancel an HTTP requests in Angular
  - Use RxJS and cancellation patterns: pass an AbortSignal via HttpClient (since Angular 16 supports abort), or use **takeUntil()** with a Subject that emits on destroy, or switchMap to replace inflight requests

  ```
    const destroy$ = new Subject<void>();
    http.get(url).pipe(takeUntil(destroy$)).subscribe();
    ngOnDestroy(){ destroy$.next(); destroy$.complete(); }
  ```

## Interceptors in Angular
  - Interceptors implement HttpInterceptor and are chained in the order provided. Each interceptor receives the request, can modify it, call next.handle(modifiedReq), and post-process the response. Interceptors are ideal for adding auth headers, logging, caching, retry logic, global error handling, and request/response transformations. Use HTTP_INTERCEPTORS multi-provider to register.

## Secure an Angular application?
  - Sanitize user-provided HTML; use DomSanitizer carefully.
  - Prevent XSS by using binding ([textContent], interpolation) instead of innerHTML.
  - Use CSP headers, secure cookies, and HTTPS.
  - Implement auth and authorization (JWT, OAuth) using secure storage (avoid localStorage for long-lived tokens) and refresh token flows.
  - Validate inputs server-side; use HttpInterceptor to attach tokens and handle 401s. Keep secrets out of client code.


## Ahead-of-Time (AOT) compilation work in Angular
  - AOT compiles templates and components at build time into JS factories and metadata, converting HTML templates into efficient code and doing template type checking. This reduces runtime parsing, detects template errors early, and shrinks runtime size. AOT leads to faster bootstrap and earlier failure detection compared to JIT.


## Scale state management in Angular
  - **NgRx (Redux style):** predictable, good for large apps, side-effect management via @ngrx/effects.
  - **Akita:** more pragmatic and flexible.
  - **ComponentStore:** RTK-like lightweight store scoped to feature.
  - **Signals:** good for local reactive state and simpler patterns.