---
title: Interfejs IDebugPropertyEnumType_All | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574316"
---
# <a name="idebugpropertyenumtype_all-interface"></a>Interfejs IDebugPropertyEnumType_All
Interfejsy `IDebugPropertyEnumType` są zdefiniowane w taki sposób, że każdy z ich IID można przesłać jako filtr do `IDebugProperty::EnumMembers` podczas żądania odpowiedniego modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Zwraca ciąg tekstowy opisujący nazwę|  
  
 Poniższe interfejsy dziedziczą z `IDebugPropertyEnumType_All` i nie mają żadnych dodatkowych metod.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)