# 开发小手册

个人的代码字典，结合docsify框架生成开发字典网站。

## 本地部署

```powershell
$ cd docs
$ docsify serve

No docs found /root/RemoteWorking/index.html
Please run docsify init first.

➜  RemoteWorking git:(master) ✗ cd docs
➜  docs git:(master) ✗ docsify serve

Serving /root/RemoteWorking/docs now.
Listening at http://localhost:3000
```

## Github部署

找到 `setting` -> `GitHub Pages`，配置分支为 `master barnch /docs folder`，点击保存后会自动发布，并且给出发布地址。（例：https://hekaiyou.github.io/code-dictionary/#/）

## Docsify项目配置

更多配置请访问[Docsify官方文档](https://docsify.js.org/#/zh-cn/quickstart)

### docs目录结构

- .nojekyll：阻止GitHub忽略下划线开头的文件
- index.html：入口文件，整个网站的核心文件
- README.md：默认页面，主页内容渲染

### index文件设置

- name：站点标题
- repo：仓库地址，会在页面右上角渲染一个挂件
- coverpage：开启渲染封面功能，对应 `_coverpage.md` 文件
- loadNavbar：配置导航栏，对应 `_navbar.md` 文件
- maxLevel：最大支持渲染的标题层级

```javascript
  <script>
    window.$docsify = {
      name: '开发小手册',
      repo: 'https://github.com/hekaiyou/code-dictionary',
      coverpage: true,
      loadNavbar: true,
      maxLevel: 3
    }
  </script>
```
