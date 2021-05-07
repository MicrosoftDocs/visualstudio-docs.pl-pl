---
title: Live Unit Testing
description: Dowiedz się więcej Live Unit Testing podczas tworzenia aplikacji, w tym obsługiwanych platform i sposobu konfigurowania Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: b9b78771c36dce26744ba74af63922cf1efa48e2
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798625"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Jak skonfigurować i używać Live Unit Testing

Podczas tworzenia aplikacji program Live Unit Testing automatycznie uruchamia wszystkie testy jednostkowe, których to miało wpływ, w tle oraz przedstawia wyniki i pokrycie kodu w czasie rzeczywistym. Podczas modyfikowania kodu program Live Unit Testing opinie na temat wpływu zmian na istniejące testy i tego, czy nowy dodany kod jest objęty co najmniej jednym istniejącym testem. To przypomnienie przypomina o pisanych testach jednostkowych podczas tworzenia poprawek błędów lub dodawania nowych funkcji.

> [!NOTE]
> Live Unit Testing jest dostępna dla projektów w języku C# i Visual Basic, które są docelowe dla programu .NET Core lub .NET Framework w wersji Enterprise programu Visual Studio.

Jeśli używasz Live Unit Testing do testów, dane o stanie testów są utrwalane. Użycie utrwalonych danych Live Unit Testing zapewnia doskonałą wydajność podczas dynamicznego uruchamiania testów w odpowiedzi na zmiany kodu.

## <a name="supported-test-frameworks"></a>Obsługiwane struktury testowe

Live Unit Testing działa z trzema popularnymi platformami testowania jednostkowego wymienionymi w poniższej tabeli. Wyświetlana jest również minimalna obsługiwana wersja kart i platform. Wszystkie struktury testowania jednostkowego są dostępne w NuGet.org.

