# aws-apps-scripts
An interface to authenticate AWS api requests from within google apps scripts.

## How to use:

1. Create a new project in google scripts.

2. Copy paste aws.js into it's own file in your project and save it.

3. Open up a new a file and setup the AWS variable with AWS.init.

4. Use AWS.request with whatever AWS API request you need! Make sure the headers and parameters are correctly set up, though. This function only sets up the Host, X-Amz-Date, X-Amz-Target, and Authorization headers by default.

Note: X-Amz-Target is (as far as I know) only used in POST requests and it is set to the "action" parameter provided by default.

Command usage:
```
AWS.request(service, region, action, params={}, method='GET', payload='', headers={"Host": GeneratedHost, "X-Amz-Date": GeneratedX-Amz-Date, "X-Amz-Target": action}, uri='/')
```

Example:

```
function myFunction() {
  AWS.init("MY_ACCESS_KEY", "MY_SECRET_KEY");
  var instanceXML = AWS.request('ec2', 'us-east-1', 'DescribeInstances', {"Version":"2015-10-01"});
  ...
}
```

Note that the current API version for EC2 is `2016-11-15` which is listed on the [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/DocumentHistory.html) page along with change history.

The reference for the [Amazon Endpoint](https://docs.aws.amazon.com/apigateway/api-reference/making-http-requests/) for the `service` parameter is available in the <b>Amazon API Gateway REST API Reference</b>.  Within that documentation, here is the [DescribeInstances](https://docs.aws.amazon.com/workspaces/latest/api/API_DescribeWorkspaces.html) reference for additional parameters and options.
