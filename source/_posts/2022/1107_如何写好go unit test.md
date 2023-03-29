---

title: 如何写好go unit test 
date: 2022-11-7 11:58:00
tags: ['go','编程语言']

---

之前没怎么写过go unit test 总结了一下如何写好unit test with golang 还有一些问题，希望大佬指正思路

1 测试代码是否和被测代码是否应该使用相同的包名？
目前compass 两种风格的代码都有？
 我的提问https://www.reddit.com/r/golang/comments/ynokeu/test_code_should_use_the_same_package_or_diff/
如果不用一个包名没法测试未导出方法，
坏:-1: 可能不够unit
好:+1: change 私有方法不会broke已有的测试用例

2 相同场景/相同测试结果 使用 table driven tests
 https://pkg.go.dev/testing#hdr-Subtests_and_Sub_benchmarks
个人观点，同一个func的不同场景应该分开不同的测试方法,不然test也不够unit ,所有的场景掺合和一个测试方法里会很难修改
比如 success是一个测试方法。
失败场景有很多可以是一个table driver tests

3 判断单元测试是否好的标准之一是否有更高的代码覆盖率但又不需要完全追求

4 除了assert结果还需要AssertNumberOfCalls

5 模式: create test function name/description =>mock=> call => assert
 description/given is a term coming from the behavior-driven design where human-readable “user stories” are used to describe your expectations