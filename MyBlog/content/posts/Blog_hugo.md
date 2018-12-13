+++
title = "Blog: hugo"
date = 2018-12-13T16:04:33+08:00
draft = true
tags = ["Blog"]
categories = ["Blog"]
+++
### 安装
+ 下载和你操作系统匹配的 Hugo [版本][1]；
+ 压缩包解压到指定路径，例如 windows 系统的 `C:\hugo_dir` 或者 Linux 系统的 `~/hugo_dir` 目录；

> 下文中的变量 `${HUGO_HOME}` 所指的路径就是这个安装目录;

+ 打开命令行终端，进入安装目录：`cd ${HUGO_HOME}`;
+ 确认 Hugo 已经启动：
++ Unix 系统：`${HUGO_HOME}/[hugo version]`；
++ Windows 系统：`${HUGO_HOME}\[hugo.exe version]`，

> 例如：cmd 命令行中输入：`c:\hugo_dir\hugo version`。
> 为了书写上的简化，下文中的 hugo 就是指 hugo 可执行文件所在的路径（包括可执行文件），
> 例如命令 hugo version 就是指命令 `c:\hugo_dir\hugo version` 

### 创建一个新的站点来作为你的博客，
`hugo new site awesome-blog；`
+ 进入新创建的路径下: cd awesome-blog
恭喜你！你已经创建了自己的新博客。

### 为博客设置主题
> 这里选择 [Kiera][3] 主题

+ 进入主题所在目录：`cd themes`；
+ 克隆主题：`git clone https://github.com/avianto/hugo-kiera kiera` 
+ 返回博客主路径：`cd awesome-blog`
+ 激活主题；通常来说，主题（包括 Kiera）都自带文件夹 exampleSite，里面存放了内容配置的示例文件。

> 激活 Kiera 主题需要拷贝它提供的 config.toml 到你的博客下：

++ Unix 系统：`cp themes/kiera/exampleSite/config.toml .`
++ Windows 系统：`copy themes\kiera\exampleSite\config.toml .`
+ [可选操作] 你可以选择可视化的方式启动服务器来验证主题是否生效：`hugo server -D` 然后在浏览器中输入 http://localhost:1313 。

> 可用通过在终端中输入 `Crtl+C` 来停止服务器运行。
> 现在你的博客还是空的，但这也给你留了写作的空间。
> 你已经成功的给博客设置了主题！你可以在官方 Hugo [主题][5] 网站上找到上百种漂亮的主题供你使用。

###  给博客添加内容

+ 添加主题中的 archtypes 至你的博客：
++ Unix 系统： `cp themes/kiera/archetypes/* archetypes/`
++ Windows 系统：`copy themes\kiera\archetypes\* archetypes\`

+ 创建博客 posts 目录：
++ Unix 系统： mkdir content/posts
++ Windows 系统： mkdir content\posts
+ 利用 Hugo 生成你的 post：
++ Unix 系统：hugo nes posts/first-post.md;
++ Windows 系统：hugo new posts\first-post.md;
+ 在文本编辑器中打开这个新建的 post 文件：`first_post.md`

可以看到：第一部分是以 +++ 符号分隔开的。它包括了提交文档的主要数据，例如名称、时间等。在 Hugo 中，这叫做前缀。
在前缀之后，才是正文。
请在最末添加你的博文内容。

+ 现在你要做的就是启动你的服务器：`hugo server -D`, 然后打开浏览器，输入 `http://localhost:1313/`。


### 调整网站

+ 打开 config.toml,编辑博客的名称，版权，你的姓名，社交网站等等。
当你再次启动服务器后，你会发现博客私人订制味道更浓了。
不过，还少一个重要的基础内容：主菜单。快速的解决这个问题。返回 config.toml 文件，在末尾插入如下一段：

```
[[menu.main]]
    name = "Home" #Name in the navigation bar
    weight = 10 #The larger the weight, the more on the right this item will be
    url = "/" #URL address
[[menu.main]]
    name = "Posts"
    weight = 20
    url = "/posts/"
```

上面这段代码添加了 Home 和 Posts 到主菜单中。

+ 你还需要一个 About 页面。这次是创建一个 .md 文件，而不是编辑 config.toml 文件：
创建 about.md 文件：`hugo new about.md` 。注意它是 `about.md`，不是 `posts/about.md`。
该页面不是博客提交内容，所以你不想它显示到博客内容提交当中吧。
用文本编辑器打开该文件，输入如下一段：

```
+++
title = "About"
date = 2018-03-03T13:50:49+01:00
menu = "main" #Display this page on the nav menu
weight = "30" #Right-most nav item
meta = "false" #Do not display tags or categories
+++
```

> Waves are the practice of the water. Shunryu Suzuki

当你启动你的服务器并输入：`127.0.0.1:1313`

> Gihub 主页上的 [例子][6] 

> 如果你想让文章的菜单栏和 Github 相似，给 themes/kiera/static/css/styles.css 打上这个 [补丁][7]。

[1]: https://github.com/gohugoio/hugo/releases
[3]: https://themes.gohugo.io/
[5]: https://themes.gohugo.io/
[6]: https://m-czernek.github.io/awesome-blog/
[7]: https://github.com/avianto/hugo-kiera/pull/18/files