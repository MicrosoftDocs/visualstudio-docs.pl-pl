---
title: Wysyłanie zdarzeń uruchamiania po uruchomieniu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713013"
---
# <a name="send-startup-events-after-a-launch"></a>Wysyłanie zdarzeń startowych po uruchomieniu
Po dołączonej do programu aparatu debugowania (DE) wysyła serię zdarzeń uruchamiania z powrotem do sesji debugowania.

 Zdarzenia uruchamiania wysyłane z powrotem do sesji debugowania obejmują:

- Zdarzenie tworzenia aparatu.

- Zdarzenie tworzenia programu.

- Zdarzenia tworzenia wątku i ładowania modułu.

- Zdarzenie zakończenia ładowania, wysyłane po załadowaniu kodu i gotowe do uruchomienia, ale przed wykonaniem dowolnego kodu.

  > [!NOTE]
  > Gdy to zdarzenie jest kontynuowane, zmienne globalne są inicjowane i uruchamianie procedur uruchamiania.

- Możliwe inne zdarzenia tworzenia wątku i ładowania modułu.

- Zdarzenie punktu wejścia, które sygnalizuje, że program **Main** osiągnął `WinMain`swój główny punkt wejścia, taki jak Main lub . To zdarzenie nie jest zazwyczaj wysyłane, jeśli DE dołącza do programu, który jest już uruchomiony.

  Programowo DE najpierw wysyła menedżera debugowania sesji (SDM) [interfejs IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) który reprezentuje zdarzenie tworzenia aparatu, a następnie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), który reprezentuje zdarzenie tworzenia programu.

  Zdarzenia te są zazwyczaj następuje co najmniej jeden [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) zdarzenia tworzenia wątku i [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) zdarzeń ładowania.

  Gdy kod jest ładowany i gotowy do uruchomienia, ale przed wykonaniem dowolnego kodu, DE wysyła SDM [IDebugLoadCompleteEVent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) załadować zdarzenie. Na koniec, jeśli program nie jest jeszcze uruchomiony, DE wysyła [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) zdarzenie punktu wejścia, sygnalizując, że program osiągnął swój główny punkt wejścia i jest gotowy do debugowania.

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania](../../extensibility/debugger/control-of-execution.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
