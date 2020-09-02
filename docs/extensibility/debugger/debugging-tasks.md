---
title: Zadania debugowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 070068853d962bdf9b209edb9410d33d46ccf853
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903557"
---
# <a name="debug-tasks"></a>Debuguj zadania
Aby debugować program, musi on zostać uruchomiony, a aparat debugowania (DE) musi być dołączony do niego lub w przeciwnym razie element DE musi być dołączony do wcześniej uruchomionego programu. Po dołączeniu Usuń musi generować pewne zdarzenia uruchamiania. W odpowiedzi pakiet debugowania próbuje powiązać punkty przerwania ustawione w IDE. Gdy program trafi związany z punktem przerwania, zatrzymuje i czeka na dane wejściowe użytkownika.

## <a name="in-this-section"></a>W tej sekcji
 [Problemy z zabezpieczeniami](../../extensibility/debugger/security-issues.md) W tym artykule omówiono kroki zabezpieczeń, które są niezbędne do debugowania programu.

 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md) Zawiera instrukcje krok po kroku dotyczące sposobu określania, która wywołuje system operacyjny, aby uruchomić program.

 [Dołącz bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md) Opisuje proces używany do debugowania programu w procesie, który jest już uruchomiony.

 [Wysyłaj zdarzenia uruchamiania po](../../extensibility/debugger/sending-startup-events-after-a-launch.md) uruchomieniu Wyświetla listę zdarzeń, które miały miejsce po dołączeniu do programu, aż do momentu, w którym program jest w jego głównym punkcie wejścia i jest gotowy do debugowania.

 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md) Wyjaśnia, w jaki sposób zwykle wysyła zdarzenie punktu wejścia, zdarzenie ukończenia obciążenia lub zdarzenie zatrzymywania, w zależności od okoliczności.

 [Powiązywanie punktów przerwania](../../extensibility/debugger/binding-breakpoints.md) Opisuje, w jaki sposób, jeśli użytkownik ustawia punkt przerwania, IDE zgłasza żądanie i poprosi o sesję debugowania, aby utworzyć punkt przerwania.

 [Oceń wyrażenia](../../extensibility/debugger/evaluating-expressions.md) Wyjaśnia sposób tworzenia wyrażeń i co się dzieje, gdy wyrażenie jest oceniane.

 [Wizualizowanie i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md) Wyjaśnia, jak Wizualizatory typów i niestandardowe osoby przeglądające są obsługiwane przez ewaluatora wyrażeń.

## <a name="related-sections"></a>Sekcje pokrewne
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) Opisuje główne koncepcje dotyczące architektury debugowania.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) Zawiera omówienie składników debugowania programu Visual Studio, które obejmują procedurę obsługi DE, EE i symboli (SH).

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśnia, jak działa w ramach kodu, dokumentacji i kontekstów oceny wyrażenia. Opisuje dla każdego z trzech kontekstów, lokalizację, pozycję lub ocenę, która jest dla niego odpowiednia.

## <a name="see-also"></a>Zobacz też
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
