# koa vs express
## How Koa Compares to Express?

Express is a complete NodeJS application framework. Koa is developed by the Express team, however, it has a different focus. Koa concentrates its efforts on core middleware functionality. NodeJS middleware are routines that have access to the Request object (req) and Response object (res). These routines are called before route handlers, so they live in the “middle” between the client the response-generating route logic. A NodeJS application can “chain” middleware routines into a custom request/response pipeline. The pipeline can act on the request and response, including the headers and body. Both Express and Koa include middleware, but the implementation approach is quite different.


## “Do one thing well” vs “Batteries Included”
The core Koa module is just the middleware kernel. Express includes a complete application framework, with features such as routing and templates. Koa does have options for these features, but they are separate modules. Koa is more modular as a result; you only have to include the modules you need. The core Koa module is only about 2K lines of code, so if you only need the core Context object (described in the next section,) Koa provides a very small download footprint. Express comes with a complete suite of middleware features built in.



## Koa vs Express Middleware: Replace vs Extend
Express augments and extends the the native NodeJS req and res objects. Koa replaces them entirely with a Context object ctx. The Context object has ctx.request and ctx.response object properties that are used instead of the NodeJS req/res objects. Koa is designed to improve the overall experience of writing middleware routines, using new features of NodeJS: async/await. These new features reduce the amount of code required to write middleware functions.


## Async/Await vs Callbacks
Javascript and NodeJS follow one rule above all: network calls are always asynchronous. There are several ways to write async code: callbacks, Promises, and the new async/await keywords available in Node 7.6 and later. Koa was developed by the Express team explicitly to take advantage of the new async/await keywords.

This is what a callback looks like:

```zsh
function myFunction(params, callback){
	//make async call here
	asyncCall(params, function(res) {
		callback(res);
	})
}

myFunction(myParams, function(data){
  //do something with 'data' here
})
```
