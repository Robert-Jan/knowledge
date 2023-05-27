Durable Functions is an extension of Azure [[Functions]] that lets you write stateful functions in a serverless compute environment. The extension lets you define stateful workflows by writing orchestrator functions and stateful entities by writing entity functions using the Azure Functions programming model. Behind the scenes, the extension manages state, checkpoints, and restarts for you, allowing you to focus on your business logic.

### Orchestrator Functions Rules
-  Must be deterministic: the whole function will be "replayed".
- Don't:
	- Use current date time.
	- Generate radnom numbers or GUIDS.
	- Access data stores (e.g. database, configurattion).
	- No I/O to disk or network
	- No `Thread.Sleep`
	- Do not initiate async operations 
		- No `Task.Run`, `Task.Delay`, `HttpClient.SendAsync`.
		- (except on `IDurableOrchestrationContext`)
	- Do not create infinite loops.
		- Recuring orchestrator functions can use `ContinueAsNew`
- Do:
	- Use `IDurableOrchestrationContext.CurrentUtsDateTime`.
	- Pass configuration into your orchestrator function
	- Retrieve data in activity functions

### Loggin in Orchestrator Functions
- Use the `ILogger` interface
- Log messages get written on every replay so use: `log = ctx.CreateReplaySafeLogger(log)` to ensure that log messages are only written once.

### Handling Errors
- Retry activitys with: `await ctx.CallActivityWithRetryAsync<>("FUNCTION_NAME", new RetryOptions(TimeSpan.FromSeconds(5), 4), FUNCTION_ARGUMENT);`
