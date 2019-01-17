---
title: Interfejs IDebugSyncOperation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724ad50771ca49460e130bf93ebc244681bd782
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349610"
---
# <a name="idebugsyncoperation-interface"></a>Interfejs IDebugSyncOperation
Umożliwia aparat skryptów tworzących warstwę abstrakcji operacji (np. Obliczanie wyrażenia), która musi zostać wykonana podczas zagnieżdżonego w określonym wątku zablokowane. Interfejs zawiera także mechanizm anulowanie operacji nie odpowiada.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugSyncOperation` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Zwraca wątku aplikacji docelowej dla tej operacji synchronicznych.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Synchronicznie wykonuje operację i zwraca.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Anuluje operację w toku na inny wątek.|