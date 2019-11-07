---
layout: default
title: Release 6.3.1
---

JHipster release v6.3.1
==================

Warning, this release fixes an **important security vulnerabilities**:

- Our previous release had an important security vulnerability, please read [the v6.3.0 release notes]({{ site.url }}/2019/09/13/jhipster-release-6.3.0.html) for more information. It was announced that this vulnerability was only for users using JWT authentication: the issue is in fact wider, and affects people using session-based authentication and UAA authentication. Only people using OAuth2 authentication (with services like Keycloak or Okta) are safe. This was already fixed in the previous release, so there is nothing specific for this in this release.
- We have a [new vulnerability that affects Gradle users](https://github.com/jhipster/generator-jhipster/security/advisories/GHSA-mc84-xr9p-938r). The generated configuration file contained one Maven repository configured with HTTP, and not HTTPS, which could lead to man-in-the-middle attacks when doing a build. You will find all information in the security advisory, but to make a long story short: you should use HTTPS both in your Maven and Gradle build files.

**更新日志**

This release closes [48 tickets and pull requests](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.3.1+is%3Aclosed). It's a patch release, so those are mostly library upgrades, bug fixes, as well as a number of smaller feature enhancements.

关闭的工单与合并请求
------------
一如既往, __[你可以在此处查看所有已关闭的工单与已接受合并请求](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.3.1+is%3Aclosed)__.

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
