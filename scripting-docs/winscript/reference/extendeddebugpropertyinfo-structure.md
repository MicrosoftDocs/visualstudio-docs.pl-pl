---
title: Struktura ExtendedDebugPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fe0eef00d2bf064a8a002925f4ba5607d36f31c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955201"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Struktura ExtendedDebugPropertyInfo
Rozszerza `DebugPropertyInfo` strukturę dodatkowe elementy członkowskie w celu scharakteryzowania właściwości rozszerzonej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwValidFields`  
 Wyliczany typ danych używany do określenia, które pola są inicjowane.  
  
 `bstrName`  
 Nazwa właściwości w kontekście.  
  
 `bstrType`  
 Typ właściwości jako sformatowany ciąg.  
  
 `bstrValue`  
 Wartość właściwości jako ciąg formatowania.  
  
 `bstrFullName`  
 Pełna nazwa właściwości.  
  
 `dwAttrib`  
 Wyliczenie, które określa flagi dla atrybutów właściwości debugowania.  
  
 `pDebugProp`  
 `IDebugProperty` Obiekt odpowiadający to `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Identyfikator wysyłki.  
  
 `nType`  
 Typ właściwości rozszerzonej.  
  
 `varValue`  
 Wartość właściwości rozszerzonej, jeśli zmieści się w WARIANCIE.  
  
 `plbValue`  
 Bajty danych rzeczywistych wartości właściwości.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` Obiekt odpowiadający to `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Interfejs IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)