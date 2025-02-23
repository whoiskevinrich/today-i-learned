# Construct Validation

Construct validation is a mechanism to validate the state of a construct before it is synthesized into a CloudFormation template. This is useful for validating the state of a construct before it is deployed, and can be used to enforce best practices, security policies, and other requirements.

Example of how to use construct validation to validate the state of a construct:

```typescript
// "aws-cdk-lib": "2.177.0",
import * as core from 'aws-cdk-lib/core';

export class MyConstruct extends core.Resource implements IMyConstruct {
    public readonly name: string;

    constructor(scope: core.Construct, id: string, props: MyConstructProps) {
        super(scope, id);

        this.node.addValidation({ validate: () => this.validateMyConstruct() });
    }

    private validateMyConstruct() {
        const results = new Array<string>();

        if (this.name.length > 10) {
            results.push('Name must be less than 10 characters');
        }

        return results;
    }
}
```
