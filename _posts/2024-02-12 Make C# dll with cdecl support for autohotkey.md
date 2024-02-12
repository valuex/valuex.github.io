The original post is here.
https://gist.github.com/ProjectEli/8d5dd08f67080cafb7dc5cb29f5eefb3

# Why this gist needs?
Autohotkey library supports ```DllCall()``` and it can call dll with standard ```decl``` feature of c dll. However, typical c# library runs on ```IL``` and cannot be called from autohotkey. To support standard dll call, ```DllExport``` package is required in Visual Studio.

# Step by step
## 1. Create C# .Net framework library project in Visual studio
![1](https://github.com/valuex/valuex.github.io/assets/3627812/13c50d19-61ad-4533-8b43-48ebf5b34e0d)


## 2. Set ```projectName```
The name will be automatically set to the namespace.
![image](https://user-images.githubusercontent.com/16854214/156904773-866da468-c184-4be8-8607-795c6f64468b.png)

## 3. Open ```Nuget Package manager``` by right click on your project name
![3](https://github.com/valuex/valuex.github.io/assets/3627812/dbda0ee8-f9fa-4871-b91f-4ee17e5ca020)


## 4. Install  ```DllExport``` package
![4-1](https://github.com/valuex/valuex.github.io/assets/3627812/f518d115-99d5-4cac-a2aa-44dfdd70b9f1)

## 5. Select install checkbox and click apply button of ```DllExport``` package configuration window
make sure that namespace is the same as your project's namespace
![4](https://github.com/valuex/valuex.github.io/assets/3627812/b4d4254a-de0b-4fbc-83b3-5add5127a1fc)



## 6. Click ```Reload all``` in VS

![6](https://github.com/valuex/valuex.github.io/assets/3627812/0367b3aa-8fc4-48df-b37a-43d90ee71357)

## 6. Write some function in your main file, and add ```[DllExport]``` on top of the function definition
Custom function should be ```statc```, to be exported using ```DllExport```, or it emits error during build process
```c#
// class1.cs
namespace myDll
{
    public class Class1 // this class name doesn't matter
    {
        [DllExport]
        public static double mySum(double x, double y)
        {
            return x + y;
        }
    }
}
```

## 7. Change build profile to release and build it
![7](https://github.com/valuex/valuex.github.io/assets/3627812/1f516227-b98d-466a-b86e-c06647e0da82)

Note1:  ** make sure that the dll is builded with 32-bit or 64-bit, this depends on your final applcation **  
Note2： if there is an error like below when compiling, un-install the previous **DllExport** and re-install it.  
```
Severity Code Description Project File Line Suppression State Error CS0246 The type or namespace name 'DllExportAttribute' could not be found
```

## 8. Get dll file in the release folder
You can check path of resulting dll file at console output.

![8](https://github.com/valuex/valuex.github.io/assets/3627812/4e999c6f-135e-4255-a04b-df1f0dd92b48)


***If you are in x64 machine, get dll file in the x64 folder!!***
ex:
```
C:\Users\Eli\Downloads\EliDll\myDll\myDll\bin\Release\x64\myDll.dll
```
![image](https://user-images.githubusercontent.com/16854214/156905449-31c27007-e120-4a33-a239-b9cef2bde841.png)

## 9. Move dll file to your autohotkey folder and make ahk file that calls dll file
```ahk
; main.ahk
; This file calls mysum function in myDll.dll
; and put double 5 and double 4 as input args and get output with double type.
; Be careful of case-sensitive function name and arg type
; See more info about syntax at https://www.autohotkey.com/docs/commands/DllCall.htm
result:=DllCall("myDll.dll\mySum", "Double", 5, "Double", 4,"Double")
MsgBox result
```

![9](https://github.com/valuex/valuex.github.io/assets/3627812/b0234f8f-9dd7-4eb0-8cb4-d57190321671)


## 10. Excute ahk file and see result
![10](https://github.com/valuex/valuex.github.io/assets/3627812/0d159500-6e8e-4fbc-aa89-a1b076693621)



# References
- https://www.autohotkey.com/docs/commands/DllCall.htm
- https://s-engineer.tistory.com/318
- https://docs.microsoft.com/en-us/cpp/build/exporting-from-a-dll-using-declspec-dllexport?view=msvc-170
