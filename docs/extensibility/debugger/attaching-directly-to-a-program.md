---
title: Dołączanie bezpośrednio do programu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4bf703544bbe1932608db17addba672bfd91a70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350897"
---
# <a name="attach-directly-to-a-program"></a>Dołączanie bezpośrednio do programu
Użytkownicy, którzy chcą do debugowania programów w procesie, który zazwyczaj jest już uruchomiony, wykonaj następujące czynności:

1. W środowisku IDE, wybierz **debugowanie procesów** polecenia **narzędzia** menu.

    **Procesy** pojawi się okno dialogowe.

2. Wybierz proces, a następnie kliknij przycisk **Dołącz** przycisku.

    **Dołączyć do procesu** pojawi się okno dialogowe, wyświetlanie listy wszystkich aparaty debugowania (DEs) zainstalowane na komputerze.

3. Określ DEs na potrzeby debugowania wybranego procesu, a następnie kliknij przycisk **OK**.

   Pakiet debugowania uruchamia sesję debugowania i przekazuje listę DEs do niego. Sesji debugowania z kolei przekazuje tej listy, wraz z funkcją wywołania zwrotnego do wybranego procesu, a następnie prosi procesu wyliczania jego uruchomione programy.

   Programowe w odpowiedzi na żądanie użytkownika, debugowanie pakietu tworzy Menedżer debugowania sesji (SDM) i przekazuje listę wybranych DEs do niego. Wraz z listy, debugowanie pakietu przekazuje SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfejsu. Debugowanie pakietu przekazuje listę DEs do wybranego procesu przez wywołanie metody [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Następnie wywołuje SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porcie wyliczyć programów uruchomionych w procesie.

   Od tego momentu każdego silnika debugowania jest dołączony do programu dokładnie zgodnie z opisem w [dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md), z dwoma wyjątkami.

   W celu zwiększenia wydajności DEs, które są wdrożone na udostępnianie przestrzeń adresową SDM są grupowane, aby każdy DE ma zestaw programów, które ma być dołączone do. W tym przypadku [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) wywołania [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) i przekazuje je tablicę programy można dołączyć do.

   Drugi wyjątek to, że zdarzenia uruchamiania wysyłane przez DE, dołączając do programu, który jest już uruchomiony zwykle obejmuje zdarzenie punktu wejścia.

## <a name="see-also"></a>Zobacz także
- [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)