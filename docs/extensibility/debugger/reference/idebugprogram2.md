---
title: Program IDebug2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722721"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Ten interfejs reprezentuje program, który jest uruchomiony w procesie.

## <a name="syntax"></a>Składnia

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs do reprezentowania programu w procesie. Menedżer debugowania sesji (SDM) implementuje również ten interfejs, aby dostarczyć informacje do [dołączania](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [Zdarzenie IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod na wielu interfejsach.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProgram2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Wylicza wątki, które są uruchomione w tym programie.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Pobiera nazwę programu.|
|[GetProcess ( GetProcess )](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Pobiera proces, w który jest uruchomiony w tym programie.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Kończy ten program.|
|[Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Dołącza do tego programu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Określa, czy aparat debugowania (DE) może odłączyć się od programu.|
|[Odłącz](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odłącza debugera od tego programu.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Pobiera globalnie unikatowy identyfikator dla tego programu.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Pobiera właściwości programu.|
|[Realizacja](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Kontynuuje uruchamianie tego programu ze stanu zatrzymanego. Każdy poprzedni stan wykonania jest wyczyszczony.|
|[Kontynuować](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Kontynuuje uruchamianie tego programu ze stanu zatrzymanego. Każdy poprzedni stan wykonania jest zachowywany.|
|[Krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Żąda, aby ten program zatrzymać wykonanie następnym razem, gdy jeden z jego wątków uruchamia kod.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Pobiera nazwę i identyfikator aparatu debugowania (DE) z uruchomionym tym programem.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Wylicza konteksty kodu dla danej pozycji w pliku źródłowym.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Pobiera bajtów pamięci dla tego programu.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Pobiera strumień demontażu dla tego programu lub części tego programu.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Wylicza moduły, które ten program załadował i jest wykonywany.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Pobiera aktualizację Edycji i Kontynuuj (ENC) dla tego programu.<br /><br /> Niestandardowy aparat debugowania nie implementuje tej `E_NOTIMPL`metody (zawsze powinna zwracać).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Wylicza ścieżki kodu tego programu.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Zapisuje zrzut do pliku.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Program jest kontenerem wątku uruchomionym w określonej architekturze w czasie wykonywania, podczas gdy proces składa się z jednego lub więcej programów.

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
