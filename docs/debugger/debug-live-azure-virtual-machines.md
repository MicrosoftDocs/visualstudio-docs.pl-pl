---
title: Debugowanie maszyn wirtualnych ASP.NET platformy Azure i zestawów skalowania na żywo
description: Dowiedz się, jak używać Snapshot Debugger w usłudze Visual Studio do tworzenia punktów przyciągania i tworzenia migawek podczas debugowania aplikacji ASP.NET na platformie Azure i zestawów skalowania.
ms.custom: SEO-VS-2020
ms.date: 02/06/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: bdab6b3f559628506dd301d6ced449f1e69152a6
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798495"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Debugowanie aplikacji ASP.NET na żywo na maszynach wirtualnych platformy Azure i w zestawach skalowania maszyn wirtualnych platformy Azure przy użyciu Snapshot Debugger

Aplikacja Snapshot Debugger migawkę aplikacji w środowisku produkcyjnym, gdy kod, który Cię interesuje, jest wykonywany. Aby poinstruować debuger, aby zrób migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie, co poszło nie tak, bez wpływu na ruch aplikacji produkcyjnej. Ten Snapshot Debugger znacznie skrócić czas rozwiązywania problemów, które występują w środowiskach produkcyjnych.

Punkty przyciągania i punkty dziennika są podobne do punktów przerwania, ale w przeciwieństwie do punktów przerwania punkty przyciągania nie zatrzymywają aplikacji po trafieniu. Zazwyczaj przechwytywanie migawki w punkcie przyciągania trwa 10–20 milisekund.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom Snapshot Debugger
> * Ustawianie punktu przyciągania i wyświetlanie migawki
> * Ustawianie punktu dziennika

## <a name="prerequisites"></a>Wymagania wstępne

* Snapshot Debugger dla usług Azure Virtual Machines (VM) i Azure Virtual Machine Scale Sets jest dostępna tylko dla wersji Visual Studio 2019 Enterprise lub wyższej z obciążeniem Tworzenie aplikacji na platformie **Azure.** (Na karcie **Poszczególne składniki** znajduje się ona w obszarze **Debugowanie i testowanie**  >  **Debuger migawek).**

    Jeśli nie jest jeszcze zainstalowany, zainstaluj program [Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/vs/)

* Kolekcja migawek jest dostępna dla następujących aplikacji internetowych Virtual Machines\Virtual Machine Scale Sets Azure:
  * ASP.NET działające w .NET Framework 4.6.1 lub nowszej.
  * ASP.NET Core działających na .NET Core 2.0 lub nowszym w systemie Windows.

  > [!NOTE]
  >  Visual Studio Enterprise w 32-bitowym systemie Windows nie będzie można wyświetlać migawek.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz projekt i uruchom Snapshot Debugger

1. Otwórz projekt, który chcesz debugować migawki.

    > [!IMPORTANT]
    > Aby debugować migawki, musisz otworzyć tę *samą* wersję kodu źródłowego, która jest opublikowana w usłudze Azure Virtual Machine\Virtual Machine Scale Set.

