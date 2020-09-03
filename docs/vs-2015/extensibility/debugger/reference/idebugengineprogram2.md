---
title: IDebugEngineProgram2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687797"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs zapewnia obsługę debugowania wielowątkowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs do obsługi jednoczesnego debugowania wielu wątków. Ten interfejs jest zaimplementowany dla tego samego obiektu, który implementuje interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , aby uzyskać ten interfejs z `IDebugProgram2` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugEngineProgram2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Przerywa wszystkie wątki działające w tym programie.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Czujki do wykonania (lub zatrzymania oglądania pod kątem wykonania) mogą wystąpić w danym wątku.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Zezwala (lub nie zezwala) na Obliczanie wyrażenia w danym wątku, nawet jeśli program został zatrzymany.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio wywołuje ten interfejs w odpowiedzi na zdarzenie [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i ustawia wartość "Watch dla kroku wątku" i "Watch for Expression Evaluation" w przypadku programu. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana za każdym razem, gdy program ma zostać zatrzymany; Ta metoda umożliwia programowi zakończenie wszystkich wątków.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
