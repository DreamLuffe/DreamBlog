---
title: "零基础搭建hugo博客 windows"
subtitle: ""
date: 2023-02-18T10:27:18+08:00
# draft: true
author: "luffy"
authorLink: ""
authorEmail: ""
description: ""
keywords: ""
license: ""
comment: false
weight: 0

tags:
- hugo
- fixit
categories:
- 技术

---

> 提前需要准备的东西    
> - [hugo](https://github.com/gohugoio/hugo/releases/tag/v0.110.0)  
> - [fixit](https://github.com/hugo-fixit/FixIt/releases/tag/v0.2.17)  

##  操作步骤
1. ### 安装hugo

下载安装[hugo](https://github.com/gohugoio/hugo/releases/tag/v0.110.0)选择hugo_extended_0.110.0_windows-amd64.zip进行下载
把hugo.exe配置到全局环境变量
```bash
PS E:\> hugo  version
hugo v0.101.0-466fa43c16709b4483689930a4f9ac8add5c9f66 windows/amd64 BuildDate=2022-06-16T07:09:16Z VendorInfo=gohugoio
PS E:\>
```
2. ### 创建项目
```bash
hugo new site hugo-demo
```
创建完项目后，Hugo会帮我们生成一堆文件，我们需要知道这些文件的用途。
```bash
PS E:\demo\hugo-demo> tree /F
卷 Work 的文件夹 PATH 列表
卷序列号为 A861-7C83
E:.
│  config.toml        # 配置文件
│
├─archetypes
│      default.md
│
├─content     # 存放博客和单页文章
├─data        # 存放其他数据
├─layouts     
├─public      # 博客构建后的静态文件路径
├─static      # 用于存放静态资源
└─themes      # 主题路径
PS E:\demo\hugo-demo>
```
3. ### 创建第一篇文章
```bash
hugo new posts/my-first-post.md
```
4. ### 配置主题
 * 可以下载[fixit](https://github.com/hugo-fixit/FixIt/releases/tag/v0.2.17) 解压到 `themes`目录中
 * 或者使用git
 ```bash
git init
git submodule add https://github.com/hugo-fixit/FixIt.git themes/FixIt # 添加子模块
sudo cp themes/FixIt/config.toml config.toml # 复制主题配置到本地
 ```

修改配置文件 (config.toml) [fixit文档](https://fixit.lruihao.cn/zh-cn/theme-documentation-basics/)
```TOML
title = "我的全新 Hugo FixIt 网站"
baseURL = "http://example.org/"
# 设置默认的语言 ["en", "zh-cn", "fr", "pl", ...]
defaultContentLanguage = "zh-cn"
# 网站语言, 仅在这里 CN 大写 ["en", "zh-CN", "fr", "pl", ...]
languageCode = "zh-CN"
# 是否包括中日韩文字
hasCJKLanguage = true

# 更改使用 Hugo 构建网站时使用的默认主题
# 如果使用 Hugo Module 加载主题，则不需要配置该参数
theme = "FixIt"

[params]
  # FixIt 主题版本
  version = "0.2.X"

[menu]
  [[menu.main]]
    identifier = "posts"
    # 你可以在名称（允许 HTML 格式）之前添加其他信息，例如图标
    pre = ""
    # 你可以在名称（允许 HTML 格式）之后添加其他信息，例如图标
    post = ""
    name = "文章"
    url = "/posts/"
    # 当你将鼠标悬停在此菜单链接上时，将显示的标题
    title = ""
    weight = 1
    # 向菜单项添加用户定义的内容
    [menu.main.params]
      # 添加 CSS 类到菜单项
      class = ""
      # 是否为草稿菜单，类似草稿页面
      draft = false
      # 添加 fontawesome 图标到菜单项
      icon = "fa-solid fa-archive"
      # 设置菜单项类型，可选值：["mobile", "desktop"]
      type = ""
  [[menu.main]]
    identifier = "categories"
    pre = ""
    post = ""
    name = "分类"
    url = "/categories/"
    title = ""
    weight = 2
    [menu.main.params]
      icon = "fa-solid fa-th"
  [[menu.main]]
    identifier = "tags"
    pre = ""
    post = ""
    name = "标签"
    url = "/tags/"
    title = ""
    weight = 3
    [menu.main.params]
      icon = "fa-solid fa-tags"

# Hugo 解析文档的配置
[markup]
  # 语法高亮设置 (https://gohugo.io/content-management/syntax-highlighting)
  [markup.highlight]
    # false 是必要的设置 (https://github.com/hugo-fixit/FixIt/issues/43)
    noClasses = false
```

5. ### 在本地启动网站
```bash
hugo server
```
去查看 http://localhost:1313



更多详细配置[fixit](https://fixit.lruihao.cn/zh-cn/theme-documentation-basics/)
