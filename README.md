# Blog_hexo
Hexo files of Blog.
---

# 网站设计初定:  

* Idea库：编辑`/source/ideas/index.md`

* 协会项目：编辑`/source/projects/index.md`

* 每周咨询：增加新咨询，用命令` hexo new news -p news/file_name "the title" `

    例如`hexo new news -p news/News1 "weekly news 1"`, 表示在 /source/_posts/news 目录下新建名为News1.md的文件，并且文章标题为“weekly news 1”，之后前往编辑该文件内容。

* 教程：增加教程，用命令` hexo new tutorials -p tutorials/path/to/the/file "the title" `

    例如`hexo new tutorials -p tutorials/Linux/linux004 "linux tutorials 004"`, 表示在 /source/_posts/tutorials/Linux 目录下新建名为linux004.md的文件，并且文章标题为“linux tutorials 004”，之后前往编辑该文件内容，（注：编辑文件时必须修改Front-matter区的`categories`项，且首字母需大写）。

生成文件同时还会在该文件所在目录自动生成同名目录，用于存放md文件中需要使用的图片等资源文件。