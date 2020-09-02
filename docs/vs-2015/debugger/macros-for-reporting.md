---
title: Makra raportowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431631"
---
# <a name="macros-for-reporting"></a>Makra raportowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć makr **_RPTn**i **_RPTFN** zdefiniowanych w CRTDBG. H, aby zastąpić użycie `printf` instrukcji na potrzeby debugowania. Te makra są automatycznie znikane w kompilacji wydania, gdy **_DEBUG** nie jest zdefiniowana, więc nie trzeba ich ujmować w **#ifdef**s.  
  
|Makro|Opis|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Wyprowadza ciąg komunikatu i zero do czterech argumentów. W przypadku _RPT1 przez **_RPT4**ciąg komunikatu służy jako ciąg formatowania printf dla argumentów.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Analogicznie jak **_RPTn** , ale te makra również wyprowadzają nazwę pliku i numer wiersza, w którym znajduje się makro.|  
  
 Rozpatrzmy następujący przykład:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ten kod wyprowadza wartości z `someVar` i `otherVar` do **stdout**. Możesz użyć następującego wywołania do, aby `_RPTF2` zgłosić te same wartości, a także nazwę pliku i numer wiersza:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Jeśli okaże się, że określona aplikacja wymaga raportowania debugowania, że makra dostarczone z biblioteką wykonawczą języka C nie zapewniają, można napisać makro zaprojektowane specjalnie w celu dopasowania do własnych wymagań. W jednym z plików nagłówkowych, na przykład, można dołączyć kod podobny do poniższego, aby zdefiniować makro o nazwie **ALERT_IF2**:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Jedno wywołanie **ALERT_IF2** może wykonać wszystkie funkcje kodu **printf** na początku tego tematu:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Ze względu na to, że niestandardowe makro można łatwo zmienić, aby zgłosić więcej lub mniej informacji do różnych miejsc docelowych (w zależności od tego, co jest bardziej wygodne), takie podejście może być szczególnie przydatne w przypadku, gdy Twoje wymagania dotyczące debugowania są rozwijane.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)
