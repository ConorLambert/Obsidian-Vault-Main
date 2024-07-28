#### Overview
 - Used in applications that have a mix between Module and Standalone based components. 
 - The `StandaloneInjector` will be created as a child of the [[EnvironmentInjector]], under which the component being created falls.
#### Example
	![[Pasted image 20240129184709.png|500]]

- The standalone component `DateModalComponent` uses another component `DatePickerComponent`, which is not standalone, and a service `CalendarService`.
- Therefore, we are forced to import the module `DatePickerModule` in which they reside.
