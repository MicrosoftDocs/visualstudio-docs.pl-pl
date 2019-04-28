---
title: Wysyłanie zdarzeń uruchamiania po uruchomieniu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f82ab0b28c1052a0d6a4cb0b2db7e6bbaaba8cc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420584"
---
# <a name="send-startup-events-after-a-launch"></a>Wysyłanie zdarzeń uruchamiania po uruchomieniu
Gdy aparat debugowania (Niemcy) jest dołączony do programu, wysyła szereg zdarzeń uruchamiania powrót do sesji debugowania.

 Zdarzenia uruchamiania wysyłanych z powrotem do sesji debugowania, obejmują:

- Zdarzenie tworzenia aparatu.

- Zdarzenie tworzenia programu.

- Wątek, tworzenia i zdarzeń ładowania modułu.

- Ładowanie ukończone zdarzenie wysyłane, gdy kod jest załadowany i gotowa do uruchomienia, ale przed wykonaniem jakiegokolwiek kodu.

  > [!NOTE]
  > Gdy to zdarzenie jest kontynuowany, zmienne globalne są inicjowane i uruchamianie procedury uruchamiania.

- Możliwe innych wątków, tworzenia i zdarzeń ładowania modułu.

- Zdarzenie punktu wejścia sygnalizuje, że program został osiągnięty jego główny punkt wejścia, takich jak **Main** lub `WinMain`. To zdarzenie nie są zwykle wysyłane, jeśli DE dołącza do programu, który jest już uruchomiony.

  Programowo, DE najpierw wysyła Menedżer debugowania sesji (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfejs, który przedstawia zdarzenie tworzenia aparatu, a następnie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , która reprezentuje zdarzenie tworzenia programu.

  Zdarzenia te są zwykle następuje co najmniej jeden [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) wątek zdarzenia tworzenia i [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) zdarzeń ładowania modułu.

  Gdy kod jest załadowany i gotowa do uruchomienia, ale przed wykonaniem jakiegokolwiek kodu DE wysyła SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) zdarzenie ukończenia obciążenia. Na koniec, jeśli program nie jest już uruchomiona, wysyła DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) zdarzenie punktu wejścia, sygnalizowania, że program osiągnęła jego główny punkt wejścia i jest gotowy do debugowania.

## <a name="see-also"></a>Zobacz także
- [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)