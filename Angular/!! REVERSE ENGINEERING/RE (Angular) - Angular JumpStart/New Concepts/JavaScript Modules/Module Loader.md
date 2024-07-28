A module loader is typically some library that can load, interpret and execute JavaScript modules you defined using a certain module format/syntax, such as AMD or CommonJS.

When you write modular JavaScript applications, you usually end up having one file per module. So when writing an application that consist of hundreds of modules it could get quite painful to make sure all files are included and in the correct order. So basically a loader will take care of the dependency management for you, by making sure all modules are loaded when the application is executed. Checkout some popular module loaders such as RequireJS and SystemJS to get an idea.


#### Disadvantages
- ??? 
