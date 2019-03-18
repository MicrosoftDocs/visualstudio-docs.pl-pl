---
title: Struktura DebugPropertyInfo | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 99208626b41f2463178bccecf73c21a1d15fa765
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155748"
---
# <a name="debugpropertyinfo-structure"></a>Struktura DebugPropertyInfo
Opisuje obiekt hierarchiczny charakter, który ma nazwę, typ i wartość. Służy do opisywania właściwości debugowania zmiennych lokalnych, parametrów, obejrzyj zmiennych i wyrażeń i rejestruje.  
  
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
  
## <a name="members"></a>Elementy członkowskie  
 dwValidFields  
 Wyliczany typ danych używany do określenia, które pola są inicjowane.  
  
 bstrName  
 Nazwa właściwości w kontekście.  
  
 bstrType  
 Typ właściwości jako sformatowany ciąg.  
  
 bstrValue  
 Wartość właściwości jako sformatowany ciąg.  
  
 bstrFullName  
 Pełna nazwa właściwości.  
  
 dwAttrib  
 Wyliczenie, które określa flagi dla atrybutów właściwości debugowania.  
  
 pDebugProp  
 `IDebugProperty` Opisanego przez informacje zawarte w tym `DebugPropertyInfo` struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)