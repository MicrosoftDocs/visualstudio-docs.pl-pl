---
title: Makra raportowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8453f00dda843f6940c518b7ed3ea83c8c261476
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989977"
---
# <a name="macros-for-reporting"></a>Makra raportowania
W przypadku debugowania, można użyć **_RPTn** i **_RPTFn** makra, zdefiniowane w CRTDBG. Godz., aby zastąpić użycie `printf` instrukcji. Nie trzeba ich w inclose **#ifdef**s, ponieważ ich automatycznie znikają w Twojej wersji podczas kompilacji **_DEBUG** nie jest zdefiniowany.  
  
|Macro|Opis|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Generuje ciąg wiadomości i zero do czterech argumentów. Dla _RPT1 za pośrednictwem **_RPT4**, ciąg komunikatu o służy jako ciąg formatowania funkcji printf stylu dla argumentów.|  
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Taki sam jak **_RPTn**, ale te makra dane wyjściowe pliku nazwa i numer wiersza gdzie znajduje się makro.|  
  
 Rozważmy następujący przykład:  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ten kod wyświetla wartości `someVar` i `otherVar` do **stdout**. Można użyć następujących wywołanie `_RPTF2` zgłosić te same wartości, a ponadto pliku nazwa i numer wiersza:  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
Może się okazać, że określona aplikacja musi raportowanie, którego nie oferują makra dostarczony wraz z biblioteki wykonawczej C debugowania. W takich przypadkach można napisać makra, zaprojektowany specjalnie w celu dopasowania do własnych wymagań. W jednym z plików nagłówka, na przykład, możesz dołączyć kod, takie jak następujące polecenie, aby zdefiniować makro o nazwie **ALERT_IF2**:  
  
```cpp
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
  
 Jedno wywołanie **ALERT_IF2** zrobić wszystkie funkcje **printf** kodu:  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Można łatwo zmienić niestandardowe — makro więcej lub mniej zgłaszania informacji dotyczących różnych miejsc docelowych. To podejście jest szczególnie przydatne w miarę ewolucji wymagań dotyczących debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)
