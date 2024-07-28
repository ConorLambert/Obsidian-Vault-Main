## @Input Required Property
- You can make an @Input required using the following syntax:
```typescript
	@Input({
		required: true
	})
	someInput: number;
```
- Note that the input passed in at runtime could be null or undefined. 
	- Forces the calling template to set a value for this property.
- Only available >= **Angular 16** .

## Browser Event Bubbling
- Native browser events bubble up the DOM tree from the source to the root. 
	- At each level of the tree, we can listen to this event and perform some action
	- Bubbling does not stop when it encounters the first listener. It continuous up the tree all the way to the root.
- Does not work with custom events in Angular i.e. events declared using @Output
	- Manually call .emit at each level.

## Self Closing Tags
- Angular has self closing tags on your custom components
	- `<course-card />` instead of `<course-card></course-card>`
- Only available >= **Angular 16** .

## @for Options Without Reference
- We can use the @for options without referencing them in the enclosing for declaration
- As seen with `$index` an `$first` below
	![[Pasted image 20240626131350.png|500]]

## Importance of a tracking in for @for/ngFor
- Prevents Angular from re-rendering the entire list
- Internally, Angular performs a diff on the old data vs the new data to see if something has changed. 
	- ???

## `[ngClass]` vs `[ngStyle]`
- `[ngClass]` should be used a lot more frequently then `[ngStyle]`.
- Further [discussion](https://www.reddit.com/r/Angular2/comments/qhjx4n/what_is_ngstyle_should_you_use_it/).

## `[ngClass]` vs `[class]`
- Use `[class]` to add only a single class conditionally.
```html
<div [class.has-error]="hasError"> </div>
<div [class.is-adult]="age >= 18 ? true : false"> </div>
```
- Use `[ngClass]` to add multiple classes conditionally.
```html
<div [ngClass]="{'error': hasError, 'warning': hasWarning}"> </div>
```
- Apparently `[class]` can now do multiple expressions like `[ngClass]` but is not recommended:
	- Check out this GitHub [thread](https://github.com/angular/angular/issues/40623) for more info
		- Theres a difference internally