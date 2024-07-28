#### Overview
- The module specifier provides a string that the JavaScript environment can resolve to a path to the module file.

#### Example
```js

import { name, draw, reportArea, reportPerimeter } from "./modules/square.js";
```

#### Valid Module Specifiers
- Valid module specifiers must match one of the following:
	- A full non-relative URL. As in, it doesn't throw an error when put through new `URL(moduleSpecifier)`.
	- Starts with `/`
	- Starts with `./`
	- Starts with `../`

