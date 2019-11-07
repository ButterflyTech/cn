---
layout: default
title: Release 6.0.0
---

JHipster release v6.0.0
==================

This is the first official release of JHipster v6.

It builds upon our v6.0.0.beta.0 release, after one month of beta testing and [120 closed tickets and pull requests](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.0.0+is%3Aclosed).

Most important new features and upgrades
-------------

Those are the release notes from our previous beta release (v6.0.0.beta.0), updated for this stable release (v6.0.0).

- Migration to Spring Boot 2.1.x
- JDK 11 support (while keeping JDK 8+ compatibility)
- HTML 5 pushstate [#9098](https://github.com/jhipster/generator-jhipster/pull/9098)
- Kubernetes enhancements (Istio, Helm)
- Migration to Spring Cloud Greenwish.x
- Upgrade to Spring Security 5.1's OIDC Support
- Upgrade to JUnit 5
- FakerJS support to generate sample data for entities [#9104](https://github.com/jhipster/generator-jhipster/pull/9104)
- Update to latest Angular version [#8161](https://github.com/jhipster/generator-jhipster/pull/8161)
- Update to latest React version
- Lazy Loading of Angular entities
- Bootswatch theme selection
- Removed CSS Option [#9350](https://github.com/jhipster/generator-jhipster/pull/9350)
- Improvements in Sonar integration [#9423](https://github.com/jhipster/generator-jhipster/pull/9423) and [#9482](https://github.com/jhipster/generator-jhipster/pull/9482), including an externalized sonar-project.properties file.
- Gatling 3 support, including several improvements with better and faster incremental builds and BOM support.
- Integration tests are set up in their separate phase for Maven and Gradle
- Update to Gradle 5
- Migration to Liquibase 3.6.x
- Update Elastic to 6.4.x
- Update to Couchbase 6.x
- Update to Infinispan 9.4.x
- Update to Cassandra 4.x
- Update to Hazelcast 3.11.x
- Logging to the console in json format
- Changing the default packaging to Jar while still being able to produce a War [#9034](https://github.com/jhipster/generator-jhipster/pull/9034)
- Prettier for formatting YAML [#9281](https://github.com/jhipster/generator-jhipster/pull/9281)
- Prettier transform to prettify the output from all sub-generators [#9371](https://github.com/jhipster/generator-jhipster/pull/9371)

We also removed a few features:

- Removed deprecated 'rancher-compose' sub-generator
- Removed Chocolatey and Homebrew installations, as we found out they didn't provide much benefits to users
- Deprecated the [JHipster Devbox](https://github.com/jhipster/jhipster-devbox) for the moment: we are looking for a maintainer, if you are interested please ping us!

关闭的工单与合并请求
------------
一如既往, __[你可以在此处查看所有已关闭的工单与已接受合并请求](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.0.0+is%3Aclosed)__.

更新指引
------------

**自动升级**

在已存在的项目上使用[JHipster upgrade sub-generator]({{ site.url }}/upgrading-an-application/)自动升级:

升级Jhipster版本:

```
npm update -g generator-jhipster
```

然后升级子生成器:

```
jhipster upgrade
```

**手动升级**

选择手动升级, 需要先升级你的Jhipster版本:

```
npm update -g generator-jhipster
```

如果你已经有了一个项目, 将会继续使用当时项目生成的Jhipster版本.
如果需要升级你的项目, 你需要先删除`node_modules`文件夹再运行:

```
jhipster
```

更新你的项目和所有的实体类

```
jhipster --with-entities
```

你也可以使用实体类子生成器挨个更新你的实体类, 例如你的实体类名字是_Foo_

```
jhipster entity Foo
```

帮助和缺陷
--------------

如果您发现这个版本的任何问题, 请随时联系我们:

- 在我们的[bug tracker](https://github.com/jhipster/generator-jhipster/issues?state=open)添加一个缺陷报告
- 在[Stack Overflow](http://stackoverflow.com/tags/jhipster/info)提交问题

If the issue you have is an urgent bug or security issue, please:

- 在推特上联系[@java_hipster](https://twitter.com/java_hipster)
