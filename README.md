# Getting Started

进入到根目录

//删除文件夹下的所有 .git 文件

find . -name ".git" | xargs rm -Rf

```
npm install
```

To start developing, run:

```
npm run start
```

This will fire up a local web server, open http://localhost:9000 in your default browser and watch files for changes, reloading the browser automatically.

To run the tests in the browser, run:

```
npm run serve:test
```

To make a production-ready build of the app, run:

```
npm run build
```

To preview the production-ready build to check if everything is ok:

```
npm run serve:dist
```

# Adding New Assets

## Sass

通常的做法是使用单个“main”Sass文件，然后使用@import语句添加其他部分。
例如，假设您为导航创建了样式表 app/styles/nav.scss，然后可以在 app/styles/main.scss中导入它，如下所示：

```
@import "nav";
```

## JavaScript

我们的构建步骤使用特殊构建注释块来标记要连接和压缩生产的资产。
可以在app / index.html的顶部和底部看到它们。

必须手动添加自己的JS文件。
例如，假设创建了 app/scripts/nav.js，为导航定义了一些特殊行为。
然后，应该将它包含在源JS文件的注释块中，其中 app/scripts/main.js 位于：

```
<!-- build:js scripts/main.js -->
<script src="scripts/main.js"></script>
<script src="scripts/nav.js"></script>
<!-- endbuild -->
```

在构建时，这些将被连接并压缩成单个文件 scripts/main.js。

注释块中的文件名和第一个源不相关，它们的名称相同是纯粹的巧合。
注释块中的文件名指定如何调用最终优化文件，而源应映射到源文件。
