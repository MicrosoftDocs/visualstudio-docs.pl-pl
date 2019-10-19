---
title: 'IDebugProperty:: GetPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562322"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Pobiera wartość `IDebugProperty` opisującą metodę lub właściwość indeksowaną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 podczas Określa `DBGPROP_INFO_FLAGS` stałe, które określają pola, które mają zostać wypełnione w strukturze `DebugPropertyInfo`.  
  
 `nRadix`  
 podczas Podstawy do użycia podczas formatowania dowolnych informacji numerycznych.  
  
 `pPropertyInfo`  
 określoną Zwraca strukturę `DebugPropertyInfo` opisującą właściwość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty   interfejsu](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)