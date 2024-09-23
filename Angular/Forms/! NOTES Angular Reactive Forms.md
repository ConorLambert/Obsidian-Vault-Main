[Source](https://app.pluralsight.com/library/courses/angular-reactive-forms/table-of-contents)

# Getting started with Angular Reactive Forms
### Angular Forms Architecture Overview
- Both Template Driven Forms and Reactive Forms use the `FormControl` and `FormGroup` classes.

### Template Driven Forms vs Reactive Forms
- Reactive forms uses one-way data binding from component to template.
- How is data changes made in the template reflected back to the component?
- When data changes in an element, internally an **input** event is created which holds the latest value and that value get's relayed to the associated FormControl inside the component.
- One-way binding approach is more performant than two-way data binding that Template Driven forms use.

# Creating Angular Reactive Forms
### The Magic of ControlValueAccessor Directive
- Keeps the HTML elements and form controls in sync.

### Saving Submitted Form Data
- Any disabled HTML form elements will not appear in the `value` property of `FormGroup`.
- However, the `getRawValue()` method will return all properties whether disabled or not.
- The `Partial` type in TypeScript allows you to accept objects that do not fully implement their interface.
- Working with `Partial` objects makes sense because not every field in a form will be filled out.

### Adding Unbounded FormControls to a FormGroup
- For fields that we need for form submission like `id`, we can add an associated entry to the `FormGroup` but just don't create a HTML element for it.

### Creating Nested FormGroups
- Use `formGroup.getRawValue()` when sending to service

### Simplifying with `FormBuilder` and `FormGroup.setValue()`
- Passing an initial value to FormControl will infer it's type.
- Pass in `{ nonNullable: true }` as second parameter to FormControl to indicate it's not nullable.
- Our form so far works, but it's very messy and verbose.
- Easier and less verbose way to define whole form using the `FormBuilder` library.
- Remove all instantiations to `FormControl()` and replace with just type value.
- Can default all members of `FormGroup` to be non-nullable like so:
	- `this.fb.nonNullable`
	- Don't forget about nested form groups
- Can then set an individual member to null using the following syntax:
	- `<number | null> null`
- Can use `formGroup.setValue(someObject)` to set all it's members (including nested form groups) to those defined by `someObject` provided that `someObject` has the same shape as `formGroup` 
	- Extremely useful for setting initial values based of a formGroup based on an object returned from an API call.
- What if we don't want to initialize all members using `setValue`
	- `patchValue` is used to update specified members
		`const names = {firstName: contact.firstName, lastName: contact.lastName}`
		`this.contactForm.patchValue(names)`
- Radio buttons from a radio group should all have the same `formControlName` for it to work.

# Working with Input Elements and Data Types
### Working with Radio Buttons
- Each input from a radio group should have the same `formControlName`.
- The value that is stored in the `FormControl` will be the `value` attribute of the selected item.

### Working with Select Lists
- `formControlName` is added to the `select` element

### Working with Check Boxes
- Don't have to specify a value
	- The `value` property of the element is completely ignored
- Reactive Forms will always treat check boxes as boolean.
- A special `ControlValueAccessor` called `CheckboxControlValueAccessor` is applied to checkbox elements

### Working with Numeric Inputs
- Even though we defined the FormControl to be a number in the component code, typescript will translate it to a string when we edit the associated input.
	- So initially it will see it as number until the user edits it
- In order to fix this, we need to update the input element in the view to include the `type="number"` attribute.
- This will cause the `NumericControlValueAccessor` to be used.

### Working with Textarea Elements
- Uses the `textarea` element
- Use the `rows` property on the element to determine the height of the textbox.

### Working with Date Values
- This is tricky
- Dates are kind of a mess in JavaScript
- Angular does not have an out of the box `DateValueAccessor`, even if we set `type="date"` on the `input` element.
- Most frontend applications use strings for their dates. 
	- Even JSON doesn't have a `Date` type which means we are getting returned a date as a string from an API call anyway.
- `toISOString` can be called on a `Date` object to convert it to a string.
- We use the `date` pipe inside the `[value]` property. ![[Pasted image 20240912184348.png]]
- We can use the following expression to convert an ISO string down to just `yyyy-MM-dd`.
![[Pasted image 20240912184058.png]]


# Validating Angular Forms
### Adding Validation to FormControls
- Each `FormControl` of your `FormGroup` has a `valid` field that is either true or false.
- This state bubbles up to the `FormGroup`.
- Can add multiple validators to a `FormControl`.
- `FormControl` also has an `invalid` state which is the opposite value of `valid`

### Displaying Validation Messages
- The `touched` property indicates that the field has been entered into and left.
- Use the `touched` property in conjunction with `valid`/`invalid` to check if a form control has been touched and is invalid.
- The expression used to access a FormControl can be quite lengthy so it's common to place this logic behind a `getter` method in the component.
	- ??? Is this efficient.

### Handling Multiple Validators
- Use array as second parameter.
- When a FormControl has multiple validators and only a subset of those validators are failing, we only want to show the error message associated with the failed validator. Using the current approach of checking for `invalid` will not work here as it will show the message if any error exists. To achieve our goal, we can use the `errors` object instead of `invalid`.
- Every `FormControl` has an `errors` property which is an object of key:value pairs where the keys are filled in for every type of error there is. For example, if a *required* error is present on the `FormControl` then the `errors` object will have a `required` property filled in.
- The `errors` object is null if there are no errors so make sure to check for `null` in the View template.
- TypeScript will complain because it doesn't know if the `required` property exists, so do the following instead
	- `firstName.errors?.['required']`

### Validating FormGroups and Form
- `dirty`: they have typed into the field.
- When displaying an error message based on the state of the FormGroup, it's better to use `invalid` in conjunction with `dirty` instead of `touched`
- When enabling/disabling a button based on a FormGroup, we can just use the `invalid` property.
- A `FormGroups` `invalid`/`valid` and `dirty` fields inherit from their `FormControls` and sub FormGroups.

### Creating Custom Validators
![[Pasted image 20240913151606.png]]
- The result of the function gets *merged* with the existing `errors` object.
- Can use the validator like so:
	- `notes: ['', restrictedWords]`

###  Passing Data to Custom Validators
- We need to wrap the validator function in another function. 
- The outer function will take the parameter(s) we wish to pass and return the validator function.
	![[Pasted image 20240913152010.png|500]]
- This validator can be called like so
	- `notes: ['', restrictedWords('foo','bar')]`
- What if we want to return what restricted words where found ?
- The object we return doesn't have to contain true or false for each of it's properties
- In fact, we can replace `true` with an array, string, object etc
- In our case, we can pass back the `invalidWords` array we created
	![[Pasted image 20240913152416.png|500]]
- Can be called from the template like so:![[Pasted image 20240913152523.png|500]]
- It acts as a truthy in the case of an if statement.

# Creating Custom Controls and ControlValueAccessor 
### Creating a custom DateValueAccessor
- ???
- Create a directive
- When creating a `ControlValueAccessor`, you need to register it as a `NG_VALUE_ACCESSOR` provider.
- This allows Angular to pick this up and use it as a provider where appropriate.
- Add the provider to the `providers` array of the new directive.
- Use `forwardRef` to circumvent TypeScript complaining that we use `DateValueAccessorDirective` before it was defined.

### Custom DateValueAccessor: Implementing `writeValue()`
- FormControl => View
- `writeValue` updates the HTML element when the FormControl value is changed.

### Custom DateValueAccessor: Handling input events
- View => FormControl
- Listen to host element input events so we can update the FormControl value
- Can be done using `@HostListener`
- Pass the event we want to listen to, which in our case is 'input'.
- Second argument to `@HostListener` is the property we wish to read from when the event happens
- A common property is the following `$event.target.value`.
- However, when dealing with input elements of type `date`, we can use the `valueAsDate` property.
- ------------------------
CONFUSING
- So the way this all works together is that when the host element's input event is fired, it will call our `onChange` method and it will pass into it this `valueAsDate` parameter, which it got from the host element's input event. And then we will pass that along to the callback function, which will actually update our FormControl's value for us.
- `registerOnTouched` works similar to the above.
- `registerOnTouched` listens to the `blur` event

# Dynamically Adding Form Elements
### Understanding FormArrays
- An array of FormControls or FormGroups
- Can access items using index
- Can push and pop items from the FormArray.
### Dynamically Adding Form Elements
- Loop over the `controls` property of the `FormArray`, not the `FormArray` itself.
- Reference the index variable in the for loop and use that index for the `formGroupName` property
- Need to create a new `FormGroup`/`FormControl` element within the `FormArray` for each item of the source data. For example, if you have an array of 3 phone numbers, then we need to create a FormArray with 3 FormGroup elements. This has to be done inside the component logic.
	- Note, you only need to create an empty `FormGroup`. Like a placeholder that will be filled in when `setValue` is called later on.

# Reacting to Changes
### Subscribing to Value Changes
- Subscribe to the `valueChanges()` observable
### Reacting to Value Changes
- Call the `updateValueAndValidity()` method when dynamically adding and removing validators. 
	- Called on the `AbstractControl` to which the validation was added/removed from.
- `updateValueAndValidity()` will cause `valueChanges` to trigger again and cause an infinite loop, so we need to use the `distinctUntilChanged()` operator after subscribing to `valueChanges`.
- `statusChanges` emits whenever the validity of an `AbstractControl` changes.
- In the View template, the for loop that iterates over the `FormArray` will reference each individual control in the array. We can use this reference to check for validity, etc.