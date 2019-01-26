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
ms.openlocfilehash: e49066d4625990119159ea72f59a3a3fe59d581c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953305"
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