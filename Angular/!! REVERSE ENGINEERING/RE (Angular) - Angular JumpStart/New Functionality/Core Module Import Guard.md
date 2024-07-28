- The core module should be imported solely into your root Angular module.
- This is due to the singleton nature of many classes that reside in the CoreModule.
- A simple means of implementing the enforcement of this rule is adding the so-called **Import Guard** to the code of your **CoreModule** class.
- A sample implementation is depicted in the snippets below:

	![[Pasted image 20240125131226.png|500]]

	![[Pasted image 20240125131815.png]]

 - To understand this approach, we need to remember a few points:
	 - The CoreModule is to be imported into the root module
	 - The root module is at the top of the Angular module hierarchy
	 - All modules are merged during the compilation phase. Thus, there’s no hierarchical relationship between the module that is imported and the module that imports.
- ???
	