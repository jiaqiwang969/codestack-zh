---
title: Setup development environment and create first Angular 8 project
caption: Create First Project
description: Setup development environment with Node.js and create first project using Angular 8 framework and Angular CLI in Visual Studio Code
image: angular-start-page.png
labels: [nodejs,visual studio code,angular cli,angular project]
order: 1
---
让我们从创建你的第一个基本Angular应用程序开始。

## 准备工作

### 安装编辑器

选择并安装一个现有的Angular代码编辑器：
* [Visual Studio Code](https://code.visualstudio.com/)
* [Atom](https://atom.io/)
* 你也可以使用Visual Studio或任何其他Angular代码编辑器（Sublime Text，Webstorm，Angular IDE等）。

*你可以跳过此步骤，稍后再回来继续开发Angular应用程序。*

在这个示例中，我将使用Visual Studio Code和cmd。

### 安装Node JS

通过在控制台中从任何位置运行以下命令来检查您的计算机上是否已安装Node JS：

~~~
> node -v
~~~

如果您看到以下“未识别”消息，则必须先安装[NodeJS](https://nodejs.org/en/)：

!['node' is not recognized](not-installed-node-console.png)

否则，您将看到Node JS的版本。您还可以通过运行以下命令来检查npm（Node JS包管理器）的版本：

~~~
> npm -v
~~~

![Node JS Version](node-js-version-console.png)

### 安装Angular CLI

要安装Angular CLI，请在cmd中运行以下命令：

~~~
> npm i -g @angular/cli  
~~~

其中**i**是install的缩写，**-g**是全局安装的标志。全局意味着angular-cli包将在您的计算机上的所有Angular应用程序中都可用。

![Install Angular CLI](angular-cli.png)

安装了Angular CLI的第8个版本。

## 创建

您可以在同一个终端中继续，或者打开Visual Studio Code并在其中继续，方法是在菜单中选择Terminal。

在选定的终端中，导航到您计算机上的源代码文件夹，并创建新的“my-first-angular-app”Angular项目：

~~~
> ng new my-first-angular-app
~~~

<video controls>
  <source src=".\init-angular-app.mp4" width="350" type="video/mp4">创建新的Angular项目
</video>

Angular CLI将为您创建应用程序环境并安装npm包。

恭喜，您的第一个Angular应用程序已创建！

## 运行

要尝试您的新应用程序，请在终端中转到应用程序文件夹并运行serve命令：

~~~
> ng s --o
~~~

其中**s**是serve的缩写，**--o**是open的缩写。

*您可以在不使用open标志的情况下启动应用程序，但在这种情况下，您需要手动在浏览器中打开http://localhost:4200/。*

应用程序将被构建并运行。

![Building and running angular project](run-angular-project-console.png)

在浏览器中查看您的第一个Angular应用程序：

![First angular application in the browser](angular-start-page.png)

## 完成

关闭浏览器不足以停止应用程序。您应该在终端中停止它。

点击ctrl+c停止服务器，并回答“Terminate batch job (Y/N)?”的问题选择y：

![Stopping the angular project](stop-angular-project.png)

*不需要为每个更改停止和运行应用程序。您可以在代码中进行更改，并立即在浏览器中看到它们。*