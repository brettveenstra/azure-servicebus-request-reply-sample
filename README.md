# Introduction 
This is a sample implementation of the request-response message bus pattern using Azure Functions and Azure Service Bus.

# Getting Started
Setup environment (or local.settings.json) values:

|Name|Description|
|---|---|
|ServiceBusConnectionString|Connection string/SAS with *full* (read,write,manage) rights to a ServiceBus namespace|
|QueueName|Name of an existing queue in the above namespace, which will be used for sending the *request*|
|RequestTimeoutInMilliseconds|(Optional) Request timeout in milliseconds, i.e. how long to wait for the response|

There will be an HTTP trigger function at *http://localhost:7071/api/messages* that will accept a simple POST with a payload:
```json
{ "name": "string", "Amount": integer, "DueDate": "20200127T23:00:00.0000000" }
```

On success, the API will respond with
```json
{
    "workId": "<GUID>",
    "timestamp": "<UTC timestamp of message received>"
}
```
