title: sass & less
date: 2015-12-12 17:00:05
tags:
    - css
    - sass
---

``&`` 父元素选择器, 将替换成所有层叠的父选择器
``@extend %button;`` 引用%button样式
``%button`` 只能被引用的样式，不能单独使用

less也有Mixins，而且可以直接引用CLASS

# less extend
T6在另一个文件CommonRules.css
```
.T6 {
  font-size: 20px;
}
```

本文件要extend T6，则必须将css处理为less，即@import (less)
```
@import (less, reference) "css/common/common-style/CommonRules.css";

#my_tv_page #record_manage_widget #mytv_record_space_tip.space-tip-withoutline{
    left: 50px;
    &:extend(.T6);
}
```


