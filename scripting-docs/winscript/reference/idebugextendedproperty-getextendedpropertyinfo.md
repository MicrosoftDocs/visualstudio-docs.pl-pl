---
title: 'IDebugExtendedProperty:: GetExtendedPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77167c46e02bcf2bf5d3ce5836ad5de103176e93
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576376"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Pobiera rozszerzone informacje dla właściwości rozszerzonej, która jest więcej informacji niż prostsze `IDebugProperty`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 podczas Określa EX_DBGPROP_INFO_FLAGS stałe, które określają pola, które mają zostać wypełnione w strukturze `ExtendedDebugPropertyInfo`.  
  
 `nRadix`  
 podczas Podstawy do użycia w interpretacji wszelkich informacji numerycznych.  
  
 `pExtendedPropertyInfo`  
 określoną Zwraca strukturę `ExtendedDebugPropertyInfo` opisującą właściwość.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugExtendedProperty  interfejsu](../../winscript/reference/idebugextendedproperty-interface.md)  
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo, struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)