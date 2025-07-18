---
slug: /optimize
sidebar_position: 1
---

# 优化

优化是做减法，清理服务器的卡顿因素，由于 Minecraft 本身的性能低下、部分插件作者并没有优化代码的意识、服务器实体过多等。

每个服务器可能有自己的卡顿原因，在这部分先做最基础的通用优化，如果你使用后作用不大请参考性能分析板块。

> "过早的优化是万恶之源",过早优化会让服务端不稳定，甚至 10x slower

在此之前，请一定查看 [优化误区](optimized-plugin.md)，停止此类无效"优化"，然后根据下面的步骤进行操作。

## 第一步 - Java 优化

为什么选择 Java 优化作为第一步 - 几乎任何情况下，服务器都会因为合适的 Java 受益，

仅仅需要你下载一个小小的 Java 安装程序，或者更改 JVM 参数 (大白话来说就是开服参数)。

参见 [JVM 优化](https://nitwikit.8aka.org/Java/optimize/jvm)

## 第二步 - 预生成

什么是预生成 - 预生成就是让服务器在玩家进入之前，预先生成区块对应方块、结构等。

在 Minecraft 服务器中，生成新区块会消耗大量服务器资源，如果要开启新的地图 / 服务器，建议先预生成地图。

[Chunky](https://hangar.papermc.io/pop4959/Chunky) 是最常用的预生成插件。
通常与 [ChunkyBorder](https://modrinth.com/plugin/chunkyborder) 结合使用，你可以根据自己的喜好自定义边界及形状。

通常来说，即使你不设置边界，也务必进行预生成大约 1w x 1w 大小的世界。这对降低后期服务器负载很有效。

预生成时应该注意，默认情况 1.20 原版 1w x 1w 的地图需要 4-5 GB 硬盘。应根据硬盘大小选择世界的预生成大小。

## 第三步 - 更换核心

在插件和配置层面能进行的优化其实不多 (受限于 API 还有服务端核心)，所以最好的方法是更换服务器核心。

:::warning

任何时候都不要再使用 CraftBukkit 和 Spigot 了。追求稳定/性能上 Purpur，追求原版特性上 Leaves，性能上 Leaf

:::

完整版请查看[核心选择](/docs-java/start/server-core-choose/server-core-choose.md)

## 第四步 - 调整服务端配置

目前，Bilibili 上面的配置都是很老的，不推荐使用

文档里的 [调服务端配置](go.md) 比较新，非常推荐

## 第五步 - 更换硬件

**不要无脑换硬件！** 首先要知道自己的硬件瓶颈在哪里。如果 CPU 负荷过高，建议先排除 CPU 异常占用，再看 CPU 总体占用情况。
一般来说服务器卡顿换 CPU 是最有效的，单核性能和 MC 服务器 TPS 几乎呈线性相关，但是换 CPU 几乎就相当于要换一台机器，迁移对于新手来说并不是易事。

对于单端服务器来说，超过 8 核心的部分基本很难通过提升 CPU 核心数量提升 TPS。不要动不动就买 E5 然后卡了就加 4 核 8G 内存，更多也没用的。

对于群组服务器来说，一般核心数量都会占用上，但是内存可能会有些捉急，对于每一个普通的生存服来说内存的推荐值为 8G - 20G 更多更少都是不推荐的。

:::warning

如果发现 CPU 占用和内存占用都不是很高但是服务器卡卡的，请考虑是不是服务器带宽受限导致玩家 ping 值突然升高的问题。请分清楚 TPS 低导致的卡顿，MSPT 高导致的卡顿，带宽占满导致的卡顿。

:::

## 第六步 - 更换操作系统

无论在性能还是稳定性，Linux 都比 Windows 更适合用于开服，对于 Linux 根据自己的使用经验选择即可，如果没有使用经验可以先使用 Ubuntu 等主流系统。

切换到 Linux 后，你还可以进行 [内核优化](kernel.md)

如果想要了解更多请前往进阶 [Linux 开服教程](https://nitwikit.8aka.org/Sundry/Advance/Linux)

## 第七步 - 性能分析

> “马克思主义活的灵魂在于对具体问题作具体分析。” - 列宁

通用优化已经差不多做好了，而每个服都有自己导致滞后的因素，可能是实体太多，可能是玩家机器多，也可能是某些插件写的太屎...

如此，那么应该如何知道服务器为何卡顿呢？

如果你是个完完全全的新手，或者懒得分析，想请教别人分析应该怎么办呢？请转跳到 [怎么让大佬帮我](ask-for-help.md)

如果你不想求助别人，亦或者你想有一些进步，请参考 [性能分析](performance-analysis.md)
