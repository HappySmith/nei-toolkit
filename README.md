# 工具简介

本工具是[NEI 接口管理平台](https://nei.netease.com/)自动化构建工具，主要功能有：

* 根据 NEI 平台定义的工程规范，生成工程的初始化目录结构
* 自动集成在 NEI 上定义的资源: 页面、异步接口、数据模型、页面模板、业务分组等
* 本地模拟容器

## 视频教程
* [NEI 视频教程](https://nei.netease.com/tutorial)

## NEI 工程规范介绍

* [NEI 工程规范介绍](./doc/工程规范介绍.md)
* [传给模板的数据格式说明](./doc/传给模板的数据格式说明.md)(**重要，必读**)
* [Handlebars](http://handlebarsjs.com/) 是本工具渲染文件内容所使用的模板引擎
* [Handlebars 辅助函数集说明](./doc/Handlebars辅助函数集.md)

## 教程
* [NEI 基本概念介绍](./doc/NEI基本概念介绍.md)
* [使用 NEI 进行前后端并行开发](./doc/使用NEI进行前后端并行开发.md)
* [使用 NEI 实现接口 Mock 服务](./doc/使用NEI进行前后端并行开发.md#如果需要使用接口的mock服务的话需要指定一个接口mock数据根路径-如下图所示)
* [从零开始使用 NEI 构建 Mock 服务器，以及配置跨域头](./doc/从零开始使用nei构建Mock服务器以及配置跨域头.md)
* [如何配置配置代理服务器](./doc/如何配置代理服务器.md)
* [老项目迁移到 NEI 上的说明](./doc/老项目的迁移说明.md)
* [一步一步教你如何愉快地生成 JavaBean 文件](./doc/一步一步教你如何愉快地生成JavaBean文件.md)
* [JavaBean 文件的示例模板](./doc/JavaBean文件的示例模板.md)
* [NEI 平台规则函数使用说明](./doc/NEI平台规则函数使用说明.md)
* [NEI 平台系统预置的规则函数集](./doc/NEI平台系统预置的规则函数集.md)
* [NEI 平台系统批量导入 HTTP 接口及格式说明](./doc/NEI导入HTTP接口列表支持的数据格式.md)
* [NEI 平台系统批量导入 RPC 接口及格式说明](./doc/NEI导入RPC接口列表支持的数据格式.md)
* [在NEI中导入接口的测试用例](./doc/在NEI中导入接口的测试用例.md)
* [使用 NEI 生成 iOS 代码](./doc/使用NEI生成iOS代码.md)
* [查看项目文档并导出为 PDF](./doc/查看项目文档并导出为pdf.md)
* [MockStore 功能介绍](./doc/mockstore.md)
  - [MockStore 实现说明](./doc/mockstore实现说明.md)
  - [RPC 在线 Mock 接口调用说明](./doc/RPC在线Mock接口调用说明.md)
  - [MockStore 示例代码](./doc/mockstore示例代码.md)
* [查看项目的 Key](./doc/查看项目的Key.md)
* [NEI 平台系统接口测试使用说明](./doc/NEI平台接口测试使用说明.md)
  - [NEI 平台系统测试集使用说明](./doc/NEI平台测试集使用说明.md)
  - [NEI 平台系统依赖测试使用说明](./doc/NEI平台依赖测试使用说明.md)
  - [如何查看实际发送的数据](./doc/NEI平台接口测试发送数据查看.md)
* [NEI 平台HTTP接口规范配置说明](./doc/NEI平台HTTP接口规范配置说明.md)
* [NEI Chrome插件使用指南](./doc/NEI-Chrome插件使用指南.md)
* [NEI 平台参数词条使用说明](./doc/参数词条使用说明.md)

## FAQ
* [常见问题](./doc/faq.md)

## 插件
* [Android Studio 插件](./doc/android_studio.md)

## 工具使用

### 环境配置
构建工具基于 [Node.js](http://nodejs.org/) 平台，因此需要先安装 Node.js 环境，Node.js 在各平台上的安装配置请参阅官方说明。

>安装的 Node.js 版本须为 v4.2 及以上

### 安装

```bash
npm install nei –g
```

>提示1: 如果安装不成功, 可以尝试命令 `npm install -g nei`

>提示2: 如果已经安装过 nei, 请使用更新命令 `npm update nei -g`

>提示3: 也可以安装某个分支，比如安装 `dev` 分支的命令如下:

```bash
sudo npm install "NEYouFan/nei-toolkit#dev" -g
```

>提示4：如果安装失败，可能是网络超时引起的，可以试着使用下面的命令安装：

```bash
sudo npm install nei -g --registry=https://registry.npm.taobao.org
```

## 指令说明

本工具使用时在终端或者命令行输入以下格式指令运行

```bash
nei [指令] [参数]
```

其中可用的指令包括：

| 指令  | 描述 |
| :--- | :--- |
| build  | 根据在 NEI 平台上定义的工程规范，生成工程的初始化目录结构 |
| update | 更新通过 `nei build` 构建的项目 |
| server | 启动本地模拟容器 |
| template | 使用本地数据解析模板 |


### build
根据在 NEI 平台上定义的工程规范，生成工程的初始化目录结构，指令的运行格式为：

```bash
nei build -k [key] [参数]
``` 

其中 [key] 是 NEI 平台上的项目的唯一标识，可以在项目的"工具(设置)"中查看

针对 `nei build` 指令可用的参数包括：

| 简写 | 全称 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- |
| -h | --help |  | 显示 build 命令的帮助信息 |
| -o | --output | ./ | 指定项目的输出目录 |
| -k | --key |  | 项目的唯一标识，可以在项目的"工具(设置)"中查看 |
| -sk| --specKey |  | 规范的唯一标识，可以在规范的"规范设置"中查看 |
| -w | --overwrite | false | 是否覆盖已存在的文件，需要下载的文件不在此列，如果需要重新下载，请先将本地的文件删除 |
| 无 | --specType | web | 要构建的规范类型，目前支持 web、aos、ios、test 四种类型 |
| -s | --server | https://nei.netease | 数据源服务器 |

使用范例：

在当前目录下构建 key 为 xyz 的项目：

```bash
nei build -k xyz
```

规范也可以独立于项目生成脚手架文件, 在当前目录下构建 key 为 xyz 的规范：

```bash
nei build -sk xyz
```

>注意: 如果 k 和 sk 参数同时存在, 系统会优先考虑 sk 参数

### update

更新通过 `nei build` 构建的项目，指令的运行格式为：

```bash
nei update [参数]
``` 

`nei update` 指令可用的参数包括：

| 简写 | 全称 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- |
| -h | --help  | | 显示 update 命令的帮助信息 |
| -o | --output | ./ | 指定的项目目录 |
| -k | --key |  | 需要更新的项目的唯一标识 |
| -a | --all | false | 是否更新指定目录下面的所有项目，前提是没有指定的 key |
| -w | --overwrite | false | 是否覆盖已存在的文件，需要下载的文件不在此列，如果需要重新下载，请先将本地的文件删除 |
| 无 | --spec | false | 是否更新规范中的普通文件和文件夹，以数据填充的文件不在此列 |
| -s | --server | https://nei.netease | 数据源服务器 |

使用范例：

更新当前目录下通过 `nei build` 生成的项目

```bash
nei update
```

>提示: 可以先在本地创建项目目录，然后在该目录下使用 `nei build` 和 `nei update` 命令，使用默认值即可.


### server
启动内置的本地模拟容器

```bash
nei server [参数]
```

`nei server` 指令可用的参数包括：

| 简写 | 全称 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- |
| -h | --help | | 显示 server 命令帮助信息 |
| -o | --output | ./ | 已构建项目的输出路径 |
| -k | --key |  | 需要启动的项目的唯一标识 |

使用范例

启动目录为 ./mypro 下的项目:

```bash
nei server -o ./mypro
```

> OS X 下如果有异常请使用 `sudo nei server` 命令启动


### template
使用本地数据解析模板。通过指定本地模板文件以及数据文件，能够将模板解析得到输出文件。目前支持的模板语言为[handlebars](http://handlebarsjs.com/)。

```bash
nei template [参数]
```

`nei template` 指令可用的参数包括:

| 简写 | 全称 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- |
| -h | --help | | 显示 template 命令帮助信息 |
| -o | --output | ./ | 输出路径 |
| -p | --path |  | 本地模板路径，必须指定 |
| -d | --data |  | 数据json文件路径,可选 |
| -b | --handlebars |  | 自定义handlebars辅助函数文件路径,可选 |
| -w | --overwrite | false | 是否覆盖已存在的文件 |

用户可以指定数据文件，如`data.json`的文件内容如下:
```json
{
  "project":{
    "name" : "test",
    "version" : "0.0.1"
  },
  "author":{
    "Netease"
  }
}
```
然后用户就可以在模板文件中访问到数据中的数据，如`{{project.name}}`就能够解析为`test`。用户同样可以指定本地handlebars辅助文件，如果用户有多个辅助函数，需要将这些都写到一个文件中，自定义辅助函数的写法与上文一致，参照[此链接](https://github.com/NEYouFan/nei-toolkit/blob/master/doc/Handlebars%E8%BE%85%E5%8A%A9%E5%87%BD%E6%95%B0%E9%9B%86.md#如何撰写自定义handlebars辅助函数)相同。 另外用户也可以不通过指定数据json文件来传入数据，可以通过命令行直接传入数据参数，如：
```bash
nei template -ProductName Test -Prefix HT [其他参数]
```
ProductName和Prefix这两个参数就会作为数据传入到模板中，其等同于
```json
{
  "args":{
    "ProductName" : "Test",
    "Prefix":  "HT"
  }
}
```
如果同时指定了数据文件，将会执行merge操作，其中命令行参数指定的方式优先于数据json文件方式。
### 设置输出信息级别
共设有"all"、"debug"、"info"、"warn"、"error"、"off"等日志级别，级别顺序由大到小，通过`--logLevel`指定一个级别之后，比该级别小的日志级别信息都将会显示出来，比如：
```bash
nei build -k xxxxxxxx --logLevel info
```
那么所有info以下级别(即warn、error)级别的信息都将会显示出来。当指定为off的时候，所有日志信息都将关闭。
## 版本更新说明
[更新说明](./CHANGELOG)

## Licence
[MIT](./LICENSE)

## 感谢
感谢[网易云](http://www.163yun.com/)提供的云服务, 目前 [NEI](https://nei.netease.com) 已经托管在网易云上。

## 讨论组:

NEI 用户交流 QQ 群(453281988):

![QQ 群](./doc/res/nei_qq.jpeg)



