---
title: Interfejs IDebugPropertyEnumType_All | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b9ddd9fb24aa83a6027d6d705de6a748a96b2e28
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149302"
---
# <a name="idebugpropertyenumtypeall-interface"></a>Interfejs IDebugPropertyEnumType_All
`IDebugPropertyEnumType` Interfejsy są zdefiniowane, tak aby każda z ich IID mogą być przekazywane jako filtr, aby `IDebugProperty::EnumMembers` podczas żądania odpowiedniego modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Zwraca ciąg tekst opisujący nazwę|  
  
 Następujące interfejsy dziedziczyć `IDebugPropertyEnumType_All`, i mieć żadnych dodatkowych metod.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)