---
title: Makra raportowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: dc2a5226b3d6f512d2c2f89d9fef2a80eef34340
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758456"
---
# <a name="macros-for-reporting"></a>Makra raportowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **_RPTn**, i **_RPTFn** makra, zdefiniowane w CRTDBG. Godz., aby zastąpić użycie `printf` instrukcje do debugowania. Te makra automatycznie znikają w Twojej wersji kompilacji, gdy **_DEBUG** nie jest zdefiniowana, więc nie ma potrzeby, należy ująć je w **#ifdef**s.  
  
|Macro|Opis|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Generuje ciąg wiadomości i zero do czterech argumentów. Dla _RPT1 za pośrednictwem **_RPT4**, ciąg komunikatu o służy jako ciąg formatowania funkcji printf stylu dla argumentów.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Taki sam jak **_RPTn** , ale te makra dane wyjściowe pliku nazwa i numer wiersza gdzie znajduje się makro.|  
  
 Rozważmy następujący przykład:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ten kod wyświetla wartości `someVar` i `otherVar` do **stdout**. Można użyć następujących wywołanie `_RPTF2` zgłosić te same wartości, a ponadto pliku nazwa i numer wiersza:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Jeśli okaże się, że określona aplikacja musi raportowanie, którego nie oferują makra dostarczony wraz z biblioteki wykonawczej C debugowania, można napisać makra, zaprojektowany specjalnie w celu dopasowania do własnych wymagań. W jednym z plików nagłówka, na przykład, możesz dołączyć kod, takie jak następujące polecenie, aby zdefiniować makro o nazwie **ALERT_IF2**:  
  
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
  
 Jedno wywołanie **ALERT_IF2** można wykonać wszystkie funkcje **printf** kod na początku tego tematu:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Ponieważ makra można łatwo zmienić więcej lub mniej zgłaszania informacji dotyczących różnych miejsc docelowych (w zależności od co to jest bardziej wygodne), to podejście może być szczególnie przydatne w miarę ewolucji wymagań dotyczących debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)



