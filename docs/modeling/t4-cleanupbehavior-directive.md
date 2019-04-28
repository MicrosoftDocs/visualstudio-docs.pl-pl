---
title: Dyrektywa T4 CleanUpBehavior
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27df15c0b935ff4bae497940c095dba1598bc4c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964108"
---
# <a name="t4-cleanupbehavior-directive"></a>Dyrektywa T4 CleanUpBehavior

Aby usunąć element appDomain po przetworzeniu szablonu tekstu, należy umieścić następujący wiersz:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Szablony tekstowe są przetwarzane w elemencie appDomain, który jest oddzielony od procesu hosta. W większości przypadków, po przetworzeniu jednego szablonu tekstu element appDomain jest używany ponownie, aby przetworzyć następny szablon. Ale jeśli określisz CleanupBehavior, element appDomain zostanie usunięty, a kolejny szablon zostanie przetworzony w nowym elemencie appDomain.

To spowalnia przetwarzanie tekstu, ale może być przydatne, aby się upewnić, że zasoby są usunięte.

Ta dyrektywa działa tylko w hoście Visual Studio.