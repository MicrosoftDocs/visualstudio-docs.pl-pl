---
title: Operatory wyszukiwania zaawansowanego w wyrażeniach wyszukiwania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c2b8df3878f67207b22127881722aedd8caae8e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775577"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatory wyszukiwania zaawansowanego w wyrażeniach wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą operatorów wyszukiwania zaawansowanego, można uściślić wyszukiwanie zawartości, tworząc bardziej złożonych wyszukiwania z tymi prostsze. Jak pokazano w poniższej tabeli, te operatory ograniczyć kontekst, w którym jest uruchamiane zapytanie.  
  
> [!WARNING]
>  Należy wprowadzić operatory wyszukiwania zaawansowanego z dwukropkiem ostateczne i nie pośredniczące odstęp przed dwukropkiem dla aparatów wyszukiwania można je rozpoznać.  
  
|Aby wyszukać|Zastosowanie|Przykład|Wynik|  
|-------------------|---------|-------------|------------|  
|Termin w tytuł tematu|Tytuł:|Tytuł: binaryreader|Tematy, które zawierają "binaryreader" w tytułach.|  
|Termin w przykładzie kodu|Kod:|Kod: readdouble|Tematy, które zawierają "readdouble" w przykładzie kodu.|  
|Termin w przykładzie określonego języka programowania|Kod: vb:|Kod: vb:string|Tematy, które zawierają "string", w przykładzie Visual Basic.|  
|Temat, który jest skojarzony z określonym indeksem słowem kluczowym|keyword:|keyword:readbyte|Tematy, które są skojarzone ze słowem kluczowym "readbyte" indeksu.|  
  
 Można użyć kodu: Aby znaleźć zawartość informacji na temat kilku języków programowania, ale zwraca wyniki tylko dla zawartości, oznaczony za pomocą określonego języka programowania. Poniższa tabela zawiera listę języków programowania, które obsługuje tego operatora:  
  
|Język programowania|Zastosowanie|  
|--------------------------|---------|  
|Visual Basic|Kod: vb<br /><br /> lub<br /><br /> code:visualbasic|  
|C#|Kod: c#<br /><br /> lub<br /><br /> Kod: csharp|  
|C++|Kod: cpp<br /><br /> lub<br /><br /> Kod: c ++<br /><br /> lub<br /><br /> code:cplusplus|  
|F#|Kod: f #<br /><br /> lub<br /><br /> Kod: fsharp|  
|JavaScript|Kod: javascript<br /><br /> lub<br /><br /> Kod: js|  
|XAML|Kod: xaml|  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md)   
 [Wskazówki dotyczące wyszukiwania pełnotekstowego](../ide/full-text-search-tips.md)
