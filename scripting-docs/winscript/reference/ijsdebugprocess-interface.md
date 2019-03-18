---
title: IJsDebugProcess Interface | Microsoft Docs
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
ms.openlocfilehash: 411679a03daf27046fdcede7ff48e76212bbd2fd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58158922"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess — Interfejs
Zawiera procedury kontroli procesu docelowego i sprawdzania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint, metoda](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Ustawia punkt przerwania w położeniu określonego dokumentu.|  
|[IJsDebugProcess::CreateStackWalker, metoda](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metoda fabryki tworząca analizatora pamięci stosu.|  
|[IJsDebugProcess::PerformAsyncBreak, metoda](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Ustawia aparat obsługi skryptów w trybie przerwania, powodując przerwanie w następnej instrukcji skryptu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)