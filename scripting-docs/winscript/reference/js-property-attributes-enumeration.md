---
title: Wyliczenie JS_PROPERTY_ATTRIBUTES | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a3fac8b1be15d1b1d26c13fe1e17e311798a3a3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088273"
---
# <a name="jspropertyattributes-enumeration"></a>Wyliczenie JS_PROPERTY_ATTRIBUTES
Określa atrybuty właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Właściwość nie ma żadnych atrybutów.|  
|`JS_PROPERTY_HAS_CHILDREN`|Właściwość ma elementy podrzędne.|  
|`JS_PROPERTY_FAKE`|Właściwość reprezentuje węzeł fałszywe, takie jak "[metody]".|  
|`JS_PROPERTY_METHOD`|Właściwość jest metodą.|  
|`JS_PROPERTY_READONLY`|Właściwość jest tylko do odczytu.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Właściwość jest wskaźnik do natywnego obiektu WinRT.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)