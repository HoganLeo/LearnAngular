# Augular5
# 1. AugularJS 和 Augular2 区别?
>AugularJS 可以看成是Augular 1.x, Augular2是第二个版本.他们之间没有关系,为完全是两个框架. ng2 是用Typescript 编写的.
# 2. 为什么没有Angular3?
> 因为路由模块比其他模块多发布一次,为了版本对齐!直接跳过3
# 3. Typescript 和 JavaScript的区别?
> Typescript 是 JavaScript的 超集! 他是有类型的!
# 4. 架构预览
* 组件
* 模块
* 模板
* 元数据
* 数据绑定
  * {{取值}}
  * [属性绑定]
  * (事件绑定)
  * [(双向绑定)]
* 依赖注入
* 服务
* 指令
# 5. 内置指令
* *ngIf 条件判断
* *ngFor 循环输出
* [ngSwitch] *switchCase *switchDefault
* ngStyle 和 ngClass
* 自定义指令 directive
  * 引入 `import { Directive, ElementRef } from '@angular/core';`
  * `@Directive({
selector: '[appHighlight]',
})`
  * `selector: '[appHighlight]'` 这里写的是选择器,规则和CSS或者jquery的用法一样! [属性选择] .class #id tag ; not()
  * `ElementRef`: 获取真实的DOM节点, `el.nativeElement `
  * `HostListener ` 可以监听当前指令所在元素的事件
  * `@Input` 定义当前组件的输入属性, 也就是说这个值是从组件外部获取, 类似于`React和Vue的props属性`
# 6. 事件绑定
* 属性绑定 [url]="myUrl"
* 事件绑定(click)="handle()"
  * 1. 自定义事件 (myClick)="handle()" [父组件]
  * 2. 子组件接收权限: `EventEmitter 和 @Output`
  * 3. `@output() myClick = new EventEmitter()`;
  * 4. 触发事件: emit `this.myClick.emit()`
* 双向绑定[()]
  * 形式: `[(fontSize)]="size"`等效于 `[fontSize]="size" (fontSizeChange)="size = $event"`
* NgModel 表单中的双向数据绑定
  * 用法: [(NgModel)] = "name"
  * 注意: 在根模块引入 `FormsModule`