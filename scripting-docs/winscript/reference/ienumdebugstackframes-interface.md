---
title: IEnumDebugStackFrames Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugStackFrames interface
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 224c26bccc5443cb20e2ca514ac6df1a111df05e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963367"
---
# <a name="ienumdebugstackframes-interface"></a>Interfejs IEnumDebugStackFrames
Wylicza ramki stosu odpowiadającej wątku.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IEnumDebugStackFrames` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|Pobiera określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|Pomija określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.|