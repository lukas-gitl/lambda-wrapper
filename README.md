# lambda-wrapper
Wrapper for running lambda modules locally or from AWS during development

## Use 

### Initializing the local Lambda

    // Loads the module in myModule/mymod.js
    var lambdaFunc = require('myModule/mymod.js');
    var lambda = require('lambda-wrapper').wrap(lambdaFunc);

### Initializing a lambda in AWS
    
    var lambda = require('lambda-wrapper').wrap({
        region: 'eu-west-1',
        lambdaFunction: 'myFunctionName'
    });

### Running the function in the Lambda module

    var event = { key1: 'val1', key2: val2 };
    lambda.run(event, function(err, data) {
        if (err) {
            ... handle error
        }
        ... process data returned by the Lambda function
    })

## Development

Run module tests using 

    npm run test

Live lambda run test requires that the function in lambdaWrapper-test.js is deployed 
to your AWS account as 'lambdaWrapper-test'.

## Release History

* 2016/04/26 - v0.1.0 - Support for running lambda functions also from AWS
* 2016/04/26 - v0.0.6 - Support for NodeJS 4.3 runtime (and callback notation)
* 2015/09/01 - v0.0.2 - Pass module object rather than path to init().
                        Removed automatic loading of module.
* 2015/07/23 - v0.0.1 - Initial version of module

## License

Copyright (c) 2015 [SC5](http://sc5.io/), licensed for users and contributors under MIT license.
https://github.com/SC5/aws-document-cache/blob/master/LICENSE


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/SC5/lambda-local/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
