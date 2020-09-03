---
title: Najlepsze rozwiązania dla programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181118"
---
# <a name="msbuild-best-practices"></a>Najlepsze praktyki w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zalecamy stosowanie następujących najlepszych rozwiązań dotyczących pisania skryptów programu MSBuild:  
  
- Domyślne wartości właściwości są najlepiej obsługiwane przy użyciu `Condition` atrybutu, a nie poprzez deklarowanie właściwości, której wartość domyślna może zostać przesłonięta w wierszu polecenia. Na przykład użyj  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- Unikaj symboli wieloznacznych podczas zaznaczania elementów. Zamiast tego należy jawnie określić pliki. Ułatwia to śledzenie błędów, które mogą wystąpić podczas dodawania lub usuwania plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
