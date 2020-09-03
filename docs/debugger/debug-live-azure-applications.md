---
title: Debuguj aplikacje Azure ASP.NET na żywo
description: Dowiedz się, jak ustawić punkty przyciągania i wyświetlić migawki przy użyciu Snapshot Debugger.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 07ebe8a583717689ca424bf969e7c19e87ebf08e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350670"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debuguj aplikacje platformy Azure ASP.NET na żywo przy użyciu Snapshot Debugger

Snapshot Debugger wykonuje migawkę aplikacji w środowisku produkcyjnym, gdy interesujący kod jest wykonywany. Aby polecić debugerowi wykonanie migawki, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło źle, bez wpływu na ruch aplikacji produkcyjnej. Snapshot Debugger może pomóc znacząco skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

Punkty przyciągania i punkty rejestrowania są podobne do punktów przerwania, ale w przeciwieństwie do punktów przerwania, punkty przyciągania nie wstrzymuje aplikacji po trafieniu. Zwykle przechwytywanie migawki w punkt przyciągania trwa 10-20 milisekund.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom Snapshot Debugger
> * Ustaw punkt przyciągania i Wyświetl migawkę
> * Ustaw punkt rejestrowania

## <a name="prerequisites"></a>Wymagania wstępne

* Snapshot Debugger jest dostępny tylko w programie Visual Studio 2017 Enterprise w wersji 15,5 lub nowszej przy użyciu **obciążeń programistycznych platformy Azure**. (Na karcie **poszczególne składniki** znajdziesz ją w obszarze **debugowanie i testowanie**  >  **Debuger migawek**.)

   ::: moniker range=">=vs-2019"
   Jeśli nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Jeśli aktualizujesz z poprzedniej instalacji programu Visual Studio, uruchom Instalator programu Visual Studio i sprawdź składnik Snapshot Debugger w **obciążeniu programowanie ASP.NET i sieci Web**.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Jeśli nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2017 Enterprise w wersji 15,5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) lub nowszej. Jeśli aktualizujesz z poprzedniej instalacji programu Visual Studio 2017, uruchom Instalator programu Visual Studio i sprawdź składnik Snapshot Debugger w **obciążeniu programowanie ASP.NET i sieci Web**.
   ::: moniker-end

* Plan Azure App Service w warstwie Podstawowa lub wyższa.

* Kolekcja migawek jest dostępna dla następujących aplikacji sieci Web działających w Azure App Service:
  * ASP.NET aplikacje działające w .NET Framework 4.6.1 lub nowszych.
  * ASP.NET Core aplikacje działające na platformie .NET Core 2,0 lub nowszej w systemie Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz projekt i uruchom Snapshot Debugger

1. Otwórz projekt, dla którego chcesz debugować migawkę.

   > [!IMPORTANT]
   > Aby przeprowadzić debugowanie migawek, należy otworzyć tę *samą wersję kodu źródłowego* , która jest publikowana w Azure App Service.

::: moniker range="<=vs-2017"

