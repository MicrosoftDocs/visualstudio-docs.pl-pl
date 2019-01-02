---
title: Zadania debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa719871e075a5448fa2d351c5bd7950a833601a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900155"
---
# <a name="debug-tasks"></a>Debugowanie zadań
Aby zdebugować program, należy uruchomić i aparat debugowania (DE) musi być dołączony do niego, w przeciwnym razie DE musi być dołączony do wcześniej uruchomionego programu. Po dołączeniu DE wygenerować pewnych zdarzeń uruchomienia. W odpowiedzi pakietu debugowania próbuje powiązać punkty przerwania ustawione w IDE. Gdy program osiągnie powiązany punkt przerwania, zatrzymuje i czeka na dane wejściowe użytkownika.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Problemy z zabezpieczeniami](../../extensibility/debugger/security-issues.md)  
 W tym artykule omówiono kroki zabezpieczeń, które są wymagane do debugowania programu.  
  
 [Uruchom program](../../extensibility/debugger/launching-a-program.md)  
 Instrukcje krok po kroku dotyczące sposobu określania DE, która wywołuje systemu operacyjnego, aby uruchomić program.  
  
 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 W tym artykule opisano proces używany do debugowania programu, w ramach procesu, który jest już uruchomiony.  
  
 [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Wyświetla listę zdarzeń, które mają miejsce, gdy DE jest dołączony do programu, dopóki nie znajduje się w jego główny punkt wejścia program jest gotowy do debugowania.  
  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)  
 W tym artykule wyjaśniono, jak DE zwykle wysyła zdarzenie punktu wejścia, to zdarzenie ukończenia obciążenia lub zdarzeń do zatrzymywania, w zależności od okoliczności.  
  
 [Powiąż punktów przerwania](../../extensibility/debugger/binding-breakpoints.md)  
 W tym artykule opisano, jak to zrobić, jeśli użytkownik ustawia punkt przerwania, IDE formulates żądanie i wyświetla monit o sesji debugowania, aby utworzyć punkt przerwania.  
  
 [Ocena wyrażenia](../../extensibility/debugger/evaluating-expressions.md)  
 Wyjaśnia sposób tworzenia wyrażenia i co się stanie, gdy wyrażenie jest obliczane.  
  
 [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 W tym artykule wyjaśniono, jak wizualizatorów typu i przeglądarek niestandardowych są obsługiwane przez ewaluatora wyrażeń (EE).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują DE EE i obsługi symboli (SH).  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak DE działa jednocześnie w ramach kodu, dokumentację i konteksty oceny wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
## <a name="see-also"></a>Zobacz także  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)