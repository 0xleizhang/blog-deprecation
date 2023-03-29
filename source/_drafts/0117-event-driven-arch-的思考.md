---
title: event driven arch 的思考
tags:
---
广受推崇的 event driven architecuture 有很多好处，但在实际使用过程中仍存在很多细节问题。

# producer&consumer关系管理缺失

一个app作为consumer不知道这个消息的producer是哪些app，很难弄清楚当前app的代码所处业务域中的位置。

一个app作为producer 不知道有哪些app是consumer，如果遇到message schema升级或者broker维护，不知道需要通知到哪些team。



## 可能的解

给 message 加上 trace_id 建立支持message的trace系统 v