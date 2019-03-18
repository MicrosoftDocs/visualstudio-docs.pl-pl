---
title: Wyliczenie JsDebugReadMemoryFlags | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58156414"
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