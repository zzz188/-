# npm基础

## Windows安装npm

- npm install npm -g     全局

也可以使用淘宝镜像进行安装

npm install  -g cnpm --registry=https://registry.npm.taobao.org

- 更改npm的源地址为淘宝源
  npm config set registry http://registry.npm.taobao.org

检查地址
npm config get registry

### npm安装Node.js模块语法格式

- npm install <Module Name>   本地安装

- npm install <Module Name>   -g  全局安装

- 例：安装web框架模块express，安装完成后express包将会存放在工程目录下的node_modules中
  npm install express
  可以通过 
  var express = require('express');
  的方式来引用

## 错误

如出现以下错误

```
npm err! Error: connect ECONNREFUSED 127.0.0.1:8087 
```

解决办法为

npm config set proxy null

## 本地安装

- 将安装包放在 ./node_modules 下（运行 npm 命令时所在的目录），如果没有 node_modules 目录，会在当前执行 npm 命令的目录下生成 node_modules 目录。
- 可以通过 require() 来引入本地安装的包。

## 全局安装

-  将安装包放在 /usr/local 下或者你 node 的安装目录。
-  可以直接在命令行里使用。

## 查看安装信息

- npm list -g    
  可查看全局安装的模块
- npm list <Moudle Name>
  可查看模块版本


## Package.json 属性说明

**name** - 包名。

**version** - 包的版本号。

**description** - 包的描述。

**homepage** - 包的官网 url 。

**author** - 包的作者姓名。

**contributors** - 包的其他贡献者姓名。

**dependencies** - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。

**repository** - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。

**main** - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。

**keywords** - 关键字



## 卸载模块

npm uninstall  <Moudle Name>

npm ls   查看包是否还存在

## 更新模块

npm update <Moudel Name>

## 搜索模块

npm search <Moudel Name>

## 创建模块  

创建模块，package.json 文件是必不可少的。我们可以使用 NPM 生成 package.json 文件，生成的文件包含了基本的结果。

```
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (node_modules) runoob                   # 模块名
version: (1.0.0) 
description: Node.js 测试模块(www.runoob.com)  # 描述
entry point: (index.js) 
test command: make test
git repository: https://github.com/runoob/runoob.git  # Github 地址
keywords: 
author: 
license: (ISC) 
About to write to ……/node_modules/package.json:      # 生成地址

{
  "name": "runoob",
  "version": "1.0.0",
  "description": "Node.js 测试模块(www.runoob.com)",
  ……
}


Is this ok? (yes) yes
```

以上的信息，你需要根据你自己的情况输入。在最后输入 "yes" 后会生成 package.json 文件。

接下来我们可以使用以下命令在 npm 资源库中注册用户（使用邮箱注册）：

```
$ npm adduser
Username: mcmohd
Password:
Email: (this IS public) mcmohd@gmail.com
```

接下来我们就用以下命令来发布模块：

```
$ npm publish
```

如果你以上的步骤都操作正确，你就可以跟其他模块一样使用 npm 来安装。

## 版本号

使用NPM下载和发布代码时都会接触到版本号。NPM使用语义版本号来管理代码，这里简单介绍一下。

语义版本号分为X.Y.Z三位，分别代表主版本号、次版本号和补丁版本号。当代码变更时，版本号按以下原则更新。

- 如果只是修复bug，需要更新Z位。
- 如果是新增了功能，但是向下兼容，需要更新Y位。
- 如果有大变动，向下不兼容，需要更新X位。

版本号有了这个保证后，在申明第三方包依赖时，除了可依赖于一个固定版本号外，还可依赖于某个范围的版本号。例如"argv": "0.0.x"表示依赖于0.0.x系列的最新版argv。

## NPM 常用命令

NPM提供了很多命令，例如install和publish，使用npm help可查看所有命令。

- NPM提供了很多命令，例如`install`和`publish`，使用`npm help`可查看所有命令。
- 使用`npm help <command>`可查看某条命令的详细帮助，例如`npm help install`。
- 在`package.json`所在目录下使用`npm install . -g`可先在本地安装当前命令行程序，可用于发布前的本地测试。
- 使用`npm update <package>`可以把当前目录下`node_modules`子目录里边的对应模块更新至最新版本。
- 使用`npm update <package> -g`可以把全局安装的对应命令行程序更新至最新版。
- 使用`npm cache clear`可以清空NPM本地缓存，用于对付使用相同版本号发布新版本代码的人。
- 使用`npm unpublish <package>@<version>`可以撤销发布自己发布过的某个版本代码。