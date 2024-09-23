### Loading Strategy ?
- Lazy loading
- PreloadAllModules

### What Interceptors where used ?
- HTTPInterceptor for errors

### How was state managed ?
- Was NGRX, then moved to NGXS

### Swagger
- We used swagger to auto-generate the C# models into TypeScript code

### What RxJS operators where used ?
[ChatGPT source](https://chatgpt.com/c/612a9b5a-de9f-496e-9621-cd40bf6bfea3)
- map()
- switchMap()
- mergeMap()
- combineLatest()
	- Can enable Submit button if username and password filled in
- share()
- retry()
- catchError()

### What caching was done ?
- share()

### How was it tested ?
- Jasmine

### What was your most important/complex feature
- InputsGrid