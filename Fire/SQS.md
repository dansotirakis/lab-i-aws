# 📨 SQS
## 🧙‍♂️ Config aws cli
### 🔑 Credentials
`aws configure`
```
    ACCESS_KEY = XXXX
    SECRET_KEY = XXXX
    REGION = XXX
```
## 📃 Infors.
```shell
aws sqs help
```
## 🏌️ Using SQS with AWS CLI
### 📤 Send
#### Default
```shell
aws sqs send-message --queue-url https://sqs.xregionx.amazonaws.com/xxx/xx --message-body "Test queue"
```
#### With FIFO
```shell
aws sqs send-message --queue-url https://sqs.xregionx.amazonaws.com/xxx/xx.fifo --message-group-id "10-10" --message-deduplication-id "20-20" --message-body "Test queue FIFO"
```
#### With parameters and body on JSON files
```shell
aws sqs send-message --queue-url https://sqs.xregionx.amazonaws.com/xxx/xx.fifo --message-body file://aws-sqs-body.json --message-group-id "10-10" --message-deduplication-id "20-20" --message-attributes file://aws-sqs-attributes.json
```
##### aws-sqs-body.json
```json
{
    "id":3, 
    "name":"test-json-file", 
    "price":125.15
}
```
##### aws-sqs-attributes.json
```json
{
  "book-id": {
    "DataType": "Number.java.lang.Integer",
    "StringValue": "1"
  },
  "contentType": {
    "DataType": "String",
    "StringValue": "1"
  },
  "id": {
    "DataType": "String",
    "StringValue": "10-10-20-20"
  },
  "timestamp": {
    "DataType": "Number.java.lang.Long",
    "StringValue": "1650850337744"
  }
}
```
### 📥 Receive
#### Default
```shell
aws sqs receive-message --queue-url https://sqs.sa-east-1.amazonaws.com/xxxx/xxx
```
#### With FIFO
```shell
aws sqs receive-message --queue-url https://sqs.sa-east-1.amazonaws.com/xxxx/xxx.fifo
```
### 🙆 Working Attributes
#### Default get attributes queue
```shell
aws sqs get-queue-attributes --queue-url https://sqs.sa-east-1.amazonaws.com/xxxx/xxx --attribute-names All
```
### ❌ Delete queue
#### Default delete
```shell
aws sqs --region sa-east-1 delete-queue --queue-url https://sqs.sa-east-1.amazonaws.com/xxxx/xxx
```
