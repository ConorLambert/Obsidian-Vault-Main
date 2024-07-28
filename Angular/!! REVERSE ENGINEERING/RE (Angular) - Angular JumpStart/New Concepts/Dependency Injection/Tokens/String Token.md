## Purpose
- Sometimes we must inject a raw string value where there is no type.
- We can use string tokens in such a scenario.

## Example
- The string `'PRODUCT_SERVICE'` in the example below is a string token:

```typescript
providers: [{ provide: 'PRODUCT_SERVICE', useClass: ProductService }]
```

- You can then use Inject the `ProductService` using the `@Inject` method

```typescript
export class AppComponent {
  products: Product[];
  constructor(
    @Inject('PRODUCT_SERVICE') private productService: ProductService
  ) {}
```

## Problem With String Tokens
- String tokens can cause name clashes so we prefer to use [[InjectionToken]] instead.
- Search for the section with heading "Problems with the String Tokens" in this [article]() to get more information on why String Tokens are problematic.