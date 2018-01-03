# 说明

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.5.0.

最近用angular做后端，需要用到markdown编辑器，网上找了许多，有html的，但是捣鼓了半天发现无法使用NgModel绑定；也有angular写的模块，但是集成到项目后发现不是很漂亮。后来无意间在博客园中看到了一位网友推荐的markdown，打开后发现完美！漂亮！和我一直喜欢的CSDN的Markdown功能一样，后来才知道CSDN的也是用的该用例。那就是**Editor.md**编辑器。地址：https://pandao.github.io/editor.md/

![这就是整体效果](http://img.blog.csdn.net/20180103132451962?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbHhwdW1l/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

指令结构：
![这里写图片描述](http://img.blog.csdn.net/20180103142428843?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbHhwdW1l/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

详细代码自行查看

# 使用
找好了要使用的Markdown之后，开始集成到Angular中。于是就写了一个指令。**并且支持NgModel**

- 使用`npm`或者`yarn`安装`jquery`
  ```
  npm install jquery
  或者
  yarn add jquery
  ```
  
- 下载`editor.md`的的文件，并放置到assets文件夹中

- `.angular-cli.json`中配置`editor.md`的`css`和`js`
   ```
"styles": [
        "assets/editor.md/css/editormd.css",
        "styles.css"
      ],
      "scripts": [
        "../node_modules/jquery/dist/jquery.js",
        "assets/editor.md/editormd.min.js"
      ]
   ```

- `textarea`需要用到`FromsModule`记得添加，另外在`module`中添加`EditorMdDirective`指令

- 引入

  **Html**
   ```
   <div id="md" appEditorMd [editormdConfig]="conf" (onEditorChange)="syncModel($event)">
	  <textarea style="display: block;" [(ngModel)]="markdown"></textarea>
  </div>
   ```
   **Component**
   ```
   conf = new EditorConfig();
  markdown = '测试语句';

  // 同步属性内容
  syncModel(str): void {
	    this.markdown = str;
  }
   ```
   
以下是效果图：

![这里写图片描述](http://img.blog.csdn.net/20180103144038363?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbHhwdW1l/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

详细配置可参考官方[Editor.md](https://pandao.github.io/editor.md/)