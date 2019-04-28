---
title: IApplicationDebugger::onDebuggerEvent | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78bb3345463dfd682534dc60a216f3e0e8fdf2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991362"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Obsługuje zdarzenie aplikacji niestandardowych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator interfejsu dla obiektu.  
  
 `punk`  
 [in] Obiekt zdarzenia, która implementuje interfejs zdefiniowany przez `riid`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest obecnie zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Semantyka `IUnknown` jest całkowicie zdefiniowane aplikacji/debugera.  
  
 Ta metoda umożliwia niestandardowe rozszerzenia modelu debuger; nie jest obecnie zaimplementowana.  
  
 Ta metoda jest wywoływana, gdy `IDebugApplication::FireDebuggerEvent` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)