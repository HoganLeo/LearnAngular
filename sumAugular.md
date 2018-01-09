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
  # 7. @Input 和 @Output 别名
> @Input 代表从外部获取数据, @Output代表对外输出事件
> 别名是因为外部传入的变量名有可能跟内部的同名,会发生覆盖,所以可以自定内部使用名称.
## 7.1 @Input
  * @Input(外部公开名) 内部使用名称
  * inputs:['内部使用名称: 外部公开名称']
## 7.2 @Output
  * @Output(外部公开名) 内部使用名称
  * outputs:['内部使用名称: 外部公开名称']
# 8. 模板引用变量 #var
> 在一个DOM元素上加一个引用名称,可以代指该片段. 类似于React中的ref.
## 8.1 用法
  * #名称 名称.value 获取表单的值
  * ref-名称`全写`,用法一致
# 9. 安全导航符 ?.
> 防止取一个空对象的属性值时报错,导致view加载不出来.使用安全导航符?.可以避免报错.
# 10.Typescript
> JS的一个超集,支持变量和方法拥有自己的数据类型.
* 定义变量:  `string` `number` `boolean` `Array` `enum` `any`
* 定义变量: `let name: string = 'Tim'`
* 定义方法: 
```
function fn(age: number): number{
  return 12;
  return '12';//报错
}
function fn(age: number): void{
  //代表没有返回值
}
```
# 11. 表单
> 既重要又复杂, 两种: 模板驱动表单 和 响应式驱动表单.
## 11.1 获取用户输入(3种)
* 事件获取$event,但是值能监听表单元素的事件
* 模板变量获取#var.value
* 双向数据绑定[(ngModel)]
## 11.2 事件修饰符
修饰事件发生的条件: (keyup.enter)="" 代表只能在enter键抬起时触发.
## 11.3 class类响应数据变化
状态	|为真时的 |CSS 类	|为假时的 CSS 类
---|---|---|---|
控件被访问过	|ng-touched	|ng-untouched
控件的值变化了	|ng-dirty	|ng-pristine
控件的值有效	|ng-valid	|ng-invalid
## 11.4 模板校验
> 在一个表单上添加双向数据绑定[(ngModel)] 和 #var ,然后两者联系起来 #var="ngModel".那么就可以通过模板变量获取校验信息.
* `valid` `invalid` `dirty` `touched` `errors`
## 11.5 表单提交
> 在`form`标签上使用`(ngSubmit)="事件方法"` 拦截表单提交请求.
## 11.6 响应式表单校验
> 数据校验和模板分离
* 依赖`ReactiveFormsModule`
* 添加`[formGroup]="myGroup"`
* 修改 
```
<input type="text" 
[(ngModel)]="user.name" 
name="name" 
required 
minlength="4">
```
为
```
<input type="text" 
name="name" 
formControlName="name">
```
只留下一个`formControlName`
* 在组件中创建FormGroup
```
myGroup: FormGroup;//指定类型为FormGroup
  
  ngOnInit() {
    //第四步 初始化 FormGroup
    this.myGroup = new FormGroup({
      // 第五步 初始化一个表单控制组件
      myAge: new FormControl(this.user.age,[
        //第六步 配置内置校验
        Validators.required,//必输
        Validators.minLength(4), //最小长度4
        forbidenNameValiator(/lala/i)
      ])
    });
  }

```
## 11.7 自定义表单校验
```
function forbiddenNameValidator(nameReg: RegExp): ValidatorFn{
return (control: AbstractControl): {[key: string]: any} =>{
const forbidden = nameReg.test(control.value);
return forbidden ? {'forbiddenName': {value: control.value}} : null;
}
}
```
使用方式: 放在 `FormC 