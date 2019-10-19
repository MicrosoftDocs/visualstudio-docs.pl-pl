---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572579"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Służy do określania pól `DebugPropertyInfo`  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DBGPROP_INFO_NAME  
 Inicjuje pole `bstrName`.  
  
 DBGPROP_INFO_TYPE  
 Inicjuje pole `bstrType`.  
  
 DBGPROP_INFO_VALUE  
 Inicjuje pole `bstrValue`.  
  
 DBGPROP_INFO_FULLNAME  
 Inicjuje pole `bstrFullName`.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Inicjuje pole `dwAttrib`.  
  
 DBGPROP_INFO_DEBUGPROP  
 Inicjuje `pDebugProp` pole, które zawiera interfejs `IDebugProperty`.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Określa, że pole wartości powinno zawierać wartość autoexpanded (jeśli jest dostępna) dla tego typu obiektu.  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [struktury DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)