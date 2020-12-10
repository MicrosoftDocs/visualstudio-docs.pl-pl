---
title: ToggleHUD | Microsoft Docs
description: Użyj metody ToggleHUD () VsgDbg, aby określić, czy podczas uruchamiania aplikacji zostanie wyświetlona opcja ekran główny diagnostyki grafiki (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60bee5a89be0fc1503595a36cfc48a692711d40a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996074"
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