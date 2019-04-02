---
title: Wyzwalacz wstrzymania, wznowienia i zdarzeń w tle podczas debugowania platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: f5ef78f64ecea712083a25ab999f1554672d3381
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790358"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Porady: wyzwalanie wstrzymania, wznowienia i zdarzeń w tle podczas debugowania aplikacji platformy UWP w programie Visual Studio
Jeśli nie debugowania, Windows **Zarządzanie okresem istnienia procesu** (elementu) określa stan wykonania aplikacji — uruchamianie, wstrzymywanie, wznawianie i przerywa aplikację w odpowiedzi na działania użytkownika i stan urządzenia. Podczas debugowania, Windows powoduje wyłączenie tych zdarzeń aktywacji. W tym temacie opisano, jak wyzwolenie tych zdarzeń w debugerze.

 W tym temacie opisano również sposób debugowania **zadania w tle**. Zadania w tle umożliwiają wykonywania pewnych operacji w tle, nawet w przypadku aplikacji nie jest uruchomiona. Debuger umożliwia Udostępnij swoją aplikację w trybie debugowania i następnie — bez konieczności uruchamiania interfejsu użytkownika — uruchomić i debugować zadanie w tle.

 Aby uzyskać więcej informacji na temat zadań Zarządzanie okresem istnienia procesu i tła zobacz [uruchamiania i wznawianie i wielozadaniowość](/windows/uwp/launch-resume/index).

##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Zdarzenia Zarządzanie okresem istnienia procesu wyzwalacza
 Windows można wstrzymać aplikacji, gdy użytkownik zmienia się od jego lub Windows wejścia w stan niskiego zużycia energii. Może odpowiadać na `Suspending` zdarzeń, aby zapisać odpowiednie dane aplikacji i użytkownika do magazynu trwałego i zwolnić zasoby. Po wznowieniu aplikacji **zawieszone** stanu, wejdzie ona **systemem** stanu i jest kontynuowane od gdzie jaką miały w chwili zawieszenia. Może odpowiadać na `Resuming` zdarzenia w celu przywrócenia lub Odśwież stan aplikacji i odzyskać zasoby.

 Mimo że Windows próbuje zachować tyle wstrzymane aplikacje w pamięci, jak to możliwe, Windows może zakończyć aplikację, jeśli nie ma za mało zasobów, aby utrzymać ją w pamięci. Użytkownik może również jawnie Zamknij aplikację. Nie ma żadnego specjalnego zdarzenia, aby wskazać, że użytkownik zamknął aplikacji.

 W debugerze programu Visual Studio można ręcznie wstrzymania, wznowienia i zakończyć swoje aplikacje, aby debugować zdarzenia cyklu życia procesu. Aby debugować zdarzenia cyklu życia procesu:

1.  Ustaw breakpooint w procedurze obsługi zdarzeń, który chcesz debugować.

2.  Naciśnij klawisz **F5** można rozpocząć debugowania.

