# Testing Matchers on Lambda Environment Variables

Example of how to use the testing matchers to test the environment variables of a Lambda function:

```typescript
// "aws-cdk-lib": "2.177.0",
import { Match, Template } from 'aws-cdk-lib/assertions';
import * as lambda from 'aws-cdk-lib/aws-lambda';
import * as cdk from 'aws-cdk-lib/core';

test('Lambda Environment Variable example', () => {
    const stack = new cdk.Stack();

    new lambda.Function(stack, 'MyFunction', {
        runtime: lambda.Runtime.NODEJS_20_X,
        handler: 'index.handler',
        code: lambda.Code.fromInline(`exports.handler = async function(event) { return "hello"; }`),
        environment: {
            ENV_VAR_1: 'VALUE_1',
            ENV_VAR_2: 'VALUE_2',
        },
    });

    const template = Template.fromStack(stack);

    template.hasResourceProperties('AWS::Lambda::Function', {
        Environment: Match.objectLike({
            Variables: {
                ENV_VAR_1: 'VALUE_1',
            },
        }),
    });
});
```
