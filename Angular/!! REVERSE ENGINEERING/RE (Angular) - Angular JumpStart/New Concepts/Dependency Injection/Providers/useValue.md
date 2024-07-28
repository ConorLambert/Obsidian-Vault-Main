## Explained
- The `useValue` key lets you associate a fixed value with a DI token.
- The fixed value can be an object or primitive value.
- Use this technique to provide runtime configuration constants such as website base addresses, feature flags and mocking services in automated tests where you need to control the inputs and outputs.
- Often used to set the initial configuration

## Example
```typescript
export const RACE_CARS_CONFIG: CARS_CONFIG= {  
  domain: 'api.race-cars.com',  
};

providers: [CarsService,  
 { provide: CARS_CONFIG, useValue: RACE_CARS_CONFIG}  
]
```

## Use Cases

#### ???
- ???
