---
title: Używanie testów w czasie wykonywania bez biblioteki wykonawczej C | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 029aafa634ba0e6837cdc7d4304d0419420dd912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72728663"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Korzystanie ze sprawdzania w trakcie wykonywania bez biblioteki wykonawczej języka C
Jeśli połączysz program bez biblioteki wykonawczej C, przy użyciu **/NODEFAULTLIB**i chcesz użyć kontroli w czasie wykonywania, musisz połączyć się z RunTmChk. lib.

`_RTC_Initialize` Inicjuje program do sprawdzania w czasie wykonywania. Jeśli nie utworzysz połączenia z biblioteką wykonawczą C, musisz sprawdzić, czy program został skompilowany z kontrolami błędów czasu wykonywania przed wywołaniem `_RTC_Initialize` , w następujący sposób:

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Jeśli nie utworzysz połączenia z biblioteką wykonawczą C, musisz również zdefiniować funkcję o nazwie `_CRT_RTC_INITW` . `_CRT_RTC_INITW` instaluje funkcję funkcji raportowania błędów domyślną w następujący sposób:

```cpp
// C version:
_RTC_error_fnW __cdecl _CRT_RTC_INITW(
        void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler.
    return &MyErrorFunc;
}

// C++ version:
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(
       void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler:
    return &MyErrorFunc;
}
```

Po zainstalowaniu domyślnej funkcji raportowania błędów można zainstalować dodatkowe funkcje raportowania błędów w programie `_RTC_SetErrorFuncW` . Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Zobacz też
[Instrukcje: korzystanie z natywnych testów w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)
