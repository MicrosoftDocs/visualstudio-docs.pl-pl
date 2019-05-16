---
title: IDebugEngineProgram2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c265cbfc89d0b637b1d2f37a3e3b9e948a8dd8f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687797"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs zapewnia obsługę debugowania wielowątkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs obsługuje jednoczesnego debugowania wielu wątków. Ten interfejs jest implementowany w ten sam obiekt, który implementuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) uzyskać ten interfejs z `IDebugProgram2` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugEngineProgram2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Zatrzymuje wszystkie wątki uruchomione w tym programie.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Oczekuje na wykonanie (lub Zatrzymaj oczekiwania na wykonanie) występuje dla danego wątku.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Zezwala lub nie zezwala na Obliczanie wyrażenia wystąpić w danym wątku, nawet jeśli program został zatrzymany.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio wywołuje ten interfejs w odpowiedzi na [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzenia i ustawić Stany "Obejrzyj dla wątku krok" i "Obejrzyj dla wyrażenia oceny w wątku" programu. [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana zawsze, gdy program jest zatrzymanie; ta metoda zapewnia program szansę, aby zakończyć wszystkie wątki.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
