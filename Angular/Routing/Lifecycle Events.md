#### Overview
- Just like a component, a router has lifecycle events

#### Events
- The events and sequence are as follows:
	- NavigationStart
	- RouteConfigLoadStart
	- RouteConfigLoadEnd
	- RoutesRecognized
	- GuardsCheckStart
	- ChildActivationStart
	- ActivationStart
	- GuardsCheckEnd
	- ResolveStart
	- ResolveEnd
	- ActivationEnd
	- ChildActivationEnd
	- NavigationEnd
	- NavigationCancel
	- NavigationError
	- Scroll
- A component is initialised after the `NavigationEnd` event but before the `Scroll` event.

#### Hooking into Router Events
- Inject the `Router` service into any class
- `Router` has an observable property that emits router events as they happen.

#### Use Cases
- Animation between views
- Logging user flows
- Run custom logic