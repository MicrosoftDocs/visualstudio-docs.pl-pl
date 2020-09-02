---
title: Operatory logiczne w wyrażeniach wyszukiwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651440"
---
# <a name="logical-operators-in-search-expressions"></a>Operatory logiczne w wyrażeniach wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą operatorów logicznych można uściślić Wyszukiwanie zawartości, tworząc bardziej skomplikowane wyrażenia wyszukiwania z prostszych. Jak pokazano w poniższej tabeli, operatory logiczne określają, jak wiele terminów wyszukiwania ma być połączonych w zapytaniu wyszukiwania.

> [!IMPORTANT]
> Należy wprowadzić operatory logiczne we wszystkich wielkich literach, aby aparat wyszukiwania mógł je rozpoznać.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|
|-------------------|---------|-------------|------------|
|Oba warunki w tym samym temacie|AND|DIB i paleta|Tematy zawierające obie wersje "DIB" i "paleta".|
|Dowolny termin w temacie|LUB|Raster lub Vector|Tematy zawierające "rastrowe" lub "Vector".|
|Pierwszy termin bez drugiego terminu w tym samym temacie|NOT|"system operacyjny" nie jest DOS|Tematy zawierające "system operacyjny", ale nie "DOS".|
|Oba terminy, blisko siebie w temacie|POBLIŻU|Użytkownik blisko jądra|Tematy zawierające "użytkownika" w bliskim sąsiedztwie "jądra".|

## <a name="see-also"></a>Zobacz też
 [Porady dotyczące wyszukiwania pełnotekstowego](../ide/full-text-search-tips.md) [lokalizowanie informacji](../ide/locate-information.md)
