---
layout: post
title: 'What is the Fragment'
date: 2017-03-21
author: Jay
tags: Android
---

Android在Android 3.0（API级别11）中引入了`Fragment`，主要用于在平板等大屏幕上支持更加动态和灵活的UI设计。
由于平板电脑的屏幕比手机的屏幕大得多，因此有更多空间可以组合和交换UI组件。
`Fragment`允许这样的设计，而无需您管理视图层次结构的复杂变化。通过将`Activity`的布局划分为`Fragment`，
您可以在运行时修改`Activity`的外观，并将这些更改保留在`Activity`管理的后端堆栈中。

>由于现在开发都是使用 support-v4 包中的 Fragment 进行开发，下面提到的源码将会以 support-v4 为主

## Activity与Fragment是什么关系？
使用 Fragment 必须要依附于 Activity，查看 Activity 源码可以发现，Activity 中有一个名叫`FragmentController`类：
>这里我们查看的是 support-v4 包中的 FragmentActivity 源码
```java
public class FragmentActivity extends BaseFragmentActivityApi16 {
    ......
    final FragmentController mFragments = FragmentController.createController(new HostCallbacks());
    ......
}
```
上面代码片段中我们可以发现有一个`FragmentController`，从类名就可以猜出，这是一个 Fragment 控制器，这里我们不深究，
但基本可以确定，在 Activity 中是有这么一个专门用于管理 Fragment 的实例，而 Fragment 的生命周期方法也是由这个`FragmentController`回调的。
而 FragmentController 实现对象会在相应的 Activity 相应的方法中去回调 Fragment 的生命周期方法。

## Fragment为何物？
要了解 Fragment 是什么，我们先看看 Fragment 类的实现，上代码：
```java
public class Fragment implements ComponentCallbacks2, OnCreateContextMenuListener {
    ......
}
```
可以看出 Fragment 并不是 View，而我们一般用到 Fragment 时，都会重写`onCreateView`方法并返回一个 View 对象，
那这个返回的 View 去哪里了？