2. W programie Cloud Explorer (**wyświetl > Cloud Explorer**) kliknij prawym przyciskiem myszy Azure App Service projekt jest wdrożony i wybierz pozycję **Dołącz Snapshot Debugger**.

   ![Uruchamianie debugera migawek](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Wybierz **> debugowania Snapshot Debugger Dołącz...**. Wybierz Azure App Service projekt jest wdrażany w programie oraz konto usługi Azure Storage, a następnie kliknij przycisk **Dołącz**. Snapshot Debugger obsługuje również Virtual Machine Scale Sets [usługi Azure Kubernetes](debug-live-azure-kubernetes.md) i [Azure Virtual Machines (VM) &](debug-live-azure-virtual-machines.md).

   ![Uruchom Debuger migawek z menu Debuguj](../debugger/media/snapshot-debug-menu-attach.png)

   ![Wybierz zasób platformy Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > Przy pierwszym wybraniu opcji **dołącz Snapshot Debugger**zostanie wyświetlony monit o zainstalowanie rozszerzenia witryny Snapshot Debugger w Azure App Service. Ta instalacja wymaga ponownego uruchomienia Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Rozszerzenie witryny Application Insights obsługuje również debugowanie migawek. Jeśli zostanie wyświetlony komunikat o błędzie "nieaktualne rozszerzenie witryny", zobacz Wskazówki dotyczące [rozwiązywania problemów i znane problemy dotyczące debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md) na potrzeby uaktualniania szczegółów.
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

2. Kliknij pozycję **Rozpocznij zbieranie** , aby włączyć punkt przyciągania.

   ![Włącz punkt przyciągania](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > Nie można wykonać kroku podczas wyświetlania migawki, ale można umieścić wiele punkty przyciągania w kodzie, aby śledzić wykonywanie w różnych wierszach kodu. Jeśli masz wiele punkty przyciągania w kodzie, Snapshot Debugger upewnij się, że odpowiednie migawki pochodzą z tej samej sesji użytkownika końcowego. Snapshot Debugger robi to nawet wtedy, gdy w aplikacji jest wielu użytkowników.

## <a name="take-a-snapshot"></a>Tworzenie migawki

Po ustawieniu punkt przyciągania można ręcznie wygenerować migawkę, przechodząc do widoku przeglądarki witryny sieci Web i uruchamiając wiersz kodu lub poczekaj, aż użytkownicy generują je na podstawie ich użycia.

## <a name="inspect-snapshot-data"></a>Sprawdzanie danych migawek

1. Po trafieniu punkt przyciągania zostanie wyświetlona migawka w oknie narzędzia diagnostyczne. Aby otworzyć to okno, wybierz **debuguj > Windows > pokaż narzędzia diagnostyczne**.

   ![Otwórz punkt przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie punkt przyciągania, aby otworzyć migawkę w edytorze kodu.

   ![Sprawdzanie danych migawek](../debugger/media/snapshot-inspect-data.png)

   Z tego widoku można przesuwać się nad zmiennymi, aby wyświetlać etykietki danych, korzystać z okien zmiennych **lokalnych**, **zegarki**i **stosu wywołań** , a także szacować wyrażenia.

   Sama witryna sieci Web jest nadal na żywo, a użytkownicy końcowi nie mają do nich wpływu. Tylko jedna migawka jest domyślnie przechwytywana na punkt przyciągania: Po przechwyceniu migawki punkt przyciągania wyłączone. Jeśli chcesz przechwycić kolejną migawkę w punkt przyciągania, możesz włączyć punkt przyciągania ponownie, klikając polecenie **Aktualizuj kolekcję**.

Możesz również dodać więcej punkty przyciągania do aplikacji i włączyć je przy użyciu przycisku **Aktualizuj kolekcję** .

**Potrzebujesz pomocy?** Zapoznaj się z tematami [Rozwiązywanie problemów i znanych problemów](../debugger/debug-live-azure-apps-troubleshooting.md) oraz [często zadawanych pytań dotyczących debugowania migawek](../debugger/debug-live-azure-apps-faq.md) .

## <a name="set-a-conditional-snappoint"></a>Ustaw punkt przyciągania warunkowe

Jeśli nie można ponownie utworzyć określonego stanu w aplikacji, należy rozważyć użycie warunkowej punkt przyciągania. Warunkowe punkty przyciągania ułatwiają kontrolowanie, kiedy należy wykonać migawkę, na przykład gdy zmienna zawiera konkretną wartość, którą chcesz sprawdzić. Można ustawić warunki przy użyciu wyrażeń, filtrów lub liczby trafień.

#### <a name="to-create-a-conditional-snappoint"></a>Aby utworzyć punkt przyciągania warunkowe

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (kulka pusta) i wybierz pozycję **Ustawienia**.

   ![Wybierz Ustawienia](../debugger/media/snapshot-snappoint-settings.png)

1. W oknie Ustawienia punkt przyciągania wpisz wyrażenie.

   ![Wpisz wyrażenie](../debugger/media/snapshot-snappoint-conditions.png)

   Na powyższej ilustracji migawka jest wykonywana tylko dla punkt przyciągania, kiedy `visitor.FirstName == "Dan"` .

## <a name="set-a-logpoint"></a>Ustaw punkt rejestrowania

Oprócz tworzenia migawek, gdy punkt przyciągania jest trafień, można także skonfigurować punkt przyciągania do rejestrowania wiadomości (to oznacza, że utworzono punkt rejestrowania). Możesz ustawić punkty rejestrowania bez konieczności ponownego wdrażania aplikacji. Punkty rejestrowania są wykonywane praktycznie i nie powodują wpływu ani efektów ubocznych działającej aplikacji.

#### <a name="to-create-a-logpoint"></a>Aby utworzyć punkt rejestrowania

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (niebieska sześciokąt), a następnie wybierz pozycję **Ustawienia**.

1. W oknie Ustawienia punkt przyciągania wybierz pozycję **Akcje**.

   ![Utwórz punkt rejestrowania](../debugger/media/snapshot-logpoint.png)

1. W polu **komunikat** można wprowadzić nowy komunikat dziennika, który ma być zalogowany. Możesz również obliczyć zmienne w komunikacie dziennika, umieszczając je w nawiasach klamrowych.

   W przypadku wybrania opcji **Wyślij do okno dane wyjściowe**, gdy zostanie trafiony punkt rejestrowania, komunikat pojawi się w oknie narzędzia diagnostyczne.

   ![Punkt rejestrowania dane w oknie narzędzia diagnostyczne](../debugger/media/snapshot-logpoint-output.png)

   Jeśli wybierzesz pozycję **Wyślij do dziennika aplikacji**, gdy punkt rejestrowania zostanie trafiony, komunikat pojawi się w dowolnym miejscu, w którym można zobaczyć komunikaty z `System.Diagnostics.Trace` (lub `ILogger` w programie .NET Core), takie jak [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób korzystania z Snapshot Debugger App Services. Możesz chcieć przeczytać więcej szczegółowych informacji na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)