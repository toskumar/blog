# Apigee
Apigee is a API Managment Platform to design, secure, analyze, and scale APIs anywhere with visibility and control.


## Apigee Proxy Model
* Apigee proxy edge stands in between the client and target endpoint
* It consists of ProxyEndpoint and TargetEndpoint
* Both endpoints are configured as preFlow => conditionalFlow => postFlow
* First the client request passthough the proxy preFlow => conditionalFlow => postFlow then target preflow => conditionalFlow => postFlow => endpoint
* Second the endpoint response passthough the target preFlow => conditionalFlow => postFlow then proxy preflow => conditionalFlow => postFlow => client

![ApigeeProxyModel](./img/ApigeeProxyModel.png)

## Apigee Policy
- [Secure Policy](#secure-policy)
- [Rate Limit Policy](#rate-limit-policy)
- Caching and Persistence
- Transforming Messages

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


[Examples](RateLimit.md)

### Concurrent Rate Limit
