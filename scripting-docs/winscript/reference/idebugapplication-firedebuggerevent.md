---
title: 'IDebugApplication:: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574999"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Uruchamia zdarzenie ogólne dla interfejsu `IApplicationDebugger` debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 podczas Identyfikator GUID dla obiektu.  
  
 `punk`  
 podczas Obiekt zdarzenia do przekazania do debugera.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest obecnie zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Semantyka identyfikatora GUID i `IUnknown` są całkowicie zdefiniowane w aplikacji/debugerze.  
  
 Ta metoda zezwala na niestandardowe rozszerzenia modelu debugera; nie jest ona obecnie zaimplementowana.  
  
 Ta metoda powoduje wywoływanie `IApplicationDebugger::onDebuggerEvent`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication  interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)