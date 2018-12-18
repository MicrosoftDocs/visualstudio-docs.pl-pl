---
title: 'Porady: Określanie dodatkowych informacji o kodzie za pomocą funkcji __analysis_assume | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de4d70dc615c14e9f9355608fa6b352b799c2c1a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776905"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Porady: określanie informacji o dodatkowym kodzie za pomocą __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz podać wskazówek, aby narzędzie do analizy kodu dla kodu C/C++, który będzie pomocy proces analizy i zmniejszyć ostrzeżenia. Podać dodatkowe informacje, należy użyć następujących funkcji:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` — Dowolne wyrażenie, które jest zakłada się, że zostało oszacowane jako prawdziwe.  
  
 Narzędzie do analizy kodu przyjęto założenie, że warunek, reprezentowane przez wyrażenie jest prawdziwe w punkt, gdzie funkcja pojawia się i pozostaje prawdziwy, do momentu wyrażenia zostanie zmieniona, na przykład przez przypisanie do zmiennej.  
  
> [!NOTE]
>  `__analysis_assume` nie ma wpływu na optymalizacji kodu. Poza narzędzia analizy kodu `__analysis_assume` jest zdefiniowany jako pusta.  
  
## <a name="example"></a>Przykład  
 Poniższy kod używa `__analysis_assume` aby poprawić to ostrzeżenie analizy kodu [C6388](../code-quality/c6388.md):  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)



