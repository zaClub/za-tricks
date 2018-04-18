## Git Commit Log Standard

### 信息结构体

  ```
  <type> (<scope>) : <summary>

  <body>

  <footer>
  ```


- type
  - `feat`: 新功能
  - `fix`: 修复错误
  - `docs`: 更新文档
  - `style`: 更新样式
  - `refactor`: 代码重构
  - `test`: 增加测试模块，不涉及生产环境的代码
  - `chore`: 更新核心模块，包配置文件，不涉及生产环境的代码


- summary
  - 使用一般现在时的祈使句作为这次提交的 `summary`
- body
  - 详细的说明以 "-" (横杠) 作为分点符号，每一点说明之间有空行


- footer
  - 结尾是可选的，通常来说可以添加对一些错误信息ID的补充

### 例子
>fix(album): 修复相册无法关闭的问题 
>
>vue2.0 弃用了 `.snyc` 关键字，因此使用`.snyc`进行父子组件中用于控制 dialog 是否显示的`visible`值双向绑定的模块，需要改用`emit`、`on`这样的父子组件通信方式来实现。
>
>Closes #007