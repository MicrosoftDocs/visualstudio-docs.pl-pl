---
title: Wyzwalaj zdarzenia zawieszenia/wznowienia/tła podczas debugowania platformy UWP
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
ms.openlocfilehash: d15a176fb378159407589af0b720d8310de8e29c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450398"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Jak wyzwolić wstrzymanie, wznowienie i zdarzenia w tle podczas debugowania aplikacji platformy UWP w programie Visual Studio

Gdy nie debugujesz programu, **Zarządzanie okresem istnienia procesu** systemu Windows (PLM) steruje stanem wykonywania aplikacji — uruchamianie, wstrzymywanie, wznawianie i kończenie aplikacji w odpowiedzi na akcje użytkownika i stan urządzenia. Podczas debugowania system Windows wyłącza te zdarzenia aktywacji. W tym temacie opisano sposób uruchamiania tych zdarzeń w debugerze.

W tym temacie opisano również sposób debugowania **zadań w tle**. Zadania w tle umożliwiają wykonywanie niektórych operacji w tle, nawet gdy aplikacja nie jest uruchomiona. Możesz użyć debugera, aby umieścić aplikację w trybie debugowania, a następnie — bez uruchamiania interfejsu użytkownika — Rozpocznij i Debuguj zadanie w tle.

Aby uzyskać więcej informacji o zarządzaniu okresem istnienia procesu i zadaniach w tle, zobacz [Uruchamianie, wznawianie i wiele zadań](/windows/uwp/launch-resume/index).

## <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a>Wyzwalaj zdarzenia zarządzania okresem istnienia procesu
 System Windows może zawiesić aplikację, gdy użytkownik przełączy się z nią lub gdy system Windows przejdzie do stanu niskiego zużycia baterii. Możesz odpowiedzieć na zdarzenie `Suspending`, aby zapisać odpowiednie dane aplikacji i użytkownika do magazynu trwałego oraz zwolnić zasoby. Gdy aplikacja zostanie wznowiona ze stanu **wstrzymania** , przejdzie do stanu **uruchomienia** i kontynuuje w miejscu, w którym była wstrzymana. Możesz odpowiedzieć na zdarzenie `Resuming`, aby przywrócić lub odświeżyć stan aplikacji i odzyskać zasoby.

 Mimo że system Windows podejmuje próbę utrzymania jak największej liczby wstrzymanych aplikacji w pamięci, system Windows może przerwać swoją aplikację, jeśli nie ma wystarczającej ilości zasobów, aby zachować ją w pamięci. Użytkownik może również jawnie zamknąć aplikację. Nie ma specjalnych zdarzeń wskazujących, że użytkownik zamknął aplikację.

 W debugerze programu Visual Studio można ręcznie wstrzymywać, wznawiać i kończyć aplikacje, aby debugować zdarzenia cyklu życia procesu. Aby debugować zdarzenie cyklu życia procesu:

1. Ustaw punkt przerwania w programie obsługi zdarzenia, które chcesz debugować.

2. Naciśnij klawisz **F5** , aby rozpocząć debugowanie.

3. Na pasku narzędzi **Lokalizacja debugowania** wybierz zdarzenie, które chcesz uruchomić:

     ![Wstrzymywanie, wznawianie, kończenie i wykonywanie zadań w tle](../debugger/media/dbg_suspendresumebackground.png)

     **Zawieszenie i zakończenie** powoduje zamknięcie aplikacji i zakończenie sesji debugowania.

