---
title: Za pomocą środowiska wykonawczego sprawdza, czy bez biblioteki wykonawczej języka C | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a2d9d97b9ba8a93864ec9af6ff02df7b20bbb35e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929648"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Korzystanie ze sprawdzania w trakcie wykonywania bez biblioteki wykonawczej języka C
W przypadku połączenia programu bez biblioteki wykonawczej C za pomocą **/nodefaultlib**i chcesz używać do sprawdzania w trakcie wykonywania, należy połączyć z RunTmChk.lib.

`_RTC_Initialize` Inicjuje program do sprawdzania w trakcie wykonywania. Jeśli nie łączysz się z biblioteki wykonawczej języka C, należy musi Sprawdź, czy program został skompilowany z sprawdzanie błędów czasu wykonywania przed wywołaniem `_RTC_Initialize`, wykonując następujące czynności:

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Jeśli nie możesz połączyć przy użyciu biblioteki wykonawczej języka C, należy zdefiniować funkcję o nazwie `_CRT_RTC_INITW`. `_CRT_RTC_INITW` funkcja zdefiniowana przez użytkownika jest instalowany jako błąd domyślny zgłoszenie funkcji w następujący sposób:

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

Po wykonaniu procedury instalacji funkcji raportowania błędów domyślne, można zainstalować dodatkowe błędów raportowania funkcje za pomocą `_RTC_SetErrorFuncW`. Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Zobacz też
[Instrukcje: Korzystanie z natywnego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)
