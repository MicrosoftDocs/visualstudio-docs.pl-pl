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
ms.openlocfilehash: 5e3444e6eedde9576216552e41abb0e97aafa2d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412377"
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
> Aparat języka może zostać wywołana przez wątek wykonywania zadań, takich jak wyliczanie stosu ramki lub obliczać wyrażeń podczas punkt przerwania.  
  
 Ta metoda powoduje `IApplicationDebugger::onHandleBreakPoint` do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION, wyliczenie](../../winscript/reference/breakresumeaction-enumeration.md)