azure-java-samples
==================

Java samples for Azure websites

# Spring Boot

Spring Boot projects are compiled as a single jar file and include their own container. In order to run one of this projects in Azure Websites, deploy the jar file and a web.config file similar to this [Spring Boot example Azure web.config](https://github.com/chanezon/azure-java-samples/blob/master/spring-boot/web.config).
The main aspect to watch out for is to start the server on the port provided by Azure in the HTTP_PLATFORM_PORT environment variable.

[Spring Boot samples has many samples that you can try out on Azure.](https://github.com/spring-projects/spring-boot/tree/master/spring-boot-samples)

*References:*
* [Upload a custom Java web site to Azure](https://azure.microsoft.com/documentation/articles/web-sites-java-custom-upload/?WT.mc_id=opensource-0000-pachanez)
* [Spring Boot Reference Guide - Change the Http Port](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/#howto-change-the-http-port)
