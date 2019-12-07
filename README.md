# V2

> A valuable technology object.


# ʹ��˵��

## ��ʽ���ַ�����һ��
> ##### ֱ��ʹ���ַ�����.�������ķ�ʽ��ʽ���ַ�����
---
    String.format(...args��any[]) ��  String.format(arg:ArrayLike); ��  String.format(arg:any);
----

#### ��ʽ����׼��\{N\}
    ˵����`N`������������±ꡣ

#### ����:
``` js
    var x = "{0}��һ��{2}�ġ�����{1}������ǰ�˿�ܡ�".format("v2","����","������Ч");
    // => v2��һ��������Ч�ġ��������̿�����ǰ�˿�ܡ�
    var y = "{0}��һ��{2}�ġ�����{1}������ǰ�˿�ܡ�".format(["v2","����","������Ч"]);
    // => v2��һ��������Ч�ġ��������̿�����ǰ�˿�ܡ�
```

## ��ʽ���ַ���������
> ##### ֱ��ʹ���ַ�����.�������ķ�ʽ��ʽ���ַ�����
>> ��������ַ�������ϵӳ�䡣

---
    String.withCb(obj:Object);
----
#### ��ʽ����׼���� \`$\{Expression\}\` �� �� \{\{Expression\}\}

˵��: Expression �ǲ���JSON�����Ի��������㡣���ʽ֧�֡�?.����`�ǿ���̽��`��֧��`��Ŀ�ϲ������`������"?"��"!"����һ�λ����Σ�

ע�������ʽ �� ֧�� if/else/for �Լ�`$`�������$"{SimpleExpression}"�����ʽ��SimpleExpression���ᱻ���㣩��

+ �ǿ���̽��:
  * x?.y ��ʾ x Ϊ **NULL** ʱ������ x �����򷵻� x.y ��ֵ��
  
+ ��Ŀ�ϲ������:
  * \{x?y\} ��ʾ x Ϊ **��** ʱ������ y ��ֵ��������ʽ���ؿ��ַ�����
  * \{x!y\} ��ʾ x Ϊ **��** ʱ������ y ��ֵ��������ʽ���ؿ��ַ�����
  * \{x??y\} ��ʾ x Ϊ **NULL** ʱ������ y ��ֵ�����򷵻� x ��ֵ�� 
  * \{x?!y\} ��ʾ x Ϊ **��** �� y Ϊ **��** ʱ������ x ��ֵ�����򷵻� y ��ֵ��
  * \{x!?y\} ��ʾ x Ϊ **��** �� y Ϊ **��** ʱ������ x ��ֵ�����򷵻� y ��ֵ��
  * \{x!!y\} ��ʾ x Ϊ **��** �� y Ϊ **��** ʱ������ x ��ֵ�����򷵻� y ��ֵ��

#### ����:
``` js
    var x = "{{name}}��һ��`${description}`�ġ�����{{mode}}������ǰ�˿�ܡ�".withCb({ name: "v2", description: "������Ч", mode: "����" });
    // => v2��һ��������Ч�ġ��������̿�����ǰ�˿�ܡ�
    var y = "`${for(var item<index> in x?.cc[0]){ return $'��{index}����{item};'; }}`".withCb({ x: { cc: { 0: [1, 2, 3] } } });
    // => ��0����1;��1����2;��2����3;
```

#### HTMLת�롣
> ##### ֱ��ʹ���ַ�����.�������ķ�ʽ���ַ���תΪ**HTML**�ַ�����
---
    String.htmlCoding();
----

˵�����﷨����� **ZenCoding** �� **Emmet**��

#### ����:
``` js
    var html = 'form.form>label.control-label[for="form-1-name"]>span.control-stamp{*}+span{����}'.htmlCoding();
    // => <form class="form"><label class="control-label" for="form-1-name"><span class="control-stamp">*</span><span>����</span></label></form>
```

#### �ؼ�ʹ�á�
> ##### ע��ؼ���
---
    v2.use(tag:string,option:Object);
----

* ��ʹ�� **v2(tag:string[,option:Object]):V2Contrl** ����ʹ�����õĿؼ���
* ��ʹ�� **v2.useMap(tag:string,flowGraph:Object):void** ���ó����������̡�
* Ĭ���������̡�
    + ���캯��������ؼ����ԡ�
    + design����ƺ͹滮������������Ҫʹ�õ����ԡ�
    + init����ʼ�����������ؼ���
    + build������HTML���롣
    + render����ȾHTML��
    + usb���������Լ�����
    + ready���ؼ����ؾ�����
    + ajax���첽�������ݣ��� **access** Ϊ **��** ʱ���� **ajax** ���̣���
    + load������ҳ�����ݡ�
    + commit����ҳ�潻���¼���
* �ɸ��� **v2.useMvc(tag:string,resolve:()=>V2Control):V2Control** ��������ӿؼ�ִ��ǰ��ִ�к����߼���
* ��ʹ�� **v2.route(tag:string,route-tag:string):void** ����tag���ؼ�ʹ�á�route-tag���ؼ�ʵ�֡�
* ��ʹ�� **v2.use(option:Object)** ע�����пؼ���Ĭ�����Ի򷽷���
* ��ʹ�� **v2.useCards(letter:char,{type:string,exec:(control:V2Contrl,value:V2Contrl[K],key:K)=>any})**�������ͨ����� ͨ������ڷ�������ǰ����ָ�����ţ���������ʱ����������ͬ�������Ƶ�����ֵ����ͨ�������ʱ����ͨ���ָ����������
    + ? ��ֵΪ **\{boolean\}** ʱ��ִ�з�����
    + % ��ֵΪ **\{number\}** ʱ��ִ�з�����
    + " �� ' ��ֵΪ **\{string\}** ʱ��ִ�з�����
    + < ��ֵΪ **\{Date\}** ʱ��ִ�з�����
    + [ ��ֵΪ **\{Array\}** ʱ��ִ�з�����
    + / ��ֵΪ **\{Regex\}** ʱ��ִ�з�����
    + \* ʼ��ִ�з�����
    + ��֧�֡�&������!������.������{������#����ͨ�����
* ֧������ע�롣
    
#### ����:
``` js
    // ���塣
    v2.use('wait', {
        wait: function () { // ���캯�����ɿؼ�ʱ���á�
            /** ��� */
            this.style = 1;
        },
        "render(style)": function (style) { // ����ע�롾style�����ԡ�
            if(style === this.style){
                this.$.classList.add('wait');
            }
        },
        build: function () {
            this.$backdrop = this.$.appendChild(".wait-backdrop".htmlCoding().html());
            this.$wait = this.$.appendChild(".wait-reveal>.shape.shape$*4".htmlCoding().html());
        },
        usb: function () {
            this.base.usb();
            this.define("style", function (style, oldStyle) {
                this.$wait.classList.remove('animation-' + oldStyle);
                this.$wait.classList.add('animation-' + style);
            });
        }
    });

    // ʹ�á�
    var wait = v2("wait", { style: 2 });
```

#### ��̬���ɵ�HTML:

``` html
    <div class="wait">
        <div class="wait-backdrop"></div>
        <div class="wait-reveal animation-6">
            <div class="shape shape1"></div>
            <div class="shape shape2"></div>
            <div class="shape shape3"></div>
            <div class="shape shape4"></div>
        </div>
    </div>
```
