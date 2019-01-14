# koa vs express 

## Reference
- [Koa vs Express in NodeJS: 2018 Edition](https://raygun.com/blog/koa-vs-express/)


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
function test(params, callback){
	//make async call here
	asyncCall(params, function(res) {
		callback(res);
	})
}

test(myParams, function(data){
  //do something with 'data' here
})
```

The myFunction function takes a function-typed parameter as its second parameter. The internal implementation of myFunction would typically make an asynchronous call. This could be an API call, or a database query. When that async operation completes, myFunction will call the function passed in, and the calling routine can access the response (or whatever else it needs to do after the async call completes.)

This is fine for a single call, however, it quickly gets unwieldy. Application code that needs to make multiple, related async calls becomes difficult to read and harder to maintain. This is such a common problem that it has a name: “callback hell.”

The keywords async and await have been present in languages such as C# for some time. They were recently added to the Javascript specification, and to Node. Here’s what the code above looks like using async/await:


```zsh
async test(){
	try	{
		let res = await asyncCall();
		return res;
	}
	catch(err){
		console.log("Error: " + err);
	}
}

let result = await test();
```

The code using async and await is shorter, easier to read, and the exception handling “just works.” This code executes asynchronously, just as the callback code does, but it looks like synchronous code.
Koa uses async/await “out of the box.” Express is callback-oriented.

## Results
- If you are deciding between Koa and Express, ask these questions:
- Is it a greenfield application? If so, you have an opportunity for cleaner, more readable async code with Koa.
- Are you adding to an existing Express-based app? If so, stick with Express. Koa and Express don’t play well together- Koa’s - Context object is not compatible with the base Node req and res objects.
- Is performance paramount? Koa has a slight edge over Express in this area.
- If you prefer a leaner download footprint for your frameworks, Koa is modular, so you can include only what you need.
- If you prefer to use a complete framework without having to pull in multiple dependencies, Express is the better choice.
