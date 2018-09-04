# Butterknife的使用简介

### 简介
  Butterknife 和 Dragger都是编译期间生成代码。
 > ##### 1、Butterknife主要用于围绕view的资源绑定。
 > ##### 2、Dragger主要用于业务框架代码注入。
 
 Butterknife因为是编译生成代码而不是通过反射注入，所以性能上没有什么损耗。
 
 ### 代码配置
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
