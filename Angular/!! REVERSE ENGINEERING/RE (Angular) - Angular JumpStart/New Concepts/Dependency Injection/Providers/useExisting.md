## Explained
- Replaces the provider with a different provider already existing within the application.
- The first token is an alias for the service associated with the second token, creating two ways to access the same service object.

## Rules
- `useExisting` follows the same rules as though it where a dependency injected into a constructor, meaning its token is searched up the hierarchy using the same [[resolution rules]]. 
- `useExisting` can result in the creation of an instance if the source provider has not yet executed and thus has not created it's instance. However, it is not useExisting that does it but rather then provider its token refers to.
- Some [examples](https://stackoverflow.com/questions/38420933/angular-2-useexisting-providers)

## Example
- In the following example, the injector injects the singleton instance of `NewLogger` when the component asks for either the new or the old logger. In this way, `OldLogger` is an alias for `NewLogger`.
- Notice how `NewLogger` was already provided in the same providers array.
```typescript
[ NewLogger, { provide: OldLogger, useExisting: NewLogger}]
```

## Use Cases

#### API Narrowing
- It works well when we have many methods on the service, and we only want to use a few of them. This helps in reducing the size of the interface.
- Example explained [here](https://developer.okta.com/blog/2022/10/11/angular-dependency-injection#configure-providers-with-useexisting)