---
title: Wysyłanie wymaganych zdarzeń | Microsoft Docs
description: Dowiedz się więcej o uporządkowanych zdarzeniach, które są wymagane podczas tworzenia aparatu debugowania i dołączania go do programu w Visual Studio debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b04ca7ed68b975bc68fa509cdc75dc507b9603d6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902270"
---
# <a name="send-the-required-events"></a>Wysyłanie wymaganych zdarzeń
Ta procedura służy do wysyłania wymaganych zdarzeń.

## <a name="process-for-sending-required-events"></a>Proces wysyłania wymaganych zdarzeń
 Następujące zdarzenia są wymagane w tej kolejności podczas tworzenia aparatu debugowania (DE) i dołączania go do programu:

1. Wyślij [obiekt zdarzenia IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do menedżera debugowania sesji (SDM), gdy de jest zainicjowany do debugowania co najmniej jednego programu w procesie.

2. Gdy program do debugowania jest dołączony do, wyślij obiekt zdarzenia [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do modelu SDM. To zdarzenie może być zdarzeniem zatrzymania, w zależności od projektu aparatu.

3. Jeśli program jest dołączony do programu, gdy proces jest uruchomiony, wyślij obiekt zdarzenia [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do programu SDM w celu powiadomienia środowiska IDE o nowym wątku. To zdarzenie może być zdarzeniem zatrzymania, w zależności od projektu aparatu.

4. Wyślij [obiekt zdarzenia IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do programu SDM po zakończeniu ładowania debugowanych programów lub po zakończeniu dołączania do programu. To zdarzenie musi być zdarzeniem zatrzymania.

5. Jeśli aplikacja do debugowania jest uruchamiana, wyślij obiekt zdarzenia [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do modelu SDM, gdy ma zostać wykonana pierwsza instrukcja kodu w architekturze czasu wykonywania. To zdarzenie jest zawsze zdarzeniem zatrzymania. Podczas przechodzenia do sesji debugowania ide zatrzymuje się na tym zdarzeniu.

> [!NOTE]
> Wiele języków używa globalnych inicjatorów lub zewnętrznych, wstępnie skompilowanych funkcji (z biblioteki CRT lub _Main) na początku kodu. Jeśli język debugego programu zawiera jeden z tych typów elementów przed początkowym punktem wejścia, ten kod jest uruchamiany, a zdarzenie punktu wejścia jest wysyłane po osiągnięciu punktu wejścia użytkownika, takiego jak **main** lub `WinMain` , .

## <a name="see-also"></a>Zobacz też
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
