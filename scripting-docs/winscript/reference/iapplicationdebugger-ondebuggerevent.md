---
title: 'IApplicationDebugger:: onDebuggerEvent | Microsoft Docs'
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
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577867"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Obsługuje zdarzenie niestandardowej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 podczas Identyfikator interfejsu dla obiektu.  
  
 `punk`  
 podczas Obiekt zdarzenia, który implementuje interfejs zdefiniowany przez `riid`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest obecnie zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Semantyką `IUnknown` jest zdefiniowana pełna aplikacja/debuger.  
  
 Ta metoda zezwala na niestandardowe rozszerzenia modelu debugera; nie jest ona obecnie zaimplementowana.  
  
 Ta metoda jest wywoływana, gdy zostanie wywołana `IDebugApplication::FireDebuggerEvent`.  
  
## <a name="see-also"></a>Zobacz także  
 [IApplicationDebugger   interfejsu](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)