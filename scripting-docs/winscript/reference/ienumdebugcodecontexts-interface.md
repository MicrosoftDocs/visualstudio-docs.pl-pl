---
title: Interfejs IEnumDebugCodeContexts | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugCodeContexts interface
ms.assetid: 47f17dc9-14bc-43c8-b874-00b5802076eb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e90e19a4bd12dfeeeef1b8f5498f729aa076adb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951461"
---
# <a name="ienumdebugcodecontexts-interface"></a>Interfejs IEnumDebugCodeContexts
Wylicza kontekstów kodu, które odnoszą się do kontekstu dokumentu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IEnumDebugCodeContexts` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugCodeContexts::Next](../../winscript/reference/ienumdebugcodecontexts-next.md)|Pobiera określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumDebugCodeContexts::Skip](../../winscript/reference/ienumdebugcodecontexts-skip.md)|Pomija określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumDebugCodeContexts::Reset](../../winscript/reference/ienumdebugcodecontexts-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumDebugCodeContexts::Clone](../../winscript/reference/ienumdebugcodecontexts-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.|