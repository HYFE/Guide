
以“体系管理”为例。

```
体系管理
    组织管理
    预案管理
    知识管理
```

# 视图

1. 在 `view` 下基于“体系管理”建立一个文件夹
2. 每个页面分别建立子文件夹，添加 `index.vue` 为入口组件，对于页面拆分出的业务或模块类组件也放入此文件夹内

**示例：**

```bash
🗁 view
 |--🗁 structure           # 体系管理
 |  |--🗁 org              # 组织管理
 |  |   |--🗎 index.vue
 |  |--🗁 plan             # 预案管理
 |  |   |--🗎 index.vue
 |  |--🗁 docs             # 知识管理
 |  |   |--🗎 index.vue
 |  |   |--🗎 moduleA.vue
 |  |   `--🗎 moduleB.vue
```

# 路由

1. `view` 下的每个目录对应到 `router/map` 文件夹下的路由模块
2. 路由访问路径 `path`，按照 `view` 下的目录结构设置

```bash
🗁 router
 |--🗁 map
 |   `--🗎 structure.js    # 体系管理相关页面的路由
 `--🗎 index.js
```

**router/map/structure.js**

```js
import org from 'view/structure/org'
import plan from 'view/structure/org'
import docs from 'view/structure/org'

export default [
    { path: '/structure/org', component: org },
    { path: '/structure/plan', component: plan },
    { path: '/structure/docs', component: docs }
]
```
