---
title: Zadania debugowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803698"
---
# <a name="debugging-tasks"></a>Zadania debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby zdebugować program, należy uruchomić i aparat debugowania (DE) musi być dołączony do niego, w przeciwnym razie DE musi być dołączony do wcześniej uruchomionego programu. Po dołączeniu DE wygenerować pewnych zdarzeń uruchomienia. W odpowiedzi pakietu debugowania próbuje powiązać punkty przerwania ustawione w IDE. Gdy program osiągnie powiązany punkt przerwania, zatrzymuje i czeka na dane wejściowe użytkownika.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Problemy dotyczące zabezpieczeń](../../extensibility/debugger/security-issues.md)  
 W tym artykule omówiono kroki zabezpieczeń, które są wymagane do debugowania programu.  
  
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)  
 Instrukcje krok po kroku dotyczące sposobu określania DE, która wywołuje systemu operacyjnego, aby uruchomić program.  
  
 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 W tym artykule opisano proces używany do debugowania programu, w ramach procesu, który jest już uruchomiony.  
  
 [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Wyświetla listę zdarzeń, które mają miejsce, gdy DE jest dołączony do programu, dopóki nie znajduje się w jego główny punkt wejścia program jest gotowy do debugowania.  
  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)  
 W tym artykule wyjaśniono, jak DE zwykle wysyła zdarzenie punktu wejścia, to zdarzenie ukończenia obciążenia lub zdarzeń do zatrzymywania, w zależności od okoliczności.  
  
 [Tworzenie powiązań punktów przerwania](../../extensibility/debugger/binding-breakpoints.md)  
 W tym artykule opisano, jak to zrobić, jeśli użytkownik ustawia punkt przerwania, IDE formulates żądanie i wyświetla monit o sesji debugowania, aby utworzyć punkt przerwania.  
  
 [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
