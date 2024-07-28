https://medium.com/@shilinpm/what-is-component-factory-in-angular-19f0c74b36fc

In Angular, a component factory is an object that creates instances of a component dynamically at runtime. It’s a low-level API that provides a way to create components programmatically, rather than through the normal process of declaring them in a template.

Component factories are useful in situations where you need to create components on the fly, such as when creating modals (popup dialogs). They allow you to create instances of components and attach them to the DOM at runtime, giving you greater control over the application’s behaviour.

To create a component factory in Angular, you need to use the `ComponentFactoryResolver` service. This service provides a method called `resolveComponentFactory`, which takes the component class as an argument and returns a `ComponentFactory` object. You can then use this factory to create instances of the component by calling its `create` method.