---
title: 'IDebugProperty:: EnumMembers — | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562421"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Wylicza elementy członkowskie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 podczas Określa `DBGPROP_INFO_FLAGS` stałe, które określają, które pola w strukturze właściwości debugowania mają być wypełnione.  
  
 `nRadix`  
 podczas Podstawy do użycia w interpretacji wszelkich informacji numerycznych.  
  
 `refiid`  
 podczas Ten identyfikator IID jest przesyłany do filtrowania modułu wyliczającego. Identyfikator IID to jeden z `IDebugPropertyEnumType` interfejsów, które dziedziczą z `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 określoną Zwraca interfejs `IEnumDebugPropertyInfo`, który wylicza właściwości elementu członkowskiego.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty  interfejsu](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
   [IDebugPropertyEnumType_All interfejsu](../../winscript/reference/idebugpropertyenumtype-all-interface.md)  
 [IEnumDebugPropertyInfo, interfejs](../../winscript/reference/ienumdebugpropertyinfo-interface.md)