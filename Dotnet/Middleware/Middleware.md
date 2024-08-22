[Source](https://app.pluralsight.com/ilx/video-courses/a1a7390d-edbc-41fd-9074-a51c5c77239e/2b46a360-978a-4e61-b35b-4d367c3c1eca/97c7d6b2-0ae3-4be6-9a98-befcc1bd0a5d)
## Overview
- A software component responsible for processing requests and generating responses in the web application pipeline
- When a HTTP request comes into your application, the middleware will take care of this using a number of middleware *components* chained together.
- The order in which middleware is added to the pipeline is important.
- Provides a modular way of processing HTTP requests and responses, allowing developers to add, remove, or reorder middleware components in the pipeline based on their specific needs.
![[Pasted image 20240822143723.png]]

## Methods
##### Run
- Last thing called in the pipeline
- Terminates the pipeline
##### Use
- Insert into pipeline
- Can terminate/short-circuit the pipeline
	- Think of **Authentication**, if the user is not authenticated, then they request will not continue onto the next component
##### Map
- Map branches the request pipeline based on matches of the given request path. 
- If the request path starts with the given path, the branch is executed.
- The new pipeline is used for the remainder of the request.
- The path is followed back for the response starting at the branched pipeline and out to the original main pipeline at the point it was branched.
- The branched pipeline has a terminating `Run` method call.
- Useful when we want to segment our URLs.
- More info [here](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-8.0#branch-the-middleware-pipeline).
- Pluralsight [video](https://app.pluralsight.com/ilx/video-courses/a1a7390d-edbc-41fd-9074-a51c5c77239e/2b46a360-978a-4e61-b35b-4d367c3c1eca/affea72e-1575-476d-9277-ca6b6b7ec257).

## Secondary Methods
##### UseWhen
- Use middleware on a *conditional* basis.
##### MapWhen
- Branch to new pipeline on a *conditional* basis.

## Endpoint Middleware
- Last middleware component in the cycle
- Executes the action endpoint.
- Where [[filters]] are applied

## Components
- Chooses whether to pass the request to the next component in the pipeline.
- Can perform work before and after the next component in the pipeline.

## Example Components
##### HttpsRedirection
- ???
##### Static Files
- ???
##### Routing
- ???
##### Authentication
- ???
- This should be added in the pipeline before components that require authorization.
##### Authorization
- ???

## Custom Components
- ???