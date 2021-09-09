# 一、Electron 文档

## 1.1 Electron 简介

- 什么是**Electron** ？
    - Electron是一个使用 JavaScript、HTML 和 CSS **构建桌面应用程序**的框架。
    - 简单来说通过**Electron**可以将我们编写好的**H5页面**打包成一个**PC端的桌面级应用**

- 使用**Electron**的前提要求

    - 熟悉**Node.js**和**h5页面**开发

        

>注：使用Electron时，要求**Node版本为14.2以上**   2021/06/19
>



## 1.2 Electron 基本使用

1. 初始化Node项目文件夹  `npm init`，并在`package.json`中添加如下字段

    <img src="images/06-Electron App.assets/image-20210619191751237.png" alt="image-20210619191751237" style="zoom:50%;" />

2. 安装第三方包：` npm install --save-dev electron`

3. 创建 ***preload.js*** 文件，编写如下代码

    - ```js
        window.addEventListener('DOMContentLoaded', () => {
            const replaceText = (selector, text) => {
                const element = document.getElementById(selector)
                if (element) element.innerText = text
            }
        
            for (const dependency of ['chrome', 'node', 'electron']) {
                replaceText(`${dependency}-version`, process.versions[dependency])
            }
        })
        ```

4. 在根目录下的`main.js`中编写如下代码

    - ```js
        const { app, BrowserWindow } = require('electron')
        const path = require('path')
        
        function createWindow() {
            const win = new BrowserWindow({
                width: 800,
                height: 600,
                webPreferences: {
                    // 关联桌面应用和网页的桥梁 js文件
                    preload: path.join(__dirname, 'public', 'preload.js')
                }
            })
        
            // 要加载的HTML文件路径
            win.loadFile(path.join(__dirname, 'public', 'index.html'))
        }
        
        app.whenReady().then(() => {
            createWindow()
        
            app.on('activate', () => {
                if (BrowserWindow.getAllWindows().length === 0) {
                    createWindow()
                }
            })
        })
        
        app.on('window-all-closed', () => {
            if (process.platform !== 'darwin') {
                app.quit()
            }
        })
        ```

5. 安装第三方包：  `npm install --save-dev @electron-forge/cli`

6. 执行`npx electron-forge import` 命令

7. 执行 `npm run make` 命令

8. 如果根目录下出现`out`文件夹，则说明打包成功

    <img src="images/06-Electron App.assets/image-20210619191528762.png" alt="image-20210619191528762" style="zoom:50%;" />



>注：打包时，***package.json***中的**author**和**description**字段不能为空
>





## 1.3 Vue项目中使用Electron

>前言：通过**页面链接跳转方式**跳转到部署到**远程服务器**上的**Vue项目**，这一方法是**行不通**的
>



>将Vue项目打包成 **Electron** 桌面级应用有如下几个步骤

1. 修改`vue-cli`中的**路径配置**，参考`vue高级 -> vue-cli -> 解决打包后页面空白问题`

    <img src="images/06-Electron App.assets/image-20210619200218149.png" alt="image-20210619200218149" style="zoom:50%;" />

    

2. 将`vue-router`修改为 **hash** 模式

     <img src="images/06-Electron App.assets/image-20210619200416717.png" alt="image-20210619200416717" style="zoom:50%;" />

​    

3. 执行`npm run build`命令，将vue项目打包到`dist`文件夹下
4. 将打包后的`dist -> index.html`文件作为要打包的**h5页面**
5. 重复`Electron基本使用`的**1 ~7 步骤**





























































































































































































































