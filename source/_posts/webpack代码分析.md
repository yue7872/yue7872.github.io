---
title: webpack学习：打包文件分析工具
date: 7/21/2021 14:45:13
tags:
  - webpack
  - 模块
  - 打包
  - npm
categories: webpack
abbrlink: webpack
---

## 1、webpack-bundle-analyzer

这是一个webpack插件，可以生成代码分析报告，帮助提升代码质量和网站性能。

## 2、安装

```bash
# NPM 
npm install --save-dev webpack-bundle-analyzer

# Yarn 
yarn add -D webpack-bundle-analyzer
```

## 3、使用

- 和一般插件使用方法相同，require之后new Plugin即可：

```js
// webpack.config.js
const BundleAnalyzerPlugin = require('webpack-bundle-analyzer')
module.exports = {
  plugins: [
    new BundleAnalyzerPlugin()    
  ]
}
```

- 开启项目(npm run dev(serve))后，打开网址 localhost:8888 即可查看分析
- 配置项说明

```js
new BundleAnalyzerPlugin({
  //  可以是`server`，`static`或`disabled`。
  //  在`server`模式下，分析器将启动HTTP服务器来显示软件包报告。
  //  在“static”模式下，会生成带有报告的单个HTML文件。
  //  在`disabled`模式下，你可以使用这个插件来将`generateStatsFile`设置为`true`来生成Webpack Stats JSON文件。
  analyzerMode: 'server',
  
  //  将在“服务器”模式下使用的主机启动HTTP服务器。
  analyzerHost: '127.0.0.1',
  
  //  将在“服务器”模式下使用的端口启动HTTP服务器。
  analyzerPort: 8888, 
  
  //  路径捆绑，将在`static`模式下生成的报告文件。
  //  相对于捆绑输出目录。
  reportFilename: 'report.html',
  
  //  模块大小默认显示在报告中。
  //  应该是`stat`，`parsed`或者`gzip`中的一个。
  //  有关更多信息，请参见“定义”一节。
  defaultSizes: 'parsed',
  
  //  在默认浏览器中自动打开报告
  openAnalyzer: true,
  
  //  如果为true，则Webpack Stats JSON文件将在bundle输出目录中生成
  generateStatsFile: false, 
  
  //  如果`generateStatsFile`为`true`，将会生成Webpack Stats JSON文件的名字。
  //  相对于捆绑输出目录。
  statsFilename: 'stats.json',
  
  //  stats.toJson（）方法的选项。
  //  例如，您可以使用`source：false`选项排除统计文件中模块的来源。
  //  在这里查看更多选项：https：  //github.com/webpack/webpack/blob/webpack-1/lib/Stats.js#L21
  statsOptions: null,
  
  logLevel: 'info' // 日志级别。可以是'信息'，'警告'，'错误'或'沉默'。
})
```

## 4、效果

![打包文件分析](/img/post/analysis.png)

