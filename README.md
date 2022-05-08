## 背景

有时候我们在同一套代码基础上，我们存在多种商业/渠道/品牌，如果写死在代码里面，每次调试、打包可能需要改代码才行，那么有没有办法实现动态的输入呢？我们可以利用MsBuild的一个高级特性，[自定义生成配置](https://docs.microsoft.com/zh-cn/visualstudio/msbuild/customize-your-build)来实现这个需求。

![image](./Assets/375390-20220507202140473-63146221.png)

## 工作原理

通过在包含源的根文件夹中名为`Directory.Build.props`的单个文件内定义一个新属性，可以向每个项目添加该属性。在MSBuild运行时，`Microsoft.Common.props`会搜索`Directory.Build.props`文件的目录结构(`Microsoft.Common.targets`将查找`Directory.Build.targets`)。如果找到了一个文件，它将导入该文件并读取其中定义的属性。

`Directory.Build.props`是用户定义文件，对目录下的项目提供自定义选项。

> 直白一点说：只要你的项目根目录或者父级目录存在一个自定义的`Directory.Build.props`，你的Visual Studio就会把它读取到可视化操作面板的配置清单中来，你就可以自由切换了。

## 相关文章

* [乘风破浪，遇见最美Windows 11之现代Windows桌面应用开发 - 自定义生成配置文件(Directory.Build.props)来实现灵活切换](https://www.cnblogs.com/taylorshi/p/16243964.html)