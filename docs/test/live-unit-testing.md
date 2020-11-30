---
title: Live Unit Testing
description: Dowiedz się więcej na temat Live Unit Testing podczas opracowywania aplikacji, w tym obsługiwanych platform i konfiguracji Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 82ed41514109887d32f38faf4f965c923864ae32
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329357"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Jak skonfigurować i używać Live Unit Testing

Podczas tworzenia aplikacji Live Unit Testing automatycznie uruchamia wszystkie testy jednostkowe, których to dotyczy, w tle i przedstawia wyniki i pokrycie kodu w czasie rzeczywistym. Podczas modyfikowania kodu Live Unit Testing zawiera informacje na temat sposobu, w jaki zmiany wpływają na istniejące testy, oraz tego, czy dodany kod został objęty co najmniej jednym istniejącym testem. To delikatnie przypomina, aby napisać testy jednostkowe podczas tworzenia poprawek błędów lub dodawania nowych funkcji.

> [!NOTE]
> Live Unit Testing jest dostępny dla projektów C# i Visual Basic przeznaczonych dla platformy .NET Core lub .NET Framework w wersji Enterprise programu Visual Studio.

W przypadku korzystania z Live Unit Testing dla testów są zachowywane dane o stanie testów. Użycie utrwalonych danych umożliwia Live Unit Testing oferowanie najwyższej wydajności podczas jednoczesnego uruchamiania testów w odpowiedzi na zmiany kodu.

## <a name="supported-test-frameworks"></a>Obsługiwane struktury testów

Live Unit Testing współpracuje z trzema popularnymi platformami testowania jednostek wymienionymi w poniższej tabeli. Wyświetlana jest również minimalna obsługiwana wersja ich kart i struktur. Platformy testów jednostkowych są dostępne z NuGet.org.

|Platforma testowa  |Minimalna wersja programu Visual Studio adapter  |Minimalna wersja platformy  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio w wersji 2.2.0-beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter w wersji 3.5.1 |NUnit wersja 3.5.0 |
|MSTest |MSTest. TestAdapter 1.1.4 — wersja zapoznawcza |MSTest. TestFramework 1.0.5 — wersja zapoznawcza |

Jeśli masz starsze projekty testowe oparte na MSTest, które odwołują się do Microsoft. VisualStudio. QualityTools. UnitTestFramework, i nie chcesz przenosić do nowszych pakietów NuGet MSTest, przeprowadź uaktualnienie do programu Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołuje się projekt, aby Live Unit Testing działała. Można to zrobić, wykonując jawną kompilację rozwiązania (wybierz opcję **Kompiluj**  >  **ponownie rozwiązanie** z menu programu Visual Studio najwyższego poziomu) lub przywracając pakiety w rozwiązaniu (kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Przywróć pakiety NuGet**).

## <a name="configure"></a>Konfigurowanie

Skonfiguruj Live Unit Testing, wybierając **Tools**  >  **Opcje** narzędzia z paska menu programu Visual Studio najwyższego poziomu, a następnie wybierając pozycję **Live Unit Testing** w lewym okienku okna dialogowego **Opcje** .

