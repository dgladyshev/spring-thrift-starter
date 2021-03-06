# Apache Thrift Starter for Spring Boot

[![Join the chat at https://gitter.im/aatarasoff/spring-thrift-starter](https://badges.gitter.im/aatarasoff/spring-thrift-starter.svg)](https://gitter.im/aatarasoff/spring-thrift-starter?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://travis-ci.org/aatarasoff/spring-thrift-starter.svg?branch=master)](https://travis-ci.org/aatarasoff/spring-thrift-starter)

## What is it

Set of cool annotations that helps you building Thrift applications with Spring Boot.

## How connect project

Its very simple:

```
repositories {
    jcenter()
}
```

```
compile 'info.developerblog.spring.thrift:spring-thrift-starter:0.1.3'
```

## How use this

Annotation @ThriftHandler("servlet_path") helps you building server controller for request processing

```
@ThriftHandler("/api")
public class TGreetingServiceHandler implements TGreetingService.Iface {

    @Override
    public String greet(TName name) throws TException {
        // your logic
    }
}
```

Other annotation @ThriftClient(serviceId = "registered_service", (path) = "server_handler_path") helps you with multithreaded client with full Spring Cloud support.

```
@ThriftClient(serviceId = "greeting-service", path = "/api")
TGreetingService.Client client;
```

###Thrift Client configuration

```
greeting-service:                     #service name
  endpoint: http://localhost:8080/api #direct endpoint
  ribbon:                             #manually ribbon
      listOfServers: localhost:8080
  path: /service                      #general path
```

If you use service discovery backend (as Eureka or Consul) only path maybe needed.

See tests for better understanding.

## Enjoy!


