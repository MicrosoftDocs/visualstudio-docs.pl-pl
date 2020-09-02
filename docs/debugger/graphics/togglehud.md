---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848476"
---
# <a name="togglehud"></a>ToggleHUD
Włącza lub wyłącza nakładkę diagnostyki grafiki ( *HUD* Display).

## <a name="syntax"></a>Składnia

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Uwagi
 HUD diagnostyki grafiki jest wyświetlana w lewym górnym rogu aplikacji, która jest uruchamiana w obszarze Diagnostyka grafiki. Są w nim wyświetlane informacje dotyczące aplikacji i przechwytywania informacji graficznych oraz komunikaty dodawane przez wywołanie funkcji elementu członkowskiego [AddMessage](addmessage.md) .

 Aby przełączać HUD, nie trzeba aktywnie przechwycić informacji graficznych — to znaczy, że można ją przełączać przez wystąpienie `VsgDbg` klasy, ale nie trzeba najpierw wywołać funkcji [inicjującej](init.md) elementu członkowskiego.