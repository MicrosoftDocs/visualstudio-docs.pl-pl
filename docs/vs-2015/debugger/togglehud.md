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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144580"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Włącza lub wyłącza nakładkę diagnostyki grafiki ( *HUD* Display).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlana w lewym górnym rogu aplikacji, która jest uruchamiana w obszarze Diagnostyka grafiki. Są w nim wyświetlane informacje dotyczące aplikacji i przechwytywania informacji graficznych oraz komunikaty dodawane przez wywołanie funkcji elementu członkowskiego [AddMessage](../debugger/addmessage.md) .  
  
 Aby przełączać HUD, nie trzeba aktywnie przechwycić informacji graficznych — to znaczy, że można ją przełączać przez wystąpienie `VsgDbg` klasy, ale nie trzeba najpierw wywołać funkcji [inicjującej](../debugger/init.md) elementu członkowskiego.
