
# 1 在VS中编译程序，关闭OneNote  
![image](https://github.com/valuex/valuex.github.io/assets/3627812/ebdf9809-bc77-4205-8e47-114497e667a9)

# 2 安装编译好的扩展，此时保持OneNote 关闭
![image](https://github.com/valuex/valuex.github.io/assets/3627812/3d5aec73-1464-41f8-befe-4fc19111e104)

# 3 启动OneNote, 进入VS调试模式 
VS: Debug -> Attach to Process	Open  
		![image](https://github.com/valuex/valuex.github.io/assets/3627812/d87e67ab-0b54-4890-87cf-980d297d616b)  
# 4  在VS中将扩展挂载到dllhost.exe上
attach to a DllHost.exe having "Managed {.NET version}" in the Type column of the Attach to Process dialog.    
![image](https://github.com/valuex/valuex.github.io/assets/3627812/3598979b-7eb9-482d-99db-6b761e0129b9)

# 5 在VS中设置断点，在OneNote 中启动扩展，愉快的开始调试吧

