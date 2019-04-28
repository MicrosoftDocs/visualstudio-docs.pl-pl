---
title: Zadania debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 299db84fb06679bfbf9dff92234c944cbdec6295
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925820"
---
# <a name="debug-tasks"></a>Debugowanie zadań
Aby zdebugować program, należy uruchomić i aparat debugowania (DE) musi być dołączony do niego, w przeciwnym razie DE musi być dołączony do wcześniej uruchomionego programu. Po dołączeniu DE wygenerować pewnych zdarzeń uruchomienia. W odpowiedzi pakietu debugowania próbuje powiązać punkty przerwania ustawione w IDE. Gdy program osiągnie powiązany punkt przerwania, zatrzymuje i czeka na dane wejściowe użytkownika.

## <a name="in-this-section"></a>W tej sekcji
 [Problemy z zabezpieczeniami](../../extensibility/debugger/security-issues.md) omówiono kroki zabezpieczeń, które są wymagane do debugowania programu.

 [Uruchom program](../../extensibility/debugger/launching-a-program.md) zawiera instrukcje krok po kroku dotyczące sposobu określania DE, która wywołuje systemu operacyjnego, aby uruchomić program.

 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md) w tym artykule opisano proces używany do debugowania programu, w ramach procesu, który jest już uruchomiony.

 [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md) zawiera listę zdarzeń, które mają miejsce, gdy DE jest dołączony do programu, dopóki nie znajduje się w jego główny punkt wejścia program jest gotowy do debugowania.

 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md) wyjaśnia, jak DE zwykle wysyła zdarzenie punktu wejścia, to zdarzenie ukończenia obciążenia lub zdarzeń do zatrzymywania, w zależności od okoliczności.

 [Powiąż punktów przerwania](../../extensibility/debugger/binding-breakpoints.md) opisano, jak to zrobić, jeśli użytkownik ustawia punkt przerwania, IDE formulates żądanie i wyświetla monit o sesji debugowania, aby utworzyć punkt przerwania.

 [Ocena wyrażenia](../../extensibility/debugger/evaluating-expressions.md) wyjaśniono sposób tworzenia wyrażenia i co się stanie, gdy wyrażenie jest obliczane.

 [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md) wyjaśnia, jak wizualizatorów typu i przeglądarek niestandardowych są obsługiwane przez ewaluatora wyrażeń (EE).

## <a name="related-sections"></a>Sekcje pokrewne
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) opisano główne pojęcia dotyczące architektury debugowania.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) zawiera omówienie składników, które obejmują DE, EE i obsługi symboli (SH) debugowania programu Visual Studio.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) wyjaśnia, jak DE działa jednocześnie w kontekstach oceny kodu, dokumentację i wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.

## <a name="see-also"></a>Zobacz także
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)