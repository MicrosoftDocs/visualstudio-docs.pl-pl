---
title: IDebugApplication::HandleBreakPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b05288a8863b2c555493d4a3f7ea8e2b7537d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146724"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o punkt przerwania do debugera w IDE.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `br`  
 [in] Powód przerwania.  
  
 `pbra`  
 [out] Akcja do wykonania, gdy debuger wznawia działanie aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat języka wywołuje tę metodę w kontekście wątku, który trafienia punktu przerwania. Ta metoda blokują bieżący wątek i wysyła powiadomienie punkt przerwania do debugera w IDE. Gdy debuger wznowieniu działania aplikacji, `pbra` parametr określa, jaką akcję należy podjąć.  
  
> [!NOTE]
>  Aparat języka może zostać wywołana przez wątek wykonywania zadań, takich jak wyliczanie stosu ramki lub obliczać wyrażeń podczas punkt przerwania.  
  
 Ta metoda powoduje `IApplicationDebugger::onHandleBreakPoint` do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION, wyliczenie](../../winscript/reference/breakresumeaction-enumeration.md)