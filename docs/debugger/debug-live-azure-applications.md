---
title: Debugowanie na żywo aplikacji ASP.NET, Azure
description: Dowiedz się, jak Ustaw punkty przyciągania i wyświetlanie migawki za pomocą rozszerzenia Snapshot Debugger.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: fae6be8932731e5589dbc27f5084bcbc509680c1
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493316"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debugowanie na żywo aplikacji ASP.NET, Azure, przy użyciu rozszerzenia Snapshot Debugger

Rozszerzenie Snapshot Debugger tworzy migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który chcesz wziąć. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

Punkty przyciągania i punkty rejestrowania są podobne do punktów przerwania, ale w przeciwieństwie do punktów przerwania, punkty przyciągania nie zatrzymanie aplikacji po trafieniu. Zazwyczaj przechwytywania migawkę punktu przyciągania zajmuje 10 20 milisekund.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom rozszerzenie Snapshot Debugger
> * Ustawianie punktu przyciągania i Wyświetl migawki
> * Ustaw punkt rejestrowania

## <a name="prerequisites"></a>Wymagania wstępne

* Snapshot Debugger jest dostępny tylko w programie Visual Studio 2017 Enterprise w wersji 15,5 lub nowszej przy użyciu **obciążeń programistycznych platformy Azure**. (Na karcie **poszczególne składniki** znajduje się w obszarze **debugowanie i testowanie** > **debugera migawek**).

   ::: moniker range=">=vs-2019"
   Jeśli nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Jeśli aktualizujesz z poprzedniej instalacji programu Visual Studio, uruchom Instalator programu Visual Studio i sprawdź składnik Snapshot Debugger w obciążeniu **programowanie ASP.NET i sieci Web**.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Jeśli jeszcze nie jest zainstalowany, zainstaluj [Visual Studio Enterprise 2017 w wersji 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) lub nowszej. Jeśli aktualizujesz z poprzedniej instalacji programu Visual Studio 2017, uruchom Instalator programu Visual Studio i sprawdź składnik Snapshot Debugger w obciążeniu **programowanie ASP.NET i sieci Web**.
   ::: moniker-end

* Planu usługi Azure App Service podstawowa lub wyższej.

* Zbieranie migawek jest dostępna dla następujących aplikacji sieci web działające w usłudze Azure App Service:
  * Aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
  * Aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz swój projekt i uruchomić rozszerzenia Snapshot Debugger

1. Otwórz projekt, który chcesz debugowania migawek.

   > [!IMPORTANT]
   > Do debugowania migawki, należy otworzyć *tę samą wersję kodu źródłowego* , są publikowane w usłudze Azure App Service.

::: moniker range="<=vs-2017"

2. W programie Cloud Explorer (**Widok > programu Cloud Explorer**), kliknij prawym przyciskiem myszy projekt jest wdrażany do usługi Azure App Service i wybierz **dołączyć rozszerzenie Snapshot Debugger**.

   ![Uruchamianie rozszerzenia snapshot debugger](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Wybierz **> debugowania Snapshot Debugger Dołącz...** . Wybierz Azure App Service projekt jest wdrażany w programie oraz konto usługi Azure Storage, a następnie kliknij przycisk **Dołącz**. Snapshot Debugger obsługuje również Virtual Machine Scale Sets [usługi Azure Kubernetes](debug-live-azure-kubernetes.md) i [Azure Virtual Machines (VM) &](debug-live-azure-virtual-machines.md).

   ![Uruchom Debuger migawek z menu Debuguj](../debugger/media/snapshot-debug-menu-attach.png)

   ![Wybierz zasób platformy Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > Po raz pierwszy wybierzesz **dołączyć rozszerzenie Snapshot Debugger**, zostanie wyświetlony monit zainstalować rozszerzenie witryny Snapshot Debugger w usłudze Azure App Service. Ta instalacja wymaga ponownego uruchomienia usługi Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Rozszerzenie witryny usługi Application Insights obsługuje również debugowania migawek. Jeśli zostanie wyświetlony komunikat o błędzie "nieaktualne rozszerzenie witryny", zobacz Wskazówki dotyczące [rozwiązywania problemów i znane problemy dotyczące debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md) na potrzeby uaktualniania szczegółów.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Program Visual Studio 2019 w wersji 16,2 lub nowszej) Snapshot Debugger włączono obsługę chmury platformy Azure. Upewnij się, że wybrane konto usługi Azure Resource i Azure Storage znajdują się w tej samej chmurze. Jeśli masz pytania dotyczące konfiguracji [zgodności platformy Azure](https://azure.microsoft.com/overview/trusted-cloud/) w przedsiębiorstwie, skontaktuj się z administratorem platformy Azure.
   ::: moniker-end

   Program Visual Studio jest teraz w trybie debugowania migawek.
   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

   Okno **moduły** pokazuje, kiedy wszystkie moduły zostały załadowane dla Azure App Service (wybierz polecenie **debuguj > moduły > systemu Windows** , aby otworzyć to okno).

   ![Sprawdź okno modułów](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustaw punkt przyciągania

1. W edytorze kodu kliknij lewy odstęp obok wiersza kodu, który interesuje Cię, aby ustawić punkt przyciągania. Upewnij się, że kod jest już wykonywany.

   ![Ustaw punkt przyciągania](../debugger/media/snapshot-set-snappoint.png)

2. Kliknij przycisk **Rozpocznij zbieranie** włączenie punktu przyciągania.

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

W tym samouczku przedstawiono sposób korzystania z Snapshot Debugger App Services. Warto przeczytać więcej na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)