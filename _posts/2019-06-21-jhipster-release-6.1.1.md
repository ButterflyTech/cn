---
layout: default
title: Release 6.1.1
---

JHipster release v6.1.1
==================

This is an emergency patch release because of a broken transitive dependency, that blocks our command line. see [#9952](https://github.com/jhipster/generator-jhipster/issues/9952) for more information.

Apart from this blocker issue, this release also includes many improvements, here are the most important ones:

- Lots of work to improve how faker.js generates fake data  - [#9862](https://github.com/jhipster/generator-jhipster/pull/9862) [#9663](https://github.com/jhipster/generator-jhipster/pull/9663) [#9890](https://github.com/jhipster/generator-jhipster/pull/9890)
- Update to Spring Boot 2.1.6 - [#9930](https://github.com/jhipster/generator-jhipster/pull/9930)

关闭的工单与合并请求
------------
一如既往, __[你可以在此处查看所有已关闭的工单与已接受合并请求](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.1.1+is%3Aclosed)__.

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
