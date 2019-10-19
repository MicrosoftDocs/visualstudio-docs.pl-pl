---
title: 'IDebugApplicationNode100:: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574725"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Ustawia filtr dla określonej implementacji [interfejsu IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) . Dzięki temu debugery skryptów mogą odfiltrować podrzędne węzły aplikacji generowane przez kompilator, dzięki czemu PDM nie będzie już wysyłać zdarzeń podczas tworzenia lub usuwania. Domyślnie zostaną wysłane wszystkie węzły.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) jest implementowany przez PDM v 10.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Plik cookie filtru.  
  
 `filter`  
 Filtr.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNode100, interfejs](../../winscript/reference/idebugapplicationnode100-interface.md)