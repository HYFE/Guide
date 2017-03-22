对于一个项目内某一个模块、实体属性、UI、动作等，提供统一的称谓。

比如：`项目 - project`，所有涉及该模块的命名都要使用 `project` 去拼接组合。

* 添加项目：`addProject`
* 项目标题：`projectTitle`
* ...

## 名称字典

在项目根目录加入 `dic.yml` 文件，供项目成员查阅相关名称，没有的自行添加新项。

两个层级，`类别 -> 项`。

```yaml
action:
  add: 添加
  get: 获取

model:
  project: 项目
  user: 用户

ui:
  header: 头部
  modal: 模态窗
```

> `yml` 格式：`属性名:[空格]属性值`，每个属性单独一行，空格必须。以 `tab` 体现层级。

## 代码内使用

对于 Api 和 Vuex 可建立各自的 `types.js` 字典映射文件，供代码内调用。

```js
// types.js
export const FETCH_ALL = 'FETCH_ALL'

// action.js
import  { FETCH_ALL } from '../types'

export default { {
  actions: {
    [FETCH_ALL] (context, payload) {
      // ...
    }
  }
}
```
