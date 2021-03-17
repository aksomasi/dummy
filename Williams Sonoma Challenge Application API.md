# Williams Sonoma Code Challenge App
Given a collection of 5-digit ZIP code ranges (each range includes both their upper and lower bounds), provide an algorithm that produces the minimum number of ranges required to represent the same restrictions as the input

## Tech Stack
| Technology | Version | Purpose |
| ------ | ------ | ------ |
| Java | 15 | Programming Language |
| SpringBoot | 2.4.3 | Application Framework |
| Embedded Tomcat Server | 9 | To Deploy Application |
| Gradle |  6.8.3 | Build Tool |
| Swagger OpenApi | 3.0 | API Dcoumentaion and Testing |
| Junit, Mockito | 5 | Unit Test Cases |
| Log4j | 2.1.3 | To maintain Logs |
| yaml |  | To write application Properties info |


## Rest Apis Info
here we used  post api which takes array of integers and returns MinRange of Zipcodes...
follwoing are the request and response models
##### Request:
[[94133,94133],[94200,94299],[94600,94699]]
##### Response:
[[94133,94133],[94200,94299],[94600,94699]]

First Tab:

```sh
Swagger Api Request
```
//  Swagger Api Request Screenshot
```sh
Swagger Api Response
```
//  Swagger Api Response Screenshot

```sh
Test Cases Results
```
//  Test Cases Results Screenshot

```sh
Code Coverage
```
//  Code Coverage Screenshot

