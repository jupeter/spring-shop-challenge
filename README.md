# Sample Java8-Spring challenge task

[Demo on Google Cloud Platform](http://spring-challenge1.pplenik.tk/)
(from branch: [`docker`](https://github.com/jupeter/spring-shop-challenge/tree/docker)).

## Technologies Used:
 - Java 8
 - Spring Boot
 - Gradle
 - Thymeleaf

## Assignment

Write a simple webapp simulating a shop with two kinds of items.
At the beginning, there are 20 units of fi rst item and 10 of the second.

## Commands

`./compile.sh` script to build the app

`./deploy.sh` script deploying the app and print out the URL

## Details about used technology

### How I chosen technology

Backend based on Spring Boot + Thymeleaf

After investigation I decided to use Spring Boot. My reasons are:
 - easy create production-ready application
 - embedded Application Server
 - clean code

Gradle is much powerful than Maven, easy to configure.
And personally I didn't have change to use it - so it was good start ;).

About Thymeleaf - I just take first template engine recommended by Spring.

Frontend - just pure HTML.

I didn't use any frontend framework or JS library to spend more time on backend side.
Of course much easier is implement Angular + Rest on server side - but then is less fan with Java.


### How would I implement persistence layer

I would choose Spring Data JPA.
Implementation: [branch spring-data](https://github.com/jupeter/spring-shop-challenge/compare/spring-data)

### How long did it take you to complete the assignment

 - Choose technology: 2h
 - Implementation: ~3h
 - Compile and deploy scripts: <1h
 - prepare readme file: <1h

## How would you modify the app if the list of items and their availability should be downloaded daily via REST API?

My propose is to create @Component with Spring Annotation Scheduled, like:
```
@Scheduled(cron="1 * * * * *")
public void updateItems() {
    // something that should execute on weekdays only
}
```

REST data loaded using `org.springframework.web.client.RestTemplate`.

## Extra stuff

### Configure docker

```
./gradlew build buildDocker
```

Deploy to Google Cloud:
```
./gradlew appengineDeploy
```

