[← Back to README](../README.md)

# Path (APP pay)
The principle of 'Money Transfer' is basically a signal to change the ledgers between two database (subtracting from Acct. A and adding in Acct. B). 

Connections between 3 components:
- User mobile Application (local)
- mobile server
- WeChat-Pay server

All the certification, authorization, etc. They are all being set here. 

There are many of features provided by WeChat Payment team, here only talks about the [App Payment](https://pay.weixin.qq.com/doc/v3/merchant/4013070158). 

USE the example of spring boot as server structure. Each built `jar` file is like the zip file, contains all of the instructions, and Java will launch it by unzip it. 

The 'trust' between two parties payment is also server to server. The payment is confirm also by mobile server and payment-provider server, it's never client-side application. 

Approximate steps:
1. user click, app sends request to backend server. 
2. backend server call WeChat's server, to get the `prepaid_id`. 
3. backend server wraps `prepaid_id` into signed package, send to app
4. app hands package to WeChat-SDK's `sendReq`, to pop out WeChat APP
5. Once WeChat APP confirms, it talks to WeChat's server directly, move money from user wallet, to merchant wallet. 
6. WeChat App notify backend server, this user is active. 

The WeChat SDK is Tencent's tool, to help you talk to WeChat App. 

So what the doc is telling you is how to follow the key and how to 'follow the rule to talk to WeChat App'.


# Hardest Part
WeChat needs to know, whether the payment request comes from real merchant, not anyone else. 

The core is WeChat Pay server needs to confirm the people who pay and the people who receive the pay is the correct one. That's why there's so many secures on online payment. 

For example, Some hacker maybe fake the 'payment successfully' signal to WeChat Pay server. 