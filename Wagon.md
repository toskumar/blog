# Wagon Runner
## JUnit Framework 
Junit is a testing framework for writing and running unit test cases for java programming language. It is designed to run the unit test cases without a server, so it is easy to writing junit test cases for simple application. However writing and running junit test cases for web based application is slightly tricky, as developer need to write test cases where the code can be executed without the applciation server runtime dependency like context, session etc or mock the object using other framework.

First developer need to focus on the application logic and secondly he has to write the unit test cases to validate the logic written is correct and there is no regression when changed. This avoids developer to learn any new testing frameworks and make the junit testing simple. The new approach is to deploy the junit test cases into the application server and execute through a web based tool.
