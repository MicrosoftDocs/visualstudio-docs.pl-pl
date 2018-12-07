---
title: Pisanie funkcji raportowania błędów czasu wykonywania | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22c508a7fa8faedc66f9122de60921878a931fae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051506"
---
# <a name="how-to-write-a-run-time-error-reporting-function"></a>Porady: pisanie funkcji raportowania błędów czasu wykonywania
Raportów niestandardowych funkcji błędów czasu wykonywania musi mieć tej samej deklaracji jako `_CrtDbgReportW`. Wartość 1 powinien zostać zwrócony do debugera.  
  
 Poniższy przykład pokazuje jak zdefiniować niestandardowe funkcji raportowania.  
  
## <a name="example"></a>Przykład  
  
```cpp
#include <stdio.h>  
int errorhandler = 0;  
void configureMyErrorFunc(int i)  
{  
    errorhandler = i;  
}  
  
int MyErrorFunc(int errorType, const wchar_t *filename,  
                int linenumber, const wchar_t *moduleName,  
                const wchar_t *format, ...)  
{  
    switch (errorhandler)  
    {  
    case 0:  
    case 1:  
        wprintf(L"Error type %d at %s line %d in %s",  
                errorType, filename, linenumber, moduleName);  
        break;  
    case 2:  
    case 3:  
        fprintf(stderr, "Error type");  
        break;  
    }  
  
    return 1;  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia bardziej złożone niestandardowe funkcji raportowania. W tym przykładzie instrukcji switch obsługuje różne typy błędów, zgodnie z definicją `reportType` parametru `_CrtDbgReportW`. Ponieważ zastępowane `_CrtDbgReportW`, nie można użyć `_CrtSetReportMode`. Funkcję musi obsługiwać dane wyjściowe. Pierwszy argument w postaci zmiennej w tej funkcji ma wiele błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).  
  
```cpp
#include <windows.h>  
#include <stdarg.h>  
#include <rtcapi.h>  
#include <malloc.h>  
#pragma runtime_checks("", off)  
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,   
                   const wchar_t *module, const wchar_t *format, ...)  
{  
    // Prevent re-entrance.  
    static long running = 0;  
    while (InterlockedExchange(&running, 1))  
        Sleep(0);  
    // Now, disable all RTC failures.  
    int numErrors = _RTC_NumErrors();  
    int *errors=(int*)_alloca(numErrors);  
    for (int i = 0; i < numErrors; i++)  
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);  
  
   // First, get the rtc error number from the var-arg list.  
    va_list vl;  
    va_start(vl, format);  
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);  
    va_end(vl);  
  
    wchar_t buf[512];  
    const char *err = _RTC_GetErrDesc(rtc_errnum);  
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",  
        err,  
        line,  
        file ? file : L"Unknown",  
        module ? module : L"Unknown");  
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;  
    // Now, restore the RTC errortypes.  
    for(int i = 0; i < numErrors; i++)  
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);  
    running = 0;  
    return res;  
}  
#pragma runtime_checks("", restore)  
```  
  
## <a name="example"></a>Przykład  
 Użyj `_RTC_SetErrorFuncW` do zainstalowania funkcji niestandardowych zamiast `_CrtDbgReportW`. Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). `_RTC_SetErrorFuncW` Zwracają wartość poprzedniej funkcji raportowania, który można zapisać i przywrócić w razie potrzeby.  
  
```cpp
#include <rtcapi.h>  
int main()  
{  
    _RTC_error_fnW oldfunction, newfunc;  
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);  
    // Run some code.  
    newfunc = _RTC_SetErrorFuncW(oldfunction);  
    // newfunc == &MyErrorFunc;  
    // Run some more code.  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie macierzystego sprawdzania w trakcie wykonywania](../debugger/native-run-time-checks-customization.md)
