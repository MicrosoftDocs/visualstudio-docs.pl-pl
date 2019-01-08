---
title: Wyliczenie JsDebugReadMemoryFlags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef1f16ebcf678452f2fe4b0df3ade6350120f05
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094032"
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
|`JsDebugAllowPartialRead`|Wskazuje, że obiekt wywołujący chce, aby operacja odczytu osiągnęła sukces, jeśli tylko część pamięci odczytu zakończyło się pomyślnie. Jeśli ta opcja jest ustawiona, błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS tylko będzie zgłaszany, jeśli "Adres" jest nieprawidłowa. Jeśli ta flaga jest wyczyszczona, zostanie wygenerowany błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli jakakolwiek część żądanej pamięci nie dała się odczytać.|  
|`None`|Wskazuje, że obiekt wywołujący chce zachowania domyślnego dla obiektu ReadMemory.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)