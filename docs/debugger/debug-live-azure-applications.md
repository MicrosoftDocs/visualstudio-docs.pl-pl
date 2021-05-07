---
title: Debugowanie aplikacji ASP.NET platformy Azure
titleSuffix: Visual Studio Enterprise
description: Dowiedz się, jak używać Snapshot Debugger w Visual Studio do tworzenia punktów przyciągania i tworzenia migawek podczas debugowania na żywo ASP.NET aplikacji platformy Azure.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 94c65814572c99f95d7a6edc6769e5af0ea6e748
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798378"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debugowanie aplikacji ASP.NET platformy Azure przy użyciu Snapshot Debugger

Aplikacja Snapshot Debugger migawkę aplikacji w środowisku produkcyjnym, gdy kod, który Cię interesuje, jest wykonywany. Aby poinstruować debuger, aby zrób migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło nie tak, bez wpływu na ruch aplikacji produkcyjnej. Ten Snapshot Debugger znacznie skrócić czas rozwiązywania problemów, które występują w środowiskach produkcyjnych.

Punkty przyciągania i punkty dziennika są podobne do punktów przerwania, ale w przeciwieństwie do punktów przerwania punkty przyciągania nie zatrzymywają aplikacji po trafieniu. Zazwyczaj przechwytywanie migawki w punkcie przyciągania trwa 10–20 milisekund.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom Snapshot Debugger
> * Ustawianie punktu przyciągania i wyświetlanie migawki
> * Ustawianie punktu dziennika

## <a name="prerequisites"></a>Wymagania wstępne

