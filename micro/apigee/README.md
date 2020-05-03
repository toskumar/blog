# Apigee
Apigee is a API Managment Platform to design, secure, analyze, and scale APIs anywhere with visibility and control.


## Apigee Proxy Model
* Apigee proxy edge stands in between the client and target endpoint
* It consists of ProxyEndpoint and TargetEndpoint
* Both endpoints are configured as **preFlow => conditionalFlow => postFlow**
* First the client request passthrough the **proxy preFlow => conditionalFlow => postFlow then target preFlow => conditionalFlow => postFlow => endpoint**
* Second the endpoint response passthrough the **target preFlow => conditionalFlow => postFlow then proxy preFlow => conditionalFlow => postFlow => client**

![ApigeeProxyModel](./img/ApigeeProxyModel.png)

## Apigee Policy
- [Secure Policy](#secure-policy)
- [Rate Limit Policy](#rate-limit-policy)
- [Caching and Persistence](#caching-and-persistence)
- [Transforming Messages](#transforming-messages)

### Secure Policy
### Rate Limit Policy
- Spike Arrest Policy - smooths the traffic spikes by dividing a limit that you define into smaller intervals. For example, if you define a limit of 60 messages per minute, the Spike Arrest policy enforces a limit of about 1 request every 1 second.

- Quota Policy - enforces consumption limits on client apps by maintaining a distributed 'counter' that tallies incoming requests.
  - Quota Types
    - default - when type is not specified, quota is based on allow count and time interval.
    - Calendar - Configure a quota based on an explicit start time.
    - RollingWindow - for example, 1 day. When a request comes in, Edge looks at the exact time of the request (say 5:01pm), counts the number of requests that came in between then and 5:01pm the previous day (1 day) and determines whether or not quota has been exceeded during that window.
    - Flexi - Configure a quota that causes the counter to begin when the first request message is received from a client, and resets based on the interval.
  - Quota Elements
    - Distributed - there can be one or more Message Processors to process incoming requests. Set this element to true to specify that the policy should maintain a central counter and continuously synchronize it across all Message Processors. Setting the element to false will have a counter for each message processor.
    - Synchronous - Set to true to update a distributed quota counter synchronously.
- Concurrent Rate Limit Policy - provides the number of concurrent connections between Apigee Edge and a backend service that are allowed at any given time.


**Difference between Spike arrest policy and Quota policy**
|Spike Arrest Policy | Quota Policy|
|---|---|
|Based on technical requirement and backend system threshold | Based on business requirement |
|Rate limit is based on per second or per minute | Rate limit is based on per subscriber per timeunit eg. minute, months|
|Supports Denial of Service (DoS/DDoS), Traffic Management, Bot protection | Supports subscriptions, usage restriction and metering|


[Rate Limit Policy Examples](RateLimit.md)

### Caching and Persistence
### Transforming Messages


## Reference Endpoint
1. [Apigee restclient](https://apigee-restclient.appspot.com)
1. [Mocktarget plain text](https://mocktarget.apigee.net)
1. [Mocktarget json api](https://mocktarget.apigee.net/json)
1. [httpbin api](http://httpbin.org/get)
1. [Google book api](https://www.googleapis.com/books/v1/volumes?q=nodejs)
1. [Swagger petstore api](https://petstore.swagger.io/v2/swagger.json)
1. [GMT time](https://time.is/GMT)
