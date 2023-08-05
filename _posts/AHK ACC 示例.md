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

# Element 的属性
包括以下内容，详见`ACC.ahk` 中 `IAccessible element properties` 这个部分的内容。
```
      Name                
      Value               
      Role                
      RoleText            
      Help                
      KeyboardShortcut    
      State               
      StateText           
      Description         
      DefaultAction       
      Focus               
                          
      Selection           
      Parent              
      IsChild             
      Length              
      Location            
      Children            
      Exists              
      ControlID           
      WinID               
      accessible          
      childId             
```
