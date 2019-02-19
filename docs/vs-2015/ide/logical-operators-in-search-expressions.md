---
title: Operatory logiczne w wyrażeniach wyszukiwania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66d6aa6a11ef0ce308c5ba2b089aaa8170b6441f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760073"
---
# <a name="logical-operators-in-search-expressions"></a>Operatory logiczne w wyrażeniach wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą operatorów logicznych, można uściślić wyszukiwanie zawartości, tworząc bardziej złożonych wyszukiwania z tymi prostsze. Jak pokazano w poniższej tabeli, operatory logiczne Określanie wielu warunków wyszukiwania powinny być one łączone w zapytaniu wyszukiwania.  
  
> [!IMPORTANT]
>  Operatory logiczne należy wprowadzić wielkimi literami dla aparatu wyszukiwania, rozpoznawał.  
  
|Aby wyszukać|Zastosowanie|Przykład|Wynik|  
|-------------------|---------|-------------|------------|  
|Oba warianty pojęć w ten sam temat|AND|dib i palety|Tematy, które zawierają "dib" i "palety".|  
|Albo termin w temacie|LUB|rastrowych wektor OR|Tematy, które zawierają "rastrowych" lub "vector".|  
|Pierwszy okres bez drugi warunek w ten sam temat|NIE|"system operacyjny" nie DOS|Tematy, które zawierają "system operacyjny", ale nie "DOS".|  
|Oba warianty pojęć blisko siebie w temacie|W POBLIŻU|użytkownik w pobliżu jądra|Tematy zawierające "user" w pobliżu "jądra".|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące wyszukiwania pełnotekstowego](../ide/full-text-search-tips.md)   
 [Znajdowanie informacji](../ide/locate-information.md)
