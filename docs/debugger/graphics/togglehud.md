---
title: PrzełącznikHUD | Microsoft Docs
description: Użyj metody ToggleHUD() programu VsgDbg, aby przełączać, czy ekran head-Up diagnostyki grafiki (HUD) jest wyświetlany podczas działania aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809b33fe3339da56507d09fcf15ec51481b751e0
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232495"
---
# <a name="togglehud"></a>ToggleHUD
Włącza lub wyłącza nakładkę *hud* diagnostyki grafiki (Head-Up Display).

## <a name="syntax"></a>Składnia

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Uwagi
 Diagnostyka grafiki HUD jest wyświetlana w lewym górnym rogu aplikacji uruchomionej w ramach diagnostyki grafiki. Wyświetla on informacje o aplikacji i przechwytywaniu informacji graficznych oraz komunikaty, które są dodawane przez wywołanie [funkcji członkowskiej AddMessage.](addmessage.md)

 Aby przełączyć funkcję HUD, nie trzeba aktywnie przechwytywać informacji graficznych, czyli można je przełączać za pośrednictwem wystąpienia klasy, ale funkcja członkowski Init nie musi być wywoływana `VsgDbg` jako pierwsza. [](init.md)