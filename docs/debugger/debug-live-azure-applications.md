---
title: Debugowanie na żywo aplikacji ASP.NET, Azure
description: Dowiedz się, jak Ustaw punkty przyciągania i wyświetlanie migawki za pomocą rozszerzenia Snapshot Debugger.
ms.custom: mvc
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: bcb25566d530f85d5ac9a8d1a5f32c770a07bf21
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863998"
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

* Rozszerzenie Snapshot Debugger jest dostępna tylko dla Visual Studio Enterprise 2017 w wersji 15.5 lub nowszej za pomocą **obciążenie programistyczne platformy Azure**. (W obszarze **poszczególne składniki** karty, możesz znaleźć go w folderze **debugowanie i testowanie** > **rozszerzenia Snapshot debugger**.)

    Jeśli jeszcze nie jest zainstalowany, zainstaluj [Visual Studio Enterprise 2017 w wersji 15.5](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) lub nowszej. Jeśli aktualizujesz z poprzedniej instalacji programu Visual Studio 2017, uruchom Instalatora programu Visual Studio i zaewidencjonuj składnika rozszerzenia Snapshot Debugger **obciążenie projektowania platformy ASP.NET i sieci web**.

* Planu usługi Azure App Service podstawowa lub wyższej.

* Zbieranie migawek jest dostępna dla następujących aplikacji sieci web działające w usłudze Azure App Service:

    * Aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
    * Aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz swój projekt i uruchomić rozszerzenia Snapshot Debugger

1. Otwórz projekt, który chcesz debugowania migawek.

    > [!IMPORTANT]
    > Do debugowania migawki, należy otworzyć **tę samą wersję kodu źródłowego** , są publikowane w usłudze Azure App Service.

1. W programie Cloud Explorer (**Widok > programu Cloud Explorer**), kliknij prawym przyciskiem myszy projekt jest wdrażany do usługi Azure App Service i wybierz **dołączyć rozszerzenie Snapshot Debugger**.

   ![Uruchamianie rozszerzenia snapshot debugger](../debugger/media/snapshot-launch.png)

    Po raz pierwszy wybierzesz **dołączyć rozszerzenie Snapshot Debugger**, zostanie wyświetlony monit zainstalować rozszerzenie witryny Snapshot Debugger w usłudze Azure App Service. Ta instalacja wymaga ponownego uruchomienia usługi Azure App Service.

   Program Visual Studio jest teraz w trybie debugowania migawek.

    > [!NOTE]
    > Rozszerzenie witryny usługi Application Insights obsługuje również debugowania migawek. Jeśli wystąpią "rozszerzenie nieaktualna witryny" komunikat o błędzie, zobacz [rozwiązania problemu wskazówki i znanych problemów dotyczących debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md) dla uaktualnienie szczegółowe informacje.

   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

   **Modułów** okna dowiesz się, gdy wszystkie moduły zostały załadowane dla usługi Azure App Service (wybierz **debugowanie / Windows / modułów** otworzyć to okno).

   ![Sprawdź okno modułów](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustaw punkt przyciągania

1. W edytorze kodu kliknij lewym marginesie na oprawę obok wiersza kodu, który Cię interesuje można ustawić punktu przyciągania. Upewnij się, że kod, który będzie wykonywać.

   ![Ustaw punkt przyciągania](../debugger/media/snapshot-set-snappoint.png)

2. Kliknij przycisk **Rozpocznij zbieranie** włączenie punktu przyciągania.

   ![Włącz punkt przyciągania](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nie można wykonać kroku podczas wyświetlania migawki, ale można umieścić wiele punktów przyciągania w kodzie z wykonania na różne wiersze kodu. Jeśli masz wiele punktów przyciągania w kodzie rozszerzenia Snapshot Debugger sprawia, że się, że odpowiednie migawek z tej samej sesji użytkownika końcowego. Rozszerzenie Snapshot Debugger robi to, nawet jeśli wielu użytkowników osiągnięcia swojej aplikacji.

## <a name="take-a-snapshot"></a>Utwórz migawkę

Po włączeniu punktu przyciągania będzie przechwytywać migawki, ilekroć wykonywany wiersza kodu, w którym znajduje się punkt przyciągania. To wykonanie może być spowodowany rzeczywistego żądania na serwerze. Aby wymusić Twojego punktu przyciągania trafień, przejdź do widoku przeglądarki witryny sieci web i podjąć działania wymaganego co powodować Twojego punktu przyciągania na.

## <a name="inspect-snapshot-data"></a>Sprawdź dane migawki

1. Po osiągnięciu punktu przyciągania migawki pojawia się w oknie narzędzia diagnostyczne. Aby otworzyć to okno, wybierz **debugowanie / Windows / Pokaż narzędzia diagnostyczne**.

   ![Otwarcie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie punktu przyciągania, aby otworzyć migawki w edytorze kodu.

   ![Sprawdź dane migawki](../debugger/media/snapshot-inspect-data.png)

   Z poziomu tego widoku możesz umieścić kursor zmienne, aby przeglądać DataTips, **zmiennych lokalnych**, **zegarki**, i **stos wywołań** systemu windows, a także obliczać wyrażeń.

    Nadal działa z witryną i nie ma to wpływ na użytkowników końcowych. Tylko jedna migawka jest przechwytywany na punkt przyciągania domyślnie: po przechwyceniu migawkę punktu przyciągania zostanie wyłączony. Chcesz przechwytywać innego migawkę punktu przyciągania, można włączyć punkt przyciągania ponownie, klikając **Aktualizuj kolekcję**.

Możesz również dodać więcej punktów przyciągania do swojej aplikacji i włączać je za pomocą **Aktualizuj kolekcję** przycisku.

**Potrzebujesz pomocy?** Zobacz [Rozwiązywanie problemów i znane problemy](../debugger/debug-live-azure-apps-troubleshooting.md) i [często zadawane pytania dotyczące debugowania migawek](../debugger/debug-live-azure-apps-faq.md) stron.

## <a name="set-a-conditional-snappoint"></a>Ustaw warunkowego punktu przyciągania

Jeśli jest trudne do odtworzenia w określonym stanie w swojej aplikacji, należy rozważyć, czy korzystanie z warunkowego punktu przyciągania mogą pomóc w. Warunkowe punkty przyciągania uniknąć wykonywania migawki, aż aplikacja przejdzie do żądanego stanu, na przykład w przypadku zmiennej określonej wartości, które chcesz sprawdzić. Można określić warunki, używając wyrażeń i filtry, lub liczbą trafień.

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

1. W polu wiadomości można wprowadzić nowy komunikat dziennika, które mają być rejestrowane. Można również obliczyć zmiennych w wiadomości dziennika, umieszczając je wewnątrz nawiasów klamrowych.

    Jeśli wybierzesz **Wyślij do okna danych wyjściowych**, gdy zostanie osiągnięty punkt rejestrowania komunikat jest wyświetlany w oknie narzędzia diagnostyczne.

    ![Punkt rejestrowania danych w oknie sesji diagnostycznej](../debugger/media/snapshot-logpoint-output.png)

    Jeśli wybierzesz **Wyślij do dziennika aplikacji**, gdy zostanie osiągnięty punkt rejestrowania, komunikat pojawi się gdziekolwiek zobaczyć komunikaty z `System.Diagnostics.Trace` (lub `ILogger` platformie .NET Core), takich jak [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób użycia rozszerzenia Snapshot Debugger. Warto przeczytać więcej na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)
