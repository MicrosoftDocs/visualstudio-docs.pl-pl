---
title: Użyj funkcji __analysis_assume dla wskazówek analizy kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f23dd3821744687d4f595ad404bc076e1d05af7b
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835918"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Instrukcje: Określanie dodatkowych informacji o kodzie za pomocą funkcji __Analysis_assume

Możesz podać wskazówek, aby narzędzie do analizy kodu dla kodu C/C++, który będzie pomocy proces analizy i zmniejszyć ostrzeżenia. Podać dodatkowe informacje, należy użyć następujących funkcji:

`_Analysis_assume(`  `expr`  `)`

`expr` — Dowolne wyrażenie, które jest zakłada się, że zostało oszacowane jako prawdziwe.

Narzędzie do analizy kodu przyjęto założenie, że warunek, reprezentowane przez wyrażenie jest prawdziwe w punkt, gdzie funkcja pojawia się i pozostaje prawdziwy, do momentu wyrażenia zostanie zmieniona, na przykład przez przypisanie do zmiennej.

> [!NOTE]
> `_Analysis_assume` nie ma wpływu na optymalizacji kodu. Poza narzędzia analizy kodu `_Analysis_assume` jest zdefiniowany jako pusta.

## <a name="example"></a>Przykład

Poniższy kod używa `_Analysis_assume` aby poprawić to ostrzeżenie analizy kodu [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Zobacz także

- [__assume](/cpp/intrinsics/assume)
