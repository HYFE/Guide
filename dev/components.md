## 可复用组件

每个可复用组件（无状态、UI、端对端）在 `components` 中建立单独的文件目录，所有与该组件相关的资源均放入该目录中。

```
🗁 components
  `--🗁 tree
  |  |--🗎 index.vue
  |  `--🗎 item.vue
```

`index.vue` 为组件入口，这样在调用组件时，路径只需要写到目录级。

```js
import tree from 'components/tree'
```

## 视图/容器组件

放入 `view` 目录，以目录提现模块或路由层级，`index.vue` 为组件入口。

```
🗁 view
  `--🗁 project
  |  |--🗎 index.vue
  |  `--🗎 details.vue
```
