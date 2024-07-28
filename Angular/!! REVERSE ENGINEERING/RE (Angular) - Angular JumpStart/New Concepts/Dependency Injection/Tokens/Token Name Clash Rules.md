What happens if you define two modules with the same provider token?

1. The provider defined in the module that imports other module always wins:
	- `AppModule` and `AModule` both contain a provider token called `'SOME_TOKEN'` then the `AppModule` version will be used.
2. The provider from the last imported module overrides providers in the preceding modules expect for the importing module (follows from the first rule). :
	- `AModule` and `BModule` both contain a provider token called `'SOME_TOKEN'` and `BModule` is imported after `AModule` then the provider for `BModule` will be used.