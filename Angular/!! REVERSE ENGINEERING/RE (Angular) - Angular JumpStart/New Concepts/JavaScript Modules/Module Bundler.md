#### Overview
- Module bundlers are programs that take JS modules as input and combine them into a single file.

#### Background
- Dividing our code into modules is nice because our codebase will be more organised and it will be easier to reuse our code.
- But this is an advantage only for the development phase of a project. 
- For every single JS file that a project uses (including third party files), this file needs to be fetched and loaded by the browser at runtime.
- This means a network request is needed for each file.
- When in production, modules are not the best thing, as forcing the browser to make a request for each JS file might hurt the site's performance.
- We should always try to reduce the requests to the minimum to increase the performance of our projects. This is where module bundlers come in.

#### Module Bundler vs Module Loader
- ???