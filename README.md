# serverlesssetup

# install serveless 
  npm install -g serverless@3
# check version 
  serverless -v
# create your AWS Lambda project:
  serverless create --template aws-python --path ai-fashion-lambda
# move to dir
  cd ai-fashion-lambda
# edit serverless.yml
  # code in yml file 
    service: ai-fashion-lambda
    provider:
      name: aws
      runtime: python3.9
    
    functions:
      hello:
        handler: handlers/hello.hello
        events:
          - http:
              path: hello
              method: get
    plugins:
      - serverless-offline
# create folder handler . for create all api in that module
  # For Example
    /handler
      |_hello.py
        # sample Python code for hello.py
            import json
            def hello(event, context):
                body = {
                    "message": "Go Serverless v1.0! Your function executed successfully!",
                    "input": event
                }
            
                response = {
                    "statusCode": 200,
                    "body": json.dumps(body)
                }
            
                return response
            
                # Use this code if you don't use the http event with the LAMBDA-PROXY
                # integration
                """
                return {
                    "message": "Go Serverless v1.0! Your function executed successfully!",
                    "event": event
                }
                """

# Install serverless-offline Plugin
  npm install serverless-offline --save-dev

# run
  serverless offline
# in terminal   
        GET  | http://localhost:3000/dev/hello                                
        POST | http://localhost:3000/2015-03-31/functions/hello/invocations   
                       
