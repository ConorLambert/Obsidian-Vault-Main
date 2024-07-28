## Explained
- Create and return a new instance of the specified class.
- Replaces the current dependency with a new instance of another class.
- The alternative class can, for example, implement a different strategy, extend the default class, or emulate the behaviour of the real class in a test case.
- Default provider configuration

## Example
- In the following example, the `BetterLogger` class would be instantiated when the `Logger` dependency is requested in a component or any other class.
```typescript
[{ provide: Logger, useClass: BetterLogger }]
```

## Use Cases
#### Unit Testing Components
- We don't have to provide the full service but instead we can create a separate class that will be able to implement the methods in a different way.
- We only test the component itself and not its interaction with the service.
#### Quick Proof of Concept
- Example explained [here](https://developer.okta.com/blog/2022/10/11/angular-dependency-injection#configure-providers-with-useclass)