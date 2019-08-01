---
title: Debuguj usługi Live ASP.NET Azure Kubernetes Services
description: Dowiedz się, jak Ustaw punkty przyciągania i wyświetlanie migawki za pomocą rozszerzenia Snapshot Debugger.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 6eb7af4ead7cd58a0ccf36cbeb2b9fc56e890315
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415754"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Debuguj usługi Live ASP.NET Azure Kubernetes Services przy użyciu Snapshot Debugger

Rozszerzenie Snapshot Debugger tworzy migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który chcesz wziąć. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

Punkty przyciągania i punkty rejestrowania są podobne do punktów przerwania, ale w przeciwieństwie do punktów przerwania, punkty przyciągania nie zatrzymanie aplikacji po trafieniu. Zazwyczaj przechwytywania migawkę punktu przyciągania zajmuje 10 20 milisekund.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom rozszerzenie Snapshot Debugger
> * Ustawianie punktu przyciągania i Wyświetl migawki
> * Ustaw punkt rejestrowania

## <a name="prerequisites"></a>Wymagania wstępne

* Snapshot Debugger usługi Azure Kubernetes Services są dostępne tylko dla programu Visual Studio 2019 Enterprise lub nowszego przy użyciu **obciążeń programistycznych platformy Azure**. (Na karcie **poszczególne składniki** znajduje się w obszarze **debugowanie i testowanie** > **debugera migawek**).

    Jeśli nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Kolekcja migawek jest dostępna dla następujących aplikacji sieci Web usług Azure Kubernetes Services:
  * ASP.NET Core aplikacje działające na platformie .NET Core 2,2 lub nowszej w systemie Debian 9.
  * ASP.NET Core aplikacje działające na platformie .NET Core 2,2 lub nowszej na Alpine 3,8.
  * ASP.NET Core aplikacje działające na platformie .NET Core 2,2 lub nowszej na Ubuntu 18,04.

    > [!NOTE]
    > Aby pomóc w włączeniu obsługi Snapshot Debugger w AKS, podano [repozytorium zawierające zestaw wieloetapowe dockerfile, który pokazuje konfigurację w obrazach platformy Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz swój projekt i uruchomić rozszerzenia Snapshot Debugger

1. Otwórz projekt, który chcesz debugowania migawek.

    > [!IMPORTANT]
    > Aby przeprowadzić debugowanie migawek, należy otworzyć tę *samą wersję kodu źródłowego* , która jest publikowana w usłudze Azure Kubernetes.

1. Wybierz **> debugowania Snapshot Debugger Dołącz...** . Wybierz zasób AKS, do którego wdrożono aplikację sieci Web, i konto usługi Azure Storage, a następnie kliknij przycisk **Dołącz**. Snapshot Debugger obsługuje także [Azure App Service](debug-live-azure-applications.md) i [Virtual Machines platformy Azure (VM) & Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md).

    ![Uruchom Debuger migawek z menu Debuguj](../debugger/media/snapshot-debug-menu-attach.png)

    ![Wybierz zasób platformy Azure](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Program Visual Studio 2019 w wersji 16,2 lub nowszej) Snapshot Debugger włączono obsługę chmury platformy Azure. Upewnij się, że wybrane konto usługi Azure Resource i Azure Storage znajdują się w tej samej chmurze. Jeśli masz pytania dotyczące konfiguracji [zgodności platformy Azure](https://azure.microsoft.com/overview/trusted-cloud/) w przedsiębiorstwie, skontaktuj się z administratorem platformy Azure.

Program Visual Studio jest teraz w trybie debugowania migawek.

   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

   Okno **moduły** pokazuje, kiedy wszystkie moduły zostały załadowane dla Azure App Service (wybierz polecenie **debuguj > moduły > systemu Windows** , aby otworzyć to okno).

   ![Sprawdź okno modułów](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustaw punkt przyciągania

1. W edytorze kodu kliknij lewy odstęp obok wiersza kodu, który interesuje Cię, aby ustawić punkt przyciągania. Upewnij się, że kod jest już wykonywany.

   ![Ustaw punkt przyciągania](../debugger/media/snapshot-set-snappoint.png)

1. Kliknij przycisk **Rozpocznij zbieranie** włączenie punktu przyciągania.

   ![Włącz punkt przyciągania](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nie można wykonać kroku podczas wyświetlania migawki, ale można umieścić wiele punktów przyciągania w kodzie z wykonania na różne wiersze kodu. Jeśli masz wiele punktów przyciągania w kodzie rozszerzenia Snapshot Debugger sprawia, że się, że odpowiednie migawek z tej samej sesji użytkownika końcowego. Rozszerzenie Snapshot Debugger robi to, nawet jeśli wielu użytkowników osiągnięcia swojej aplikacji.

## <a name="take-a-snapshot"></a>Utwórz migawkę

Po ustawieniu punkt przyciągania można ręcznie wygenerować migawkę, przechodząc do widoku przeglądarki witryny sieci Web i uruchamiając wiersz kodu lub poczekaj, aż użytkownicy generują je na podstawie ich użycia.

## <a name="inspect-snapshot-data"></a>Sprawdź dane migawki

1. Po osiągnięciu punktu przyciągania migawki pojawia się w oknie narzędzia diagnostyczne. Aby otworzyć to okno, wybierz **debuguj > Windows > pokaż narzędzia diagnostyczne**.

    ![Otwarcie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie punktu przyciągania, aby otworzyć migawki w edytorze kodu.

    ![Sprawdź dane migawki](../debugger/media/snapshot-inspect-data.png)

    Z poziomu tego widoku możesz umieścić kursor zmienne, aby przeglądać DataTips, **zmiennych lokalnych**, **zegarki**, i **stos wywołań** systemu windows, a także obliczać wyrażeń.

    Sama witryna sieci Web jest nadal na żywo, a użytkownicy końcowi nie mają do nich wpływu. Tylko jedna migawka jest przechwytywany na punkt przyciągania domyślnie: po przechwyceniu migawkę punktu przyciągania zostanie wyłączony. Chcesz przechwytywać innego migawkę punktu przyciągania, można włączyć punkt przyciągania ponownie, klikając **Aktualizuj kolekcję**.

Możesz również dodać więcej punktów przyciągania do swojej aplikacji i włączać je za pomocą **Aktualizuj kolekcję** przycisku.

**Potrzebujesz pomocy?** Zobacz [Rozwiązywanie problemów i znane problemy](../debugger/debug-live-azure-apps-troubleshooting.md) i [często zadawane pytania dotyczące debugowania migawek](../debugger/debug-live-azure-apps-faq.md) stron.

## <a name="set-a-conditional-snappoint"></a>Ustaw warunkowego punktu przyciągania

Jeśli nie można ponownie utworzyć określonego stanu w aplikacji, należy rozważyć użycie warunkowej punkt przyciągania. Warunkowe punkty przyciągania ułatwiają kontrolowanie, kiedy należy wykonać migawkę, na przykład gdy zmienna zawiera konkretną wartość, którą chcesz sprawdzić. Można określić warunki, używając wyrażeń i filtry, lub liczbą trafień.

#### <a name="to-create-a-conditional-snappoint"></a>Aby utworzyć warunkowego punktu przyciągania

1. Kliknij prawym przyciskiem myszy ikoną punkt przyciągania (piłka puste), a następnie wybierz **ustawienia**.

   ![Wybierz ustawienia](../debugger/media/snapshot-snappoint-settings.png)

1. W oknie Ustawienia punktu przyciągania wpisz wyrażenie.

   ![Wpisz wyrażenie](../debugger/media/snapshot-snappoint-conditions.png)

   Na powyższej ilustracji tylko migawki dla punktu przyciągania podczas `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Ustaw punkt rejestrowania

Oprócz wykonywania migawki po trafieniu punktu przyciągania, można również skonfigurować punktu przyciągania, aby zarejestrować komunikat (to znaczy, Utwórz punkt rejestrowania). Możesz ustawić punkty rejestrowania, bez konieczności ponownego wdrażania aplikacji. Punkty rejestrowania są wykonywane w praktycznie i spowodować nie wpływu i efekty uboczne uruchomionej aplikacji.

#### <a name="to-create-a-logpoint"></a>Aby utworzyć punkt rejestrowania

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (sześciokąt niebieski), a następnie wybierz **ustawienia**.

1. W oknie Ustawienia punktu przyciągania wybierz **akcje**.

    ![Utwórz punkt rejestrowania](../debugger/media/snapshot-logpoint.png)

1. W polu **komunikat** można wprowadzić nowy komunikat dziennika, który ma być zalogowany. Można również obliczyć zmiennych w wiadomości dziennika, umieszczając je wewnątrz nawiasów klamrowych.

    Jeśli wybierzesz **Wyślij do okna danych wyjściowych**, gdy zostanie osiągnięty punkt rejestrowania komunikat jest wyświetlany w oknie narzędzia diagnostyczne.

    ![Punkt rejestrowania dane w oknie narzędzia diagnostyczne](../debugger/media/snapshot-logpoint-output.png)

    Jeśli wybierzesz **Wyślij do dziennika aplikacji**, gdy zostanie osiągnięty punkt rejestrowania, komunikat pojawi się gdziekolwiek zobaczyć komunikaty z `System.Diagnostics.Trace` (lub `ILogger` platformie .NET Core), takich jak [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Następne kroki

W ramach tego samouczka nauczysz się używać Snapshot Debugger platformy Azure Kubernetes. Warto przeczytać więcej na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)