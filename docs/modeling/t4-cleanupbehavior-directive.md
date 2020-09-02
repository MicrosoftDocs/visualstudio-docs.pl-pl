---
title: Dyrektywa T4 CleanUpBehavior
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5883cd8a1e30e007db41d5aa73f882e1d7edd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591882"
---
# <a name="t4-cleanupbehavior-directive"></a>Dyrektywa T4 CleanUpBehavior

Aby usunąć element appDomain po przetworzeniu szablonu tekstu, należy umieścić następujący wiersz:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Szablony tekstowe są przetwarzane w elemencie appDomain, który jest oddzielony od procesu hosta. W większości przypadków, po przetworzeniu jednego szablonu tekstu element appDomain jest używany ponownie, aby przetworzyć następny szablon. Ale jeśli określisz CleanupBehavior, element appDomain zostanie usunięty, a kolejny szablon zostanie przetworzony w nowym elemencie appDomain.

To spowalnia przetwarzanie tekstu, ale może być przydatne, aby się upewnić, że zasoby są usunięte.

Ta dyrektywa działa tylko w hoście Visual Studio.
