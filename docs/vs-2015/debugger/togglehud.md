---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767883"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Włącza/wyłącza diagnostyki grafiki *HUD* nakładki (wyświetlanie Head telefoniczny), lub wyłączyć.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona w ramach diagnostyki grafiki. Wyświetla informacje czasu wykonywania dotyczące aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie metody [AddMessage](../debugger/addmessage.md) funkcja elementu członkowskiego.  
  
 Aby przełączyć HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — czyli może być przełączane przez wystąpienie `VsgDbg` klasy, ale [Init](../debugger/init.md) funkcji składowej nie musi być wywołana jako pierwsza.