## <a name="BKMK_Trigger_background_tasks"></a>Wyzwalanie zadań w tle
 Każda aplikacja może zarejestrować zadanie w tle w celu reagowania na określone zdarzenia systemowe nawet wtedy, gdy aplikacja nie jest uruchomiona. Zadania w tle nie mogą uruchamiać kodu, który bezpośrednio aktualizuje interfejs użytkownika; Zamiast tego wyświetlają informacje dla użytkownika z aktualizacjami kafelków, aktualizacjami znaczków i wyskakującymi powiadomieniami. Aby uzyskać więcej informacji, zobacz [Obsługa aplikacji za pomocą zadań w tle](https://msdn.microsoft.com/library/4c7bb148-eb1f-4640-865e-41f627a46e8e).

 Możesz wyzwolić zdarzenia, które uruchamiają zadania w tle dla aplikacji z debugera.

> [!NOTE]
> Debuger może wyzwolić tylko te zdarzenia, które nie zawierają danych, takie jak zdarzenia wskazujące na zmianę stanu urządzenia. Trzeba ręcznie wyzwolić zadania w tle, które wymagają wprowadzenia danych przez użytkownika lub inne dane.

 Najbardziej realistycznym sposobem wyzwalania zdarzenia zadania w tle jest to, że aplikacja nie jest uruchomiona. Jednak jest obsługiwane również Wyzwalanie zdarzenia w standardowej sesji debugowania.

### <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a>Wyzwalanie zdarzenia zadania w tle z standardowej sesji debugowania

1. Ustaw punkt przerwania w kodzie zadania w tle, który chcesz debugować.

2. Naciśnij klawisz **F5** , aby rozpocząć debugowanie.

3. Z listy zdarzenia na pasku narzędzi **Lokalizacja debugowania** wybierz zadanie w tle, które chcesz uruchomić.

     ![Wstrzymywanie, wznawianie, kończenie i wykonywanie zadań w tle](../debugger/media/dbg_suspendresumebackground.png)

### <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a>Wyzwalaj zadanie w tle, gdy aplikacja nie jest uruchomiona

1. Ustaw punkt przerwania w kodzie zadania w tle, który chcesz debugować.

2. Otwórz stronę właściwości debugowania dla projektu startowego. W Eksplorator rozwiązań wybierz projekt. W menu **debugowanie** wybierz polecenie **Właściwości**.

     W C++ obszarze projekty rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.

3. Wykonaj jedną z następujących czynności:

    - W przypadku C# projektów wizualizacji i Visual Basic wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po rozpoczęciu**

         ![Właściwość&#35;&#47;uruchamiania debugowania języka C VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - W C++ polu projekty wybierz pozycję **nie** na liście **Uruchom aplikację** .

         ![Właściwość&#43;&#43;&#47;debugowania uruchamiania aplikacji języka C VB](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Naciśnij klawisz **F5** , aby umieścić aplikację w trybie debugowania. Uwaga Lista **procesów** na pasku narzędzi **Lokalizacja debugowania** wyświetla nazwę pakietu aplikacji, aby wskazać, że jesteś w trybie debugowania.

     ![Lista procesów zadań w tle](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. Z listy zdarzenia na pasku narzędzi **Lokalizacja debugowania** wybierz zadanie w tle, które chcesz uruchomić.

     ![Wstrzymywanie, wznawianie, kończenie i wykonywanie zadań w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a>Wyzwalaj zdarzenia zarządzania okresem istnienia procesu i zadania w tle z zainstalowanej aplikacji
 Okno dialogowe **Debuguj zainstalowany pakiet aplikacji** służy do ładowania aplikacji, która jest już zainstalowana w debugerze. Na przykład można debugować aplikację, która została zainstalowana z poziomu Microsoft Store lub debugować aplikację, jeśli masz pliki źródłowe dla aplikacji, ale nie projekt programu Visual Studio dla aplikacji. W oknie dialogowym **Debuguj zainstalowany pakiet aplikacji** można uruchomić aplikację w trybie debugowania na maszynie programu Visual Studio lub na urządzeniu zdalnym albo skonfigurować aplikację do uruchamiania w trybie debugowania, ale nie należy jej uruchamiać. Aby uzyskać więcej informacji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

 Po załadowaniu aplikacji do debugera można użyć dowolnej procedury opisanej powyżej.

## <a name="BKMK_Diagnosing_background_task_activation_errors"></a>Diagnozowanie błędów aktywacji zadań w tle
 Dzienniki diagnostyczne w systemie Windows Podgląd zdarzeń dla infrastruktury w tle zawierają szczegółowe informacje, których można użyć do diagnozowania i rozwiązywania problemów z błędami zadań w tle. Aby wyświetlić dziennik:

1. Otwórz aplikację Podgląd zdarzeń.

2. W okienku **Akcje** wybierz **Widok** i upewnij się, że jest zaznaczone pole wyboru **Pokaż dzienniki analityczne i debugowania** .

3. W drzewie **Podgląd zdarzeń (lokalne)** rozwiń węzeł węzły **aplikacje i usługi Dzienniki** > **Microsoft** > **Windows** > **BackgroundTasksInfrastructure**.

4. Wybierz dziennik **diagnostyczny** .

## <a name="see-also"></a>Zobacz też
- [Testowanie aplikacji platformy UWP za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
- [Cykl życia aplikacji](/windows/uwp/launch-resume/app-lifecycle)
- [Uruchamianie, wznawianie i wielozadania](/windows/uwp/launch-resume/index)