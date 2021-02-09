---
title: Makra raportowania | Microsoft Docs
description: Dowiedz się więcej na temat makr debugowania _RPTn i _RPTFn określonych w CRTDBG. H i informacje o tworzeniu własnych makr debugowania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0356f05c3f0dac636813d1632f628dd02dd28923
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893129"
---
# <a name="macros-for-reporting"></a>Makra raportowania
Na potrzeby debugowania można użyć makr **_RPTn** i **_RPTFN** zdefiniowanych w CRTDBG. H, aby zastąpić użycie `printf` instrukcji. Nie musisz zamykać ich w **#ifdef** s, ponieważ nie jest on automatycznie znikany w kompilacji wydania, gdy **_DEBUG** nie jest zdefiniowana.

|Makro|Opis|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Wyprowadza ciąg komunikatu i zero do czterech argumentów. W przypadku **_RPT1** przez **_RPT4** ciąg komunikatu służy jako ciąg formatowania printf dla argumentów.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|Analogicznie jak **_RPTn**, ale te makra również wyprowadzają nazwę pliku i numer wiersza, w którym znajduje się makro.|

 Rozpatrzmy następujący przykład:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Ten kod wyprowadza wartości z `someVar` i `otherVar` do **stdout**. Możesz użyć następującego wywołania do, aby `_RPTF2` zgłosić te same wartości, a także nazwę pliku i numer wiersza:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Może się okazać, że określona aplikacja wymaga debugowania, że makra dostarczone z biblioteką wykonawczą języka C nie zapewniają. W takich przypadkach można napisać makro zaprojektowane specjalnie w celu dopasowania do własnych wymagań. W jednym z plików nagłówkowych, na przykład, można dołączyć kod podobny do poniższego, aby zdefiniować makro o nazwie **ALERT_IF2**:

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

 Jedno wywołanie **ALERT_IF2** mogło wykonać wszystkie funkcje kodu **printf** :

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Możesz łatwo zmienić niestandardowe makro, aby zgłosić więcej lub mniej informacji do różnych miejsc docelowych. Takie podejście jest szczególnie przydatne, gdy Twoje wymagania dotyczące debugowania są rozwijane.

## <a name="see-also"></a>Zobacz też
- [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)
