# Butterknife的使用简介

### ButterKnife项目地址：
```
https://github.com/JakeWharton/butterknife
```
### 简介
  Butterknife 和 Dragger都是编译期间生成代码, 实现代码的解耦。
 > ##### 1、Butterknife主要用于围绕view的资源绑定。
 > ##### 2、Dragger主要用于业务框架代码注入。
 
 Butterknife因为是编译生成代码而不是通过反射注入，所以性能上没有什么损耗。
 > 绑定View、资源、事件、获取多个view.
 
 ### 环境配置
 >* step1: 在Project的 build.gradle 中添加代码
 ```gradle
 buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        ...
        classpath 'com.jakewharton:butterknife-gradle-plugin:8.8.1'  //添加这一行
   }
 }
```

>* step2: dependencies中添加
 ```gradle
 compile 'com.jakewharton:butterknife:8.8.1'
 annotationProcessor 'com.jakewharton:butterknife-compiler:8.8.1'
 ```

### 使用心得与注意事项

 > 1、在Activity 类中绑定 ：**ButterKnife.bind(this);** 必须在**setContentView();** 之后绑定；
 >  且父类bind绑定后，子类不需要再bind。

 > 2、在非Activity 类（eg：Fragment、ViewHold）中绑定： ButterKnife.bind(**this，view**);
 >   这里的**this**不能替换成getActivity（）。

 > 3、在Activity中不需要做解绑操作，在Fragment 中必须在onDestroyView()中做解绑操作。

 > 4、使用**ButterKnife** 修饰的方法和控件，不能用private or static 修饰，否则会报错。
   错误: @BindView fields must not be private or static. (com.lxl.test.ButterknifeActivity.icon)

 > 5、setContentView()不能通过注解实现。（其他的有些注解框架可以）

 > 6、使用Activity为根视图绑定任意对象时，如果你使用类似MVC的设计模式你可以在Activity 
   调用ButterKnife.bind(this, activity)，来绑定Controller。

 > 7、使用ButterKnife.bind(this，view)绑定一个view的子节点字段。如果你在子View的布局里或者自定义view的构造方法里 使用了inflate,
   你可以立刻调用此方法。或者，从XML inflate来的自定义view类型可以在onFinishInflate回调方法中使用它。
   
   ### Butterknife插件：zelezny
   > 工具栏File 找到Settings…或者使用快捷点Ctrl+Alt+s 打开。搜索zelezny下载插件并安装，重启Android Studio
   
   ### Butterknife插件：zelezny
> @BindView—->绑定一个view；id为一个view 变量

> @BindViews —-> 绑定多个view；id为一个view的list变量

> @BindArray—-> 绑定string里面array数组；@BindArray(R.array.city ) String[] citys ;

> @BindBitmap—->绑定图片资源为Bitmap；@BindBitmap( R.mipmap.wifi ) Bitmap bitmap;

> @BindBool —->绑定boolean值

> @BindColor —->绑定color；@BindColor(R.color.colorAccent) int black;

> @BindDimen —->绑定Dimen；@BindDimen(R.dimen.borth_width) int mBorderWidth;

> @BindDrawable —-> 绑定Drawable；@BindDrawable(R.drawable.test_pic) Drawable mTestPic;

> @BindFloat —->绑定float

> @BindInt —->绑定int

> @BindString —->绑定一个String id为一个String变量；@BindString( R.string.app_name ) String meg;

> @OnClick—->点击事件

> @OnCheckedChanged —->选中，取消选中

> @OnEditorAction —->软键盘的功能键

> @OnFocusChange —->焦点改变

> @OnItemClick item—->被点击(注意这里有坑，如果item里面有Button等这些有点击的控件事件的，需要设置这些控件属性focusable为false)

> @OnItemLongClick item—->长按(返回真可以拦截onItemClick)

> @OnItemSelected —->item被选择事件

> @OnLongClick —->长按事件

> @OnPageChange —->页面改变事件

> @OnTextChanged —->EditText里面的文本变化事件

> @OnTouch —->触摸事件

> @Optional —->选择性注入，如果当前对象不存在，就会抛出一个异常，为了压制这个异常，可以在变量或者方法上加入一下注解,让注入变成选择性的,如果目标View存在,则注入, 不存在,则什么事情都不做


