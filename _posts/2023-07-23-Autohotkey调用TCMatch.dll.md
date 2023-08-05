---
layout:     post
title:      Autohotkey 调用 TCMatch.dll
subtitle:   Autohotkey V2
date:       2023-07-23
author:     Valuex
header-img: 
catalog: 	 true
tags:
    - AutoHotKey
---
# Autohotkey 调用 TCMatch.dll 
需要将需要将 tcmatch.ini, tcmatch64.dll, tcmatch.tbl  放到一起
```autohotkey
TCMatchPath:=A_ScriptDir . "\TCMatch\tcmatch64.dll"
g_TCMatchModule := DllCall("LoadLibrary", "Str", TCMatchDllPath, "Ptr")

a:= TCMatch("TCMatch.dll教师节快乐","j j")
msgbox a 
DllCall("FreeLibrary", "Ptr", g_TCMatchModule)  ; free memory
g_TCMatchModule := ""
return

TCMatch(aHaystack, aNeedle)
{
    if (A_PtrSize == 8)
    {
        return DllCall("TCMatch64\MatchFileW", "WStr", aNeedle, "WStr", aHaystack)
    }

    return DllCall("TCMatch\MatchFileW", "WStr", aNeedle, "WStr", aHaystack)
}
```
# tcmatch.tbl 说明
tcmatch.tbl 是码表，记录了汉字和拼音之间的对应关系
码表构造：
https://xbeta.info/tc-pinyin-quicksearch.htm
# TCMatch.ini 说明
来自 https://github.com/goreliu/runz
```ini
[general]
simple_search_activate_char=
; 简单搜索前导符号
regex_search_activate_char=?
; 正则搜索前导符号
leven_search_activate_char=<
srch_activate_char=*
preset_activate_char=>
; 加载搜索模版前导符号
simple_search_match_beginning_activate_char=^
and_separator_char=" "
; 与 关系符号
or_separator_char=|
; 或 关系符号
wdx_separator_char=/
negate_char=!
case_sensitive=0
; 大小写敏感
allow_empty_result=0
filter_files_and_folders=3
match_beginning=0
; 从第几个字符开始匹配
use_pinyin=1
; 使用中文
use_korean=0
; 使用韩文
[gui]
override_search=1
invert_result=0
one_line_gui=1
show_presets=0
[presets]
e=.exe|.bat|.com|.scr|.lnk
; 搜索模版，输入 >e 即可搜索对应字符串
[replace]
chars1=》|>
; 搜索前先替换字符，可用于中文输入法没切换的情况
chars2=？|?
```
