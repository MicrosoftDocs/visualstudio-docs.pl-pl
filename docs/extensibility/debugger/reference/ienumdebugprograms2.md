---
title: Program IEnumDebug2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715569"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Ten interfejs wylicza programy uruchomione w bieżącej sesji debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby zapewnić listę programów są debugowane przez DE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio wywołuje [EnumPrograms,](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) aby uzyskać ten interfejs. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) nie jest używany przez program Visual Studio.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugPrograms2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Pobiera określoną liczbę programów w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Pomija określoną liczbę programów w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Pobiera liczbę programów w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Visual Studio używa tego interfejsu do:

- Wypełnij okno **Moduły** (wywołując [EnumPrograms,](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) a następnie wywołując [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) w każdym programie).

- Wypełnij dołącz **do procesu** listy `IDebugProcess2::EnumPrograms` (wywołując, a następnie wywołując [QueryInterface](/cpp/atl/queryinterface) na każdym interfejsie [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) aby uzyskać interfejs [IDebugEngineProgram2).](../../../extensibility/debugger/reference/idebugengineprogram2.md)

- Generowanie listy DEs, które mogą debugować każdy program w procesie (za pomocą [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Zastosuj aktualizacje edycji i kontynuowania (ENC) do każdego programu (wywołując IDebugProcess2::EnumPrograms, a następnie wywołując [GetENCUpdate).](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
