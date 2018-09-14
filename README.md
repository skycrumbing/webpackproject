# 一个学习webpack的简单例子
## 因为webpack会使用到CommonJS规范首先介绍一下CommonJS规范
CommonJS规范规定一个文件就是一个模块，CommonJS规范需要node.js环境支持  
目的是弥补JavaScript没有标准的缺陷，已达到像Python、Ruby和Java那样具备开发大型应用的基础能力  
CommonJS模块规范主要分为三部分：模块引用、模块定义、模块标识。    
### 模块引用
```
var Math=require('math');
```
### 模块定义  
module对象：在每一个模块中，module对象代表该模块自身。
export属性：module对象的一个属性，它向外提供接口。
假设add.js中的代码如下  
```
function add(num1,num2){
    alert(num1+num2);
}
```
a.js已经引用了该模块，但是仍然无法使用它  
add.js中的函数要能被其他模块使用，就需要暴露一个对外的接口，export属性用于完成这一工作。将add.js中代码改为如下：  
```
exports.add=function (num1,num2){
    alert(num1+num2);
}
```
a.js文件就可以正常调用add.js中的方法，例如  
```
add.add(3,5)
```  
这样的调用能够正常执行，前一个add意为本文件中add变量代表的模块，后一个add是引入模块的add方法。
### 模块标识
模块标识指的是传递给require方法的参数，必须是符合小驼峰命名的字符串，或者以 . 、..开头的相对路径，或者绝对路径。  
##通过配置文件来使用Webpack
*在项目根目录建一个名为webpack.config.js的文件
其中写入如下所示的简单配置代码
```
module.exports = {
  entry:  __dirname + "/app/main.js",//唯一入口文件
  output: {
    path: __dirname + "/public",//打包后的文件存放的地方
    filename: "bundle.js"//打包后输出文件的文件名
  }
}
```
* 打包文件
在当前项目打开命令行，通过使用命令webpack进行打包
