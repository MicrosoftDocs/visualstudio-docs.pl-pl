---
title: Dołączanie i odłączanie do programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a751e6aa70c1aacd5df598e0c0e62da3b9d14b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903153"
---
# <a name="attaching-and-detaching-to-a-program"></a>Dołączanie i odłączanie do programu
Dołączenie debugera wymaga wysłania odpowiedniej sekwencji metod i zdarzeń z odpowiednimi atrybutami.

## <a name="sequence-of-methods-and-events"></a>Sekwencja metod i zdarzeń

1. Menedżer debugowania sesji (SDM) wywołuje metodę [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

    W oparciu o model procesów aparatu debugowania (DE) `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca jedną z następujących metod, która określa, co się stanie dalej.

    Jeśli `S_FALSE` jest zwracana, aparat debugowania został pomyślnie dołączony do programu. W przeciwnym razie metoda [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) jest wywoływana w celu dokończenia procesu dołączania.

    Jeśli `S_OK` jest zwracana, wartość de jest załadowana w tym samym procesie co model SDM. Model SDM wykonuje następujące zadania:

   1. Wywołuje [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) , aby uzyskać informacje o aparacie.

   2. Współtworzenie.

   3. [Dołączone](../../extensibility/debugger/reference/idebugengine2-attach.md)wywołania.

2. Element DE wysyła [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

3. Element DE wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

4. Element DE wysyła [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do modelu SDM z `EVENT_SYNC_STOP` atrybutem.

   Odłączanie od programu to prosty, dwuetapowy proces w następujący sposób:

5. Wywołania modelu SDM [odłączają](../../extensibility/debugger/reference/idebugprogram2-detach.md)się.

6. Element DE wysyła [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
