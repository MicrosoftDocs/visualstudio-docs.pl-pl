---
title: 'IDebugApplication:: HandleBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574966"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Powoduje, że bieżący wątek blokuje i wysyła powiadomienie o punkcie przerwania do środowiska IDE debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `br`  
 podczas Powód przerwania.  
  
 `pbra`  
 określoną Akcja podejmowana, gdy debuger wznawia działanie aplikacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat języka wywołuje tę metodę w kontekście wątku, który trafi punkt przerwania. Ta metoda blokuje bieżący wątek i wysyła powiadomienie punktu przerwania do środowiska IDE debugera. Gdy debuger wznawia działanie aplikacji, parametr `pbra` określa akcję do wykonania.  
  
> [!NOTE]
> Aparat języka może być wywoływany przez wątek w celu wykonywania zadań, takich jak wyliczanie ramek stosu lub obliczanie wyrażeń w punkcie przerwania.  
  
 Ta metoda powoduje wywoływanie `IApplicationDebugger::onHandleBreakPoint`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication  interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
   [Wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md)  
 [BREAKRESUMEACTION, wyliczenie](../../winscript/reference/breakresumeaction-enumeration.md)