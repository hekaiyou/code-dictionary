# docs中的3个文件

 - .nojekyll：让gitHub不忽略掉以 _ 打头的文件
 - index.html：整个网站的核心文件
 - README.md：默认页面
 
## 本地预览文档

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

## GitHub预览文档

找到 `setting` -> `GitHub Pages`，配置分支为 `master barnch /docs folder`，点击保存后会自动发布，并且给出发布地址。（例：https://hekaiyou.github.io/code-dictionary/#/）