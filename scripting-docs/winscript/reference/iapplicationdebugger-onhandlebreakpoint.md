---
title: IApplicationDebugger::onHandleBreakPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edf8816cd646596ce1f897dfd9d949790d52b7b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148220"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Obsługuje zdarzenie punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prpt`  
 [in] Wątek, gdzie wystąpił punkt przerwania.  
  
 `br`  
 [in] Przyczyna punkt przerwania.  
  
 `pError`  
 [in] Informacje o błędzie środowiska uruchomieniowego, pod warunkiem, gdy wartość `br` jest BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy punkt przerwania zostaje trafiony i `IDebugApplication::HandleBreakPoint` jest wywoływana.  
  
 Aplikacja pozostanie wstrzymany, dopóki nie wywołuje debugera IDE `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON, wyliczenie](../../winscript/reference/breakreason-enumeration.md)