---
layout: post
title: 'What is the Fragment'
date: 2017-03-21
author: Jay
tags: Android
---

Android在Android 3.0（API级别11）中引入了`Fragment`，主要用于在平板等大屏幕上支持更加动态和灵活的UI设计。由于平板电脑的屏幕比手机的屏幕大得多，因此有更多空间可以组合和交换UI组件。`Fragment`允许这样的设计，而无需您管理视图层次结构的复杂变化。通过将`Activity`的布局划分为`Fragment`，您可以在运行时修改`Activity`的外观，并将这些更改保留在`Activity`管理的后端堆栈中。

## Activity与Fragment是什么关系？