---
title: DBGPROP_INFO_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 517999bce9c85475bd91ad2e54e7ed49cda23aab
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095761"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Używany do określenia `DebugPropertyInfo` pola  
  
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
 Inicjuje `bstrName` pola.  
  
 DBGPROP_INFO_TYPE  
 Inicjuje `bstrType` pola.  
  
 DBGPROP_INFO_VALUE  
 Inicjuje `bstrValue` pola.  
  
 DBGPROP_INFO_FULLNAME  
 Inicjuje `bstrFullName` pola.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Inicjuje `dwAttrib` pola.  
  
 DBGPROP_INFO_DEBUGPROP  
 Inicjuje `pDebugProp` pola, które zawiera `IDebugProperty` interfejsu.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Oznacza, że wartość pola może zawierać wartość rozwinięte automatycznie, jeśli są dostępne dla tego typu obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)