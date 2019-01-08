---
title: Struktura ExtendedDebugPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e0251d4b578a33a9eb5448c1ceb2b2607f82d43a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096775"
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