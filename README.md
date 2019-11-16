# localstack-demo
Develop and test your cloud &amp; Serverless apps offline! 

- Launch a terminal
- Clone the repo
- Go to the repo
- Run the below command

```
docker-compose up
```

- Wait till the localstack is ready 

```
Creating network "localstack-demo_default" with the default driver
Creating localstack_main ... done
Attaching to localstack_main
localstack_main | Waiting for all LocalStack services to be ready
localstack_main | 2019-11-16 07:38:20,335 CRIT Supervisor is running as root.  Privileges were not dropped because no user is specified in the config file.  If you intend to run as root, you can set user=root in the config file to avoid this message.
localstack_main | 2019-11-16 07:38:20,337 INFO supervisord started with pid 16
localstack_main | 2019-11-16 07:38:21,342 INFO spawned: 'dashboard' with pid 22
localstack_main | 2019-11-16 07:38:21,345 INFO spawned: 'infra' with pid 23
localstack_main | (. .venv/bin/activate; bin/localstack web)
localstack_main | 2019-11-16 07:38:21,351 INFO success: dashboard entered RUNNING state, process has stayed up for > than 0 seconds (startsecs)
localstack_main | (. .venv/bin/activate; exec bin/localstack start --host)
localstack_main | 2019-11-16 07:38:22,353 INFO success: infra entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
localstack_main | 2019-11-16T07:38:23:WARNING:bootstrap.py: Unable to load plugins from file /opt/code/localstack/.venv/lib/python3.7/site-packages/localstack_ext/plugins.py: No module named 'localstack_ext.utils.aws.aws_models'
localstack_main | Starting local dev environment. CTRL-C to quit.
localstack_main | Starting mock ES service (http port 4578)...
localstack_main | Starting local Elasticsearch (http port 4571)...
localstack_main | Starting mock S3 (http port 4572)...
localstack_main | Starting mock SNS (http port 4575)...
localstack_main | 2019-11-16T07:38:25:INFO:localstack.multiserver: Starting multi API server process on port 51492
localstack_main | Starting mock SQS (http port 4576)...
localstack_main | Starting mock SES (http port 4579)...
localstack_main | Starting mock SSM (http port 4583)...
localstack_main | Starting mock STS (http port 4592)...
localstack_main | Starting mock IAM (http port 4593)...
localstack_main | Starting mock Secrets Manager (http port 4584)...
localstack_main | Starting mock API Gateway (http port 4567)...
localstack_main | Starting mock DynamoDB (http port 4569)...
localstack_main | Starting mock DynamoDB Streams service (http port 4570)...
localstack_main | Starting mock Firehose service (http port 4573)...
localstack_main | Starting mock Lambda service (http port 4574)...
localstack_main | Starting mock Kinesis (http port 4568)...
localstack_main | Starting mock Redshift (http port 4577)...
localstack_main | Starting mock Route53 (http port 4580)...
localstack_main | Starting mock CloudFormation (http port 4581)...
localstack_main | Starting mock CloudWatch (http port 4582)...
localstack_main | Starting mock CloudWatch Events (http port 4587)...
localstack_main | Starting mock CloudWatch Logs (http port 4586)...
localstack_main | Starting mock StepFunctions (http port 4585)...
localstack_main | Starting mock EC2 (http port 4597)...
localstack_main | Waiting for all LocalStack services to be ready
localstack_main | Waiting for all LocalStack services to be ready
localstack_main | Waiting for all LocalStack services to be ready
localstack_main | Waiting for all LocalStack services to be ready
localstack_main | Ready.
```

- Launch another tab in the terminal
- Go to the same directory inside the repo
- Run the below command

```
chmod +x setup.sh
./setup.sh
```

- This will create few resources around Lambda and API Gateway

```
{
    "FunctionName": "api",
    "FunctionArn": "arn:aws:lambda:us-east-1:000000000000:function:api",
    "Runtime": "nodejs8.10",
    "Role": "arn:aws:iam::123456:role/irrelevant",
    "Handler": "lambda.apiHandler",
    "CodeSize": 397,
    "Description": "",
    "Timeout": 3,
    "MemorySize": 128,
    "LastModified": "2019-11-16T07:39:29.377+0000",
    "CodeSha256": "x1VZZ4NxopLeMUqs8/HVsRW21a3MDZEUleNT2znMR9I=",
    "Version": "$LATEST",
    "TracingConfig": {
        "Mode": "PassThrough"
    },
    "RevisionId": "662a2584-8315-444f-9977-885bcab539c1"
}
{
    "id": "gm6irjbk94",
    "name": "api",
    "createdDate": 1573889970
}
{
    "id": "cf6198a97k",
    "parentId": "29sevmzh29",
    "pathPart": "{somethingId}",
    "path": "/{somethingId}",
    "resourceMethods": {
        "GET": {}
    }
}
{
    "httpMethod": "GET",
    "authorizationType": "NONE"
}
{
    "type": "AWS_PROXY",
    "httpMethod": "GET",
    "uri": "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:000000000000:function:api/invocations",
    "integrationResponses": {
        "200": {
            "statusCode": 200,
            "responseTemplates": {
                "application/json": null
            }
        }
    }
}
{
    "id": "ao2v4v2o90",
    "description": "",
    "createdDate": 1573889974
}
API available at: http://localhost:4567/restapis/gm6irjbk94/test/_user_request_/HowMuchIsTheFish
Testing GET:
HTTP/1.1 201 Created
Server: BaseHTTP/0.6 Python/3.7.5
Date: Sat, 16 Nov 2019 07:39:36 GMT
X-Custom-Header: ASDF
Content-Length: 25
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: HEAD,GET,PUT,POST,DELETE,OPTIONS,PATCH
Access-Control-Allow-Headers: authorization,content-type,content-md5,cache-control,x-amz-content-sha256,x-amz-date,x-amz-security-token,x-amz-user-agent,x-amz-target,x-amz-acl,x-amz-version-id,x-localstack-target,x-amz-tagging
Access-Control-Expose-Headers: x-amz-version-id

{"message":"Hello World"}%
```
