---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 372c119b6a841d7d4b349e85548914f7641b53d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753613"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje program, który jest uruchomiony w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i dostawcy niestandardowego portu należy zaimplementować ten interfejs do reprezentowania program w procesie. Menedżer debugowania sesji (SDM) również implementuje ten interfejs, aby zapewnić informacje [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProgram2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Wylicza wątków, które są uruchomione w tym programie.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Pobiera nazwę programu.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Pobiera procesu, który tego programu.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Przerywa ten program.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Dołącza do tego programu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Określa, jeśli aparat debugowania (DE) można odłączyć od program.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odłącza debuger z tego programu.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Pobiera unikatowy identyfikator globalny dla tego programu.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Pobiera program właściwości.|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Nadal uruchomiony ten program w stanie zatrzymania. Jest wyczyszczone wszelkie poprzedniego stanu wykonywania.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Nadal uruchomiony ten program w stanie zatrzymania. Dowolnego poprzedniego stanu wykonywania są zachowywane.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Żądania, że ten program zatrzymać wykonywanie następnej czasu jeden z jego kod uruchamia wątków.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Pobiera nazwę i identyfikator aparat debugowania (DE), program został uruchomiony.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Wylicza kontekstów kodu dla danego stanowiska w pliku źródłowym.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Pobiera bajtów pamięci dla tego programu.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Pobiera strumień dezasemblacji dla tego programu lub część tego programu.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Wylicza modułów, w których ten program został załadowany i jest wykonywany.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Pobiera aktualizację Edytuj i Kontynuuj (ENC) dla tego programu.<br /><br /> Niestandardowego aparatu debugowania nie obsługuje tej metody (zawsze powinna zwrócić `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Wylicza ścieżki kodu, w tym programie.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Zapisuje plik zrzutu.|  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Program jest kontenerem wątków, uruchomiony w ramach określonej architektury czasu wykonywania, podczas procesu składa się z jednego lub wielu programów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
