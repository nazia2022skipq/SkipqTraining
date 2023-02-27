
# Deploying a "Hello Lambda" Lambda function using AWS CDK in TypeScript

This README file will guide you through the steps necessary to deploy a simple "Hello Lambda" Lambda function using AWS CDK in TypeScript.


## Prerequisites

Before proceeding with the steps below, you'll need the following:

- An AWS account with appropriate permissions to create and manage Lambda functions.
- Node.js installed on your computer.
- An AWS CDK project initialized in TypeScript.
## Installation

To get started, you'll need to install the necessary dependencies. Open a terminal window and navigate to the root of your AWS CDK project. Then, run the following command:

```
npm install @aws-cdk/aws-lambda
```

This will install the `@aws-cdk/aws-lambda` package, which we'll use to create our Lambda function.


## Creating the Lambda Function
Next, we'll create the Lambda function itself. Open the file 'lib/your-lambda-stack.ts' in your code editor, and add the following code:

```
import * as cdk from 'aws-cdk-lib';
import * as lambda from 'aws-cdk-lib/aws-lambda';

export class NaziaStack extends cdk.Stack {
  constructor(scope: cdk.App, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    // defines an AWS Lambda resource
    const hello = new lambda.Function(this, 'HelloHandler', {
      runtime: lambda.Runtime.NODEJS_16_X,    // execution environment
      code: lambda.Code.fromAsset('lambda'),  // code loaded from "lambda" directory
      handler: 'hello.handler'                // file is "hello", function is "handler"
    });
  }
}
```

This code creates a new Lambda function named `HelloWorldFunction` and sets its runtime to Node.js 14.x. It also specifies the handler function and the location of the Lambda function code.
## Adding the Lambda Function to the Stack

Now that we've created the Lambda function, we need to add it to our AWS CDK stack. Open the file `bin/your-lambda.ts` in your code editor, and add the following code:

```
import 'source-map-support/register';
import * as cdk from 'aws-cdk-lib';
import { NaziaStack } from '../lib/nazia-stack';

const app = new cdk.App();
new NaziaStack(app, 'NaziaStack', {

});
```

This code creates a new instance of the 'YourLambdaStack' class and adds it to the AWS CDK app.
## Deploying the Stack

Finally, we're ready to deploy our Lambda function using AWS CDK. Open a terminal window and navigate to the root of your AWS CDK project. Then, run the following command:

```
cdk deploy
```

This will deploy the AWS CDK stack, which includes our new Lambda function. Once the deployment is complete, you'll see the output in the terminal window.
## Testing the Lambda Function

To test the Lambda function, open the AWS Management Console and navigate to the Lambda service. Find the HelloWorldFunction function and click on it to view its details. Then, click on the "Test" button to create a new test event. Enter the following JSON code as the test event:

```
{
  "message": "Hello, World!"
}
```

Then, click on the "Create" button to create the test event. Finally, click on the "Test" button to run the test. You should see the output "Hello, World!" in the Lambda function's logs.

Congratulations, you've successfully deployed and tested a "Hello, World" Lambda function using AWS CD
