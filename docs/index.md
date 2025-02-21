---
title: Homepage
description: AWS Lambda Powertools for TypeScript
---

AWS Lambda Powertools for TypeScript provides a suite of utilities for AWS Lambda functions running on the Node.js runtime, to ease the adoption of best practices such as tracing, structured logging, custom metrics, and more.  

You can use the library in both TypeScript and JavaScript code bases.

## Tenets

Core utilities such as Tracer, Logger, Metrics, and Event Handler will be available across all Lambda Powertools runtimes. Additional utilities are subjective to each language ecosystem and customer demand.

* **AWS Lambda only**. We optimise for AWS Lambda function environments and supported runtimes only. Utilities might work with web frameworks and non-Lambda environments, though they are not officially supported.
* **Eases the adoption of best practices**. The main priority of the utilities is to facilitate best practices adoption, as defined in the AWS Well-Architected Serverless Lens; all other functionality is optional.
* **Keep it lean**. Additional dependencies are carefully considered for security and ease of maintenance, and prevent negatively impacting startup time.
* **We strive for backwards compatibility**. New features and changes should keep backwards compatibility. If a breaking change cannot be avoided, the deprecation and migration process should be clearly defined.
* **We work backwards from the community**. We aim to strike a balance of what would work best for 80% of customers. Emerging practices are considered and discussed via Requests for Comment (RFCs)
* **Progressive**. Utilities are designed to be incrementally adoptable for customers at any stage of their Serverless journey. They follow language idioms and their community’s common practices.

## Features

| Utility | Description
| ------------------------------------------------- | ---------------------------------------------------------------------------------
[Tracer](./core/tracer.md) | Trace Lambda function handlers, and both synchronous and asynchronous functions
[Logger](./core/logger.md) | Structured logging made easier, and a middleware to enrich log items with key details of the Lambda context
[Metrics](./core/metrics.md) | Custom Metrics created asynchronously via CloudWatch Embedded Metric Format (EMF)

## Installation

The AWS Lambda Powertools for TypeScript utilities (which from here will be referred as Powertools) follow a modular approach, similar to the official [AWS SDK v3 for JavaScript](https://github.com/aws/aws-sdk-js-v3).
Each TypeScript utility is installed as standalone NPM package.

Install all three core utilities at once with this single command:

```shell
npm install @aws-lambda-powertools/logger @aws-lambda-powertools/tracer @aws-lambda-powertools/metrics
```


Or refer to the installation guide of each utility: 

[Installation guide for the **Tracer** utility](./core/tracer.md#getting-started)

[Installation guide for the **Logger** utility](./core/logger.md#getting-started)

[Installation guide for the **Metrics** utility](./core/metrics.md#getting-started)

## Instrumentation

You can instrument your code with Powertools in three different ways:  

* **Middy** middleware. It is the best choice if your existing code base relies on the [Middy](https://middy.js.org/docs/) middleware engine. Powertools offers compatible Middy middleware to make this integration seamless.
* **Method decorator**. Use [TypeScript method decorators](https://www.typescriptlang.org/docs/handbook/decorators.html#method-decorators) if you prefer writing your business logic using [TypeScript Classes](https://www.typescriptlang.org/docs/handbook/classes.html). If you aren’t using Classes, this requires the most significant refactoring.
* **Manually**. It provides the most granular control. It’s the most verbose approach, with the added benefit of no additional dependency and no refactoring to TypeScript Classes.

The examples in this documentation will feature all the approaches described above, when applicable.

## Environment variables

!!! info
    **Explicit parameters passed in constructors or in middleware/decorators take precedence over environment variables.**

| Environment variable                         | Description                                                                            | Utility                   | Default               |
|----------------------------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------|
| **POWERTOOLS_SERVICE_NAME**                  | Sets service name used for tracing namespace, metrics dimension and structured logging | All                       | `"service_undefined"` |
| **POWERTOOLS_METRICS_NAMESPACE**             | Sets namespace used for metrics                                                        | [Metrics](./core/metrics) | `None`                |
| **POWERTOOLS_TRACE_ENABLED**                 | Explicitly disables tracing                                                            | [Tracer](./core/tracer)   | `true`                |
| **POWERTOOLS_TRACER_CAPTURE_RESPONSE**       | Captures Lambda or method return as metadata.                                          | [Tracer](./core/tracer)   | `true`                |
| **POWERTOOLS_TRACER_CAPTURE_ERROR**          | Captures Lambda or method exception as metadata.                                       | [Tracer](./core/tracer)   | `true`                |
| **POWERTOOLS_TRACER_CAPTURE_HTTPS_REQUESTS** | Captures HTTP(s) requests as segments.                                                 | [Tracer](./core/tracer)   | `true`                |
| **POWERTOOLS_LOGGER_LOG_EVENT**              | Logs incoming event                                                                    | [Logger](./core/logger)   | `false`               |
| **POWERTOOLS_LOGGER_SAMPLE_RATE**            | Debug log sampling                                                                     | [Logger](./core/logger)   | `0`                   |
| **LOG_LEVEL**                                | Sets logging level                                                                     | [Logger](./core/logger)   | `INFO`                |

## Examples

* [CDK](https://github.com/awslabs/aws-lambda-powertools-typescript/tree/main/examples/cdk){target="_blank"}
* [SAM](https://github.com/awslabs/aws-lambda-powertools-typescript/tree/main/examples/sam){target="_blank"}

## Serverless TypeScript demo application

The [Serverless TypeScript Demo](https://github.com/aws-samples/serverless-typescript-demo) shows how to use Lambda Powertools for TypeScript.  
You can find instructions on how to deploy and load test this application in the [repository](https://github.com/aws-samples/serverless-typescript-demo).

## Contribute

If you are interested in contributing to this project, please refer to our [Contributing Guidelines](https://github.com/awslabs/aws-lambda-powertools-typescript/blob/main/CONTRIBUTING.md).

## Roadmap

The roadmap of Powertools is driven by customers’ demand.  
Help us prioritize upcoming functionalities or utilities by [upvoting existing RFCs and feature requests](https://github.com/awslabs/aws-lambda-powertools-typescript/issues), or [creating new ones](https://github.com/awslabs/aws-lambda-powertools-typescript/issues/new/choose), in this GitHub repository.

## Connect

* **AWS Developers Slack**: `#lambda-powertools` - [Invite, if you don't have an account](https://join.slack.com/t/awsdevelopers/shared_invite/zt-yryddays-C9fkWrmguDv0h2EEDzCqvw){target="_blank"}
* **Email**: aws-lambda-powertools-feedback@amazon.com

## Credits

Credits for the Lambda Powertools idea go to [DAZN](https://github.com/getndazn){target="_blank"} and their [DAZN Lambda Powertools](https://github.com/getndazn/dazn-lambda-powertools/){target="_blank"}.

## License

This library is licensed under the MIT-0 License. See the [LICENSE](https://github.com/awslabs/aws-lambda-powertools-typescript/blob/main/LICENSE) file.

