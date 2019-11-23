---
title: 'IApplicationDebugger:: onHandleBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577840"
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
 podczas Wątek, w którym wystąpiło punkt przerwania.  
  
 `br`  
 podczas Przyczyna punktu przerwania.  
  
 `pError`  
 podczas Informacje o błędzie środowiska uruchomieniowego, pod warunkiem, że wartość `br` jest BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy punkt przerwania jest trafiony i `IDebugApplication::HandleBreakPoint` jest wywoływana.  
  
 Aplikacja pozostanie zawieszona do momentu wywołania środowiska IDE debugera `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Zobacz także  
 [IApplicationDebugger  interfejsu](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON, wyliczenie](../../winscript/reference/breakreason-enumeration.md)