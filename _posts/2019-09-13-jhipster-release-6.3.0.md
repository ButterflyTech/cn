---
layout: default
title: Release 6.3.0
---

JHipster release v6.3.0
==================

这个版本修复了一个**重要的安全漏洞**:

- 请浏览这篇文章[security advisory here](https://github.com/jhipster/generator-jhipster/security/advisories/GHSA-mwp6-j9wf-968c).
- **是否受影响?** 如果你使用JWT, session或者UAA认证, 而且发送我们系统发送密码重置链接, 那么恭喜你, 你受影响了. 机密算法等级不够安全导致攻击者可以猜出密码重置链接, 便可以黑进系统中任何一个账号.
- **如何修复** 无需升级Jhipster, 这个漏洞只影响几个生成的文件, 所以你可以手动修复. 罪魁祸首就是`RandomUtil`这个类. [Here is this class in our sample application generated with JHipster v6.2.0](https://github.com/jhipster/jhipster-sample-app/blob/v6.2.0/src/main/java/io/github/jhipster/sample/service/util/RandomUtil.java) and [here is the updated version, using JHipster v6.3.0](https://github.com/jhipster/jhipster-sample-app/blob/v6.3.0/src/main/java/io/github/jhipster/sample/service/util/RandomUtil.java). 复制这个使用了`SecureRandom`的新文件然后替换旧文件.
- **问题处理流程** 这个问题被[Jonathan Leitschuh](https://github.com/JLLeitschuh)发现, 几个小时之后被[Frederik Hahne](https://github.com/atomfrede)修复. 我们奖励了[Jonathan500刀漏洞赏金](https://github.com/jhipster/generator-jhipster/issues/10401), 同时奖励了[Frederik300刀漏洞赏金](https://github.com/jhipster/generator-jhipster/issues/10402). 从安全角度考虑, 当前只有[JHipster核心团队](https://www.jhipster.tech/team/)知道这个问题. 一天之后我们告诉了所有人这个问题, 包括[推特客服咨询](https://twitter.com/java_hipster/status/1172387424715988994), 以便我们的用户不会对这个紧急发布感到惊讶.
- **后续** 这是我们第一次使用到GitHub的"安全咨询". 我们受益匪浅, 而且在不久的将来, 我们要提供一条简洁的途径用于团队反馈安全建议.      


**更新日志**

除了安全漏洞之外, 这个版本还[关闭了247个工单和合并请求](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.3.0+is%3Aclosed).

最重要的如下:

- 更新至Spring Boot2.1.8和Spring Cloud Greenwich SR3
- 所有Docker镜像更新到最新
- 从Tslint迁移到Eslint([#10187](https://github.com/jhipster/generator-jhipster/pull/10187) and [#10213](https://github.com/jhipster/generator-jhipster/pull/10213)). 新的Jhipster Eslint配置文件提供在一个新的仓库: https://github.com/jhipster/eslint-config-jhipster [#10358](https://github.com/jhipster/generator-jhipster/pull/10358)
- 创建的Jar包默认不可执行 [#10282](https://github.com/jhipster/generator-jhipster/pull/10282)
- 使用ArchUnit检查架构特征 [#10274](https://github.com/jhipster/generator-jhipster/pull/10274)
- 基于OpenAPIGenerator添加了一个新的Feign客户端子生成器 [#9548](https://github.com/jhipster/generator-jhipster/issues/9548)
- Liquibase支持一个应用中不同的认证 (所以运行中的应用不能修改表结构)
- 支持Caffeine Cache [#10303](https://github.com/jhipster/generator-jhipster/pull/10303)
- 通过Java 11，Jar支持等等增强Google App Engine生成器的功能
 ([#10284](https://github.com/jhipster/generator-jhipster/pull/10284) and [#10336](https://github.com/jhipster/generator-jhipster/pull/10336))
- 修复AWS generator整体流程 [#10376](https://github.com/jhipster/generator-jhipster/pull/10376)
- 修复Angular中管理日志页面 [jhipster/ng-jhipster#97](https://github.com/jhipster/ng-jhipster/pull/97)
- Fix interactions between main generator and blueprint when one is installed globally and the other locally [#10257](https://github.com/jhipster/generator-jhipster/issues/10257)
- 解决一些Istio URLs的问题 [#10135](https://github.com/jhipster/generator-jhipster/issues/10135)

关闭的工单与合并请求
------------
一如既往, __[你可以在此处查看所有已关闭的工单与已接受合并请求](https://github.com/jhipster/generator-jhipster/issues?q=milestone%3A6.3.0+is%3Aclosed)__.

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
