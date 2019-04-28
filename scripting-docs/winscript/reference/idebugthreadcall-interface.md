---
title: Interfejs IDebugThreadCall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004860"
---
# <a name="idebugthreadcall-interface"></a>Interfejs IDebugThreadCall
`IDebugThreadCall` Interfejs jest zwykle implementowany przez składnik, który sprawia, że wywołania międzywątkowe z `IDebugThread` kierowania wdrażania udostępniane przez Menedżer debugowania procesów (menedżerów PDM).  
  
 Wywołuje program PDM `IDebugThreadCall` interfejsu w żądany wątek i `IDebugThreadCall` interfejsu wywołuje wywołania do żądanej implementacji. `IDebugThreadCall` Interfejsu rzutuje informacje o parametrach przekazywane jako parametry odpowiednie u góry.  
  
 `IDebugThreadCall` Interfejs jest obiekt bezwątkowego.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IDebugThreadCall` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Obsługuje wywołania, aby uruchomić kod w innym wątku.|