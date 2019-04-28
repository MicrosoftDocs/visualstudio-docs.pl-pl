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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848476"
---
# <a name="togglehud"></a>ToggleHUD
Włącza/wyłącza diagnostyki grafiki *HUD* nakładki (wyświetlanie Head telefoniczny), lub wyłączyć.

## <a name="syntax"></a>Składnia

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Uwagi
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona w ramach diagnostyki grafiki. Wyświetla informacje czasu wykonywania dotyczące aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie metody [AddMessage](addmessage.md) funkcja elementu członkowskiego.

 Aby przełączyć HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — czyli może być przełączane przez wystąpienie `VsgDbg` klasy, ale [Init](init.md) funkcji składowej nie musi być wywołana jako pierwsza.