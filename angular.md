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