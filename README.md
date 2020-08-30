# Python小手册

使用 `Markdown` 文档记录开发文档与代码，并使用 [Node.js](https://nodejs.org/zh-cn/) 语言的 [Docsify](https://docsify.js.org/#/zh-cn/) 框架自动生成一个网站，便于在开发过程中快速查阅！

## 本地预览

```powershell
$ cd code-dictionary
$ docsify serve

Serving C:\Users\hekaiyou\Documents\code-dictionary now.
Listening at http://localhost:3000
```

## 部署

### GitHub Pages

找到 `setting` -> `GitHub Pages`，配置分支为 `master barnch folder`，点击保存后会自动发布，并且给出发布地址。( 例如: https://hekaiyou.github.io/code-dictionary/#/ )

### Nginx

和部署所有静态网站一样，只需将服务器的访问根目录设定为 `index.html` 文件，在 `Nginx` 配置中添加如下内容。

```nginx
server {
  listen 3000;
  server_name  localhost;

  location / {
    alias /usr/code-dictionary/;
    index index.html;
  }
}
```

## Docsify项目配置

更多配置请访问 [Docsify官方文档](https://docsify.js.org/#/zh-cn/configuration) 查阅。

### docs目录结构

- .nojekyll：阻止GitHub忽略下划线开头的文件
- index.html：入口文件，整个网站的核心文件
- README.md：默认页面，主页内容渲染

### index文件设置

- name：站点标题
- repo：仓库地址，会在页面右上角渲染一个挂件
- coverpage：开启渲染封面功能，对应 `_coverpage.md` 文件
- loadNavbar：配置导航栏，对应 `_navbar.md` 文件
- subMaxLevel：生成目录的最大层级
- loadSidebar：加载自定义侧边栏，对应 `_sidebar.md` 文件
- search：全文搜索插件配置，配合 `search.min.js` 使用

```javascript
  <script>
    window.$docsify = {
      name: '开发小手册',
      repo: 'https://github.com/hekaiyou/code-dictionary',
      coverpage: true,
      loadNavbar: true,
      loadSidebar: true,
      subMaxLevel: 3,
      search: {
        maxAge: 86400000, // 过期时间，单位毫秒，默认一天
        paths: 'auto', // [] or 'auto'
        placeholder: '搜索',
        noData: '没有结果!',
        depth: 2, // 搜索标题的最大层级, 1 - 6
      }
    }
  </script>
```
