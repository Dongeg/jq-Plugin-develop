# jq-Plugin-develop
jq开发插件常用的三个函数介绍

$.fn是指jquery的命名空间，加上fn上的方法及属性，会对jquery实例每一个有效。

如扩展$.fn.abc(),即$.fn.abc()是对jquery扩展了一个abc方法,那么后面你的每一个jquery实例都可以引用这个方法了.

那么你可以这样子：$("#div").abc(); 

jQuery为开发插件提拱了两个方法，分别是： 

jQuery.extend(object);为扩展jQuery类本身.为类添加新的方法。

jQuery.fn.extend(object);给jQuery对象添加方法。 
<h3>$.fn</h3>
fn是什么东西呢。查看jQuery代码，就不难发现。 

代码如下:
```javascript
jQuery.fn = jQuery.prototype ={ 
　　　init: function( selector, context ){//....　 
　　　//...... 
}; 
```
原来 jQuery.fn =jQuery.prototype.对prototype肯定不会陌生啦。 

jQuery便是一个封装得非常好的类，比如我们用语句　$("#btn1") 会生成一个 jQuery类的实例。 
<h3>$.extend</h3>
jQuery.extend(object);　为jQuery类添加添加类方法，可以理解为添加静态方法。如：

代码如下:

        $.extend({ 
        　　add:function(a,b){returna+b;} 
        }); 

便为　jQuery　添加一个为add　的　“静态方法”，之后便可以在引入 jQuery　的地方，使用这个方法了，

       $.add(3,4); //return 7 

<b>jQuery.fn.extend(object)</b>;对jQuery.prototype进得扩展，就是为jQuery类添加“成员函数”。jQuery类的实例可以使用这个“成员函数”。 

比如我们要开发一个插件，做一个特殊的编辑框，当它被点击时，便alert当前编辑框里的内容。可以这么做： 

jQuery代码

代码如下:

      $.fn.extend({ 
      
        alertWhileClick:function(){ 
          
              $(this).click(function(){ 
          
                      alert($(this).val()); 
          }); 
        } 
      }); 

<h3>jQuery.data() 方法</h3>
data() 方法向被选元素附加数据，或者从被选元素获取数据。

从被选元素中返回附加的数据。

语法

    $(selector).data(name)

name:	可选。规定要取回的数据的名称。如果没有规定名称，则该方法将以对象的形式从元素中返回所有存储的数据。

向被选元素附加数据。

语法

    $(selector).data(name,value)

name	必需。规定要设置的数据的名称。

value	必需。规定要设置的数据的值。

使用带有名称/值对的对象向被选元素添加数据。

语法

       $(selector).data(object)

object	必需。规定包含名称/值对的对象。
