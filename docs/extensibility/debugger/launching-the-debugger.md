---
title: Uruchamianie debugera | Microsoft Docs
description: Dowiedz się więcej na temat sekwencji metod i zdarzeń z odpowiednimi atrybutami wymaganymi do uruchomienia debugera.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 40b91ae695a5e78745c01c5ac974411ac924f8f0
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606661"
---
# <a name="launch-the-debugger"></a>Uruchom debuger
Uruchomienie debugera wymaga wysłania odpowiedniej sekwencji metod i zdarzeń z odpowiednimi atrybutami.

## <a name="sequences-of-methods-and-events"></a>Sekwencje metod i zdarzeń

1. Menedżer debugowania sesji (SDM) jest wywoływany przez wybranie menu **Debuguj** , a następnie polecenie **Uruchom**. Aby uzyskać więcej informacji, zobacz [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md).

2. Metoda [dołączania](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) modelu SDM.

3. W oparciu o model procesów aparatu debugowania (DE) `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca jedną z następujących metod, która określa, co się stanie dalej.

     Jeśli `S_FALSE` zwraca, aparat debugowania (de) jest ładowany w procesie maszyny wirtualnej.

     -lub-

     Jeśli `S_OK` zwraca, to de ma być załadowany w procesie modelu SDM. Model SDM wykonuje następnie następujące zadania:

    1. Wywołuje [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) , aby uzyskać informacje o aparacie.

    2. Współtworzenie.

    3. [Dołączone](../../extensibility/debugger/reference/idebugengine2-attach.md)wywołania.

4. Element DE wysyła [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

5. Element DE wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

6. Element DE wysyła [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

7. Element DE wysyła [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

8. Element DE wysyła [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do modelu SDM z `EVENT_SYNC` atrybutem.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
- [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)
