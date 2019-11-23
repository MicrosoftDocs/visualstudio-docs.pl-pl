---
title: Struktura DebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575066"
---
# <a name="debugpropertyinfo-structure"></a>Struktura DebugPropertyInfo
Opisuje obiekt o rodzaju hierarchicznej, który ma nazwę, typ i wartość. Służy do opisywania właściwości debugowania zmiennych lokalnych, parametrów, zmiennych i wyrażeń oraz rejestrów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Members  
 dwValidFields  
 Wyliczany typ danych służący do określania, które pola są inicjowane.  
  
 bstrName  
 Nazwa właściwości w kontekście.  
  
 bstrtype  
 Typ właściwości, jako sformatowany ciąg.  
  
 bstrValue  
 Wartość właściwości, jako sformatowany ciąg.  
  
 bstrFullName  
 Pełna nazwa właściwości.  
  
 dwAttrib  
 Wyliczenie określające flagi dla atrybutów właściwości debugowania.  
  
 pDebugProp  
 `IDebugProperty` opisany przez informacje zawarte w tej strukturze `DebugPropertyInfo`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty  interfejsu](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)