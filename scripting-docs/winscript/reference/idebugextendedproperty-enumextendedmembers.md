---
title: 'IDebugExtendedProperty:: EnumExtendedMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fd225be9504254965eab77b912f50fb5c777e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576389"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Wylicza elementy członkowskie właściwości rozszerzonej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 podczas Określa EX_DBGPROP_INFO_FLAGS stałe, które określają pola w wyliczeniowych strukturach właściwości rozszerzonego debugowania, które mają zostać wypełnione.  
  
 `nRadix`  
 podczas Podstawy do użycia w interpretacji wszelkich informacji numerycznych.  
  
 `ppeepi`  
 określoną Zwraca interfejs `IEnumDebugExtendedPropertyInfo`, który wylicza właściwości elementu członkowskiego.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugExtendedProperty  interfejsu](../../winscript/reference/idebugextendedproperty-interface.md)  
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo, struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)