<h1>props.ok?.() 报错</h1>
<div align="center">
<img src="./img/01props报错.png" width=35% />
</div>
报错


解决办法： 

不要用太新的语法

二、rollup -c 报错 error: Unexpected "<" 

image.png
解决办法： 
1、下载我的最终版 package.json（不是 commit 里的 package.json，而是当前视频结束时提供的最终里的 package.json）
2、覆盖你的 package.json，注意文件内的 name 你要自己改一下
3、 yarn install 
4、 rollup -c 
bug 就会消失。 

三、Invalid VNode type: Symbol(Comment) 解决办法 

报错截图

解决办法：  
要解决这个问题很简单，请把和组件库运行时无关的依赖移至 devDependencies 和 peerDependencies。  也就是说， 
1、打开你的轮子项目的 package.json
2、看看 dependencies 里面有没有 vue，有的话就移到 devDependencies 里
3、重新 publish 你的轮子库，bug 就消除了
相关讨论： 

截图

四、sass 报错解决办法 

image.png

解决办法: 
1、打开 package.json
2、把 dependencies 里的 sass 这一行，移到 devDependencies  

image.png
3、重新运行  yarn install  或者  npm install  即可

五、VSCode 报错解决办法 
报 vue/valid-template-root 错误 

image.png
这个错是因为 VSCode 的 Vetur 插件还没支持 Vue 3，解决办法是在 VSCode 配置里添加一行 "vetur.validation.template": false, 来关闭检查。

报 'X.vue' is not a module. Vetur(2306) 错误 


image.png

解决方法是在 X.vue 中添加一个 <script> 即可，内容如下： 
<script>
export default {}
</script>
只要有一个默认导出，Vetur 就不会报错了，是不是很傻…… 

六、WebStorm 报错解决办法 
TypeScript 配置 
1、全局安装 typescript： yarn global add typescript 
2、在项目根目录运行： tsc --init  就可以得到 tsconfig.json
3、把 tsconfig.json 的内容改为如下内容： 
 {
     "compilerOptions": {
         "target": "esnext",
         "module": "esnext",
         "strict": false,
         "jsx": "preserve",
         "moduleResolution": "node"
     }
 }
这样就配置好了 TypeScript。 

七、不想总是打开 shims-vue.d.ts 来解决 TS 报错? 
那么你可以在项目跟目录创建一个 tsconfig.json 文件，文件内容为： 
{
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "strict": false,
    "jsx": "preserve",
    "moduleResolution": "node"
  }
}
也许就不用再打开 shims-vue.d.ts 了。 

八、TS1192: Module '"fs"' has no default export. 
把 
import  fs from 'fs'; 
改为 
import * as fs from 'fs';