> [!TIP]
> Po włączeniu Live Unit Testing (zobacz następną sekcję, [Uruchamianie, wstrzymywanie i zatrzymywanie Live Unit Testing](#start-pause-and-stop)), możesz również otworzyć okno dialogowe **Opcje** , wybierając opcję Live Unit Testing **testów**  >  **Live Unit Testing**  >  **Options**.

Na poniższej ilustracji przedstawiono opcje konfiguracji Live Unit Testing dostępne w oknie dialogowym:

![Opcje konfiguracji Live Unit Testing](./media/lut-options.png)

Konfigurowalne opcje obejmują:

- Czy Live Unit Testing wstrzymuje się, gdy rozwiązanie jest skompilowane i debugowane.

- Czy Live Unit Testing wstrzymuje się, gdy moc baterii systemu spadnie poniżej określonego progu.

- Czy Live Unit Testing uruchamiane automatycznie po otwarciu rozwiązania.

- Określa, czy ma zostać włączona generacja symboli i komentarzy dokumentacji XML.

- Katalog, w którym mają być przechowywane utrwalone dane.

- Możliwość usunięcia wszystkich danych trwałych. Jest to przydatne, gdy Live Unit Testing zachowuje się w nieprzewidywalny lub nieoczekiwany sposób, co sugeruje, że utrwalone dane uległy uszkodzeniu.

- Interwał, po którym przypadek testowy przeprowadzi limit czasu. Wartość domyślna to 30 sekund.

- Maksymalna liczba procesów testowych, które Live Unit Testing utworzyć.

- Maksymalna ilość pamięci, jaką mogą zużywać procesy Live Unit Testing.

- Poziom informacji zapisany w oknie **danych wyjściowych** Live Unit Testing.

   Opcje nie obejmują rejestrowania (**none**), komunikatów o błędach (**Error**), błędów i komunikatów informacyjnych (**informacje**, ustawienia domyślne) lub wszystkie szczegóły (**pełne**).

   Możesz również wyświetlić pełne dane wyjściowe w oknie **danych wyjściowych** Live Unit Testing, przypisując wartość "1" do zmiennej środowiskowej na poziomie użytkownika o nazwie `VS_UTE_DIAGNOSTICS` , a następnie uruchamiając ponownie program Visual Studio.

   Aby przechwycić szczegółowe komunikaty dziennika MSBuild z Live Unit Testing w pliku, należy ustawić `LiveUnitTesting_BuildLog` zmienną środowiskową na poziomie użytkownika na nazwę pliku, który będzie zawierać dziennik.

## <a name="start-pause-and-stop"></a>Uruchamianie, wstrzymywanie i zatrzymywanie

Aby włączyć Live Unit Testing, wybierz pozycję **Testuj**  >  **Live Unit Testing**  >  **Rozpocznij** od menu programu Visual Studio najwyższego poziomu. Gdy Live Unit Testing jest włączona, opcje dostępne w menu **Live Unit Testing** zmieniają się z jednego elementu, **zaczynają** się, aby **wstrzymywać** i **zatrzymywać**:

- **Wstrzymuje** tymczasowo wstrzymywanie Live Unit Testing.

  Gdy Live Unit Testing jest wstrzymana, Wizualizacja pokrycia nie jest wyświetlana w edytorze, ale wszystkie zebrane dane są zachowywane. Aby wznowić Live Unit Testing, wybierz pozycję **Kontynuuj** w menu Live Unit Testing. Live Unit Testing wykonuje czynności, które należy wykonać, aby przechwycić wszystkie zmiany, które zostały wprowadzone, gdy została wstrzymana, i odpowiednio aktualizuje symbole.

- **Zatrzymaj** całkowicie zatrzymuje Live Unit Testing. Live Unit Testing odrzuca wszystkie zebrane dane.

> [!NOTE]
> Po rozpoczęciu Live Unit Testing w rozwiązaniu, które nie zawiera projektu testu jednostkowego, opcje **Wstrzymaj** i **Zatrzymaj** są wyświetlane w menu **Live Unit Testing** , ale Live Unit Testing nie zostanie uruchomiony. W oknie **danych wyjściowych** zostanie wyświetlony komunikat o rozpoczęciu "Brak obsługiwanych adapterów testowych, do których odwołuje się to rozwiązanie...".

W dowolnym momencie można tymczasowo wstrzymywać lub całkowicie zatrzymywać Live Unit Testing. Można to zrobić na przykład, jeśli jesteś w trakcie refaktoryzacji i wiadomo, że testy zostaną przerwane przez pewien czas.

## <a name="view-coverage-visualization"></a>Wyświetl wizualizację pokrycia

Po włączeniu Live Unit Testing aktualizuje każdy wiersz kodu w edytorze programu Visual Studio, aby pokazać, czy kod, który jest pisany jest objęty testami jednostkowymi, oraz czy testy, które je obejmują, są przekazywane. Na poniższej ilustracji przedstawiono wiersze kodu z testami przechodzącymi i zakończonymi niepowodzeniem, a także wierszy kodu, które nie są objęte testami. Linie oznaczone zielonym "✓" są objęte tylko przekazywaniem testów, linie oznaczone czerwoną literą "x" są objęte co najmniej jednym testem, a linie oznaczone niebieską "➖" nie są objęte żadnym testem.

![Pokrycie kodu w programie Visual Studio](./media/lut-codewindow.png)

Wizualizacja pokrycia Live Unit Testing jest aktualizowana natychmiast po zmodyfikowaniu kodu w edytorze kodu. Podczas przetwarzania zmian wizualizacji w celu wskazania, że dane nie są aktualne przez dodanie obrazu czasomierza okrągłego poniżej symboli zakończonych niepowodzeniem i nie pokrytych, jak pokazano na poniższej ilustracji.

![Pokrycie kodu w programie Visual Studio przy użyciu ikony czasomierza](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Pobierz informacje o stanie testu

Przez umieszczenie kursora nad symbolem pomyślnym lub niepomyślnym w oknie kodu, można zobaczyć, ile testów jest w tym wierszu. Aby wyświetlić stan poszczególnych testów, wybierz symbol:

![Stan testu dla symbolu w programie Visual Studio](./media/lut-failedinfo.png)

Oprócz podawania nazw i wyników testów, etykietka narzędzia umożliwia ponowne uruchomienie lub debugowanie zestawu testów. W przypadku wybrania co najmniej jednego testu w etykietce narzędzia można również uruchomić lub debugować tylko te testy. Pozwala to debugować testy bez konieczności opuszczania okna kodu. Podczas debugowania, oprócz obserwowania wszystkich punktów przerwania, które można już ustawić, wykonanie programu jest wstrzymywane, gdy debuger wykonuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodę, która zwraca nieoczekiwany wynik.

Po umieszczeniu wskaźnika myszy na teście zakończonym niepowodzeniem w etykietce narzędzia rozszerza się, aby podać dodatkowe informacje o awarii, jak pokazano na poniższej ilustracji. Aby przejść bezpośrednio do testu zakończonego niepowodzeniem, kliknij go dwukrotnie w etykietce narzędzia.

![Nie można przetestować informacji o etykietce narzędzia w programie Visual Studio](./media/lut-failedmsg.png)

Gdy przejdziesz do testu zakończonego niepowodzeniem, Live Unit Testing wizualnie wskazuje, że w metodzie podpisuje testy, które mają:

- zakończony zakończono (wskazywanym przez pół zlewki i zieloną "✓")
- Niepowodzenie (połowa-pełna zlewka wraz z czerwonym " 🞩 ")
- nie są wykorzystywane w Live Unit Testing (połowa-pełna zlewka wraz z niebieską "➖")

Metody inne niż testowe nie są dekoracyjne symbolem. Na poniższej ilustracji przedstawiono wszystkie cztery typy metod.

![Metody testowe w programie Visual Studio z symbolem powodzenia lub niepowodzenia](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnozuj i popraw błędy testów

W teście zakończonym niepowodzeniem można łatwo debugować kod produktu, wprowadzać zmiany i kontynuować tworzenie aplikacji. Ponieważ Live Unit Testing działa w tle, nie trzeba przerywać ani ponownie uruchamiać Live Unit Testing podczas debugowania, Edytuj i Kontynuuj.

Na przykład niepowodzenie testu pokazane na poprzednim obrazie zostało spowodowane przez nieprawidłowe założenie w metodzie testowej, że znaki niealfabetyczne zwracają, `true` gdy są przesyłane do <xref:System.Char.IsLower%2A?displayProperty=fullName> metody. Po naprawieniu metody testowej należy przekazać wszystkie testy. Nie musisz wstrzymywać ani zatrzymywać Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Eksplorator testów

**Eksplorator testów** udostępnia interfejs, który umożliwia uruchamianie i debugowanie testów oraz analizowanie wyników testów. Live Unit Testing integruje się z **Eksploratorem testów**. Gdy Live Unit Testing nie jest włączona lub zatrzymana, **Eksplorator testów** wyświetla stan testów jednostkowych przy ostatnim uruchomieniu testu. Zmiany kodu źródłowego wymagają ponownego uruchomienia testów. Natomiast po włączeniu Live Unit Testing stan testów jednostkowych w **Eksploratorze testów** jest natychmiast aktualizowany. Nie musisz jawnie uruchamiać testów jednostkowych.

> [!TIP]
> Otwórz **Live Unit Testing** , wybierając pozycję **Testuj**  >  **Windows**  >  **Eksplorator testów** systemu Windows z menu programu Visual Studio najwyższego poziomu.

W oknie **Eksploratora testów** można zauważyć, że niektóre testy są wyblakłe. Na przykład po włączeniu Live Unit Testing po otwarciu wcześniej zapisanego projektu okno **Eksplorator testów** zostało podpięte wszystkie oprócz testu zakończonego niepowodzeniem, jak pokazano na poniższej ilustracji. W takim przypadku Live Unit Testing ponownie uruchamia test zakończony niepowodzeniem, ale nie uruchamia ponownie testów zakończonych powodzeniem. Wynika to z faktu, że dane utrwalone Live Unit Testing wskazują, że nie zostały wprowadzone żadne zmiany, ponieważ testy zostały ostatnio wykonane pomyślnie.

![Test zakończony niepowodzeniem w Eksploratorze testów](media/lut-test-explorer.png)

Wszystkie testy, które są wyświetlane, można uruchomić ponownie, wybierając opcję **Uruchom wszystkie** lub **Uruchom** z menu **Eksplorator testów** . Lub wybierz jeden lub więcej testów w menu  **Eksploratora testów** , kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom wybrane testy** lub **Debuguj wybrane testy** z menu podręcznego. Gdy testy są uruchamiane, są one rzutowane do góry.

Istnieją pewne różnice między Live Unit Testing automatycznie uruchamiać i aktualizować wyniki testów oraz jawnie uruchamiać testy z **Eksploratora testów**. Różnice te obejmują:

- Uruchamianie lub debugowanie testów z okna Eksploratora testów powoduje uruchomienie zwykłych plików binarnych, podczas gdy Live Unit Testing uruchamia instrumentację plików binarnych.
- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów, ale zamiast uruchamiania testów z domeny domyślnej. Testy przebiega z okna **Eksploratora testów** Utwórz nową domenę aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testów sekwencyjnie. W oknie **Eksplorator testów** można uruchomić wiele testów równolegle.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Okno Live Unit Testing

**Live Unit Testing**, podobnie jak w **Eksploratorze testów**, udostępnia interfejs, który umożliwia uruchamianie i debugowanie testów oraz analizowanie wyników testów. Po włączeniu Live Unit Testing stan testów jednostkowych w **Eksploratorze testów** zostaje natychmiast zaktualizowany. Nie musisz jawnie uruchamiać testów jednostkowych. Gdy Live Unit Testing nie jest włączona lub zatrzymana, **Live Unit Testing** wyświetla stan testów jednostkowych przy ostatnim uruchomieniu testu. Po ponownym uruchomieniu Live Unit Testing wymagana jest zmiana kodu źródłowego, aby ponownie uruchomić testy.

> [!TIP]
> Rozpocznij Live Unit Testing, wybierając pozycję **test**  >  **Live Unit Testing**  >  **Rozpocznij** od menu programu Visual Studio najwyższego poziomu. Okno **Live Unit Testing** można również otworzyć, korzystając z okna **Wyświetl**  >  **inne**  >  **okno Live Unit Testing** systemu Windows.

W oknie **Live Unit Testing** można zauważyć, że niektóre testy są wyblakłe. Na przykład po zatrzymaniu i ponownym uruchomieniu Live Unit Testing okno **Live Unit Testing** zanika wszystkie testy, jak pokazano na poniższej ilustracji. Wynikowe wyniki testów wskazują, że test nie był częścią najnowszego przebiegu testu jednostkowego na żywo. Testy są uruchamiane tylko wtedy, gdy zostanie wykryta zmiana lub zależności testu. W przypadku braku zmian nie jest to konieczne do uruchomienia testu. W takim przypadku szary wynik testu nadal jest "aktualny", mimo że nie był częścią ostatniego uruchomienia.

![Wyblakłe testy w Eksploratorze testów](media/vs-2019/lut-test-explorer.png)

Możesz ponownie uruchomić wszystkie testy, które są wyświetlane jako wyblakłe, wprowadzając zmiany w kodzie.

Istnieją pewne różnice między Live Unit Testing automatycznie uruchamiać i aktualizować wyniki testów oraz jawnie uruchamiać testy z **Eksploratora testów**. Różnice te obejmują:

- Uruchamianie lub debugowanie testów z okna Eksploratora testów powoduje uruchomienie zwykłych plików binarnych, podczas gdy Live Unit Testing uruchamia instrumentację plików binarnych.
- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów, ale zamiast uruchamiania testów z domeny domyślnej. Testy przebiega z okna **Eksploratora testów** Utwórz nową domenę aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testów sekwencyjnie. W oknie **Eksplorator testów** można uruchomić wiele testów równolegle.
::: moniker-end

## <a name="large-solutions"></a>Duże rozwiązania

Jeśli rozwiązanie ma 10 lub więcej projektów, program Visual Studio wyświetli następujące okno dialogowe:

- Rozpocznij Live Unit Testing i nie ma żadnych utrwalonych danych
- Wybierz **Tools**  >  **Opcje** narzędzi  >  **Live Unit Testing**  >  **Usuń utrwalone dane**

![Okno dialogowe Live Unit Testing dla dużych projektów](media/lut-large-project.png)

Okno dialogowe ostrzega o tym, że dynamiczne wykonywanie dużej liczby testów w dużych projektach może poważnie wpłynąć na wydajność. Jeśli wybierzesz **przycisk OK**, Live Unit Testing wykonuje wszystkie testy w rozwiązaniu. Jeśli wybierzesz pozycję **Anuluj**, możesz wybrać testy do wykonania. W poniższej sekcji wyjaśniono, jak to zrobić.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Uwzględnianie i Wykluczanie projektów testowych i metod testowych

W przypadku rozwiązań z wieloma projektami testowymi można kontrolować, które projekty i poszczególne metody w projekcie biorą udział w Live Unit Testing. Jeśli na przykład masz rozwiązanie z setkami projektów testowych, możesz wybrać zestaw projektów testowych przeznaczony do uczestnictwa w Live Unit Testing. Istnieje kilka sposobów, w zależności od tego, czy chcesz wykluczyć wszystkie testy w projekcie lub rozwiązaniu, dołączyć lub wykluczyć większość testów lub wykluczyć poszczególne testy. Live Unit Testing zapisuje stan dołączania/wykluczania jako ustawienia użytkownika i zapamiętuje je po zamknięciu i ponownym otwarciu rozwiązania.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Wyklucz wszystkie testy w projekcie lub rozwiązaniu

Aby wybrać poszczególne projekty w testach jednostkowych, wykonaj następujące czynności po rozpoczęciu Live Unit Testing:

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz **Live Unit Testing**  >  **Wyklucz** , aby wykluczyć całe rozwiązanie.
1. Kliknij prawym przyciskiem myszy każdy projekt testowy, który ma zostać uwzględniony w testach, a następnie wybierz **Live Unit Testing**  >  **Uwzględnij**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Wyklucz pojedyncze testy z okna edytora kodu

Można użyć okna edytora kodu, aby dołączyć lub wykluczyć poszczególne metody testowe. Kliknij prawym przyciskiem myszy podpis metody testowej w oknie Edytor kodu, a następnie wybierz jedną z następujących opcji:

- **Live Unit Testing**  >  **Uwzględnij \<selected method>**
- **Live Unit Testing**  >  **Wyklucz \<selected method>**
- **Live Unit Testing**  >  **Wyklucz wszystkie \<selected method> oprócz**

### <a name="exclude-tests-programmatically"></a>Programowe wykluczanie testów

Można zastosować atrybut, <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> Aby programowo wykluczyć metody, klasy lub struktury z raportowania ich pokrycia w Live Unit Testing.

Użyj następujących atrybutów, aby wykluczyć poszczególne metody z Live Unit Testing:

- Dla xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Dla NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Dla MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Użyj następujących atrybutów, aby wykluczyć cały zestaw testów z Live Unit Testing:

- Dla xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Dla NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Dla MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz też

- [Narzędzia do testowania kodu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)
- [Wideo Channel 9: Live Unit Testing w programie Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