3.  Na **Lokalizacja debugowania** narzędzi, wybierz zdarzenie, które chcesz uruchomić:

     ![Wstrzymać, wznowić, zakończenia i zadania w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

     Należy pamiętać, że **Wstrzymaj i zakończyć** nie zamknie aplikacji i kończy się sesja debugowania.

##  <a name="BKMK_Trigger_background_tasks"></a> Zadania w tle wyzwalacza
 Dowolna aplikacja można zarejestrować zadania w tle mogą odpowiadać na określone zdarzenia systemowe, nawet wtedy, gdy aplikacja nie jest uruchomiona. Zadania w tle nie może uruchomić kod, który bezpośrednio aktualizacje interfejsu użytkownika; Zamiast tego zawierają one informacje dla użytkownika przy użyciu aktualizacji kafelka, wskaźnik aktualizacji i powiadomień wyskakujących. Aby uzyskać więcej informacji, zobacz [obsługi aplikacji przy użyciu zadań w tle](https://msdn.microsoft.com/library/4c7bb148-eb1f-4640-865e-41f627a46e8e)

 Możesz wyzwolić wydarzenia, uruchamianych zadań w tle dla swojej aplikacji za pomocą debugera.

> [!NOTE]
>  Debuger może wyzwalać tylko te zdarzenia, które nie zawierają danych, takich jak zdarzenia, które wskazuje na zmianę stanu na urządzeniu. Musisz ręcznie wyzwolić zadania w tle, które wymagają wprowadzenia danych przez użytkownika lub inne dane.

 Najbardziej realistyczne sposób, aby wyzwolić zdarzenie zadania w tle jest, gdy Twoja aplikacja nie działa. Wyzwalanie zdarzenia w sesji debugowania standardowa również jest jednak obsługiwane.

###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Wyzwalacz zdarzenia zadań tła, z sesji debugowania standardowe

1.  Ustaw punkt przerwania w kodzie zadań tła, który chcesz debugować.

2.  Naciśnij klawisz **F5** można rozpocząć debugowania.

3.  Z listy zdarzeń na **Lokalizacja debugowania** narzędzi, wybierz zadanie w tle, który chcesz uruchomić.

     ![Wstrzymać, wznowić, zakończenia i zadania w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Wyzwalanie zadania w tle, gdy aplikacja nie jest uruchomiony.

1.  Ustaw punkt przerwania w kodzie zadań tła, który chcesz debugować.

2.  Otwórz stronę właściwości debugowania projektu startowego. W Eksploratorze rozwiązań wybierz projekt. Na **debugowania** menu, wybierz **właściwości**.

     Dla projektów języka C++, rozwiń węzeł **właściwości konfiguracji** , a następnie wybierz **debugowanie**.

3.  Wykonaj jedną z następujących czynności:

    -   Dla projektów języka Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**

         ![C&#35;&#47;właściwości aplikacji Uruchamianie debugowania VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    -   Dla projektów Visual C++, wybierz **nie** z **uruchamianie aplikacji** listy.

         ![C&#43;&#43;&#47;Uruchom VB właściwości debugowania aplikacji](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4.  Naciśnij klawisz **F5** do umieszczenia aplikacji w trybie debugowania. Uwaga **procesu** listy na **Lokalizacja debugowania** narzędzi Wyświetla nazwę pakietu aplikacji, aby wskazać, że jesteś w trybie debugowania.

     ![Lista procesów zadań tła](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5.  Z listy zdarzeń na **Lokalizacja debugowania** narzędzi, wybierz zadanie w tle, który chcesz uruchomić.

     ![Wstrzymać, wznowić, zakończenia i zadania w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Wyzwalaj zdarzenia Zarządzanie okresem istnienia procesu i zadania z zainstalowaną aplikację w tle
 Użyj **pakietu debugowania zainstalowanej aplikacji** okno dialogowe, aby załadować aplikację, która jest już zainstalowany w debugerze. Na przykład możesz debugować aplikację, która została zainstalowana z Microsoft Store, lub debugować aplikację, gdy masz pliki źródłowe dla aplikacji, ale nie projekt programu Visual Studio dla aplikacji. **Pakietu debugowania zainstalowanej aplikacji** okno dialogowe pozwala uruchomić aplikację w trybie debugowania na komputerze programu Visual Studio lub na zdalnym urządzeniu lub w celu ustawienia aplikacji, aby uruchomić tryb debugowania, ale nie można go uruchomić. Aby uzyskać więcej informacji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

 Po załadowaniu aplikacji w debugerze, można użyć dowolnej z procedur opisanych powyżej.

##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnozowanie błędów aktywacji zadania w tle
 Dzienniki diagnostyczne w Podglądzie zdarzeń Windows infrastruktury tła zawiera szczegółowe informacje, które umożliwia diagnozowanie i rozwiązywanie problemów z błędami zadania w tle. Aby wyświetlić dziennik:

1.  Otwórz aplikację Podgląd zdarzeń.

2.  W **akcje** okienku wybierz **widoku** i upewnij się, że **Pokaż analityczne i debugowania dzienniki** jest zaznaczone.

3.  Na **podglądu zdarzeń (lokalne)** drzewa, rozwiń węzły **Dzienniki aplikacji i usług** > **Microsoft** > **Windows**   >  **BackgroundTasksInfrastructure**.

4.  Wybierz **diagnostycznych** dziennika.

## <a name="see-also"></a>Zobacz też
- [Testowanie aplikacji platformy UWP za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
- [Cykl życia aplikacji](/windows/uwp/launch-resume/app-lifecycle)
- [Uruchamianie, wznawianie i wielozadaniowość](/windows/uwp/launch-resume/index)