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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67764a7f59c1b44e7e8cbc7a81befb120c541461
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094669"
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

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
- [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)
