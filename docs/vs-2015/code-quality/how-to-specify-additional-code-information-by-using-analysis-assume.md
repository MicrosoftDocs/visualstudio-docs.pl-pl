---
title: 'Instrukcje: Określanie dodatkowych informacji o kodzie przy użyciu __analysis_assume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277974"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Porady: określanie informacji o dodatkowym kodzie za pomocą __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dostarczyć wskazówki do narzędzia do analizy kodu dla języka C/C++ kodu, które ułatwią proces analizy i zmniejszają ostrzeżenia. Aby podać dodatkowe informacje, użyj następującej funkcji:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` — dowolne wyrażenie, które ma zostać obliczone na wartość true.  
  
 Narzędzie do analizy kodu zakłada, że warunek reprezentowany przez wyrażenie ma wartość true w punkcie, w którym funkcja jest wyświetlana i pozostaje prawdziwa do momentu zmiany wyrażenia, na przykład przez przypisanie do zmiennej.  
  
> [!NOTE]
> `__analysis_assume` nie ma wpływu na optymalizację kodu. Na zewnątrz narzędzia do analizy kodu `__analysis_assume` jest definiowana jako No-op.  
  
## <a name="example"></a>Przykład  
 Poniższy kod używa `__analysis_assume` do skorygowania ostrzeżenia analizy kodu [C6388](../code-quality/c6388.md):  
  
```  
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
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
