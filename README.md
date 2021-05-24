# myblog
此项目是 `hexo+github` 搭建的个人博客，用于记录学习日常和心得。

### 博客地址 [myblog](yue7872.github.io)

- master分支为hexo生成并部署的静态资源分支，主要是博客的html文件。
- hexo分支为hexo部署之前的源文件（md）。

### hexo常用命令
```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
```
### 缩写
```
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```

hexo g生成静态页面至public，hexo d部署到github，hexo s开启预览。
