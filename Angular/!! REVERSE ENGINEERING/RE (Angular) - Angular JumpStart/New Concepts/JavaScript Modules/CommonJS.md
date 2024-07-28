#### Overview
- CommonJS is a set of *standards* used to implement [[Modules]] in JavaScript.
- Introduced in 2009

#### Implementations
- Important to note that it is a standard and not code in any form (library, etc).
- There are a number of tools and technologies that implement the standard as part of their operation (full list [here](https://en.wikipedia.org/wiki/CommonJS#Implementations)):
	- Node.js
	- MongoDB
	- JSBuild

#### Use Cases
- CommonJS is mainly used in server-side JS apps with Node.
- It is also used for browser-side JavaScript, but that code must be packaged with a transpiler since browsers don't support CommonJS.

#### Example
- CommonJS can be recognised by the use of `module.exports` and the `require()` function as the example below shows:

**mod1.js**
```
const mod1Function = () => console.log('Mod1 is alive!')
const mod1Function2 = () => console.log('Mod1 is rolling, baby!')

module.exports = { mod1Function, mod1Function2 }
```

**main.js**
```
({ mod1Function, mod1Function2 } = require('./mod1.js'))

const testFunction = () => {
    console.log('Im the main function')
    mod1Function()
    mod1Function2()
}

testFunction()
```