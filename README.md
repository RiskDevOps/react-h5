## 简述
基于最基础的create-react-app dva antd-mobile webpack做一定的修改而来, 做了一部分的`ES next` `Flow` 和一部分的Polyfill的支持 如 [optional-chaining](https://github.com/tc39/proposal-optional-chaining)  `Object.keys` `array.flatMap` 等

> 部分Polyfill暂时还未提交,现在已经添加对`optional-chaining`和`Flow`的支持

**移动端适配**

现在移动端适配是将所有`px`单位全部转换为`rem`, 并且根据设备大小动态计算出 `html` 节点的`font-size`值, 以此来达到适配不同设备显示不一样的问题! 这意味着你可以为所欲为用 `px` 作为单位了, 从未如此舒服的写过`px`😂

> 😲注意事项: <br><br>暂时还不支持 `百分比` 和 `vw vh` 统一转换为 `rem`, 提及这一点是因为 `百分比或者vw vh与px的缩放规则并不相同`, 建议使用 `px` 或者是 `rem` 作为开发时的单位...<br> 如果你的 `px` 值是不需要转换为 `rem`, 只需要将单位任意或者所有字母大写即可<br><br>💭举个栗子: <br>```.container { font-size: 12Px; margin: 12PX; padding: 12pX }```<br>这几个情况都不会将单位转换为 `rem`

## 静态类型支持

> 计画除了原生的`React PropTypes`类型支持外, 还将提供 [Flow](https://zhenyong.github.io/flowtype/) 和 `TypeScript` 支持, 现在已经支持 `Flow`静态类型分析

**Flow 静态类型检查器**

现在语言采用JavaScript, 如果你需要使用 静态类型分析 可以添加 Flow 来进行支持, [Flow官网](https://zhenyong.github.io/flowtype/)

但是使用了 Flow 方案后, 请在打包前置使用 `remove-flow-types-loader` 将Flow的支持移除, 因为Flow的语法在JS中并不支持, 如果不移除将会引起Build后无法使用, 具体配置与 `webpack loader` 配置完全相同!

**在 customize-cra 中配置**

`安装`

``` bash
npm install --save-dev babel-preset-flow remove-flow-types-loader
```

`.babelrc中使用`

``` bash
{
  "presets": [..., "babel-preset-flow", ...]
}
```

`config-overrides.js中配置移除`

``` javascript
    const {
        override,
        ...,
        addWebpackModuleRule,
        ...
    } = require('customize-cra');

    module.exports = override(
        addWebpackModuleRule({
            test: /\.jsx?$/,
            enforce: "pre",
            use: ["remove-flow-types-loader"],
            include: path.join(__dirname, "src")
        })
    )
```
你可能会遇到 `你可能需要使用其他loader进行解析的报错` 那是因为 `Pre` 被 `Eslint-loader` 占用, `/\.jsx?$/` 这个规则被 `babel-loader` 占用, 需要先将Eslint-loader禁用, 然后在规则的use处添加上对 react 的解析loader => `babel-loader`

**React PropTypes**

中小型项目可以使用 `PropTypes` 作为类型静态类型支持工具, 但是也会有一些不足

[PropTypes 文档](https://reactjs.org/docs/typechecking-with-proptypes.html)

**TypeScript 支持**

暂时还未支持TypeScript, 现在这个库只是 JavaScript 版本 将在不久会推出 TypeScript 版本

## 调试

我们推荐使用 Sizzy [下载地址](https://sizzy.co/) 进行多端调试, 前提是你需要能 `科学上网` 因为这个工具是放在国外的! 国内没有办法下载和获取注册码

如果不能进行科学上网 也可选择Chrome控制台和Chrome远程调试方案...

## 问题

如果你在使用过程中遇到一些问题, 可以给我们提交 `Issues` 或者是直接添加微信 `soc686` 反馈你的问题

**提交Issues**

为了更高效的解决问题 我们希望您的 Issues 可以注明以下信息
- `想要达到是什么效果?`
- `遇到什么问题?`
- `做了哪些尝试?`
- `我怀疑是什么问题?`
- `如果可以请尽量附加上你的代码 和 错误信息`

**微信反馈**

可能通过时间比较慢,添加时候请注明 `来自Github`

**一些文档**

[可能存在的一些问题, 正在编写中](./docs/md/QUESTION.md)

[正在修复的BUG](./docs/md/FIXBUG.md)

## 示例

基于第三方在线图片托管平台
[Sizzy展示](https://img.wenhairu.com/image/YLVCI)

在仓库文件中查看:
在仓库文件中也有提供示例截图, 在 `docs/image` 文件夹下可以找到, 但是可能由于您本地HOST问题, DNS无法解析到 `github.com` .

你可以在HOST文件中尝试添加 DNS 解析地址, 或者是将仓库 `Clone` 到本地进行查看

## TODO

[TODO-LIST](./docs/md/TODO.md)
