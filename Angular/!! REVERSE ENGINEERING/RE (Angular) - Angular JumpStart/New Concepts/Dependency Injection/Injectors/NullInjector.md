- Special kind of injector that lacks providers. 
- If you attempt to retrieve a provider from it, an error is returned or `null` if the [[@Optional]] decorator was used. 
- This serves as a useful fallback mechanism to ensure that if a provider is not found in any of the parent injectors, an error or null will be returned. 
- This makes it easier to debug issues related to missing providers. 
- This is the top-level injector in the [[! Injector Hierarchies|Injector hierarchy]].