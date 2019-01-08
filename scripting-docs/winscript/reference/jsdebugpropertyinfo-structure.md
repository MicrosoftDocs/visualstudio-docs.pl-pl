---
title: Struktura JsDebugPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 317cf5adc459c1491d037678616c17de2a619d96
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095475"
---
# <a name="jsdebugpropertyinfo-structure"></a>Struktura JsDebugPropertyInfo
Zawiera informacje o właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `name`  
 Nazwa właściwości.  
  
 `type`  
 Typ właściwości.  
  
 `value`  
 Wartość właściwości.  
  
 `fullName`  
 Pełna nazwa właściwości.  
  
 `attr`  
 Wyliczenie, które reprezentuje atrybuty właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)