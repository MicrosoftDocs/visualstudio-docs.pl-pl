---
title: MSBuild — najlepsze praktyki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 622d7b087e94d21f86691b88c3af4891aa533e9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013213"
---
# <a name="msbuild-best-practices"></a>Najlepsze rozwiązania programu MSBuild
Zalecamy następujące najlepsze rozwiązania dotyczące pisania skryptów programu MSBuild:  
  
-   Domyślne wartości właściwości najlepiej są obsługiwane przy użyciu `Condition` atrybutu, a nie przez zadeklarowanie właściwość, której domyślna wartość może zostać przesłonięta w wierszu polecenia. Na przykład użyć  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   Po zaznaczeniu elementów, należy unikać symboli wieloznacznych. Zamiast tego należy jawnie określić pliki. Ta funkcja ułatwia śledzenie błędów, które mogą wystąpić podczas dodawania i usuwania plików.  
  
## <a name="see-also"></a>Zobacz także  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
