---
title: Pisanie funkcji raportowania błędów czasu | Microsoft Docs
description: Zobacz przykłady pisania niestandardowej funkcji raportowania błędów czasu Visual Studio. Musi mieć tę samą deklarację co _CrtDbgReportW i zwracać wartość 1.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ff82afdfda8af746533f07f21d330c359a1618c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385141"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>How to: Write a Run-Time Error Reporting Function (C++)
Niestandardowa funkcja raportowania dla błędów czasu działania musi mieć taką samą deklarację jak `_CrtDbgReportW` . Powinna zostać zwrócona wartość 1 do debugera.

W poniższym przykładzie pokazano, jak zdefiniować niestandardową funkcję raportowania.

## <a name="example-1"></a>Przykład 1

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

## <a name="example-2"></a>Przykład 2
W poniższym przykładzie przedstawiono bardziej złożoną niestandardową funkcję raportowania. W tym przykładzie instrukcja switch obsługuje różne typy błędów, zgodnie z definicją `reportType` parametru `_CrtDbgReportW` . Ponieważ zastępujesz , `_CrtDbgReportW` nie możesz użyć . `_CrtSetReportMode` Funkcja musi obsługiwać dane wyjściowe. Pierwszy argument zmiennej w tej funkcji przyjmuje numer błędu czasu działania. Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

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

## <a name="example-3"></a>Przykład 3
Użyj `_RTC_SetErrorFuncW` , aby zainstalować funkcję niestandardową, a nie . `_CrtDbgReportW` Aby uzyskać więcej informacji, [zobacz _RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). Zwracana `_RTC_SetErrorFuncW` wartość to poprzednia funkcja raportowania, którą można zapisać i przywrócić w razie potrzeby.

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
[Dostosowywanie Run-Time macierzystego sprawdzania](../debugger/native-run-time-checks-customization.md)
