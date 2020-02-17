---
title: Użyj _Analysis_assume na potrzeby wskazówek dotyczących analizy kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1fec348108afdfe3cdac3325e0a1750b55332db4
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271638"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Instrukcje: Określanie dodatkowych informacji o kodzie przy użyciu _Analysis_assume

Możesz dostarczyć wskazówki do narzędzia do analizy kodu dla języka C/C++ kodu, które ułatwią proces analizy i zmniejszają ostrzeżenia. Aby podać dodatkowe informacje, użyj następującej funkcji:

`_Analysis_assume(`  `expr`  `)`

`expr` — dowolne wyrażenie, które ma zostać obliczone na wartość true.

Narzędzie do analizy kodu zakłada, że warunek reprezentowany przez wyrażenie ma wartość true w punkcie, w którym funkcja jest wyświetlana i pozostaje prawdziwa do momentu zmiany wyrażenia, na przykład przez przypisanie do zmiennej.

> [!NOTE]
> `_Analysis_assume` nie ma wpływu na optymalizację kodu. Na zewnątrz narzędzia do analizy kodu `_Analysis_assume` jest definiowana jako No-op.

## <a name="example"></a>Przykład

Poniższy kod używa `_Analysis_assume` do skorygowania ostrzeżenia analizy kodu [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Zobacz też

- [__assume](/cpp/intrinsics/assume)
