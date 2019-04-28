---
title: IDebugHelper::CreateSimpleConnectionPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f909a63f0f7ba70fca3c5e30e32a2d64c0147e9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979178"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Zwraca interfejs zdarzenia, który otacza danego `IDispatch` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 [in] `IDispatch` Obiekt do opakowania.  
  
 `ppscp`  
 [out] Interfejs zdarzeń, który otacza `pdisp`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zwraca interfejs zdarzenia, który otacza danego `IDispatch` (zobacz [interfejs ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint, interfejs](../../winscript/reference/isimpleconnectionpoint-interface.md)