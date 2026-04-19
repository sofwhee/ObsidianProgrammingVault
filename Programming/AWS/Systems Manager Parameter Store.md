Parameter Store allows for easy externalization of parameters, such as an API key. 

The secure string option provides for data security by keeping the value encrypted at rest. Authorized access to the parameter is governed by IAM permissions. 

Parameter values can be easily changed by authorized principals at any time without requiring a re-deployment of the function, although the function would require intelligence to re-read the parameter values.