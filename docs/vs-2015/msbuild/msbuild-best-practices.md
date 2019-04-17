---
title: MSBuild — najlepsze praktyki | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6973e905a0587ffdc7cbd0a401e03f933fc60a3a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662222"
---
# <a name="msbuild-best-practices"></a>Najlepsze praktyki w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zalecamy następujące najlepsze rozwiązania dotyczące pisania skryptów programu MSBuild:  
  
-   Domyślne wartości właściwości najlepiej są obsługiwane przy użyciu `Condition` atrybutu, a nie przez zadeklarowanie właściwość, której domyślna wartość może zostać przesłonięta w wierszu polecenia. Na przykład użyć  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Po zaznaczeniu elementów, należy unikać symboli wieloznacznych. Zamiast tego należy jawnie określić pliki. Ta funkcja ułatwia śledzenie błędów, które mogą wystąpić podczas dodawania i usuwania plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
