<h2>jq插件开发方式</h2>
<h3>闭包</h3>

    (function($){
        //do sth
    })(jquery);

闭包的作用

避免全局依赖

避免第三方破坏

兼容jQuery操作符"$"和jQuery

<h3>开发方式</h3>
<h4>类级别的开发</h4>
即给jQuery命名空间下添加新的全局函数，也称为静态方法

    jQuery.myPiugn=function(){
        //do sth
    };
    例如$.ajax()  $.extend()
    
<h4>对象级别的组件开发</h4>
即挂在jQuery原型下的方法，这样通过选择器获取的jQuery对象也能共享该方法，也称为动态方法

    $.fn.myPlugin=function(){
        //do sth
    };
    //$.fn===$.prototype

例如：addClass(),attr()等，需要创建实例来调用