* Snapshot Debugger jest dostępna tylko od wersji Visual Studio 2017 Enterprise w wersji 15.5 lub wyższej z obciążeniem **Tworzenie aplikacji na platformie Azure.** (Na karcie **Poszczególne składniki** znajduje się ona w obszarze **Debugowanie i testowanie**  >  **Debuger migawek).**

   ::: moniker range=">=vs-2019"
   Jeśli nie jest jeszcze zainstalowany, zainstaluj program [Visual Studio 2019.](https://visualstudio.microsoft.com/downloads) Jeśli aktualizujesz z poprzedniej instalacji Visual Studio, uruchom program Instalator programu Visual Studio i sprawdź składnik Snapshot Debugger w obciążeniu tworzenie aplikacji ASP.NET i **aplikacji internetowych.**
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Jeśli nie jest jeszcze zainstalowany, zainstaluj program [Visual Studio 2017 Enterprise w wersji 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) lub nowszej. Jeśli aktualizujesz z poprzedniej instalacji programu Visual Studio 2017, uruchom program Instalator programu Visual Studio i sprawdź składnik Snapshot Debugger w obciążeniu tworzenie aplikacji internetowych ASP.NET i **aplikacji internetowych.**
   ::: moniker-end

* Plan podstawowy lub Azure App Service wyższego.

* Kolekcja migawek jest dostępna dla następujących aplikacji internetowych uruchomionych w Azure App Service:
  * ASP.NET działające w .NET Framework 4.6.1 lub nowszej.
  * ASP.NET Core działających na .NET Core 2.0 lub nowszym w systemie Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz projekt i uruchom Snapshot Debugger

1. Otwórz projekt, który chcesz debugować migawki.

   > [!IMPORTANT]
   > Aby debugować migawki, należy otworzyć tę *samą wersję* kodu źródłowego, która jest opublikowana w Azure App Service.

::: moniker range="<=vs-2017"

2. W eksploratorze chmury **(Wyświetl > Cloud Explorer)** kliknij prawym przyciskiem myszy ikonę Azure App Service do wdrożenia projektu, a następnie wybierz pozycję **Dołącz** Snapshot Debugger .

   ![Uruchamianie debugera migawek](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Wybierz **pozycję Debuguj > dołącz Snapshot Debugger...**. Wybierz adres Azure App Service w programie i konto usługi Azure Storage, a następnie kliknij pozycję **Dołącz**. Snapshot Debugger obsługuje również usługi [Azure Kubernetes Service](debug-live-azure-kubernetes.md) [i Azure Virtual Machines (VM) & Virtual Machine Scale Sets.](debug-live-azure-virtual-machines.md)

   ![Uruchamianie debugera migawek z menu Debugowanie](../debugger/media/snapshot-debug-menu-attach.png)

   ![Wybieranie zasobu platformy Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > Przy pierwszym wybraniu polecenia **Dołącz Snapshot Debugger** zostanie wyświetlony monit o zainstalowanie rozszerzenia Snapshot Debugger na komputerze Azure App Service. Ta instalacja wymaga ponownego uruchomienia Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Rozszerzenie Application Insights obsługuje również debugowanie migawek. Jeśli wystąpi komunikat o błędzie "Rozszerzenie witryny jest aktualne", zobacz wskazówki dotyczące rozwiązywania problemów i znane problemy dotyczące debugowania migawek, aby [uzyskać](../debugger/debug-live-azure-apps-troubleshooting.md) szczegółowe informacje.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 w wersji 16.2 lub nowszej) Snapshot Debugger włączono obsługę chmury platformy Azure. Upewnij się, że zarówno zasób platformy Azure, jak i wybrane konto usługi Azure Storage znajdują się w tej samej chmurze. Jeśli masz pytania dotyczące konfiguracji zgodności platformy Azure w przedsiębiorstwie, skontaktuj się z [administratorem platformy Azure.](https://azure.microsoft.com/overview/trusted-cloud/)
   ::: moniker-end

   Visual Studio jest teraz w trybie debugowania migawek.
   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

   Okno **Moduły** pokazuje, kiedy wszystkie moduły zostały załadowane dla Azure App Service (wybierz pozycję Debuguj moduły > **Windows > Modules,** aby otworzyć to okno).

   ![Sprawdź okno Moduły](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustawianie punktu przyciągania

1. W edytorze kodu kliknij lewy rynnę obok wiersza kodu, który Cię interesuje, aby ustawić punkt przyciągania. Upewnij się, że jest to kod, który będzie wykonywany.

   ![Ustawianie punktu przyciągania](../debugger/media/snapshot-set-snappoint.png)

2. Kliknij **przycisk Start Collection** (Rozpocznij zbieranie), aby włączyć punkt przyciągania.

   ![Włączanie punktu przyciągania](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > Nie można wykonać kroku podczas wyświetlania migawki, ale można umieścić wiele punktów przyciągania w kodzie, aby śledzić wykonywanie w różnych wierszach kodu. Jeśli w kodzie istnieje wiele punktów przyciągania, Snapshot Debugger upewnia się, że odpowiednie migawki są z tej samej sesji użytkownika końcowego. Aplikacja Snapshot Debugger to zrobić, nawet jeśli wielu użytkowników dobije aplikację.

## <a name="take-a-snapshot"></a>Tworzenie migawki

Po skonfigurowaniu punktu przyciągania możesz ręcznie wygenerować migawkę, przechodząc do widoku przeglądarki witryny internetowej i uruchamiając wiersz kodu oznaczony lub czekając, aż użytkownicy wygenerują migawkę na podstawie użycia witryny.

## <a name="inspect-snapshot-data"></a>Sprawdzanie danych migawki

1. Po trafieniu punktu przyciągania w oknie narzędzia diagnostyczne zostanie wyświetlona migawka. Aby otworzyć to okno, wybierz pozycję **Debuguj > Windows > Pokaż narzędzia diagnostyczne.**

   ![Otwieranie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie punkt przyciągania, aby otworzyć migawkę w edytorze kodu.

   ![Sprawdzanie danych migawki](../debugger/media/snapshot-inspect-data.png)

   W tym widoku możesz umieścić wskaźnik myszy na zmiennych, aby wyświetlić etykietki danych, użyć okien Zmiennych **lokalnych,** Wyrażeń zegarowych i Stos **wywołań,** a także ocenić wyrażenia.

   Sama witryna internetowa nadal działa i nie ma to wpływu na użytkowników końcowych. Domyślnie dla każdego punktu przyciągania jest przechwytywana tylko jedna migawka: po przechwyceniu migawki punkt przyciągania jest wyłączany. Jeśli chcesz przechwycić kolejną migawkę w punkcie przyciągania, możesz ponownie włączyć punkt przyciągania, klikając pozycję **Aktualizuj kolekcję**.

Możesz również dodać więcej punktów przyciągania do aplikacji i włączyć je za pomocą **przycisku Aktualizuj kolekcję.**

**Potrzebujesz pomocy?** Zobacz Rozwiązywanie [problemów i znane problemy oraz Często](../debugger/debug-live-azure-apps-troubleshooting.md) zadawane pytania dotyczące stron [debugowania migawek.](../debugger/debug-live-azure-apps-faq.yml)

## <a name="set-a-conditional-snappoint"></a>Ustawianie warunkowego punktu przyciągania

Jeśli trudno jest odtworzyć konkretny stan w aplikacji, rozważ użycie warunkowego punktu przyciągania. Warunkowe punkty przyciągania ułatwiają kontrolowanie, kiedy należy utworzyć migawkę, na przykład gdy zmienna zawiera określoną wartość, którą chcesz sprawdzić. Warunki można ustawiać przy użyciu wyrażeń, filtrów lub liczby trafień.

#### <a name="to-create-a-conditional-snappoint"></a>Aby utworzyć warunkowy punkt przyciągania

1. Kliknij prawym przyciskiem myszy ikonę punktu przyciągania (ikonę piłki pustej), a następnie wybierz pozycję **Ustawienia**.

   ![Wybierz Ustawienia](../debugger/media/snapshot-snappoint-settings.png)

1. W oknie ustawień punktu przyciągania wpisz wyrażenie.

   ![Wpisywanie wyrażenia](../debugger/media/snapshot-snappoint-conditions.png)

   Na powyższej ilustracji migawka jest ciągnięta tylko do punktu przyciągania, gdy `visitor.FirstName == "Dan"` .

## <a name="set-a-logpoint"></a>Ustawianie punktu dziennika

Oprócz tworzenia migawki po trafieniu punktu przyciągania można również skonfigurować punkt przyciągania do rejestrować komunikat (czyli utworzyć punkt dziennika). Punkty dziennika można ustawiać bez konieczności ponownego wdychaj aplikacji. Punkty logowania są wykonywane wirtualnie i nie powodują żadnego wpływu ani skutków ubocznych na uruchamianą aplikację.

#### <a name="to-create-a-logpoint"></a>Aby utworzyć punkt dziennika

1. Kliknij prawym przyciskiem myszy ikonę punktu przyciągania (niebieski sześciokąt) i wybierz pozycję **Ustawienia**.

1. W oknie ustawień punktu przyciągania wybierz pozycję **Akcje**.

   ![Tworzenie punktu dziennika](../debugger/media/snapshot-logpoint.png)

1. W **polu Komunikat** możesz wprowadzić nowy komunikat dziennika, który chcesz rejestrować. Możesz również ocenić zmienne w komunikacie dziennika, umieszczając je w nawiasach klamrowych.

   Jeśli wybierzesz **opcję Wyślij do Okno Dane wyjściowe**, po trafieniu punktu dziennika komunikat zostanie wyświetlony w narzędzia diagnostyczne dziennika.

   ![Dane punktu dziennika w narzędzia diagnostyczne dziennika](../debugger/media/snapshot-logpoint-output.png)

   W przypadku **wybrania** opcji Wyślij do dziennika aplikacji po trafieniu punktu logowania komunikat pojawia się w dowolnym miejscu, z którym można zobaczyć komunikaty z (lub na .NET Core), na przykład z usługi `System.Diagnostics.Trace` `ILogger` App [Insights.](/azure/application-insights/app-insights-asp-net-trace-logs)

## <a name="next-steps"></a>Następne kroki

W tym samouczku opisano sposób używania Snapshot Debugger dla App Services. Możesz przeczytać więcej szczegółów na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.yml)