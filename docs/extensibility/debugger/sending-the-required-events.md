---
title: Wysyłanie wymaganych zdarzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ef1bb6c436faaefb309ab62db02ee43a0486ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345594"
---
# <a name="send-the-required-events"></a>Wysyłanie wymaganych zdarzeń
Użyj tej procedury związane z przesyłaniem zdarzeń wymagane.

## <a name="process-for-sending-required-events"></a>Proces wysyłanie wymaganych zdarzeń
 Następujące zdarzenia są wymagane w następującej kolejności podczas tworzenia debugowania aparatu (DE) i dołączania ich do programu:

1. Wyślij [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) obiekt zdarzenia do Menedżer debugowania sesji (SDM) DE jest inicjowany do jednego lub wielu programów w procesie debugowania.

2. Gdy program ma być debugowany jest dołączony do, Wyślij [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) obiekt zdarzenia do SDM. To zdarzenie może być to zdarzenie zatrzymywania, w zależności od projektu aparatu.

3. Jeśli program jest dołączony do, gdy proces jest uruchamiany, Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiekt zdarzenia do SDM, by powiadomić IDE nowy wątek. To zdarzenie może być to zdarzenie zatrzymywania, w zależności od projektu aparatu.

4. Wyślij [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) obiekt zdarzenia do SDM po debugowanego Zakończono ładowania lub po wykonaniu dołączanie do programu. To zdarzenie musi być zdarzeń zatrzymywania.

5. Jeśli nie uruchomiono aplikacji przeznaczonej do debugowania, Wyślij [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) obiekt zdarzenia do SDM, gdy pierwsza instrukcja kodu w architekturze środowiska wykonawczego ma zostać wykonana. To zdarzenie jest zawsze zdarzeń zatrzymywania. Po przejściu do sesji debugowania, IDE zatrzymuje się na to zdarzenie.

> [!NOTE]
> Wiele języków użycia inicjatorów globalnych lub zewnętrznymi, wstępnie skompilowanych funkcji (od biblioteki CRT lub _Main) na początku swój kod. Jeśli język programu debugowania zawierają dowolne z tych typów elementów przed punktu wejścia początkowej, ten kod jest uruchamiany i jest wysyłane zdarzenie punktu wejścia po użytkownik punkt wejścia, takich jak **głównego** lub `WinMain`, jest osiągnięta.

## <a name="see-also"></a>Zobacz także
- [Włączanie programu do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)