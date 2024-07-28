- Parameter decorator used in constructor parameters.
- Tells the DI framework to look for dependency resolution starting at the parent component and beyond (up the hierarchy).

	![[Pasted image 20240125133652.png|500]]

- In the above code snippet, the **@SkipSelf** parameter decorator instructs the DI framework to resolve the **LoggerService** dependency starting at the parent component of **ChildComponent**.
- The DI framework will first check the parent components *provider* array. 
- If not found, it will repeat the check for the parent component of that parent component and so on up the hierarchy. 
- If no provider is found then an error is thrown.
- The code snippet below shows the definition for **ParentComponent** which is the parent component of **ChildComponent** defined above.

	![[Pasted image 20240125134705.png|500]]

- We can see that **LoggerService** is declared in the providers array here.
- This means the DI framework will resolve the LoggerService dependency at the parent component level (and will not be required to go any further up the chain).