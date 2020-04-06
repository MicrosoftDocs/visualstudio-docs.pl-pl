---
title: Uruchamianie debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738456"
---
# <a name="launch-the-debugger"></a>Uruchamianie debugera
Uruchamianie debugera wymaga wysłania poprawnej sekwencji metod i zdarzeń z ich odpowiednich atrybutów.

## <a name="sequences-of-methods-and-events"></a>Sekwencje metod i zdarzeń

1. Menedżer debugowania sesji (SDM) jest wywoływany przez wybranie menu **Debugowania,** a następnie **wybranie**opcji Start . Aby uzyskać więcej informacji, zobacz [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md).

2. SDM wywołuje [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.

3. Na podstawie modelu procesu aparatu debugowania `IDebugProgramNodeAttach2::OnAttach` (DE) metoda zwraca jedną z następujących metod, która określa, co dzieje się dalej.

     Jeśli `S_FALSE` zwraca, aparat debugowania (DE) ma zostać załadowany w procesie maszyny wirtualnej.

     — lub —

     Jeśli `S_OK` zwraca, DE ma być ładowany w procesie SDM. Następnie sdm wykonuje następujące zadania:

    1. Wywołuje [GetEngineInfo,](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) aby uzyskać informacje o silniku DE.

    2. Współtworzy DE.

    3. [Dołączanie](../../extensibility/debugger/reference/idebugengine2-attach.md)połączeń .

4. DE wysyła [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM `EVENT_SYNC` z atrybutem.

5. DE wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM `EVENT_SYNC` z atrybutem.

6. DE wysyła [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do SDM `EVENT_SYNC` z atrybutem.

7. DE wysyła [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM `EVENT_SYNC` z atrybutem.

8. DE wysyła [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM `EVENT_SYNC` z atrybutem.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
- [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)
