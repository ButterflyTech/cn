---
layout: default
title: 生产中的微服务
permalink: /microservices-in-production/
sitemap:
    priority: 0.7
    lastmod: 2017-05-03T00:00:00-00:00
---

# <i class="fa fa-cloud"></i> 生产中的微服务

微服务是一种特殊的Jhipster应用。有关执行生产构建、优化和保护生产构建的更多信息，请参阅我们的主要 [Using JHipster in production documentation]({{ site.url }}/production) 。

## <a name="elk"></a> 微服务监控

请参阅我们的 [JHipster Registry documentation]({{ site.url }}/jhipster-registry) ，了解哪些运行时仪表板可用，以及如何使用它们。

我们的 [monitoring documentation]({{ site.url }}/monitoring) 也非常重要，了解有关使用的特定信息：

- jhipster控制台与您的微服务体系结构一起使用elk
- Zipkin在整个服务中跟踪HTTP请求
- Elastalert，在出现问题时发出警报

使用docker compose子生成器时，将询问您是否要向基础结构添加监视。此选项将把jhipster控制台添加到“docker compose.yml”文件中。一旦启动，它将在[http://localhost:5601](http://localhost:5601)上可用，并开始收集应用程序的日志和度量。

对于网关和微服务应用程序，还提供了其他功能来帮助您有效地监视微服务集群。例如，日志中丰富了每个应用程序的名称、主机、端口和eureka/consul serviceid，这样您就可以跟踪它们来自哪个服务实例。jhipster控制台还附带了默认的仪表盘，这些仪表盘为您提供了所有服务指标的概述。

## <a name="docker_compose"></a> Using Docker Compose to develop and deploy

Working on a microservices architecture means you will need several different services and databases working together, and in that context Docker Compose is a great tool to manage your development, testing and production environments.

A specific section on microservices is included in our [Docker Compose documentation]({{ site.url }}/docker-compose#microservices), and we highly recommend that you get familiar with it when working on a microservices architecture.

As Docker Swarm uses the same API as Docker Machine, deploying your microservices architecture in the cloud is exactly the same as deploying it on your local machine. Follow our [Docker Compose documentation]({{ site.url }}/docker-compose/) to learn more about using Docker Compose with JHipster.

## <a name="cloudfoundry"></a> Going to production with Cloud Foundry

The [Cloud Foundry sub-generator]({{ site.url }}/cloudfoundry/) works the same with a microservices architecture, the main difference is that you have more applications to deploy:

- Use the [Cloud Foundry sub-generator]({{ site.url }}/cloudfoundry/) to deploy first the JHipster Registry (which is a normal JHipster application).
- Note the URL on which your JHipster Registry is deployed. Your applications must all point to that URL:
  - In the `bootstrap-prod.yml` file, the `spring.cloud.config.uri` must point to `http(s)://<your_jhipster_registry_url>/config/`
  - In the `application-prod.yml` file, the `eureka.client.serviceUrl.defaultZone` must point to `http(s)://<your_jhipster_registry_url>/eureka/`
- Deploy your gateway(s) and microservices
- Scale your applications as usual with Cloud Foundry

One important point to remember is that the JHipster Registry isn't secured by default, and that the microservices are not supposed to be accessible from the outside world, as users are supposed to use the gateway(s) to access your application.

Two solutions are available to solve this issue:

- Secure your Cloud Foundry using specific routes.
- Keep everything public, but use HTTPS everywhere, and secure your JHipster Registry using Spring Security's basic authentication support

## <a name="heroku"></a> Going to production with Heroku

The [Heroku sub-generator]({{ site.url }}/heroku/) works nearly the same with a microservices architecture, the main difference is that you have more applications to deploy:

Deploy a JHipster Registry directly with one click:

[![Deploy to Heroku](https://camo.githubusercontent.com/c0824806f5221ebb7d25e559568582dd39dd1170/68747470733a2f2f7777772e6865726f6b7563646e2e636f6d2f6465706c6f792f627574746f6e2e706e67)](https://dashboard.heroku.com/new?&template=https%3A%2F%2Fgithub.com%2Fjhipster%2Fjhipster-registry)

Please follow the [Heroku sub-generator documentation]({{ site.url }}/heroku/) in order to understand how to secure your JHipster Registry.

Note the URL on which your JHipster Registry is deployed. Your applications must all point to that URL in their `application-prod.yml` file. Change that configuration to be:

    eureka:
        instance:
            hostname: https://admin:[password]@[appname].herokuapp.com
            prefer-ip-address: false

You can now deploy and scale the gateway(s) and microservices. The Heroku sub-generator will ask you a new question, to know the URL of your JHipster Registry: this will allow your applications to fetch their configuration on the Spring Cloud Config server.
