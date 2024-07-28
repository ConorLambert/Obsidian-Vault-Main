Dev.to [Article](https://dev.to/this-is-angular/angular-revisited-tree-shakable-components-and-optional-ngmodules-36d2#transitive-module-scope)

----------------------------------------------------------------------
#### Introduction
- Every Angular module has a **transitive module scope** which is decided at *compile time*. 
- The transitive module scope actually consists of two scopes: 
	- Transitive exported scope
	- Transitive compilation scope 
##### Transitive Exported Scope
- The transitive exported scope of an Angular module is all the declarables that an Angular module lists in its `exports` array. 
- It can also re-export other Angular modules by listing them in that same array. 
##### Transitive Compilation Scope
- The transitive compilation scope of an Angular module consists of all the declarables that a component declared by that Angular module can use in its template.
- This includes not only the declarables defined in that Angular modules `declarations` array but also those defined in the `exports` array of all modules imported by that Angular module.

![[Pasted image 20240127140030.png|400]]

- The image above is a simple example of a HeroModule. 
- The transitive compilation scope of HeroModule is highlighted in red and consists of:
	- HeroComponent
	- HeroListComponent 
	- AsyncPipe
	- NgIf
	- NgForOf
- Because HeroModule imports CommonModule, the exports declared by the CommonModule become part of the transitive compilation scope of HeroModule.