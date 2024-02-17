
# wxl 扩展
## pdf
使用TCSumatraPDF
1. 在`sumatrapdf.ini` 中配置`SumatraPDF.exe` 所在位置
2. 在`SumatraPDF.exe` 同级目录下的`SumatraPDF-settings.txt` 中进行对`SumatraPDF.exe`的设置，比如不显示书签 `ShowToc=flase`
## 网页文件
使用 EdgeViewer, 在`edgeviewer.ini` 中配置文件扩展名
``` ini
[Extensions]
; should be uppercase to form the right detect string
HTML=SVG,HTM,HTML,XML
Markdown=MD,MARKDOWN
AsciiDoc=ADOC,ASCIIDOC
URL=URL
MHTML=MHT,MHTML
```
