---
title: 项目中有关webpack出现的一些问题
date: 2019-03-20 14:45:47
tags: [error, webpack]
---

在做项目的时候， 使用 webpack 所遇到的一些问题， 可能不是很好找到解决办法， 在此记录一些尝试的解决方案

<!-- more -->

# npm run build 出现的问题

问题描述： 再 npm run dev 打包的时候项目并没有报错， 但是在 npm run build 的时候控制台报错了， 问题如下

<div style="overflow: auto;"><img style="max-width: none;margin: 0;" src="../../../../../assets/images/error-webpack-npmrunbuild.png"></div>

尝试了度娘提供的各种方法

1.  babel-preset-es2015
    尝试后发现并没有解决

    ```javascript
    //安装依赖包
    $ npm install --save-div babel-preset-es2015

    //修改【webpack.base.conf.js】配置文件， 找到 /\.js$/的rules，进行修改
    {
        test: /\.js$/,
        use: [{
            loader: 'babel-loader',
            options: {
                presets: ['es2015']
            }
        }]
    }
    //根目录下.babelrc文件中presets下添加es2015
    {
        "presets": ["es2015"]
    }

    ```

    后来想到自己项目中是用了 babel-preset-env 的， 不需要再使用 babel-preset-es2015, 可能是脑子抽抽了

1.  修改【webpack.base.conf.js】配置文件， 找到 /\.js\$/的 exclude，进行修改

    ```javascript
      {
        test: /\.js$/,
        loader: 'babel-loader',
        exclude: /node_modules/, //表示node_modules中的 .js 文件不要进行 babel-loader
        include: [resolve('src'), resolve('test')]
      }
    ```

    同样一点变化都没有

1.  修改【webpack.base.conf.js】配置文件， 找到 /\.js\$/的 include，进行修改

    ```javascript
      {
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test'), resolve('node_modules/fusioncharts')] //include 表示哪些目录中的 .js 文件需要进行 babel-loader
      }
    ```

    此时稍微有了些起色， 但还是有个问题

1.  又看到有人说是因为 uglifyjs 版本问题
    于是尝试了修改 uglifyjs-webpack-plugin 插件

    ```javascript
    //安装依赖包
    cnpm install uglifyjs-webpack-plugin@beta --save-dev

    //修改【webpack.prod.conf.js】配置文件
    var UglifyJSPlugin = require('uglifyjs-webpack-plugin');
    //把
    //new webpack.optimize.UglifyJsPlugin({
    //  compress: {
    //    warnings: false
    //  },
    //  sourceMap: true
    //}),
    //修改为

    new UglifyJSPlugin({
      uglifyOptions: {
        warnings: false
      },
      sourceMap: true
    }),

    ```

    问题终于解决了
