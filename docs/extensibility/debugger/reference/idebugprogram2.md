---
title: IDebugProgram2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722721"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Ten interfejs reprezentuje program uruchomiony w procesie.

## <a name="syntax"></a>Składnia

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs, aby reprezentować program w procesie. Menedżer debugowania sesji (SDM) implementuje także ten interfejs, aby podać informacje do [dołączenia](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Zdarzenie [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProgram2` .

|Metoda|Opis|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Wylicza wątki, które są uruchomione w tym programie.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Pobiera nazwę programu.|
|[GetProcess —](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Pobiera proces, w którym działa ten program.|
|[Zakończ](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Kończy ten program.|
|[Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Dołącza do tego programu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Określa, czy aparat debugowania (DE) może odłączać od programu.|
|[Odłącz](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odłącza debuger od tego programu.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Pobiera unikatowy identyfikator globalny dla tego programu.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Pobiera właściwości programu.|
|[Realizacja](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania są wyczyszczone.|
|[Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania są zachowywane.|
|[Krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Żąda zatrzymania wykonywania tego programu przy następnym uruchomieniu kodu przez jeden z jego wątków.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Pobiera nazwę i identyfikator aparatu debugowania (DE), na którym działa ten program.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Wylicza konteksty kodu dla danego położenia w pliku źródłowym.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Pobiera bajty pamięci dla tego programu.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Pobiera strumień demontażu dla tego programu lub części tego programu.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Wylicza moduły załadowane i wykonywane przez ten program.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Pobiera aktualizację Edytuj i Kontynuuj (ENC) dla tego programu.<br /><br /> Niestandardowy aparat debugowania nie implementuje tej metody (zawsze powinna zostać zwrócona `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Wylicza ścieżki kodu tego programu.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Zapisuje zrzut do pliku.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Program jest kontenerem wątków działającym w określonej architekturze czasu wykonywania, podczas gdy proces składa się z jednego lub kilku programów.

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