|Test Framework  |Visual Studio wersji karty sieciowej  |Minimalna wersja struktury  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio w wersji 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter w wersji 3.5.1 |NUnit w wersji 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Jeśli masz starsze projekty testowe oparte na narzędziu MSTest odwołujące się do pakietu Microsoft.VisualStudio.QualityTools.UnitTestFramework i nie chcesz przechodzić do nowszej wersji pakietów NuGet MSTest, uaktualnij program do wersji Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołuje się projekt, aby Live Unit Testing działać. Możesz to zrobić, wykonując jawną kompilację rozwiązania (wybierz pozycję Build Rebuild Solution (Sbuduj ponownie rozwiązanie) z menu Visual Studio najwyższego poziomu lub przywracając pakiety w rozwiązaniu (kliknij rozwiązanie prawym przyciskiem myszy i wybierz polecenie Restore NuGet Packages (Przywróć pakiety  >   **NuGet).**

## <a name="configure"></a>Konfigurowanie

Skonfiguruj Live Unit Testing, wybierając pozycję Opcje narzędzi na pasku menu Visual Studio najwyższego poziomu, a następnie wybierając pozycję Live Unit Testing w lewym okienku  >   **okna dialogowego** Opcje. 

> [!TIP]
> Po Live Unit Testing (zobacz następną sekcję Uruchamianie, wstrzymywanie i zatrzymywanie usługi  [Live Unit Testing),](#start-pause-and-stop)możesz również otworzyć okno dialogowe  >  **Opcje,** wybierając pozycję Test Live Unit Testing  >  **Opcje.**

Na poniższej ilustracji przedstawiono Live Unit Testing konfiguracji dostępnych w oknie dialogowym:

![Live Unit Testing konfiguracji](./media/lut-options.png)

Konfigurowalne opcje obejmują:

- Czy Live Unit Testing wstrzymuje się, gdy rozwiązanie jest budowane i debugowane.

- Czy Live Unit Testing się, gdy poziom naładowania baterii systemu spadnie poniżej określonego progu.

- Czy Live Unit Testing automatycznie po otwarciu rozwiązania.

- Czy włączyć generowanie komentarzy do symboli debugowania i dokumentacji XML.

- Katalog, w którym mają być przechowywane utrwalone dane.

- Możliwość usunięcia wszystkich utrwalonych danych. Jest to przydatne, Live Unit Testing działa w sposób nieprzewidywalny lub nieoczekiwany, co sugeruje, że utrwalone dane zostały uszkodzone.

- Interwał, po upływie którego ujmuje się czas przypadku testowego. Wartość domyślna to 30 sekund.

- Maksymalna liczba procesów testowych, które Live Unit Testing procesów.

- Maksymalna ilość pamięci, którą mogą Live Unit Testing procesy.

- Poziom informacji zapisywanych w oknie Live Unit Testing **Dane** wyjściowe.

   Opcje obejmują brak rejestrowania **(Brak),** tylko komunikaty o błędach **(Błąd),** komunikaty o błędach i komunikaty informacyjne **(informacje**, wartość domyślna) lub wszystkie szczegóły (**Pełne**).

   W oknie Dane wyjściowe usługi Live Unit Testing można **również** wyświetlić pełne dane wyjściowe, przypisując wartość "1" do zmiennej środowiskowej na poziomie użytkownika o nazwie , a następnie ponownie uruchamiając `VS_UTE_DIAGNOSTICS` Visual Studio.

   Aby przechwycić szczegółowe komunikaty dziennika programu MSBuild Live Unit Testing pliku, ustaw zmienną środowiskową na poziomie użytkownika na nazwę pliku `LiveUnitTesting_BuildLog` zawierającego dziennik.

## <a name="start-pause-and-stop"></a>Uruchamianie, wstrzymywanie i zatrzymywanie

Aby włączyć Live Unit Testing, **wybierz** Live Unit Testing Start z menu Visual Studio  >    >   najwyższego poziomu. Gdy Live Unit Testing włączona, opcje dostępne w menu usługi **Live Unit Testing** zmienią się z pojedynczego **elementu,** Start , na **Wstrzymaj** i **Zatrzymaj:**

- **Wstrzymanie** tymczasowo wstrzymuje Live Unit Testing.

  Po Live Unit Testing wizualizacja pokrycia nie jest wyświetlana w edytorze, ale wszystkie zebrane dane są zachowywane. Aby wznowić Live Unit Testing, wybierz **pozycję Kontynuuj** z Live Unit Testing menu. Live Unit Testing pracę niezbędną do nadrobić zaległości ze wszystkimi edytować, które zostały wprowadzone, gdy została wstrzymana, i odpowiednio aktualizuje glify.

- **Zatrzymaj** całkowicie Live Unit Testing. Live Unit Testing odrzuca wszystkie zebrane dane.

> [!NOTE]
> Jeśli zaczniesz Live Unit Testing w rozwiązaniu, które nie zawiera  projektu  testu jednostkowego, opcje Wstrzymaj i Zatrzymaj są wyświetlane w **menu** Live Unit Testing, ale nie Live Unit Testing uruchomić. W **oknie** Dane wyjściowe zostanie wyświetlony komunikat "To rozwiązanie nie odwołuje się do obsługiwanych adapterów testowych...".

W dowolnym momencie możesz tymczasowo wstrzymać lub całkowicie zatrzymać Live Unit Testing. Możesz to zrobić, na przykład jeśli jesteś w trakcie refaktoryzacji i wiesz, że testy zostaną przerwane przez jakiś czas.

## <a name="view-coverage-visualization"></a>Wyświetlanie wizualizacji pokrycia

Po włączeniu tej funkcji program Live Unit Testing aktualizuje każdy wiersz kodu w edytorze Visual Studio, aby pokazać, czy pisany kod jest objęty testami jednostkowymi i czy testy, które go obejmują, są mijające. Na poniższej ilustracji przedstawiono wiersze kodu z testami zarówno z podań, jak i testów, które się nie popełnią, a także wiersze kodu, które nie są objęte testami. Linie dekorowane zielonym "są pokrywane tylko przez testy, linie dekorowane czerwonymi znakami "x" są objęte co najmniej jednym testem nieudanym, a linie dekorowane niebieskimi "➖" nie są objęte żadnym testem.

![Pokrycie kodu w Visual Studio](./media/lut-codewindow.png)

Live Unit Testing wizualizacja pokrycia jest aktualizowana natychmiast po zmodyfikowaniu kodu w edytorze kodu. Podczas przetwarzania edycji wizualizacja zmienia się, aby wskazać, że dane nie są aktualne, dodając obraz czasomierza rundy poniżej symboli przekazujących, nieudanych i nieukrytych, jak pokazano na poniższej ilustracji.

![Pokrycie kodu w Visual Studio ikoną czasomierza](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Uzyskiwanie informacji o stanie testu

Po umieszczeniu wskaźnika myszy na symbolu powodzenie lub niepowodzenie w oknie kodu możesz zobaczyć, ile testów trafia do tego wiersza. Aby wyświetlić stan poszczególnych testów, wybierz symbol:

![Stan testu symbolu w Visual Studio](./media/lut-failedinfo.png)

Etykietka narzędzia pozwala nie tylko na podanie nazw i wyników testów, ale także na ponowne uruchomić lub debugować zestaw testów. Jeśli wybierzesz co najmniej jeden test w etykietce narzędzia, możesz również uruchomić lub debugować tylko te testy. Dzięki temu można debugować testy bez konieczności opuszczania okna kodu. Podczas debugowania, oprócz obserwowania punktów przerwania, które być może zostały już ustawione, wykonywanie programu jest wstrzymywane, gdy debuger wykonuje metodę, która <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> zwraca nieoczekiwany wynik.

Po umieszczeniu wskaźnika myszy na teście, który zakończył się niepowodzeniem w etykietce narzędzia, następuje rozszerzenie w celu podania dodatkowych informacji o niepowodzeniu, jak pokazano na poniższej ilustracji. Aby przejść bezpośrednio do testu, który zakończył się niepowodzeniem, kliknij go dwukrotnie w etykietce narzędzia.

![Informacje o etykietce narzędzia testu, które zakończyły się niepowodzeniem w Visual Studio](./media/lut-failedmsg.png)

Po przechodzeniu do testu, który zakończył się niepowodzeniem, Live Unit Testing wizualnie wskazuje w metodzie podpis testów, które mają:

- passed (wskazywana przez połowię pełną zębnikę z zielonym "").")
- failed (połowia pełna zmyka z czerwonym " 🞩 ")
- nie są zaangażowani w Live Unit Testing (połowię pełnej zdjętą ząbkową "➖")

Metody inne niż testowe nie są dekorowane symbolem. Na poniższej ilustracji przedstawiono wszystkie cztery typy metod.

![Metody testowe w Visual Studio z symbolem pass or fail](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnozowanie i poprawianie błędów testów

W teście, który zakończył się niepowodzeniem, można łatwo debugować kod produktu, edytować i kontynuować tworzenie aplikacji. Ponieważ Live Unit Testing działa w tle, nie trzeba zatrzymywać i uruchamiać ponownie Live Unit Testing podczas cyklu debugowania, edytowania i kontynuowania.

Na przykład niepowodzenie testu pokazane na poprzedniej ilustracji zostało spowodowane niepoprawnym założeniem w metodzie testowej, które zwraca znaki inne niż alfabetyczne po przekazyciu `true` do <xref:System.Char.IsLower%2A?displayProperty=fullName> metody. Po skorygowaniu metody testu wszystkie testy powinny zostać zmieściły się. Nie trzeba wstrzymywać ani zatrzymywać Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Eksplorator testów

**Eksplorator testów** udostępnia interfejs, który umożliwia uruchamianie i debugowanie testów oraz analizowanie wyników testów. Live Unit Testing integruje się z **Eksploratorem testów.** Gdy Live Unit Testing nie jest włączona lub zatrzymana, Eksplorator **testów** wyświetla stan testów jednostkowych podczas ostatniego uruchomienia testu. Zmiany kodu źródłowego wymagają ponownego uruchomić testy. Z kolei po Live Unit Testing testów jednostkowych stan testów jednostkowych w Eksploratorze **testów** jest natychmiast aktualizowany. Nie trzeba jawnie uruchamiać testów jednostkowych.

> [!TIP]
> Otwórz **Live Unit Testing,** wybierając pozycję **Testuj**  >    >  **Eksploratora testów systemu** Windows z menu Visual Studio najwyższego poziomu.

W oknie Eksplorator **testów** można zauważyć, że niektóre testy są wyblakły. Na przykład po włączeniu funkcji Live Unit Testing wcześniej zapisany projekt  okno Eksploratora testów wygasło, ale test zakończył się niepowodzeniem, jak pokazano na poniższej ilustracji. W takim przypadku Live Unit Testing ponownie uruchomić test, który zakończył się niepowodzeniem, ale nie został ponownie uruchomić pomyślnie testów. Jest to spowodowane Live Unit Testing danych utrwalonych przez program wskazuje, że nie było żadnych zmian od czasu ostatniego pomyślnego uruchomienia testów.

![Test nieudany w Eksploratorze testów](media/lut-test-explorer.png)

Możesz ponownie uruchomić wszystkie testy, które wydają się wygasnąć, wybierając opcje **Uruchom** wszystko lub **Uruchom** z menu Eksplorator **testów.** Możesz też wybrać jeden lub więcej testów w menu **Eksploratora** testów, kliknąć prawym przyciskiem myszy, a następnie wybrać polecenie Uruchom wybrane testy lub **Debuguj** wybrane testy z menu podręcznego.  Podczas uruchamiania testów są one bąbelkami w górę.

Istnieją pewne różnice między tym, Live Unit Testing automatycznie uruchamiać i aktualizować wyniki testów oraz jawnie uruchamiać testy z **Eksploratora testów.** Różnice te obejmują:

- Uruchamianie lub debugowanie testów w oknie Eksplorator testów uruchamia zwykłe pliki binarne, a Live Unit Testing instrumentowane pliki binarne.
- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów, ale uruchamia testy z domeny domyślnej. Testy uruchamiane w **oknie Eksplorator testów** tworzą nową domenę aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testowym sekwencyjnie. W **oknie Eksplorator** testów można uruchomić wiele testów równolegle.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing okno

**Live Unit Testing**, podobnie jak **Eksplorator testów,** udostępnia interfejs, który umożliwia uruchamianie i debugowanie testów oraz analizowanie wyników testów. Gdy Live Unit Testing jest włączona, stan testów jednostkowych w Eksploratorze **testów** jest aktualizowany natychmiast. Nie trzeba jawnie uruchamiać testów jednostkowych. Gdy Live Unit Testing nie jest włączona lub  zatrzymana, Live Unit Testing wyświetla stan testów jednostkowych podczas ostatniego uruchomienia testu. Po ponownym uruchomieniu Live Unit Testing ponowne uruchomienie testów wymaga zmiany kodu źródłowego.

> [!TIP]
> Rozpocznij Live Unit Testing, wybierając pozycję **Live Unit Testing** Start z menu Visual Studio  >    >   najwyższego poziomu. Możesz również otworzyć okno **Live Unit Testing** za pomocą **polecenia View** Other Windows Live Unit Testing Window (Wyświetl inne  >  **okna**  >  **Live Unit Testing Windows).**

W oknie **Live Unit Testing,** że niektóre testy są wyblakły. Na przykład po zatrzymaniu i ponownym uruchomieniu Live Unit Testing okno Live Unit Testing zanika we wszystkich testach, jak pokazano na poniższej ilustracji.  Wyniki testów zanikanych wskazują, że test nie był częścią najnowszego uruchomienia testu jednostkowego na żywo. Testy są uruchamiane tylko wtedy, gdy zostanie wykryta zmiana w teście lub zależności testu. Jeśli nie ma żadnych zmian, pozwala to uniknąć niepotrzebnych testów. W tym przypadku wyszarzony wynik testu jest nadal "aktualny", chociaż nie był częścią najnowszego uruchomienia.

![Wygasły testy w Eksploratorze testów](media/vs-2019/lut-test-explorer.png)

Możesz ponownie uruchomić wszystkie testy, które wyglądają na wyblakły, przez wprowadzenie zmiany kodu.

Istnieją pewne różnice między tym, Live Unit Testing automatycznie uruchamiać i aktualizować wyniki testów oraz jawnie uruchamiać testy z **Eksploratora testów.** Różnice te obejmują:

- Uruchamianie lub debugowanie testów w oknie Eksploratora testów uruchamia zwykłe pliki binarne, podczas gdy Live Unit Testing instrumentowane pliki binarne.
- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów, ale uruchamia testy z domeny domyślnej. Testy uruchamiane w **oknie Eksplorator** testów tworzą nową domenę aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testowym sekwencyjnie. W **oknie Eksplorator** testów można uruchomić wiele testów równolegle.
::: moniker-end

## <a name="large-solutions"></a>Duże rozwiązania

Jeśli rozwiązanie ma co najmniej 10 projektów, Visual Studio zostanie wyświetlone następujące okno dialogowe:

- uruchom Live Unit Testing i nie ma żadnych utrwalonych danych
- wybieranie **opcji**  >  **Narzędzia**  >  **Live Unit Testing**  >  **usuwanie utrwalonych danych**

![Live Unit Testing dialogowe dla dużych projektów](media/lut-large-project.png)

W oknie dialogowym zostanie wyświetlone ostrzeżenie, że dynamiczne wykonywanie dużej liczby testów w dużych projektach może poważnie wpłynąć na wydajność. Jeśli wybierzesz **przycisk OK,** Live Unit Testing wszystkie testy w rozwiązaniu. Jeśli wybierzesz **pozycję Anuluj,** możesz wybrać testy do wykonania. W poniższej sekcji wyjaśniono, jak to zrobić.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Dołączanie i wykluczanie projektów testowych i metod testowych

W przypadku rozwiązań z wieloma projektami testowym możesz kontrolować, które projekty i poszczególne metody w projekcie uczestniczą w Live Unit Testing. Jeśli na przykład masz rozwiązanie z setkami projektów testowych, możesz wybrać docelowy zestaw projektów testowych, które będą uczestniczyć w Live Unit Testing. Istnieje wiele sposobów, aby to zrobić, w zależności od tego, czy chcesz wykluczyć wszystkie testy w projekcie lub rozwiązaniu, dołączyć lub wykluczyć większość testów lub wykluczyć poszczególne testy. Live Unit Testing zapisuje stan dołączania/wykluczania jako ustawienie użytkownika i zapamiętuje je po zamknięciu i ponownym otwarciu rozwiązania.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Wykluczanie wszystkich testów w projekcie lub rozwiązaniu

Aby wybrać poszczególne projekty w testach jednostkowych, po Live Unit Testing wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i **wybierz** Live Unit Testing  >  **Wyklucz,** aby wykluczyć całe rozwiązanie.
1. Kliknij prawym przyciskiem myszy każdy projekt testowy, który chcesz uwzględnić w testach, a następnie wybierz polecenie **Live Unit Testing**  >  **uwzględnij**.

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>Wykluczanie poszczególnych testów z okna edytora kodu

Za pomocą okna edytora kodu można dołączać lub wykluczać poszczególne metody testowe. Kliknij prawym przyciskiem myszy podpis metody testowej w oknie edytora kodu, a następnie wybierz jedną z następujących opcji:

- **Live Unit Testing**  >  **Uwzględnij \<selected method>**
- **Live Unit Testing**  >  **Wyklucz \<selected method>**
- **Live Unit Testing**  >  **Wyklucz \<selected method> wszystko, ale**

### <a name=&quot;exclude-tests-programmatically&quot;></a>Programowe wykluczanie testów

Atrybut można zastosować do programowego wykluczania metod, klas lub struktur z raportowania ich pokrycia w <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> Live Unit Testing.

Użyj następujących atrybutów, aby wykluczyć poszczególne metody z Live Unit Testing:

- Dla xUnit: `[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- Dla NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- W przypadku programu MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Użyj następujących atrybutów, aby wykluczyć cały zestaw testów z Live Unit Testing:

- Dla xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Dla NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- W przypadku programu MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz też

- [Narzędzia do testowania kodu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing bloga](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.yml)
- [Wideo z kanału Channel 9: Live Unit Testing w Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
