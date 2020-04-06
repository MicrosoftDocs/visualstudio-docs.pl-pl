---
title: IDebugProgramNode2::Attach_V7 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722141"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Przestarzałe. NIE UŻYWAĆ.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Parametry

`pMDMProgram`\
[w] Interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) reprezentujący program do dołączenia.

`pCallback`\
[w] Interfejs [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) który ma być używany do wysyłania zdarzeń debugowania do SDM.

`dwReason`\
[w] Wartość z [wyliczenia ATTACH_REASON,](../../../extensibility/debugger/reference/attach-reason.md) która określa przyczynę dołączania.

## <a name="return-value"></a>Wartość zwracana

Implementacja powinna `E_NOTIMPL`zawsze zwracać .

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Od programu Visual Studio 2005 ta metoda nie `E_NOTIMPL`jest już używana i zawsze powinna zwracać . Zobacz interfejs [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) dla alternatywnego podejścia, jeśli węzeł programu musi wskazać, że nie można `GUID`go podłączyć lub jeśli węzeł programu po prostu ustawia program . W przeciwnym razie należy zaimplementować [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.

## <a name="prior-to-visual-studio-2005"></a>Przed programem Visual Studio 2005

Ta metoda musi być zaimplementowana tylko wtedy, gdy DE działa w przestrzeni adresowej programu jest debugowany. W przeciwnym razie `S_FALSE`ta metoda powinna zwrócić .

Gdy ta metoda jest wywoływana, DE musi wysłać [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) obiektu zdarzenia, jeśli nie został już wysłany dla tego wystąpienia interfejsu [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) a także [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) obiektów zdarzeń. Obiekt zdarzenia [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) jest `dwReason` wysyłany, `ATTACH_REASON_LAUNCH`jeśli parametr jest .

DE musi wywołać [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metody na [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiektu dostarczonego przez [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) obiektu zdarzenia i musi przechowywać identyfikator GUID tego programu w danych wystąpienia dla `IDebugProgram2` obiektu zaimplementowanego przez DE.

## <a name="see-also"></a>Zobacz też

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
