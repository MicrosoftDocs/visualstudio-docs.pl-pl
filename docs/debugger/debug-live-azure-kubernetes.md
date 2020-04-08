---
title: Debugowanie ASP.NET usług Kubernetes na żywo na żywo
description: Dowiedz się, jak ustawić punkty przyciągania i wyświetlić migawki za pomocą debugera migawek.
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
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Debugowanie ASP.NET usług Kubernetes na żywo na żywo przy użyciu debugera migawek

Debuger migawki wykonuje migawkę aplikacji w produkcji, gdy kod, który cię interesuje wykonuje. Aby poinstruować debugera, aby zrobić migawkę, należy ustawić punkty przyciągania i punkty dziennika w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło nie tak, bez wpływu na ruch aplikacji produkcyjnej. Debuger migawek może pomóc znacznie skrócić czas potrzebny do rozwiązania problemów występujących w środowiskach produkcyjnych.

Punkty przyciągania i punkty dziennika są podobne do punktów przerwania, ale w przeciwieństwie do punktów przerwania punkty przyciągania nie zatrzymują aplikacji po trafieniu. Zazwyczaj przechwytywanie migawki w punkcie przyciągania trwa 10-20 milisekund.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Uruchamianie debugera migawki
> * Ustawianie punktu przyciągania i wyświetlanie migawki
> * Ustawianie punktu logpoint

## <a name="prerequisites"></a>Wymagania wstępne

