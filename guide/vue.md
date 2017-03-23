## 命名

组件文件命名与引用使用 `CamelCase` 规则，首字母小写，其余单词首字母大写。

```
app.vue
navMenu.vue
```

```js
import navMenu from 'components/navMenu'

export default {
    components: {
        navMenu
    }
}
```

模版内组件遵循 `自定义元素规范`：全小写，使用 `-` 分隔单词。

```html
<app-header></app-header>
<user-list></user-list>
<range-slider></range-slider>
```

# 书写顺序

三小节的书写顺序按关注度排列。

```html
<template></template>
<script></script>
<style></style>
```

实例属性顺序书写建议：

```js
export default {
    // 扩展
    mixins,
    extends,
    // 子级
    components,
    // 属性
    props,
    propsData,
    data,
    computed,
    // 函数
    watch,
    methods,
    // 生命周期
    beforeCreate,
    created,
    beforeMount,
    mounted,
    beforeUpdate,
    updated,
    activated,
    deactivated,
    beforeDestroy,
    destroyed
}
```

引用按类别分组：

```js
// bad
import comp1 from 'comp1'
import Api from 'Api'
import comp2 from 'comp2'
import util from 'util'

// good
// -> 组件
import comp1 from 'comp1'
import comp2 from 'comp2'
// -> 库
import util from 'util'
// -> 服务
import Api from 'Api'
```

Todo...
