# General
### What is RxJS Map and What is Higher-Order Observable Mapping ?
- **RxJS Map** 
	- Flattening operator used to transform current emitted data values to the desired data format.
- **Higher-Order Mapping**
	- RxJS operators used to map source observable values into other observables.

### What are inner and outer observables ?
- [ChatGPT answer](https://chatgpt.com/c/66e4049d-5008-8012-958b-ffaec6d66b37)
- The outer observable is the main or higher-level observable that emits values, and these values are often themselves observables. The outer observable contains a stream of events that could be primitive values (like numbers or strings) or complex values like observables.
- An inner observable is the values emitted from an outer observable when those values are themselves observables.
- The inner observable is the observable that is emitted by the outer observable. When the outer observable emits an observable, the emitted observable becomes the "inner observable." 
- Typically, we want to flatten these inner observables to work with the values they emit.

# concatMap
### What is the `concatMap` operator ?
- Used when the source observable emits values that are themselves observables (or when you return observables from the transformation function). 
- It subscribes to each emitted observable one at a time and waits for the current one to complete before subscribing to the next one.

### How is `concatMap` different from `map` ?
- [ChatGPT Answer](https://chatgpt.com/c/66e401d2-e3a8-8012-8108-f79ec1348f56)
- `concatMap` processes each observable sequentially, waiting for each one to complete before moving to the next. 
- `map` simply transforms the value, with no concern for dealing with observables or concurrency.

### What is a use case for `concatMap` ?
- Used to combine multiple HTTP requests; alleviating the need for nested subscribers.
- All HTTP requests are sent to the backend sequentially; Once the previous request has been completed.

# mergeMap
### What is the `mergeMap` operator ?
[ChatGPT Answer](https://chatgpt.com/c/66e40475-2f14-8012-b8ce-d452d30780ec)
- ???
- Similar to `concatMap` but is done in parallel rather than sequentially.
