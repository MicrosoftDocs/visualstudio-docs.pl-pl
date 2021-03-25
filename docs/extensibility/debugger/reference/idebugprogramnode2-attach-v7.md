---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft Docs'
description: Ta metoda interfejsu jest stara, przestarzałą metodą Attach używaną przed Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c949bba45457917e4dd00bdc05bc300f3a38eb7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053597"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Przestarzałe. NIE NALEŻY UŻYWAĆ.

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
podczas Interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program do dołączenia.

`pCallback`\
podczas Interfejs [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który ma być używany do wysyłania zdarzeń debugowania do modelu SDM.

`dwReason`\
podczas Wartość z wyliczenia [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , która określa przyczynę dołączenia.

## <a name="return-value"></a>Wartość zwracana

Implementacja powinna zawsze zwrócić `E_NOTIMPL` .

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Począwszy od programu Visual Studio 2005, ta metoda nie jest już używana i zawsze powinna zostać zwrócona `E_NOTIMPL` . Zapoznaj się z interfejsem [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) , jeśli węzeł programu ma wskazywać, że nie można go dołączyć do programu, lub jeśli węzeł programu jest po prostu ustawiony na program `GUID` . W przeciwnym razie Zaimplementuj metodę [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="prior-to-visual-studio-2005"></a>Przed Visual Studio 2005

Ta metoda musi być implementowana tylko wtedy, gdy wszystkie uruchomienia w przestrzeni adresowej debugowanego programu. W przeciwnym razie ta metoda powinna zwrócić `S_FALSE` .

Gdy ta metoda jest wywoływana, element DE musi wysłać obiekt zdarzenia [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , jeśli nie został jeszcze wysłany do tego wystąpienia interfejsu [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , a także obiektów zdarzeń [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Obiekt zdarzenia [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) jest następnie wysyłany, jeśli `dwReason` parametr ma wartość `ATTACH_REASON_LAUNCH` .

DE musi wywołać metodę [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na obiekcie [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dostarczonym przez obiekt zdarzenia [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i musi przechowywać identyfikator GUID tego programu w danych wystąpienia dla `IDebugProgram2` obiektu zaimplementowanego przez de.

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
