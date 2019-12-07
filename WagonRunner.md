# Wagon Runner
## JUnit Framework 
Junit is a testing framework for writing and running unit test cases for java programming language. It is designed to run the unit test cases without a server, so it is easy to write junit test cases for simple application. However writing and running junit test cases for web based application is slightly tricky, as the developer need to write test cases where the code can be executed without the applciation server runtime dependency like context, request, session etc or mock the object using other framework.

First and foremost developers like me are struggling to write the application logic within the estimated timelines and secondly he has to write the unit test cases to validate the application logic written is correct and there are no regression when it is changed. 

Wagon Runner is an approach to deploy the junit test cases into the application server and execute the test cases through a web based tool, this avoids the developer to focus on the application logic and write the test cases without the fear of bypassing the application server runtime dependency. 

To reiterate Wagon Runner is not a framework to learn but it is an approach to run the unit test cases inside the application server with the JUnit framework.

