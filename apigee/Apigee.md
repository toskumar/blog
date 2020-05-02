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
    - default
    - Calendar
    - RollingWindow
    - Flexi
  
- Concurrent Rate Limit Policy - provides the number of concurrent connections between Apigee Edge and a backend service that are allowed at any given time.
  

### Concurrent Rate Limit
