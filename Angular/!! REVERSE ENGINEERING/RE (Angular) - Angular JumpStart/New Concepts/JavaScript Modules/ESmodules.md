#### Overview
- ESmodules is a set of *standards* used to implement [[Modules]] in JavaScript.
- Introduced in 2015
- ES stands for [[ECMAScript]]
- The idea was to standardise how JS modules worked in both browsers and servers.
- [[CommonJS]] (which was the main standard used prior) only worked mainly on the server-side.
- ESmodules are often to as ESM (ECMAScript Modules).

#### Example
- ES modules can be recognised by the use of `import` and `export`.

**mod1.js**
```
const mod1Function = () => console.log("Mod 1 is alive");
export { mod1Function }
```

**main.js**
```
import { mod1Function} from './mod1.js';

const testFunction = () => {
	console.log('main.js is alive');
	mod1Function();
}

testFunction();
```