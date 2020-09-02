---
title: Używanie testów w czasie wykonywania bez biblioteki wykonawczej C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eefddd21817360736b9f20f74ca3dc8a83683fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684022"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Korzystanie ze sprawdzania w trakcie wykonywania bez biblioteki wykonawczej języka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli połączysz program bez biblioteki wykonawczej C, przy użyciu **/NODEFAULTLIB**i chcesz użyć kontroli w czasie wykonywania, musisz połączyć się z RunTmChk. lib.  
  
 `_RTC_Initialize` Inicjuje program do sprawdzania w czasie wykonywania. Jeśli nie utworzysz połączenia z biblioteką wykonawczą C, musisz sprawdzić, czy program został skompilowany z kontrolami błędów czasu wykonywania przed wywołaniem `_RTC_Initialize` , w następujący sposób:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Jeśli nie utworzysz połączenia z biblioteką wykonawczą C, musisz również zdefiniować funkcję o nazwie `_CRT_RTC_INITW` . `_CRT_RTC_INITW` instaluje funkcję funkcji raportowania błędów domyślną w następujący sposób:  
  
```  
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
  
 Po zainstalowaniu domyślnej funkcji raportowania błędów można zainstalować dodatkowe funkcje raportowania błędów w programie `_RTC_SetErrorFuncW` . Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorFuncW](https://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z natywnych testów w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)
