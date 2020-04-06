---
title: Wysyłanie wymaganych zdarzeń | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712995"
---
# <a name="send-the-required-events"></a>Wysyłanie wymaganych zdarzeń
Ta procedura służy do wysyłania wymaganych zdarzeń.

## <a name="process-for-sending-required-events"></a>Proces wysyłania wymaganych zdarzeń
 Następujące zdarzenia są wymagane, w tej kolejności, podczas tworzenia aparatu debugowania (DE) i dołączania go do programu:

1. Wyślij obiekt zdarzenia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do menedżera debugowania sesji (SDM), gdy de jest inicjowany do debugowania jednego lub więcej programów w procesie.

2. Gdy program, który ma być debugowany jest dołączony do, wyślij [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) obiektu zdarzenia do SDM. To zdarzenie może być zdarzeniem zatrzymania, w zależności od projektu silnika.

3. Jeśli program jest dołączony do podczas uruchamiania procesu, wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiektu zdarzenia do SDM powiadomić IDE nowego wątku. To zdarzenie może być zdarzeniem zatrzymania, w zależności od projektu silnika.

4. Wyślij obiekt zdarzenia [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM po zakończeniu ładowania debugowanego programu lub zakończeniu dołączania do programu. To zdarzenie musi być zdarzeniem zatrzymania.

5. Jeśli aplikacja, która ma być debugowana, zostanie uruchomiona, wyślij obiekt zdarzenia [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM, gdy ma zostać wykonana pierwsza instrukcja kodu w architekturze czasu wykonywania. To zdarzenie jest zawsze zdarzeniem zatrzymującym. Podczas przechodzenia do sesji debugowania IDE zatrzymuje się w tym zdarzeniu.

> [!NOTE]
> Wiele języków używa globalnych inicjatorów lub zewnętrznych, wstępnie skompilowanych funkcji (z biblioteki CRT lub _Main) na początku ich kodu. Jeśli język debugowania programu zawiera jeden z tych typów elementów przed początkowym punktem wejścia, ten kod jest uruchamiany, **main** a `WinMain`zdarzenie punktu wejścia jest wysyłane po osiągnięciu punktu wejścia użytkownika, takiego jak main lub ,.

## <a name="see-also"></a>Zobacz też
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
