---
title: JS_PROPERTY_MEMBERS, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_MEMBERS
apilocation:
- jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3645e95859e2c2b785e01c7ee9a3cbee8155138d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571731"
---
# <a name="js_property_members-enumeration"></a>Wyliczenie JS_PROPERTY_MEMBERS
Flagi określające typ informacji, które będą zwracane w żądaniu o dane elementów członkowskich obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum JS_PROPERTY_MEMBERS{   JS_PROPERTY_MEMBERS_ALL = 0,   JS_PROPERTY_MEMBERS_ARGUMENTS = 1} JS_PROPERTY_MEMBERS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|Reprezentuje żądanie wyliczenia wszystkich elementów członkowskich.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|Reprezentuje żądanie wyliczenia tylko argumentów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)