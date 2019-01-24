---
title: 'Porady: wyzwalanie wstrzymania, wznowienia i zdarzeń aplikacji Windows Store w tle'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58280cda7f9556596de84d144602c97cc1f59bb9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772345"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio"></a>Wyzwalanie wstrzymania, wznowienia i zdarzeń w tle w aplikacjach Sklepu Windows w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli nie debugowania, Windows **Zarządzanie okresem istnienia procesu** (elementu) określa stan wykonania aplikacji — uruchamianie, wstrzymywanie, wznawianie i przerywa aplikację w odpowiedzi na działania użytkownika i stan urządzenia. Podczas debugowania, Windows powoduje wyłączenie tych zdarzeń aktywacji. W tym temacie opisano, jak wyzwolenie tych zdarzeń w debugerze.

 W tym temacie opisano również sposób debugowania **zadania w tle**. Zadania w tle umożliwiają wykonywania pewnych operacji w tle, nawet w przypadku aplikacji nie jest uruchomiona. Debuger umożliwia Udostępnij swoją aplikację w trybie debugowania i następnie — bez konieczności uruchamiania interfejsu użytkownika — uruchomić i debugować zadanie w tle.

 Aby uzyskać więcej informacji na temat zadań Zarządzanie okresem istnienia procesu i tła zobacz [uruchamiania i wznawianie i wielozadaniowość](http://msdn.microsoft.com/04307b1b-05af-46a6-b639-3f35e297f71b).

##  <a name="BKMK_In_this_topic"></a> W tym temacie
 [Zdarzenia Zarządzanie okresem istnienia procesu wyzwalacza](#BKMK_Trigger_Process_Lifecycle_Management_events)

 [Zadania w tle wyzwalacza](#BKMK_Trigger_background_tasks)

- [Wyzwalacz zdarzenia zadań tła, z sesji debugowania standardowe](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)

- [Wyzwalanie zadania w tle, gdy aplikacja nie jest uruchomiony.](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)

  [Wyzwalaj zdarzenia Zarządzanie okresem istnienia procesu i zadania z zainstalowaną aplikację w tle](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)

  [Diagnozowanie błędów aktywacji zadania w tle](#BKMK_Diagnosing_background_task_activation_errors)

##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Zdarzenia Zarządzanie okresem istnienia procesu wyzwalacza
 Windows można wstrzymać aplikacji, gdy użytkownik zmienia się od jego lub Windows wejścia w stan niskiego zużycia energii. Może odpowiadać na `Suspending` zdarzeń, aby zapisać odpowiednie dane aplikacji i użytkownika do magazynu trwałego i zwolnić zasoby. Po wznowieniu aplikacji **zawieszone** stanu, wejdzie ona **systemem** stanu i jest kontynuowane od gdzie jaką miały w chwili zawieszenia. Może odpowiadać na `Resuming` zdarzenia w celu przywrócenia lub Odśwież stan aplikacji i odzyskać zasoby.

 Mimo że Windows próbuje zachować tyle wstrzymane aplikacje w pamięci, jak to możliwe, Windows może zakończyć aplikację, jeśli nie ma za mało zasobów, aby utrzymać ją w pamięci. Użytkownik może również jawnie Zamknij aplikację. Nie ma żadnego specjalnego zdarzenia, aby wskazać, że użytkownik zamknął aplikacji.

 W debugerze programu Visual Studio można ręcznie wstrzymania, wznowienia i zakończyć swoje aplikacje, aby debugować zdarzenia cyklu życia procesu. Aby debugować zdarzenia cyklu życia procesu:

1.  Ustaw breakpooint w procedurze obsługi zdarzeń, który chcesz debugować.

2.  Naciśnij klawisz **F5** można rozpocząć debugowania.

3.  Na **Lokalizacja debugowania** narzędzi, wybierz zdarzenie, które chcesz uruchomić:

     ![Wstrzymać, wznowić, zakończenia i zadania w tle](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

     Należy pamiętać, że **Wstrzymaj i zakończyć** nie zamknie aplikacji i kończy się sesja debugowania.

##  <a name="BKMK_Trigger_background_tasks"></a> Zadania w tle wyzwalacza
 Dowolna aplikacja można zarejestrować zadania w tle mogą odpowiadać na określone zdarzenia systemowe, nawet wtedy, gdy aplikacja nie jest uruchomiona. Zadania w tle nie może uruchomić kod, który bezpośrednio aktualizacje interfejsu użytkownika; Zamiast tego zawierają one informacje dla użytkownika przy użyciu aktualizacji kafelka, wskaźnik aktualizacji i powiadomień wyskakujących. Aby uzyskać więcej informacji, zobacz [obsługi aplikacji przy użyciu zadań w tle](http://msdn.microsoft.com/4c7bb148-eb1f-4640-865e-41f627a46e8e)

 Możesz wyzwolić wydarzenia, uruchamianych zadań w tle dla swojej aplikacji za pomocą debugera.

> [!NOTE]
>  Debuger może wyzwalać tylko te zdarzenia, które nie zawierają danych, takich jak zdarzenia, które wskazuje na zmianę stanu na urządzeniu. Musisz ręcznie wyzwolić zadania w tle, które wymagają wprowadzenia danych przez użytkownika lub inne dane.

 Najbardziej realistyczne sposób, aby wyzwolić zdarzenie zadania w tle jest, gdy Twoja aplikacja nie działa. Wyzwalanie zdarzenia w sesji debugowania standardowa również jest jednak obsługiwane.

###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Wyzwalacz zdarzenia zadań tła, z sesji debugowania standardowe

1.  Ustaw punkt przerwania w kodzie zadań tła, który chcesz debugować.

2.  Naciśnij klawisz **F5** można rozpocząć debugowania.

3.  Z listy zdarzeń na **Lokalizacja debugowania** narzędzi, wybierz zadanie w tle, który chcesz uruchomić.

     ![Wstrzymać, wznowić, zakończenia i zadania w tle](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Wyzwalanie zadania w tle, gdy aplikacja nie jest uruchomiony.

1.  Ustaw punkt przerwania w kodzie zadań tła, który chcesz debugować.

2.  Otwórz stronę właściwości debugowania projektu startowego. W Eksploratorze rozwiązań wybierz projekt. Na **debugowania** menu, wybierz **właściwości**.

     Dla projektów języka C++, Niewykluczone, że rozwinąć **właściwości konfiguracji** , a następnie wybierz **debugowanie**.

3.  Wykonaj jedną z następujących czynności:

    -   Dla projektów języka Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**

         ![C&#35;&#47;właściwości aplikacji Uruchamianie debugowania VB](../debugger/media/dbg-csvb-dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    -   Dla projektów języka Visual C++ i JavaScript, wybierz **nie** z **uruchamianie aplikacji** listy.

         ![C&#43;&#43;&#47;Uruchom VB właściwości debugowania aplikacji](../debugger/media/dbg-cppjs-dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4.  Naciśnij klawisz **F5** do umieszczenia aplikacji w trybie debugowania. Uwaga **procesu** listy na **Lokalizacja debugowania** narzędzi Wyświetla nazwę pakietu aplikacji, aby wskazać, że jesteś w trybie debugowania.

     ![Lista procesów zadań tła](../debugger/media/dbg-backgroundtask-processlist.png "DBG_BackgroundTask_ProcessList")

5.  Z listy zdarzeń na **Lokalizacja debugowania** narzędzi, wybierz zadanie w tle, który chcesz uruchomić.

     ![Wstrzymać, wznowić, zakończenia i zadania w tle](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Wyzwalaj zdarzenia Zarządzanie okresem istnienia procesu i zadania z zainstalowaną aplikację w tle
 Użyj okna dialogowego Debuguj zainstalowana aplikacja można załadować aplikacji, która jest już zainstalowany w debugerze. Na przykład może debugować aplikację, która została zainstalowana ze Sklepu Windows lub debugowania aplikacji, gdy masz pliki źródłowe dla aplikacji, ale Visual Studio projekt aplikacji. Okno dialogowe debugowania zainstalowana aplikacja pozwala uruchomić aplikację w trybie debugowania na komputerze programu Visual Studio lub na zdalnym urządzeniu lub w celu ustawienia aplikacji, aby uruchomić tryb debugowania, ale nie można go uruchomić. Zobacz **Uruchom zainstalowaną aplikację w debugerze** sekcji albo [JavaScript](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Start_an_installed_app_in_the_debugger) lub [Visual C++, Visual C# i Visual Basic](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md#BKMK_Start_an_installed_app_in_the_debugger) wersje **sposobu uruchamiania sesję debugowania** Aby uzyskać więcej informacji.

 Po załadowaniu aplikacji w debugerze, można użyć dowolnej z procedur opisanych powyżej.

##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnozowanie błędów aktywacji zadania w tle
 Dzienniki diagnostyczne w Podglądzie zdarzeń Windows infrastruktury tła zawiera szczegółowe informacje, które umożliwia diagnozowanie i rozwiązywanie problemów z błędami zadania w tle. Aby wyświetlić dziennik:

1.  Otwórz aplikację Podgląd zdarzeń.

2.  W **akcje** okienku wybierz **widoku** i upewnij się, że **Pokaż analityczne i debugowania dzienniki** jest zaznaczone.

3.  Na **podglądu zdarzeń (lokalne)** drzewa, rozwiń węzły **Dzienniki aplikacji i usług** / **Microsoft** / **Windows**   /  **BackgroundTasksInfrastructure**.

4.  Wybierz **diagnostycznych** dziennika.

## <a name="see-also"></a>Zobacz też
 [Testowanie aplikacji Store za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [zarządzania cyklem życia aplikacji](http://msdn.microsoft.com/53cdc987-c547-49d1-a5a4-fd3f96b2259d) [uruchamiania i wznawianie i wielozadaniowość](http://msdn.microsoft.com/04307b1b-05af-46a6-b639-3f35e297f71b)
