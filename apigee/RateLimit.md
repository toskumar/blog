# Rate Limit Policy

## Spike Control
Example 1
1. Create and deploy a reverse proxy type by using a target endpoint
1. Add spike arrest policy in the request preFlow to limit 5 request per second (5ps)
1. Save and deploy the proxy api in the test environment
1. Test the url in browser or any rest client
```xml
<SpikeArrest async="false" continueOnError="false" enabled="true" name="Spike-Arrest-1">
    <DisplayName>Spike Arrest-1</DisplayName>
    <Properties/>
    <Rate>5ps</Rate>
</SpikeArrest>
```
  
## Sample Endpoint
1. [Apigee restclient](https://apigee-restclient.appspot.com)
1. [Mocktarget plain text](https://mocktarget.apigee.net)
1. [Mocktarget json api](https://mocktarget.apigee.net/json)
1. [httpbin api](http://httpbin.org/get)
1. [Google book api](https://www.googleapis.com/books/v1/volumes?q=nodejs)
1. [Swagger petstore api](https://petstore.swagger.io/v2/swagger.json)
