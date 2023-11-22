## Creating and Deploying a Function App in Azure
```c#
using System.IO;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using Newtonsoft.Json;

public static class SampleFunction
{
    [FunctionName("SampleFunction")]
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function, "get", "post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        string name = req.Query["name"];

        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        dynamic data = JsonConvert.DeserializeObject(requestBody);
        name = name ?? data?.name;

        string responseMessage = string.IsNullOrEmpty(name)
            ? "This HTTP triggered function executed successfully. Pass a name in the query string or in the request body for a personalized response."
            : $"Hello, {name}. This HTTP triggered function executed successfully.";

        return new OkObjectResult(responseMessage);
    }
}
```
## Create durable functions
Creating a Durable Function in C# involves a bit more setup compared to a standard Azure Function, as it typically involves orchestrating multiple function calls. Here's a simple example of a Durable Function that includes an orchestrator function, an activity function, and a client function.

#Activity Function:
This function does the actual work. In this example, it just returns a string.
```c#
using Microsoft.Azure.WebJobs;
using Microsoft.Extensions.Logging;

public static class SayHelloActivity
{
    [FunctionName("SayHelloActivity")]
    public static string SayHello([ActivityTrigger] string name, ILogger log)
    {
        log.LogInformation($"Saying hello to {name}.");
        return $"Hello {name}!";
    }
}

```
#Orchestrator Function:
This function orchestrates the calls to the activity functions.

```c#
using System.Collections.Generic;
using System.Threading.Tasks;
using Microsoft.Azure.WebJobs;
using Microsoft.Extensions.Logging;

public static class HelloSequenceOrchestrator
{
    [FunctionName("HelloSequenceOrchestrator")]
    public static async Task<List<string>> RunOrchestrator(
        [OrchestrationTrigger] IDurableOrchestrationContext context,
        ILogger log)
    {
        var outputs = new List<string>();

        // Replace "hello" with the name of your Durable Activity Function.
        outputs.Add(await context.CallActivityAsync<string>("SayHelloActivity", "Tokyo"));
        outputs.Add(await context.CallActivityAsync<string>("SayHelloActivity", "Seattle"));
        outputs.Add(await context.CallActivityAsync<string>("SayHelloActivity", "London"));

        // returns ["Hello Tokyo!", "Hello Seattle!", "Hello London!"]
        return outputs;
    }
}
```
#Client Function:
This function is the entry point and is used to start the orchestrator.
```c#
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using System.Net.Http;
using System.Threading.Tasks;

public static class HelloSequenceClient
{
    [FunctionName("HelloSequenceClient")]
    public static async Task<HttpResponseMessage> Run(
        [HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
        [DurableClient] IDurableOrchestrationClient starter,
        ILogger log)
    {
        // Function input comes from the request content.
        string instanceId = await starter.StartNewAsync("HelloSequenceOrchestrator", null);

        log.LogInformation($"Started orchestration with ID = '{instanceId}'.");

        return starter.CreateCheckStatusResponse(req, instanceId);
    }
}
```
This set of functions demonstrates a basic Durable Function pattern. The client function triggers the orchestrator, which then calls the activity function multiple times. The activity function does some work (in this case, just returns a string) and returns the result to the orchestrator.

To deploy and test this Durable Function, you'll need to set it up in your Azure environment with the necessary configurations for Durable Tasks. Be sure to include the Durable Task extension in your function app dependencies.

