# QueueTrigger - Python

The `QueueTrigger` makes it incredibly easy to react to new Queues inside of Azure Queue Storage. This sample demonstrates a simple use case of processing data from a given Queue.

## How it works

For a `QueueTrigger` to work, you provide a path which dictates where the queue messages are located inside your container.

## Getting Started

This is a boilerplate sample of an Azure function written in Python and bound to a Queue Trigger for execution

## Prerequisites

* An Azure subscription
* An [Azure Storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal)
* Python 3.6.x installed. ([3.6.8 for Windows](https://www.python.org/downloads/release/python-368/), [3.6.9 for *NIX based systems](https://www.python.org/downloads/release/python-369/))
  * Note that Python version 3.7 and above is not currently supported with Azure Functions
* [NodeJS (for NPM)](https://nodejs.org/)
* [.NET Core 2.x](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* [VS Code](https://code.visualstudio.com/) installed
* [Azure Functions extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)
* [Azure Storage Emulator](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-emulator)
* [Azure Functions Core Tools](https://www.npmjs.com/package/azure-functions-core-tools)

## Quickstart

1. Begin by [creating an Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal) and [creating a queue within the resource](https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal)

2. Then, in this project's root directory, create a `local.settings.json` file with the following schema and replace <STORAGE_ACCOUNT_NAME> and <SOTRAGE_ACCOUNT_CONNECTION_STRING> with your own account name and connection string:

  ```  {
    "IsEncrypted": false,
    "Values": {
      "AzureWebJobsStorage": "UseDevelopmentStorage=true",
      "FUNCTIONS_WORKER_RUNTIME": "python",
      "<CONNECTION_NAME>": "<STORAGE_ACCOUNT_CONNECTION_STRING>"
    }
  }
  ```

3.For most Azure Functions, a storage account is needed for the runtime itself. For local development, run the ```Azure Storage Storage Emulator``` installed as part of the prerequisites. After running, a shell will appear with instructions detailing how to use the tool. To start, run the `AzureStorageEmulator.exe init` command. Then, enter the `AzureStorageEmulator.exe start` command to run the emulator.

4.Check the `function.json` file to ensure that the value for `"connection"` matches the key for `"<CONNECTION_NAME>"` in the `local.settings.json` file.

5.Run the project either in Visual Studio Code or in your terminal by entering `func host start` in the root directory. As a message is entered in the Azure Storage Queue, it should be dequeued by the function and printed to the console. 