---
layout:     post
title:      ACC 示例
subtitle:   ACC 示例
date:       2023-08-05
author:     Valuex
header-img: 
catalog: 	 true
tags:
    - AutoHotKey
---

# Get Element's role text under cursor
``` autohotkey
#include ACC.ahk

obj_Element:=  Acc.ElementFromPoint()
Elm_RoleText:=obj_Element.RoleText
msgbox Elm_RoleText
```
