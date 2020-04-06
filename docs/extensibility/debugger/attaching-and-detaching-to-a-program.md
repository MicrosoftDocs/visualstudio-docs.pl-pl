---
title: Dołączanie i odłączanie do programu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739272"
---
# <a name="attaching-and-detaching-to-a-program"></a>Dołączanie i odłączanie do programu
Dołączanie debugera wymaga wysłania poprawnej sekwencji metod i zdarzeń z odpowiednimi atrybutami.

## <a name="sequence-of-methods-and-events"></a>Kolejność metod i zdarzeń

1. Menedżer debugowania sesji (SDM) wywołuje [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.

    Na podstawie modelu procesu aparatu debugowania `IDebugProgramNodeAttach2::OnAttach` (DE) metoda zwraca jedną z następujących metod, która określa, co dzieje się dalej.

    Jeśli `S_FALSE` jest zwracany, aparat debugowania został pomyślnie dołączony do programu. W przeciwnym razie [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest wywoływana, aby zakończyć proces dołączania.

    Jeśli `S_OK` jest zwracany, DE ma być ładowany w tym samym procesie co SDM. SDM wykonuje następujące zadania:

   1. Wywołuje [GetEngineInfo,](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) aby uzyskać informacje o silniku DE.

   2. Współtworzy DE.

   3. [Dołączanie](../../extensibility/debugger/reference/idebugengine2-attach.md)połączeń .

2. DE wysyła [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM `EVENT_SYNC` z atrybutem.

3. DE wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM `EVENT_SYNC` z atrybutem.

4. DE wysyła [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM `EVENT_SYNC_STOP` z atrybutem.

   Odłączanie od programu jest prostym, dwuetapowym procesem, w następujący sposób:

5. SDM wywołuje [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. DE wysyła [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
