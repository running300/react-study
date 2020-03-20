### react 安装脚手架

```
npx create-react-app my-app
```



import React from 'react' => 其实就是导入React.createElement()方法编译jsx

方式使用jsx的文件必须导入react

可以使用.js / .jsx为后缀的

推荐VScode安装插件 :

eslint: 代码风格检查

es7 React/Redux/GraphQl/React-Native snippets: 快速代码编写 => rcc + tab

chrome: 安装react Developer tool



### JSX

- hello wold;

#### 什么是JSX

- facebook起草的js扩展语法
- 本质是一个js对象,会被babel编译,最终会被转换为createElement
- 每个JSX表达式,有且仅有一个根节点
  + 每个JSX元素必须结束(XML规范)  <img></img>  or <img />

```js
// => 不想要外层盒子,又不想报错 
< > < h1 > HELLO React < /h1><p>React.Fragment</p > < /> => 等效

import { Fragment } from 'react';
 <React.Fragment > < h1 > HELLO React < /h1><p>React.Fragment</p > < /React.Fragment>
```



####  在JSX嵌入表达式

- 表达式作为内容的一部分
  + null 和 false和 undefined 不会显示

- 将表达式作为元素的属性

  const cls = 'color'   color写一个属性,      <div clasName ={cls} style={{width:"100px", height: "100px"}}></div>

  const url ='xxxx'    <img src={url}/>

- {}  不能出现普通对象 eg:   <p>{obj}</p>    

- 数组 { [1,2,3] } => 123

- 注释 {/* 多行注释*/} 

- 属性使用小驼峰命名

- 防止注入攻击

  + 自动编码
  + dangerouslySetInnerHTM = {{ __html: cont}}  => 实在要用,太恶心了(还是不用了)

  const cont = "<h1>111</h1>"

  <div>  {cont}</div>  => 解析出来 <h1>111</h1>

#### 元素的不可变性

创建以后属性,和 内容不能改,只能重新渲染

```js
let num = 1;
const div = (
	<div title='aa'>
    	{num}
    </div>
)
div.props.children = 2;//报错
div.props.title = 'abc'; //报错
```

Object.freeze() => 冻结对象

