---
title: DBGPROP_ATTRIB_FLAGS | Microsoft Docs
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
ms.openlocfilehash: 3170e310aa3177e2ca7a1dd81ead02bcc4050114
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572595"
---
# <a name="dbgprop_attrib_flags"></a>DBGPROP_ATTRIB_FLAGS
Opisuje różne atrybuty `IDebugProperty`. Składowa struktury `DebugPropertyInfo`.  
  
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
  
## <a name="members"></a>Members  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Nie wskazuje żadnych atrybutów.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Wskazuje, że wartość w `DebugPropertyInfo::bstrValue` jest nieprawidłowa.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Wskazuje, że odwołanie lub właściwość zawiera elementy podrzędne.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Wskazuje, że wartość jest tylko do odczytu.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Wskazuje obiekt, który ma dostęp publiczny.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Wskazuje obiekt z dostępem prywatnym.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Wskazuje obiekt z dostępem chronionym.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Wskazuje obiekt, który ma końcowy dostęp.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Wskazuje globalny magazyn.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Wskazuje magazyn statyczny.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Wskazuje obiekt, który jest właściwością.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Wskazuje magazyn wirtualny.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Wskazuje, że typem obiektu jest stała.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Wskazuje, że to miejsce jest zsynchronizowane z wątkiem.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Wskazuje, że to miejsce jest nietrwałe w odniesieniu do magazynu trwałego.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Wskazuje, że to miejsce ma atrybuty powyżej i wykracza poza te wstępnie zdefiniowane bity.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Wskazuje, że wartość jest wartością zwracaną z funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są również używane do filtrowania elementów podrzędnych obiektu. Wartości mogą być połączone z bitowym lub.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty  interfejsu](../../winscript/reference/idebugproperty-interface.md)  
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)