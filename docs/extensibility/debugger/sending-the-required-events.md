---
title: Wysyłanie wymaganych zdarzeń | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712995"
---
# <a name="send-the-required-events"></a>Wyślij wymagane zdarzenia
Użyj tej procedury, aby wysłać wymagane zdarzenia.

## <a name="process-for-sending-required-events"></a>Proces wysyłania wymaganych zdarzeń
 Podczas tworzenia aparatu debugowania (DE) i dołączania do programu wymagane są następujące zdarzenia:

1. Wyślij obiekt zdarzenia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do Menedżera debugowania sesji (SDM), gdy wyjątek jest zainicjowany do debugowania jednego lub kilku programów w procesie.

2. Gdy jest dołączony program do debugowania, Wyślij obiekt zdarzenia [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do modelu SDM. To zdarzenie może być zdarzeniem zatrzymania, w zależności od projektu aparatu.

3. Jeśli program jest dołączony do momentu uruchomienia procesu, Wyślij obiekt zdarzenia [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do modelu SDM, aby powiadomić IDE o nowym wątku. To zdarzenie może być zdarzeniem zatrzymania, w zależności od projektu aparatu.

4. Wyślij obiekt zdarzenia [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do modelu SDM, gdy debugowany program zakończył ładowanie lub po zakończeniu dołączania do programu. To zdarzenie musi być zdarzeniem zatrzymania.

5. Jeśli uruchamiana jest aplikacja, która ma być debugowana, Wyślij obiekt zdarzenia [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do modelu SDM, gdy pierwsza instrukcja kodu w architekturze czasu wykonywania ma zostać wykonana. To zdarzenie jest zawsze zdarzeniem zatrzymywania. Podczas przechodzenia do sesji debugowania środowisko IDE zostaje zatrzymane na tym zdarzeniu.

> [!NOTE]
> W wielu językach są używane globalne inicjatory lub zewnętrzne, wstępnie skompilowane funkcje (z biblioteki CRT lub _Main) na początku ich kodu. Jeśli język debugowania programu zawiera jeden z tych typów elementów przed początkowym punktem wejścia, ten kod jest uruchamiany, a zdarzenie punktu wejścia jest wysyłane, gdy punkt wejścia użytkownika, taki jak **Main** lub `WinMain` , zostanie osiągnięty.

## <a name="see-also"></a>Zobacz też
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
