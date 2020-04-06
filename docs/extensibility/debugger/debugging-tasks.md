---
title: Zadania debugowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738959"
---
# <a name="debug-tasks"></a>Zadania debugowania
Aby debugować program, musi zostać uruchomiony i aparat debugowania (DE) musi być dołączony do niego, w przeciwnym razie DE musi być dołączony do wcześniej uruchomionego programu. Po dołączeniu DE musi generować pewne zdarzenia uruchamiania. W odpowiedzi pakiet debugowania próbuje powiązać punkty przerwania ustawione w IDE. Gdy program osiągnie powiązany punkt przerwania, zatrzymuje się i czeka na dane wejściowe użytkownika.

## <a name="in-this-section"></a>W tej sekcji
 [Problemy z bezpieczeństwem](../../extensibility/debugger/security-issues.md) W tym artykule omówiono kroki zabezpieczeń, które są potrzebne do debugowania programu.

 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md) Zawiera instrukcje krok po kroku dotyczące określania de, który wywołuje system operacyjny, aby uruchomić program.

 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md) Opisuje proces używany do debugowania programu w procesie, który jest już uruchomiony.

 [Wysyłanie zdarzeń startowych po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Wyświetla listę zdarzeń, które mają miejsce po de jest dołączony do programu, dopóki program jest w głównym punkcie wejścia i jest gotowy do debugowania.

 [Kontrola wykonania](../../extensibility/debugger/control-of-execution.md) W tym artykule wyjaśniono, jak DE zazwyczaj wysyła zdarzenie punktu wejścia, zdarzenie zakończenia obciążenia lub zdarzenie zatrzymania, w zależności od okoliczności.

 [Punkty przerwania wiązania](../../extensibility/debugger/binding-breakpoints.md) Opisuje, jak, jeśli użytkownik ustawia punkt przerwania, IDE formułuje żądanie i monituje sesji debugowania, aby utworzyć punkt przerwania.

 [Ocena wyrażeń](../../extensibility/debugger/evaluating-expressions.md) Wyjaśniono, jak wyrażenia są tworzone i co się dzieje, gdy wyrażenie jest oceniane.

 [Wizualizuj i wyświetlaj dane](../../extensibility/debugger/visualizing-and-viewing-data.md) W tym artykule wyjaśniono, jak wizualizatory typów i przeglądarki niestandardowe są obsługiwane przez oceniającego wyrażenie (EE).

## <a name="related-sections"></a>Powiązane sekcje
 [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md) W tym artykule opisano główne debugowanie koncepcji architektury.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) Zawiera omówienie składników debugowania programu Visual Studio, które obejmują DE, EE i obsługi symboli (SH).

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśniono, jak DE działa jednocześnie w kontekście oceny kodu, dokumentacji i wyrażenia. Opisuje, dla każdego z trzech kontekstów, lokalizacji, pozycji lub oceny istotne dla niego.

## <a name="see-also"></a>Zobacz też
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