1. Wybierz **pozycję Debuguj > dołącz Snapshot Debugger...**. Wybierz pozycję Azure Virtual Machine\Virtual Machine Scale Set, w ramach których wdrożono aplikację internetową, i konto usługi Azure Storage, a następnie kliknij pozycję **Dołącz.** Snapshot Debugger obsługuje również [Azure Kubernetes Service](debug-live-azure-kubernetes.md) i [Azure App Service](debug-live-azure-applications.md).

    ![Uruchamianie debugera migawek z menu Debugowanie](../debugger/media/snapshot-debug-menu-attach.png)

    ![Wybieranie zasobu platformy Azure](../debugger/media/snapshot-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Przy pierwszym wybraniu opcji **Dołącz Snapshot Debugger** maszyny wirtualnej usługi IIS zostaną automatycznie uruchomione ponownie.
    > Przy pierwszym wybraniu opcji **Dołącz Snapshot Debugger** dla Virtual Machine Scale Sets wymaga ręcznego uaktualnienia każdego wystąpienia Virtual Machine Scale Sets.

    > [!NOTE]
    > (Visual Studio 2019 w wersji 16.2 lub nowszej) Snapshot Debugger włączono obsługę chmury platformy Azure. Upewnij się, że zarówno zasób platformy Azure, jak i wybrane konto usługi Azure Storage znajdują się w tej samej chmurze. Jeśli masz pytania dotyczące konfiguracji zgodności platformy Azure w przedsiębiorstwie, skontaktuj się z [administratorem platformy Azure.](https://azure.microsoft.com/overview/trusted-cloud/)

    Metadane modułów nie **zostaną** początkowo aktywowane, przejdź do aplikacji internetowej, a przycisk Rozpocznij kolekcję stanie się aktywny.  Visual Studio jest teraz w trybie debugowania migawek.

    ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > W przypadku usługi VMSS użytkownik musi ręcznie uaktualnić wystąpienia w Virtual Machine Scale Sets po dołączeniu Snapshot Debugger po raz pierwszy.

    Okno **Moduły** pokazuje, kiedy wszystkie moduły zostały załadowane dla maszyny wirtualnej platformy Azure\zestawu skalowania maszyn wirtualnych (wybierz pozycję Debuguj moduły > **Windows > Modules,** aby otworzyć to okno).

    ![Sprawdź okno Moduły](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustawianie punktu przyciągania

1. W edytorze kodu kliknij lewą rynnę obok wiersza kodu, który Cię interesuje, aby ustawić punkt przyciągania. Upewnij się, że jest to kod, który będzie wykonywany.

    ![Ustawianie punktu przyciągania](../debugger/media/snapshot-set-snappoint.png)

1. Kliknij **przycisk Start Collection** (Rozpocznij zbieranie), aby włączyć punkt przyciągania.

    ![Włączanie punktu przyciągania](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nie można wykonać kroku podczas wyświetlania migawki, ale można umieścić wiele punktów przyciągania w kodzie, aby śledzić wykonywanie w różnych wierszach kodu. Jeśli w kodzie istnieje wiele punktów przyciągania, Snapshot Debugger się, że odpowiednie migawki pochodziją z tej samej sesji użytkownika końcowego. Aplikacja Snapshot Debugger to zrobić, nawet jeśli wielu użytkowników nacisnie aplikację.

## <a name="take-a-snapshot"></a>Tworzenie migawki

Po skonfigurowaniu punktu przyciągania możesz ręcznie wygenerować migawkę, przechodząc do widoku przeglądarki witryny internetowej i uruchamiając wiersz kodu oznaczony lub czekając, aż użytkownicy wygenerują migawkę na podstawie użycia witryny.

## <a name="inspect-snapshot-data"></a>Sprawdzanie danych migawki

1. Po trafieniu punktu przyciągania w oknie narzędzia diagnostyczne zostanie wyświetlona migawka. Aby otworzyć to okno, wybierz pozycję **Debuguj > Windows > Pokaż narzędzia diagnostyczne.**

    ![Otwieranie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie punkt przyciągania, aby otworzyć migawkę w edytorze kodu.

    ![Sprawdzanie danych migawki](../debugger/media/snapshot-inspect-data.png)

    W tym widoku możesz umieścić wskaźnik myszy na zmiennych, aby wyświetlić etykietki danych, użyć okien Zmiennych **lokalnych,** Wyrażeń zegarowych i Stos **wywołań,** a także ocenić wyrażenia.

    Sama witryna internetowa nadal działa i nie ma to wpływu na użytkowników końcowych. Domyślnie na punkt przyciągania jest przechwytywana tylko jedna migawka: po przechwyceniu migawki punkt przyciągania jest wyłączany. Jeśli chcesz przechwycić kolejną migawkę w punkcie przyciągania, możesz ponownie włączyć punkt przyciągania, klikając pozycję **Aktualizuj kolekcję**.

Możesz również dodać więcej punktów przyciągania do aplikacji i włączyć je za pomocą **przycisku Aktualizuj kolekcję.**

**Potrzebujesz pomocy?** Zobacz Rozwiązywanie [problemów i znane problemy oraz Często zadawane](../debugger/debug-live-azure-apps-troubleshooting.md) pytania dotyczące stron [debugowania migawek.](../debugger/debug-live-azure-apps-faq.yml)

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

1. W polu **Komunikat** możesz wprowadzić nowy komunikat dziennika, który chcesz rejestrować. Możesz również ocenić zmienne w komunikacie dziennika, umieszczając je w nawiasach klamrowych.

    Jeśli wybierzesz **pozycję Wyślij do Okno Dane wyjściowe**, po trafieniu punktu dziennika komunikat zostanie wyświetlony w narzędzia diagnostyczne dziennika.

    ![Dane punktu logowania w narzędzia diagnostyczne dziennika](../debugger/media/snapshot-logpoint-output.png)

    W przypadku **wybrania** opcji Wyślij do dziennika aplikacji po trafieniu punktu logowania komunikat pojawia się w dowolnym miejscu, z którym można zobaczyć komunikaty z (lub na .NET Core), na przykład z usługi `System.Diagnostics.Trace` `ILogger` App [Insights.](/azure/application-insights/app-insights-asp-net-trace-logs)

## <a name="next-steps"></a>Następne kroki

W tym samouczku opisano sposób korzystania z usługi Azure Snapshot Debugger dla usług Azure Virtual Machines i Azure Virtual Machine Scale Sets. Możesz przeczytać więcej szczegółów na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.yml)
