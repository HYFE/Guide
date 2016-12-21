# 目录结构

![目录结构](http://note.youdao.com/yws/public/resource/390e8cfca2424b9e883bc33c43a6beec/xmlnote/1558D48918A04A91AA058EF6693E3876/2335)

# 数据请求

```bash
🗁 api
|--🗎 index.js
|--🗎 hello.js
`--🗎 util.js
```

* 所有的数据请求统一放到 `api` 目录下
* `util.js` 为 HTTP 工具函数，供每个模块调用

```js
import Vue from 'vue'

const TO_JSON = res => res.json()
const ERROR_HANDLE = res => console.error('ERROR: ', res.status, res.statusText)

const HTTP = (method, args) => Vue.http[method].apply(Vue.http, args).then(TO_JSON, ERROR_HANDLE)

export const GET = (...args) => HTTP('get', args)
export const POST = (...args) => HTTP('post', args)
export const PUT = (...args) => HTTP('put', args)
export const DELETE = (...args) => HTTP('delete', args)
```

* `index.js` 为公共数据请求，其余按模块命名 `name.js`

```js
import { GET } from './util'

export default {
    getCitys: () => GET('/city')
}
```

# 静态资源

主要是字体和图标，分类别放置 `assets` 目录。

```bash
🗁 assets
 |--🗁 fonts
 `--🗁 images
```

图片命名规则：`module-position-element-name-number.ext`，任选 2 个类型以上名称，以 `-` 连接，但需保持一组图片资源的命名一致性。

**示例：**

```bash
# module-name
global-avater.jpg

# module-position-element
global-top-header.jpg

# module-element-name
admin-footer-sprite.png

# module-name-number
home-banner-1.jpg
```

# 公共组件

公共组件或称 UI 组件，指不涉及具体业务逻辑的组件，只使用 `props` 和 `event` 进行组件交互（非父子关系的组件可以使用 `eventbus` 传递）。

* 单文件的组件直接以组件名命名，放置 `components` 目录
* 多文件的组件以组件名建立文件夹，添加 `index.vue` 或 `index.js` 作为组件入口
* 组件中不仅有 `.vue` 文件，也可以有其他脚本、图片等文件（推荐使用字体图标或CSS绘制等解决方案替代简单的图片）

```bash
🗁 components
|--🗁 tree
|  |--🗎 util.js
|  |--🗎 Index.vue
|  `--🗎 Item.vue
`--Button.vue
```

# CSS/LESS

```
🗁 less
|--🗎 app.less
|--🗎 base.less
|--🗎 icons.less
|--🗎 mixins.less
|--🗎 reset.less
|--🗎 utils.less
`--🗎 variables.less
```

* `app.less` 为入口文件，所有公共样式在其中导入
* 除以上公共样式文件外，新增公共样式以 `name.less` 格式命名

# 第三方库

* 无定制化需求的第三方库使用 npm 管理，否则放入 `libs` 目录中。
* 无 npm 版本的第三方库也放 `libs` 目录。
* 对于单独某个组件需要的第三方库可放入那个组件目录中。

# Vue 插件

指令、过滤器、过渡、Vue全局或实例成员等，放入 `plugins` 目录中。
每个插件单独一个目录，放入一个 `index.js` 为入口文件。所有插件在 `plugins/index.js` 中注册。

```bash
🗁 plugins
|--🗁 sort
|  |--🗎 index.js
`--🗎 index.js
```

```js
import Vue from 'vue'
import Sort from './sort'

Vue.use(Sort)
```

# 路由

```bash
🗁 router
|--🗁 map
|  |--🗎 hello.js
|  `--🗎 tree.js
`--🗎 index.js
```

* 新增路由按模块分类，以 `name.js` 格式放入 `router/map` 目录

```js
import a from 'view/a'
import ab from 'view/ab'

export default [
    { path: '/a', component: a },
    { path: '/a/b', component: ab }
]
```

* `index.js` 为路由入口调用各个路由模块，也可在此添加公共路由

```js
import Vue from 'vue'
import VueRouter from 'vue-router'
import hello from './map/hello'
import index from 'view/index'

Vue.use(VueRouter)

export default new VueRouter({
    routes: [
        ...hello,   // hello 模块
        { path: '/', component: index }       // 公共路由
    ]
})
```

# Vuex

```js
🗁 store
|--🗁 modules
|--🗎 actions.js
|--🗎 index.js
`--🗎 mutations.js
```

遵循官方推荐目录结构，按全局或模块划分文件。

# 页面和模块

页面和模块组件会涉及具体的业务逻辑和功能，只允许此类组件调用 `api` 接口或 `vuex` 状态。

```bash
🗁 view
|--🗁 moduleName
|--🗎 Hello.vue
```

* 单文件的页面组件可直接放入 `view` 目录
* 多页面或涉及子模块的组件建立对应的目录存放

# 公共脚本

项目中需要的公共脚本放入 `util` 目录。

# 其他

* 常用路径可在 `webpack` 中注册以避免代码中过长的引入路径

