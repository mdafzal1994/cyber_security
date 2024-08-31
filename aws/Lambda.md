AWS Lambda functions, there are several security misconfigurations and considerations to check. 

1) **Apply ‘Principle of Least Privilege’ to Your IAM Policies**
    **Resource-Based Policies:** Control which entities can invoke the Lambda function.
   These policies are attached to the Lambda function itself.

  **IAM Roles:** Provide permissions to the Lambda function to access other AWS resources. 
  These roles are assigned to the Lambda function and include policies that define what the function
  can do with other AWS services.
2) **Avoid Storing Sensitive Data in Lambda Function Code or Configurations**
    Adopt AWS Secret Management Services: AWS offers dedicated services for secure
    storage, rotation, and access of sensitive information.
3) **Logging and Monitoring CloudWatch Logs:** Verify that CloudWatch Logs are enabled for the Lambda
   function to ensure that you can monitor and respond to any unusual activities.
   
