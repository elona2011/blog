title: 正则表达式笔记
tags:
  - 正则
  - javascript
date: 2015-07-01 00:13:50

---

# 字符
``\d`` 匹配数字
``\D`` 匹配非数字
``\w`` 匹配字母或数字或下划线或汉字
``\W`` 匹配非单词字符
``\s`` 匹配任意的空白符
``\S`` 匹配非空白字符
``\b`` 匹配单词边界
``\B`` 匹配非单词边界
``.`` 匹配除换行符以外的任意字符
``^`` 匹配字符串开始
``/test$/`` 匹配字符串结束 

# 范围(类操作符)
``[abc]`` 匹配abc中的一个
``[^abc]`` 匹配abc以外的任意一个字符
``[a-z]`` 匹配a-z所有小写字母

有两个字符在[]中有特殊含义，其它均表示字面含义

^ 必须是[]中的第一个字符
[^]表示匹配一切字符,而.不包括换行符

\- 连字符

# 转义
需要用斜杠转义的，一共有12个字符：``^ . [ $ ( ) | * + ? {  \ ``

``\\`` 匹配\
``\[`` 匹配[

当操作符的组合可以形成语义时，如果只是想使用其字面量含义，则必须转义
``/1{0}/.test('1{0}') //true``
``/1{2}/.test('1{2}') //false``
``/1\{2}/.test('1{2}') //true``

# 次数
``/tes?t/`` 匹配出现0次或1次
``/te+st/`` 匹配出现1次或更多
``/t*est/`` 匹配出现0次或更多
``/test{n}/`` 匹配出现n次
{n,} 表示至少重复n次
{n,m} 表示重复不少于n次，不多于m次
默认是贪婪的,匹配尽可能多

``/e+?/`` 次数操作符后加?,则变为懒惰,匹配尽可能少

# 分组
``/(ab)+/`` 匹配一个或多个连续出现的ab

# 或操作
``/(ab)+|(cd)+/`` 匹配出现一次或多次的ab或cd
``/ab|cd/`` 匹配ab或者cd
``/a(b|c)d/`` 匹配abd或acd

# 反向引用
``/^([dtn])a\1/`` 匹配a前后的字母相同,如dad

# 后行断言
x(?!y) x只有不在y前面才匹配，y不会被计入返回结果
```
/\d+(?!\.)/.exec('3.14') // ["14"]
```

# 尾部标志
i 不区分大小写
g 匹配所有，而不是第一个
m 允许匹配多行

```
/test/ig
```

# RegExp
``(new RegExp('1\\+1')).test('1+1')`` 转义需要两个\\