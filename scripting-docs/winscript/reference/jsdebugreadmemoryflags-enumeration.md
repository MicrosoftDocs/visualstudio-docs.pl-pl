---
title: JsDebugReadMemoryFlags, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571697"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Wyliczenie JsDebugReadMemoryFlags
Flagi określające zachowanie podczas odczytu pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Wskazuje, że obiekt wywołujący chce, aby operacja odczytu zakończyła się pomyślnie, jeśli tylko część odczytu pamięci zakończyła się powodzeniem. W przypadku ustawienia tej opcji błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS zostanie zgłoszony tylko wtedy, gdy element "Address" jest nieprawidłowy. Jeśli ta flaga jest wyczyszczona, zostanie zgłoszony błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli jakakolwiek część żądanych pamięci nie została odczytana.|  
|`None`|Wskazuje, że obiekt wywołujący chce, aby domyślne zachowanie ReadMemory —.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)