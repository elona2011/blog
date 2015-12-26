title: unit-test
date: 2015-12-24 00:04:48
tags:
---


The BDD interface provides describe(), context(), it(), before(), after(), beforeEach(), and afterEach().
context() is just an alias for describe()
异步测试时，在it('xx', function(done){setTimeout(function(){assert(true);done();}, 0);});中使用done
mocha 教程

# 单元测试
http://www.alloyteam.com/2013/12/hour-class-learning-costs-javascript-unit-testing-tool-matcha-mocha-and-chai/

# 集成测试

