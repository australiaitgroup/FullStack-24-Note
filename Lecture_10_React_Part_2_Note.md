# Lecture 10 React (2)

本篇笔记以 Zhao Long 老师的 Lecture 10 React (Part 2) 的课堂内容整理的随堂笔记

## Table of Contents

1. [前端工程化与 React](#1-前端工程化与-react)
2. [React 的特性](#2-react-的特性)
   - 2.1. [命令式 VS 声明式](#21-命令式-vs-声明式)
   - 2.2. [组件化](#22-组件化---就像乐高积木)
3. [创建 React App](#3-创建-react-app)

## 1. 前端工程化与 React
- JavaScript vs Vanilla JavaScript vs Node.js
  - JavaScript：一种语法
  - Vanilla JavaScript：一系列的API用来操作HTML和CSS （操作页面和样式以实现相应的功能）
  - Node.js: 一系列的API用来操作DB，Q，FS
- JavaScript(Vanilla JS | Node.js)  
  - Vanilla JavaScript 是指原生 JavaScript，未经任何库或者框架修改的纯粹的 JavaScript。它不依赖于任何外部库，如 jQuery 或 React。
  - 使用 Vanilla JavaScript 操作前端页面，引入了 DOM.

- DOM（Document Object Model，文档对象模型）: 是一个编程接口，它允许 JavaScript 动态地访问和更新文档内容、结构和样式。当浏览器加载页面时，他会创建页面的文档对象模型。DOM API 就是让开发者可以通过变成方式与 DOM 交互的一组方法和属性。

  > 参考 MDN: [Document Object Model (DOM)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

  - DOM API 是框架和库操作浏览器的唯一方法
  - 由于 Vanilla JavaScript 自身存在的问题（语法复杂、可读性差等），jQurey 被引入。

- JQuery（更加符合人类的思考方式，致力于解决难以写出高质量代码的问题）

  - 跨浏览器的兼容性
  - 简化的语法
  - 易用的 AJAX 语法
  - 强大的选择器引擎

  > 虽然 jQurey 极大地简化了前端开发，但其在处理大型、复杂应用时的局限性导致了现代框架和库的出现。

## 2. React 的特性

- Declarative 声明式编程
  - 在Vanilla JS中，你明确地描述了如何操作DOM：查询元素、添加事件监听器、手动更新内容。
  - 在React中，你只描述了界面应该如何呈现（声明式）。实现了在js中直接写html。实际的DOM操作是React库在背后为你处理的。
  - React允许开发者更加关注应用的状态和逻辑，而不是繁琐的DOM操作细节。
- Component-Based 组件化
  - 随着互联网和Web技术的发展，前端项目逐渐变得复杂。

### 2.1. 命令式 VS 声明式

命令式编程和声明式编程是两种不同的编程范式，它们在解决问题和描述程序行为的方式上有所不同。

1. 命令式：（注重**过程**而不是结果）

   - 命令式编程强调编写详细的指令，告诉计算机如何执行任务。
   - 开发者需要显式地指定每个步骤和每个操作的执行顺序。
   - 代码通常包含大量的控制结构（如循环和条件语句）和副作用（直接修改状态）。

   ```js
   const db = sql.connect(str);
   const table = db.readTable("student");
   const result = [];

   for (let i = 0; i < table.data.length; i++) {
     if (table.data[i].score < 50) {
       result.push(table.data[i]);
     }
   }

   result.slice(0, 10);
   ```

2. 声明式：（注重**结果**而不是过程）

   - 声明式编程更关注描述问题的解决方案，而不是具体的实现细节。
   - 开发者描述所需的结果，而不是详细说明如何达到这个结果。
   - 代码更加简洁、易读和易维护，因为它们通常更抽象，不涉及具体的操作步骤。

   ```sql
   SELECT name, score, id FROM student WHERE score < 50
   ```

> 💡 总的来说，随着前端应用的复杂性不断增加，从命令式到声明式的转变已经成为了一种必然。这种转变为前端开发带来了更高的效率，可读性和可维护性，从而支持了大规模项目的持续发展和创新。

**Example**

```js
<button id="alertButton">Show Alert</button>

<script>
  document.getElementById('alertButton').addEventListener('click', function()) {
    alert('Button was clicked!');
  }
</script>
```

```js
import React from "react";

function AlertButton() {
  return (
    <button onClick={() => alert("Button was clicked!")}>Show Alert</button>
  );
}

export default AlertButton;
```

上面的两个例子都达到了同样的效果，但是方法不同：

- Vanilla JS，使用了命令式，明确描述了如何操作 DOM
- React，使用了声明式，只描述了界面应该如何呈现。实际的 DOM 操作是 react 库在背后处理的。

### 2.2. 组件化 - 就像乐高积木

组件化是为解决以下前端项目问题而产生的：

- 复杂性增加：现代Web应用不再只是简单的静态页面。它们可以是完全交互的、有多个视图、与后端系统集成并处理大量的数据和状态。
- 代码重复与冗余：在没有组件化的环境下，为实现相似功能的不同部分，开发者可能会重复编写相同或者类似的代码，导致冗余。
- 难以维护：随着代码量和功能的增加，项目变得难以维护。小的更改可能会导致不可预测的后果，或需要在多个地方更改代码。
- 团队协作困难：当多个开发者同时在一个大型项目上工作，如果没有明确的结构或模块化，代码合并或解决冲突可能会非常困难。
- 缺乏 UI 和功能的一致性：在大型项目中，如果没有共享和重用代码的机制，不同的部分或者页面可能会有不同的UI或行为，导致用户体验不一致。

而组件化就像乐高积木一样：

- 模块化与可重用性   
- 简单与清晰的结构  
- 易于维护
- 团队协作  

## 3. 创建 React App

- [React](https://react.dev/): 一个Facebook开发的用于构建用户界面的JavaScript 库，它允许开发者使用组件化的方式创建声明式UI，而不需要关心如何高效地更新和渲染UI。但React本身只是一个库，它并不包括一些必要的工具和功能使其在现代浏览器中运行，特别是当我们考虑到ES6+语法和JSX。
> JSX 是 JavaScript XML 的缩写，是一种在 React 应用程序中使用的语法扩展。它允许开发者在 JavaScript 代码中写出类似 HTML 的结构。
- 对react来说必不可少的两样东西：
   - [Babel](https://babeljs.io/): 让现代 JavaScript 兼容所有浏览器，引入非标准化的 JavaScript 版本。
   - [Webpack](https://webpack.js.org/): 模块捆绑器和任务运行器

- 脚手架： create react app
  - npx = npm execute (安装并执行)
  - npx create-react-app my-app = npm i create-react-app + create-react-app my-app 
