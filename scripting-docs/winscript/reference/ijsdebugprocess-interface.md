---
title: Interfejs IJsDebugProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577349"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess — Interfejs
Zawiera procedury do sprawdzania i kontrolowania procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint, metoda](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Ustawia punkt przerwania w określonym położeniu dokumentu.|  
|[IJsDebugProcess::CreateStackWalker, metoda](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metoda fabryki analizatora stosu.|  
|[IJsDebugProcess::PerformAsyncBreak, metoda](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Przełącza aparat skryptu w tryb przerwania, powodując przerwanie w następnej instrukcji skryptu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)