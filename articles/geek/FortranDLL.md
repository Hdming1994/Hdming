[返回目录](../../catalogue.md)
# C++调用Fortran DLL程序

### 显式调用的程序

```
#pragma once
#include "stdafx.h"
#include <stdexcept>
#include <stdio.h>
#include <iostream>
#include <stdlib.h>
#include <windows.h>
using namespace std;
int getSolidTideCorrect(double T,double L,double B,double &h_correct)
{
	cout << "Out:正在尝试调用SolTid.dll" << endl;
	typedef double(_stdcall* SolTid)(double T, double L, double B);
	HINSTANCE hLibrary = LoadLibrary(L"SolTid.dll");//显式调用
	if (hLibrary == NULL)
	{
        cout << "Err:无法正确调用SolTid.dll！" << endl;
		return -1;
	}

	try{
		SolTid solidTideCorrect = (SolTid)GetProcAddress(hLibrary, "SolTid");//找到dll中的函数
		h_correct = solidTideCorrect(T, L, B);
	}catch (exception err){
		return -1;
		cout << "Err:无法正确调用SolTid.dll中函数！" << endl;
	}

	FreeLibrary(hLibrary);//释放
	return 0;
}
```

对于C++调用Fortran程序，需要注意：
+ intelVisualFortran2013可以对应vs2010和vs2013
+ 所依赖的DLL需要从对应的32或者64位目录中拷贝
```
C:\Program Files (x86)\Intel\Composer XE 2013 SP1\redist\ia32\compiler
C:\Program Files (x86)\Intel\Composer XE 2013 SP1\redist\intel64\compiler\
```