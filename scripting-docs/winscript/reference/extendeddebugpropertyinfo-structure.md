---
title: Struktura ExtendedDebugPropertyInfo | Microsoft Docs
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
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575832"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Struktura ExtendedDebugPropertyInfo
Rozszerza strukturę `DebugPropertyInfo` z dodatkowymi elementami członkowskimi w celu scharakteryzowania właściwości rozszerzonej.  
  
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
 Wyliczany typ danych służący do określania, które pola są inicjowane.  
  
 `bstrName`  
 Nazwa właściwości w kontekście.  
  
 `bstrType`  
 Typ właściwości jako sformatowany ciąg.  
  
 `bstrValue`  
 Wartość właściwości jako sformatowany ciąg.  
  
 `bstrFullName`  
 Pełna nazwa właściwości.  
  
 `dwAttrib`  
 Wyliczenie określające flagi dla atrybutów właściwości debugowania.  
  
 `pDebugProp`  
 `IDebugProperty` obiekt odpowiadający tej `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Identyfikator wysyłania.  
  
 `nType`  
 Typ właściwości rozszerzonej.  
  
 `varValue`  
 Wartość właściwości rozszerzonej, jeśli może pasować do WARIANTu.  
  
 `plbValue`  
 Rzeczywiste bajty danych wartości właściwości.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` obiekt odpowiadający tej `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [struktury DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 [IDebugProperty   interfejsu](../../winscript/reference/idebugproperty-interface.md)  
 [IDebugExtendedProperty   interfejsu](../../winscript/reference/idebugextendedproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)