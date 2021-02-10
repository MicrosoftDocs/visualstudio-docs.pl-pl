---
title: Wysyłanie zdarzeń uruchamiania po uruchomieniu | Microsoft Docs
description: Zapoznaj się z serią zdarzeń uruchamiania wysyłanych przez aparat debugowania do sesji debugowania po dołączeniu aparatu debugowania do programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5263c696f9f76c71463538d56414702e616a670
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960848"
---
# <a name="send-startup-events-after-a-launch"></a>Wysyłaj zdarzenia uruchamiania po uruchomieniu
Po dołączeniu aparatu debugowania (DE) do programu wysyła on serię zdarzeń uruchomienia z powrotem do sesji debugowania.

 Zdarzenia uruchamiania wysyłane z powrotem do sesji debugowania obejmują:

- Zdarzenie tworzenia aparatu.

- Zdarzenie tworzenia programu.

- Tworzenie wątku i zdarzenia ładowania modułu.

- Zdarzenie ukończenia ładowania wysyłane, gdy kod jest ładowany i gotowy do uruchomienia, ale przed wykonaniem dowolnego kodu.

  > [!NOTE]
  > W przypadku kontynuowania tego zdarzenia zmienne globalne są inicjowane i uruchamiane są procedury uruchamiania.

- Możliwe inne zdarzenia tworzenia wątku i ładowania modułu.

- Zdarzenie punktu wejścia, które sygnalizuje, że program osiągnął swój główny punkt wejścia, taki jak **Main** lub `WinMain` . To zdarzenie nie jest zwykle wysyłane, jeśli jest niedołączone do programu, który jest już uruchomiony.

  Program programowo, a najpierw wysyła do Menedżera debugowania sesji (SDM) Interfejs [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , który reprezentuje zdarzenie tworzenia aparatu, a następnie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), który reprezentuje zdarzenie tworzenia programu.

  Zdarzenia te są zwykle następują co najmniej jednym zdarzeniem tworzenia wątku [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) i zdarzeniami ładowania modułu [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .

  Gdy kod jest ładowany i gotowy do uruchomienia, ale przed wykonaniem dowolnego kodu, ANULUJe to zdarzenie załadowania modelu SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Na koniec, jeśli program nie jest jeszcze uruchomiony, kończy wysyłanie zdarzenia punktu wejścia [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , sygnalizując, że program osiągnął główny punkt wejścia i jest gotowy do debugowania.

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
