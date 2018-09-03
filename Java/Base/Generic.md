# Java中`<? extends T>` 和 `<? super T>` 的理解

>* `<? extends T>`表示类型上界， 说明类型是T或者是T的子类；
>* `<? super T>`  表示类型的下界，说明类型是T或者T的父类，直至Object；

上界<? extends T>不能往里存，只能往外取.

下界<? super T>

PECS原则
最后看一下什么是PECS（Producer Extends Consumer Super）原则，已经很好理解了：

频繁往外读取内容的，适合用上界Extends。
经常往里插入的，适合用下界Super。
总结
extends 可用于返回类型限定，不能用于参数类型限定（换句话说：? extends xxx 只能用于方法返回类型限定，jdk能够确定此类的最小继承边界为xxx，只要是这个类的父类都能接收，但是传入参数无法确定具体类型，只能接受null的传入）。
super 可用于参数类型限定，不能用于返回类型限定（换句话说：? supper xxx 只能用于方法传参，因为jdk能够确定传入为xxx的子类，返回只能用Object类接收）。
? 既不能用于方法参数传入，也不能用于方法返回。
