---
title: IDebugCookie Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee129526113a1c8af8f918de81c1f286d5cb703
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974517"
---
# <a name="idebugcookie-interface"></a>Interfejs IDebugCookie
Zezwala na plik cookie debugowania, należy ustawić do użytku z programem `IMachineDebugManagerCookie` interfejsu. Aby uzyskać więcej informacji, zobacz [interfejs IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md). Ten interfejs jest implementowany przez proces debugowania Menedżera (menedżerów PDM) i używane przez debugery skryptu.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IDebugCookie` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Ustawia plik cookie debugowania aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [IMachineDebugManagerCookie, interfejs](../../winscript/reference/imachinedebugmanagercookie-interface.md)