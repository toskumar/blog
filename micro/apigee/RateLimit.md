# Rate Limit Policy

## Spike Control
**Example : Spike Arrest rate limiting policy per unit time**
1. Create and deploy a reverse proxy type by using a [Mocktarget](https://mocktarget.apigee.net/json) endpoint 
1. Add spike arrest policy in the proxy request preFlow and set the limit to 10 request/minute (10pm) or (2ps)
1. Save and deploy the api proxy in the test environment
1. Test the URL in browser or any REST client http://demo-test.apigee.net/spike-arrest-per-second
```xml
<SpikeArrest async="false" continueOnError="false" enabled="true" name="Spike-Arrest-1">
    <DisplayName>Spike Arrest-1</DisplayName>
    <Properties/>
    <Rate>2ps</Rate>
</SpikeArrest>
```

**Example : Spike Arrest rate limiting policy by identifier**
1. Create and deploy a reverse proxy type by using a [Mocktarget](https://mocktarget.apigee.net/json) endpoint 
1. Add spike arrest policy in the proxy request preFlow and set the limit to 2 request per minute 
1. Save and deploy the api proxy in the test environment
1. Test the URL in browser or any REST client
1. scenario 1 - http://demo-test.apigee.net/spike-arrest-by-identifier?appname=mobile
1. scenario 2 - http://demo-test.apigee.net/spike-arrest-by-identifier?appname=web
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<SpikeArrest async="false" continueOnError="false" enabled="true" name="Spike-Arrest-1">
    <DisplayName>Spike Arrest-1</DisplayName>
    <Properties/>
    <Identifier ref="request.queryparam.appname"/>
    <MessageWeight ref="request.header.weight"/>
    <Rate>2pm</Rate>
</SpikeArrest>
```

## Quota Policy

**Example : Default quota type, allow count, interval, timeunit ,flowvariable and distributed/synchronized=true|fase behaviour**
1. Create and deploy a reverse proxy type by using a [Mocktarget](https://mocktarget.apigee.net/json) endpoint 
1. Add quota policy type to the proxy request preFlow
1. In Quota element remove the attribute type
1. Set Allow count, Interval and Timeunit
1. Identifier request queryparam appname ensure that each app has a counter/timeunit
1. Set the distributed and synchronous element to true and false to see the counter behaviour
1. Test the URL in browser or any REST client 
1. scenario 1 - http://demo-test.apigee.net/quota-policy-per-user?appname=mobile
1. scenario 2 - http://demo-test.apigee.net/quota-policy-per-user?appname=web

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

**Example : Message weight quota policy**
1. Create and deploy a standard reverse proxy type
1. Add Javascript policy in proxy request preFlow
1. Add Quota policy to proxy request preFlow
1. Test the URL in browser or any REST client 
1. scenario 1 - GET http://demo-test.apigee.net/quota-weight
1. scenario 2 - POST http://demo-test.apigee.net/quota-weight

```javascript
var verb = context.getVariable("request.verb");
context.setVariable("messageWeight","1");
if(verb == "POST") {
 context.setVariable("messageWeight","2");
}
```

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

**Example : Quota calendar policy**
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy to the proxy request preFlow and set the type="calendar"
1. Set the StartTime element to the future date and time
1. Test the URL in browser or any REST client http://demo-test.apigee.net/quota-calendar

```xml
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1" type="calendar">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow count="4" countRef="request.header.allowed_quota"/>
    <Interval ref="request.header.quota_count">1</Interval>
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <TimeUnit ref="request.header.quota_timeout">minute</TimeUnit>
    <StartTime>2020-04-28 10:48:00</StartTime>
</Quota>
```

**Example : Quota rolling window policy**
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy the proxy request preFlow and set the type="rollingwindow"
1. Test the URL in browser or any REST client http://demo-test.apigee.net/quota-rolling-window

```xml
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1" type="rollingwindow">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow count="3" countRef="request.header.allowed_quota"/>
    <Interval ref="request.header.quota_count">2</Interval>
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <TimeUnit ref="request.header.quota_timeout">minute</TimeUnit>
</Quota>
```

**Example : Quota flexi policy** (Counter start after receiving the first request and thereafter at regular interval)
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy to the proxy request preFlow and set the type="flexi"
1. Test the URL in browser or any REST client http://demo-test.apigee.net/quota-flexi

```xml
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1" type="flexi">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow count="3" countRef="request.header.allowed_quota"/>
    <Interval ref="request.header.quota_count">1</Interval>
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <TimeUnit ref="request.header.quota_timeout">minute</TimeUnit>
</Quota>
```

**Example : Conditional quota policy - (Assigning quota for each appname)**
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy to the proxy request preFlow and set the Allow/Class ref
1. Set Allow partner count and public count 
1. Test the URL in browser or any REST client 
1. scenario 1 - http://demo-test.apigee.net/quota-count-per-client?appname=partner
1. scenario 1 - http://demo-test.apigee.net/quota-count-per-client?appname=public

```xml
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow>
	<Class ref="request.queryparam.appname">
 	  <Allow class="partner" count="4">
	  <Allow class="public" count="2"/>
	</Class>
    </Allow>
    <Interval>1</Interval>
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <TimeUnit>minute</TimeUnit>
</Quota>
```

**Example : To display the available count, used count and total count in the response**
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy to the proxy request preFlow
1. Add an AssignMessage policy to the proxy response preFlow
1. Set the payload as application/json and the output response
1. Test the URL in browser or any REST client http://demo-test.apigee.net/quota-message-count

```xml
<!--Quota policy -->
<Quota async="false" continueOnError="false" enabled="true" name="Quota-1">
    <DisplayName>Quota-1</DisplayName>
    <Properties/>
    <Allow count="3"/>
    <Interval>1</Interval>
    <Distributed>true</Distributed>
    <Synchronous>true</Synchronous>
    <TimeUnit>minute</TimeUnit>
</Quota>

<!--AssignMessage policy -->
<AssignMessage name="set-dynamic-content">
  <AssignTo createNew="false" type="response"></AssignTo>
  <Set>
    <Payload contentType="application/json" variablePrefix="@" variableSuffix="#">
      {"quotaAvailable": "@ratelimit.Quota-1.available.count#", "quotaUsed":"@ratelimit.Quota-1.used.count#"}
    </Payload>
  </Set>
  <IgnoreUnresolvedVariables>false</IgnoreUnresolvedVariables>
</AssignMessage>
```

**Example : Quota policy to handle fault error and custom error message**
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy to the proxy request preFlow
1. Add an AssignMessage policy to the proxy response preFlow
1. Set the payload as application/json and the output response
1. Test the URL in browser or any REST client http://demo-test.apigee.net/quota-error-message

```xml
<!-- Add fault rules element under ProxyEndpoint element-->
<FaultRules>
  <FaultRule name="Quota Errors">
    <Step>
      <Name>set-quota-error-message</Name>
      <Condition>(fault.name Matches "QuotaViolation")</Condition>
    </Step>
    <Condition>ratelimit.Quota-1.failed=true</Condition>
  </FaultRule>
</FaultRules>

<!--Add AssignMessage policy and set the name to the FaultRule/Step/Name -->
<AssignMessage name="set-quota-error-message">
  <AssignTo createNew="false" type="response"/>
  <Set>
    <Payload contentType="application/json" variablePrefix="@" variableSuffix="#">
      {"errorCode": "EQ001", "message": "Quota Exceeded"}
    </Payload>
  </Set>
  <IgnoreUnresolvedVariables>false</IgnoreUnresolvedVariables>
</AssignMessage>
```

**Example 10 - **
1. Create and deploy a standard reverse proxy type
1. Add a Quota type policy to the proxy request preFlow
1. Add an AssignMessage policy to the proxy response preFlow
1. Set the payload as application/json and the output response
1. Test the URL in browser or any REST client http://demo-test.apigee.net/example10


## Reference Endpoint
1. [Apigee restclient](https://apigee-restclient.appspot.com)
1. [Mocktarget plain text](https://mocktarget.apigee.net)
1. [Mocktarget json api](https://mocktarget.apigee.net/json)
1. [httpbin api](http://httpbin.org/get)
1. [Google book api](https://www.googleapis.com/books/v1/volumes?q=nodejs)
1. [Swagger petstore api](https://petstore.swagger.io/v2/swagger.json)
1. [GMT time](https://time.is/GMT)
