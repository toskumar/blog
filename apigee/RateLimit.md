# Rate Limit Policy

## Spike Control
**Example 1 - Spike Arrest rate limiting policy**
1. Create and deploy a reverse proxy type by using a [Mocktarget](https://mocktarget.apigee.net/json) endpoint 
1. Add spike arrest policy in the request preFlow to limit 5 request per second (5ps)
1. Save and deploy the api proxy in the test environment
1. Test the url in browser or any rest client
```xml
<SpikeArrest async="false" continueOnError="false" enabled="true" name="Spike-Arrest-1">
    <DisplayName>Spike Arrest-1</DisplayName>
    <Properties/>
    <Rate>5ps</Rate>
</SpikeArrest>
```

## Quota Policy

**Example 2 - Default quota, allow, internval, timeunit and distributed/synchronized=true|fase behaviour**
1. Create and deploy a reverse proxy type by using a [Mocktarget](https://mocktarget.apigee.net/json) endpoint 
1. Use the default quota type by removing the attribute type="calendar"
1. Set Allow, Interval and Timeunit
1. Identifier appname ensure that each app has a counter/timeunit
1. Set the distributed and synchronous element to true and false to see the counter behavour
1. Test the url in browser or any rest client 
1. scenario 1 - http://demo-test.apigee.net/example2?appname=mobile
1. scenario 2 - http://demo-test.apigee.net/example2?appname=web

```xml
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow count="3" countRef="request.header.allowed_quota"/>
    <Interval ref="request.header.quota_count">1</Interval>
    <TimeUnit ref="request.header.quota_timeout">minute</TimeUnit>    
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <Identifier ref="request.queryparam.appname"/>
</Quota>
```

**Example 3 - Message weight quota policy **
1. Create and deploy a standard reverse proxy type
1. Add Javascript policy in proxy request preFlow
```javascript
var verb = context.getVariable("request.verb");
context.setVariable("messageWeight","1");
if(verb == "POST") {
 context.setVariable("messageWeight","2");
}
```
1. Add Quota policy to proxy request preFlow
```xml
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow count="4" countRef="request.header.allowed_quota"/>
    <Interval ref="request.header.quota_count">1</Interval>
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <TimeUnit ref="request.header.quota_timeout">minute</TimeUnit>
    <MessageWeight ref="messageWeight"/>
</Quota>
```
1. Test the url in browser or any rest client 
1. scenario 1 - GET http://demo-test.apigee.net/example3
1. scenario 2 - POST http://demo-test.apigee.net/example3


  
## Sample Endpoint
1. [Apigee restclient](https://apigee-restclient.appspot.com)
1. [Mocktarget plain text](https://mocktarget.apigee.net)
1. [Mocktarget json api](https://mocktarget.apigee.net/json)
1. [httpbin api](http://httpbin.org/get)
1. [Google book api](https://www.googleapis.com/books/v1/volumes?q=nodejs)
1. [Swagger petstore api](https://petstore.swagger.io/v2/swagger.json)
1. [GMT time](https://time.is/GMT)
