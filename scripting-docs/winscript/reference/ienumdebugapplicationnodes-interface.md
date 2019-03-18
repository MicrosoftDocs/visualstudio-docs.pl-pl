---
title: IEnumDebugApplicationNodes Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugApplicationNodes interface
ms.assetid: 4fd38b44-3f9a-4d23-9a8f-7dc98f72725f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d23f8a8eaa8e10c503d7ec73f4cd5d4f6ea24404
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145281"
---
# <a name="ienumdebugapplicationnodes-interface"></a>Interfejs IEnumDebugApplicationNodes
Wylicza węzłów podrzędnych węzła skojarzone z aplikacją.  
  
 Oprócz metod odziedziczone `IUnknown`, `IEnumDebugApplicationNodes` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugApplicationNodes::Next](../../winscript/reference/ienumdebugapplicationnodes-next.md)|Pobiera określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumDebugApplicationNodes::Skip](../../winscript/reference/ienumdebugapplicationnodes-skip.md)|Pomija określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumDebugApplicationNodes::Reset](../../winscript/reference/ienumdebugapplicationnodes-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumDebugApplicationNodes::Clone](../../winscript/reference/ienumdebugapplicationnodes-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.|