* Debuger migawek dla usług Kubernetes platformy Azure jest dostępny tylko dla programu Visual Studio 2019 Enterprise lub nowszego z **obciążeniem dewelopera platformy Azure.** (Na karcie **Poszczególne składniki** znajdziesz ją w obszarze **Debugowanie i testowanie** > **debugera migawki).**

    Jeśli nie jest jeszcze zainstalowany, zainstaluj [program Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Kolekcja migawek jest dostępna dla następujących aplikacji sieci Web usług Azure Kubernetes Services:
  * ASP.NET aplikacje Core działające w serwisie .NET Core 2.2 lub nowszym w debianie 9.
  * ASP.NET aplikacje Core działające w programie .NET Core 2.2 lub nowszym w programie Alpine 3.8.
  * ASP.NET aplikacje Core uruchomione na .NET Core 2.2 lub nowszym na Ubuntu 18.04.

    > [!NOTE]
    > Aby ułatwić włączenie obsługi debugera migawek w ukasza, udostępniliśmy [repozytorium zawierające zestaw plików dockerfiles, które pokazują konfigurację obrazów platformy Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz projekt i uruchom debuger migawki

1. Otwórz projekt, który chcesz debugować migawką.

    > [!IMPORTANT]
    > Aby migawkę debugowania, należy otworzyć *tę samą wersję kodu źródłowego,* który jest publikowany w usłudze Azure Kubernetes.

1. Wybierz **debugowanie > dołącz debuger migawki...**. Wybierz zasób AKS, na który jest wdrażana aplikacja internetowa, oraz konto magazynu platformy Azure, a następnie kliknij pozycję **Dołącz**. Debuger migawek obsługuje również [usługę Azure App Service](debug-live-azure-applications.md) i zestawy [skalowania maszyn wirtualnych platformy Azure (VM) &.](debug-live-azure-virtual-machines.md)

    ![Uruchamianie debugera migawki z menu Debugowania](../debugger/media/snapshot-debug-menu-attach.png)

    ![Wybieranie zasobu platformy Azure](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 w wersji 16.2 i wyższej) Debuger migawek włączył obsługę chmury platformy Azure. Upewnij się, że zarówno zasoby platformy Azure, jak i wybrane konto usługi Azure Storage pochodzą z tej samej chmury. Skontaktuj się z administratorem platformy Azure, jeśli masz pytania dotyczące konfiguracji [zgodności platformy Azure](https://azure.microsoft.com/overview/trusted-cloud/) w przedsiębiorstwie.

Visual Studio jest teraz w trybie debugowania migawki.

   ![Tryb debugowania migawki](../debugger/media/snapshot-message.png)

   Okno **Moduły** pokazuje, kiedy wszystkie moduły zostały załadowane do usługi Azure App Service (wybierz **debugowanie > modułów > systemu Windows,** aby otworzyć to okno).

   ![Sprawdź okno Moduły](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustawianie punktu przyciągania

1. W edytorze kodu kliknij lewy margines marginesu na wiersz kodu, który Cię interesuje, aby ustawić punkt przyciągania. Upewnij się, że jest to kod, który wiesz, że zostanie wykonany.

   ![Ustawianie punktu przyciągania](../debugger/media/snapshot-set-snappoint.png)

1. Kliknij **przycisk Rozpocznij zbieranie danych,** aby włączyć punkt przyciągania.

   ![Włączanie punktu przyciągania](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nie można krok podczas wyświetlania migawki, ale można umieścić wiele punktów przyciągania w kodzie, aby wykonać w różnych wierszach kodu. Jeśli masz wiele punktów przyciągania w kodzie, Debuger migawki upewnia się, że odpowiednie migawki są z tej samej sesji użytkownika końcowego. Debuger migawki robi to, nawet jeśli istnieje wiele użytkowników trafienia aplikacji.

## <a name="take-a-snapshot"></a>Tworzenie migawki

Po ustawieniu punktu dostępu można ręcznie wygenerować migawkę, przechodząc do widoku przeglądarki witryny sieci Web i uruchamiając zaznaczony wiersz kodu lub poczekać, aż użytkownicy wygenerują ją z użycia witryny.

## <a name="inspect-snapshot-data"></a>Sprawdzanie danych migawek

1. Po naciśnięciu punktu przyciągania w oknie Narzędzia diagnostyczne pojawi się migawka. Aby otworzyć to okno, wybierz pozycję **Debugowanie > > programu Windows Show Diagnostic Tools**.

    ![Otwieranie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie punkt przyciągania, aby otworzyć migawkę w edytorze kodu.

    ![Sprawdzanie danych migawek](../debugger/media/snapshot-inspect-data.png)

    W tym widoku można najechać kursorem na zmienne, aby wyświetlić końcówki danych, użyć okien **Locals**, **Watches**i **Call Stack,** a także ocenić wyrażenia.

    Sama strona internetowa jest nadal owana, a użytkownicy końcowi nie mają wpływu. Domyślnie na punkt przyciągania jest rejestrowana tylko jedna migawka: po przechwyceniu migawki punkt przyciągania jest wyłączany. Jeśli chcesz przechwycić inną migawkę w punkcie przyciągania, możesz ponownie włączyć punkt przyciągania, klikając pozycję **Aktualizuj kolekcję**.

Możesz również dodać więcej punktów przyciągania do aplikacji i włączyć je za pomocą przycisku **Kolekcja aktualizacji.**

**Potrzebujesz pomocy?** Zobacz [rozwiązywanie problemów i znane problemy](../debugger/debug-live-azure-apps-troubleshooting.md) oraz często zadawane pytania dotyczące stron [debugowania migawek.](../debugger/debug-live-azure-apps-faq.md)

## <a name="set-a-conditional-snappoint"></a>Ustawianie punktu przyciągania warunkowego

Jeśli trudno jest odtworzyć określony stan w aplikacji, należy rozważyć użycie punktu przyciągania warunkowego. Warunkowe punkty przyciągania ułatwiają kontrolowanie, kiedy należy zrobić migawkę, na przykład gdy zmienna zawiera określoną wartość, którą chcesz sprawdzić. Można ustawić warunki przy użyciu wyrażeń, filtrów lub liczby trafień.

#### <a name="to-create-a-conditional-snappoint"></a>Aby utworzyć punkt przyciągania warunkowego

1. Kliknij prawym przyciskiem myszy ikonę punktu przyciągania (pustą kulkę) i wybierz pozycję **Ustawienia**.

   ![Wybierz Ustawienia](../debugger/media/snapshot-snappoint-settings.png)

1. W oknie ustawień punktu przyciągania wpisz wyrażenie.

   ![Wpisz wyrażenie](../debugger/media/snapshot-snappoint-conditions.png)

   Na poprzedniej ilustracji migawka jest pobierana `visitor.FirstName == "Dan"`tylko dla punktu przyciągania tylko wtedy, gdy .

## <a name="set-a-logpoint"></a>Ustawianie punktu logpoint

Oprócz robienia migawki po naciśnięciu punktu przyciągania można również skonfigurować punkt przyciągania do rejestrowania wiadomości (czyli utworzenia punktu dziennika). Można ustawić punkty dziennika bez konieczności ponownego rozmieszczenia aplikacji. Punkty dziennika są wykonywane wirtualnie i nie powodują wpływu lub skutków ubocznych dla uruchomionej aplikacji.

#### <a name="to-create-a-logpoint"></a>Aby utworzyć punkt dziennika

1. Kliknij prawym przyciskiem myszy ikonę punktu przyciągania (niebieski sześciokąt) i wybierz polecenie **Ustawienia**.

1. W oknie ustawień punktu przyciągania wybierz pozycję **Akcje**.

    ![Tworzenie punktu dziennika](../debugger/media/snapshot-logpoint.png)

1. W polu **Wiadomość** można wprowadzić nowy komunikat dziennika, który chcesz zarejestrować. Można również ocenić zmienne w komunikacie dziennika, umieszczając je wewnątrz nawiasów klamrowych.

    Jeśli wybierzesz **okno Wyślij do wyjścia**, po naciśnięciu punktu logpointa komunikat pojawi się w oknie Narzędzia diagnostyczne.

    ![Dane punktu dziennika w oknie Narzędzia diagnostyczne](../debugger/media/snapshot-logpoint-output.png)

    Jeśli wybierzesz **wyślij do dziennika aplikacji**, po naciśnięciu punktu logpoint, komunikat pojawi się w dowolnym miejscu, które można zobaczyć wiadomości z `System.Diagnostics.Trace` (lub `ILogger` w .NET Core), takich jak App [Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak używać debugera migawek dla platformy Azure Kubernetes. Możesz przeczytać więcej szczegółów na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)