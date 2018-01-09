# Augular5
# 1. AugularJS �� Augular2 ����?
>AugularJS ���Կ�����Augular 1.x, Augular2�ǵڶ����汾.����֮��û�й�ϵ,Ϊ��ȫ���������. ng2 ����Typescript ��д��.
# 2. Ϊʲôû��Angular3?
> ��Ϊ·��ģ�������ģ��෢��һ��,Ϊ�˰汾����!ֱ������3
# 3. Typescript �� JavaScript������?
> Typescript �� JavaScript�� ����! ���������͵�!
# 4. �ܹ�Ԥ��
* ���
* ģ��
* ģ��
* Ԫ����
* ���ݰ�
  * {{ȡֵ}}
  * [���԰�]
  * (�¼���)
  * [(˫���)]
* ����ע��
* ����
* ָ��
# 5. ����ָ��
* *ngIf �����ж�
* *ngFor ѭ�����
* [ngSwitch] *switchCase *switchDefault
* ngStyle �� ngClass
* �Զ���ָ�� directive
  * ���� `import { Directive, ElementRef } from '@angular/core';`
  * `@Directive({
selector: '[appHighlight]',
})`
  * `selector: '[appHighlight]'` ����д����ѡ����,�����CSS����jquery���÷�һ��! [����ѡ��] .class #id tag ; not()
  * `ElementRef`: ��ȡ��ʵ��DOM�ڵ�, `el.nativeElement `
  * `HostListener ` ���Լ�����ǰָ������Ԫ�ص��¼�
  * `@Input` ���嵱ǰ�������������, Ҳ����˵���ֵ�Ǵ�����ⲿ��ȡ, ������`React��Vue��props����`
# 6. �¼���
* ���԰� [url]="myUrl"
* �¼���(click)="handle()"
  * 1. �Զ����¼� (myClick)="handle()" [�����]
  * 2. ���������Ȩ��: `EventEmitter �� @Output`
  * 3. `@output() myClick = new EventEmitter()`;
  * 4. �����¼�: emit `this.myClick.emit()`
* ˫���[()]
  * ��ʽ: `[(fontSize)]="size"`��Ч�� `[fontSize]="size" (fontSizeChange)="size = $event"`
* NgModel ���е�˫�����ݰ�
  * �÷�: [(NgModel)] = "name"
  * ע��: �ڸ�ģ������ `FormsModule`
  # 7. @Input �� @Output ����
> @Input ������ⲿ��ȡ����, @Output�����������¼�
> ��������Ϊ�ⲿ����ı������п��ܸ��ڲ���ͬ��,�ᷢ������,���Կ����Զ��ڲ�ʹ������.
## 7.1 @Input
  * @Input(�ⲿ������) �ڲ�ʹ������
  * inputs:['�ڲ�ʹ������: �ⲿ��������']
## 7.2 @Output
  * @Output(�ⲿ������) �ڲ�ʹ������
  * outputs:['�ڲ�ʹ������: �ⲿ��������']
# 8. ģ�����ñ��� #var
> ��һ��DOMԪ���ϼ�һ����������,���Դ�ָ��Ƭ��. ������React�е�ref.
## 8.1 �÷�
  * #���� ����.value ��ȡ����ֵ
  * ref-����`ȫд`,�÷�һ��
# 9. ��ȫ������ ?.
> ��ֹȡһ���ն��������ֵʱ����,����view���ز�����.ʹ�ð�ȫ������?.���Ա��ⱨ��.
# 10.Typescript
> JS��һ������,֧�ֱ����ͷ���ӵ���Լ�����������.
* �������:  `string` `number` `boolean` `Array` `enum` `any`
* �������: `let name: string = 'Tim'`
* ���巽��: 
```
function fn(age: number): number{
  return 12;
  return '12';//����
}
function fn(age: number): void{
  //����û�з���ֵ
}
```
# 11. ��
> ����Ҫ�ָ���, ����: ģ�������� �� ��Ӧʽ������.
## 11.1 ��ȡ�û�����(3��)
* �¼���ȡ$event,����ֵ�ܼ�����Ԫ�ص��¼�
* ģ�������ȡ#var.value
* ˫�����ݰ�[(ngModel)]
## 11.2 �¼����η�
�����¼�����������: (keyup.enter)="" ����ֻ����enter��̧��ʱ����.
## 11.3 class����Ӧ���ݱ仯
״̬	|Ϊ��ʱ�� |CSS ��	|Ϊ��ʱ�� CSS ��
---|---|---|---|
�ؼ������ʹ�	|ng-touched	|ng-untouched
�ؼ���ֵ�仯��	|ng-dirty	|ng-pristine
�ؼ���ֵ��Ч	|ng-valid	|ng-invalid
## 11.4 ģ��У��
> ��һ���������˫�����ݰ�[(ngModel)] �� #var ,Ȼ��������ϵ���� #var="ngModel".��ô�Ϳ���ͨ��ģ�������ȡУ����Ϣ.
* `valid` `invalid` `dirty` `touched` `errors`
## 11.5 ���ύ
> ��`form`��ǩ��ʹ��`(ngSubmit)="�¼�����"` ���ر��ύ����.
## 11.6 ��Ӧʽ��У��
> ����У���ģ�����
* ����`ReactiveFormsModule`
* ���`[formGroup]="myGroup"`
* �޸� 
```
<input type="text" 
[(ngModel)]="user.name" 
name="name" 
required 
minlength="4">
```
Ϊ
```
<input type="text" 
name="name" 
formControlName="name">
```
ֻ����һ��`formControlName`
* ������д���FormGroup
```
myGroup: FormGroup;//ָ������ΪFormGroup
  
  ngOnInit() {
    //���Ĳ� ��ʼ�� FormGroup
    this.myGroup = new FormGroup({
      // ���岽 ��ʼ��һ�����������
      myAge: new FormControl(this.user.age,[
        //������ ��������У��
        Validators.required,//����
        Validators.minLength(4), //��С����4
        forbidenNameValiator(/lala/i)
      ])
    });
  }

```
## 11.7 �Զ����У��
```
function forbiddenNameValidator(nameReg: RegExp): ValidatorFn{
return (control: AbstractControl): {[key: string]: any} =>{
const forbidden = nameReg.test(control.value);
return forbidden ? {'forbiddenName': {value: control.value}} : null;
}
}
```
ʹ�÷�ʽ: ���� `FormC 