---
title: DBGPROP_ATTRIB_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0324353d716430148b4b3c7b8adf9262e0dc3b7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955279"
---
# <a name="dbgpropattribflags"></a>DBGPROP_ATTRIB_FLAGS
W tym artykule opisano różne atrybuty dla `IDebugProperty`. Członek `DebugPropertyInfo` struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Wskazuje żadnych atrybutów.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Oznacza to, że wartość w `DebugPropertyInfo::bstrValue` jest nieprawidłowy.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Wskazuje, że odwołanie lub właściwość ma elementy podrzędne.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Wskazuje, że wartość jest tylko do odczytu.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Określa obiekt, który ma dostęp publiczny.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Określa obiekt, który ma dostęp prywatny.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Określa obiekt, który został ochroną dostępu.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Określa obiekt, który ma dostęp do końcowej.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Wskazuje globalnej pamięci masowej.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Wskazuje statycznego magazynu.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Określa obiekt, który jest właściwością.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Wskazuje magazynu wirtualnego.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Wskazuje, że typ obiektu jest stały.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Wskazuje, że to gniazdo jest synchronizowane wątku.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Wskazuje to gniazdo volatile w odniesieniu do skorzystania z magazynu trwałego.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Wskazuje, że to miejsce ma atrybuty niż te wstępnie zdefiniowane usługi bits.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Wskazuje, że wartość jest wartość zwracaną przez funkcję.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są również używane do filtrowania elementów podrzędnych obiektu. Wartości mogą być łączone z bitowe OR.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)