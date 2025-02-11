# Testing Matchers

The AWS CDK includes a set of testing matchers that you can use to test your CDK applications. These matchers are designed to make it easier to write tests for your CDK applications by providing a set of common assertions that you can use to verify the state of your CDK stacks.

Here are some examples of how you can use the testing matchers to test your CDK applications:

## Testing Array Value Matchers

Array equality can be tested with either `Match.arrayWith` or `Match.arrayEquals`. `Match.arrayWith` is used when you want to test that an array contains a specific set of values, while `Match.arrayEquals` is used when you want to test that an array is equal to a specific set of values.

```typescript
// "aws-cdk-lib": "2.177.0",
import { Match, Template } from 'aws-cdk-lib/assertions';
import * as sqs from 'aws-cdk-lib/aws-sqs';
import * as cdk from 'aws-cdk-lib/core';

test('arrayWith example', () => {
    const stack = new cdk.Stack();
    const queue = new sqs.Queue(stack, 'Queue');
    cdk.Tags.of(queue).add('tag1', 'value1');
    cdk.Tags.of(queue).add('tag2', 'value2');

    const template = Template.fromStack(stack);

    template.hasResourceProperties('AWS::SQS::Queue', {
        Tags: Match.arrayWith([
            {
                Key: 'tag1',
                Value: 'value1',
            },
        ]),
    });
});
```
