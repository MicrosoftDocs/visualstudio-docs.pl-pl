---
title: Live Unit Testing
ms.date: 2017-03-07
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 7be078044454ebf5d6b3a6d99a60fff66ab1f69b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066213"
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing w programie Visual Studio 2017

Ponieważ tworzysz aplikację Live Unit Testing automatycznie wykonuje w tle, wszystkie objęte testy jednostek i przedstawia wyniki i pokrycie kodu na żywo w programie Visual Studio IDE w czasie rzeczywistym. Jak można zmodyfikować kod, Live Unit Testing zapewnia informacje zwrotne na wpływ zmiany na istniejące testy i czy nowego kodu po dodaniu zgodnie z co najmniej jeden z istniejących testów. To delikatnie przypomni, do pisania testów jednostkowych, podczas wprowadzania poprawek lub dodawanie nowych funkcji.

> [!NOTE]
> Live Unit Testing jest dostępna dla projektów C# i Visual Basic, przeznaczonych dla platformy .NET Core lub .NET Framework w przedsiębiorstwie wersji programu Visual Studio 2017.

Korzystając z Live Unit Testing dla testów, Live Unit Testing utrzymuje dane o stanie testów. Możliwość użycia danych umożliwia Live Unit Testing można oferują doskonałą wydajność podczas uruchamiania testów dynamicznie w odpowiedzi na zmiany w kodzie.

## <a name="supported-test-frameworks"></a>Platformy obsługiwane testowe
Live Unit Testing działa z trzech struktur testowania jednostek popularne, wymienione w poniższej tabeli. Minimalna obsługiwana wersja ich kart i struktur również znajduje się w tabeli. Struktur testowania jednostek są dostępne w witrynie NuGet.org.

<table>
<tr>
   <th>Struktury testowej</th>
   <th>Minimalna wersja programu Visual Studio karty</th>
   <th>Minimalna wersja Framework</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> 2.2.0-beta3-build1187 wersji xunit.Runner.VisualStudio</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>Rozszerzenie NUnit</td>
   <td>NUnit3TestAdapter wersji 3.5.1</td>
   <td>Wersja 3.5.0 NUnit</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>1.0.5-preview rozwiązań MSTest.TestFramework</td>
</tr>
</table>

Jeśli masz starszą MSTest na podstawie projekty testowe, które odwołują się do `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i nie chcesz przejść do nowszych pakietów MSTest NuGet, przeprowadź uaktualnienie do programu Visual Studio 2017 w wersji 15.4.

W niektórych przypadkach może być konieczne jawne Przywracanie pakietów NuGet, odwołują się projekty w rozwiązaniu aby Live Unit Testing do pracy. Możesz to zrobić, wykonując jawną kompilację rozwiązania (wybierz **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio) lub przywracając pakiety (rozwiązanie Kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Przywróć pakiety NuGet**) przed włączeniem życia Unit Testing.

## <a name="configure-live-unit-testing"></a>Konfigurowanie Live Unit Testing

Live Unit Testing można skonfigurować, wybierając **narzędzia** > **opcje** z najwyższego paska menu programu Visual Studio, a następnie wybierając pozycję **Live Unit Testing** w okienku po lewej stronie **opcje** okna dialogowego.

> [!TIP]
> Po włączeniu Live Unit Testing (zobacz następną sekcję [uruchomić, wstrzymać, a następnie Zatrzymaj Live Unit Testing](#start-pause-and-stop-live-unit-testing)), możesz również otworzyć **opcje** okna dialogowego wybierając **testu**  >  **Live Unit Testing** > **opcje**.

Na poniższej ilustracji przedstawiono opcje konfiguracji Live Unit Testing dostępny w oknie dialogowym:

  ![Obraz](./media/lut-options.png)

Można skonfigurować opcje:

- Czy Live Unit Testing wstrzymuje, gdy rozwiązanie jest skompilowane i debugowania.

- Czy Live Unit Testing wstrzymuje, gdy system baterii spadnie poniżej określonego progu.

- Czy Live Unit Testing działa automatycznie po otwarciu rozwiązania.

- Czy włączyć debugowanie symboli i generowanie komentarzy dokumentacji XML.

- Katalog do przechowywania danych.

- Możliwość usunięcia wszystkich danych. Jest to przydatne, gdy Live Unit Testing zachowuje się w sposób nieprzewidziane bądź nieoczekiwane, co sugeruje utrwalonych danych została uszkodzona.

- Interwał, po którym przypadek testowy upłynie limit czasu; Wartość domyślna to 30 sekund.

- Maksymalna liczba procesów testu, utworzone przez funkcję Live Unit Testing.

- Maksymalna ilość pamięci, którą może wykorzystać funkcję Live Unit Testing procesów.

- Poziom informacji zapisywane Live Unit Testing **dane wyjściowe** okna.

   Dostępne są następujące opcje bez rejestrowania (**Brak**), tylko komunikaty o błędach (**błąd**), błędów i komunikaty informacyjne (**informacje**, wartość domyślna), lub wszystkie szczegóły (**pełne** ).

   Można również wyświetlić pełne dane wyjściowe w Live Unit Testing **dane wyjściowe** okna, przypisując wartość "1" do zmiennej środowiska na poziomie użytkownika o nazwie `VS_UTE_DIAGNOSTICS`, a następnie ponownie uruchom program Visual Studio.

   Aby przechwycić szczegółowe komunikaty dziennika MSBuild z Live Unit Testing w pliku, należy ustawić `LiveUnitTesting_BuildLog` zmiennej środowiskowej poziomie użytkownika, aby nazwa pliku zawiera dziennik.

## <a name="start-pause-and-stop-live-unit-testing"></a>Rozpocznij, wstrzymać lub zatrzymać Live Unit Testing

Włącz funkcję Live Unit Testing, wybierając **testu** > **Live Unit Testing** > **Start** menu najwyższego poziomu programu Visual Studio. Po włączeniu Live Unit Testing, opcji dostępnych w **Live Unit Testing** zmiany menu z pojedynczego elementu **Start**, **Wstrzymaj**, **zatrzymać**, i **Resetuj i wyczyść**.

> [!NOTE]
> Jeśli uruchamiasz Live Unit Testing w rozwiązaniu, który nie zawiera projekt testu jednostkowego **Wstrzymaj**, **zatrzymać**, i **resetowania czyste** opcje są wyświetlane na **na żywo Testowanie jednostkowe** menu, ale Live Unit Testing nie rozpoczyna się. **Dane wyjściowe** okno zostanie wyświetlony komunikat, który rozpoczyna się, że "nie adapterów testowych obsługiwane są przywoływane przez to rozwiązanie..."

W dowolnym momencie możesz czasowo wstrzymać lub całkowite zatrzymanie Live Unit Testing. Można to zrobić, na przykład, jeśli są w trakcie refaktoryzacji i dowiedzieć się, że testy zostanie przerwane przez jakiś czas. Są trzy opcje:

- **Wstrzymaj**, który tymczasowo wstrzymuje Live Unit Testing.

    Po wstrzymaniu Live Unit Testing wizualizacji pokrycia nie jest wyświetlana w edytorze, ale zostaną zachowane wszystkie dane, które zostały zebrane. Aby wznowić działanie Live Unit Testing, wybierz **Kontynuuj** menu Live Unit Testing. Live Unit Testing działa niezbędne nadążyć za pomocą wszystkie zmiany wprowadzone podczas został wstrzymany i odpowiednio aktualizuje symbole.

- **Zatrzymaj**, całkowite zatrzymanie Live Unit Testing. Live Unit Testing odrzuca wszystkie dane, które zostały zebrane.

- **Resetuj czysty**, co uniemożliwia Live Unit Testing, usuwa dane utrwalone i ponownym uruchomieniu Live Unit Testing.

- **Opcje**, co spowoduje otwarcie **opcje** okna dialogowego opisanego w [skonfigurować Live Unit Testing](#configure-live-unit-testing) sekcji.

## <a name="view-coverage-visualization-in-the-editor-as-you-type"></a>Wyświetlanie wizualizacji pokrycia w edytorze podczas pisania

Gdy włączone Live Unit Testing aktualizacji, które każdego wiersza kodu w edytorze programu Visual Studio, aby pokazać, czy kod piszesz jest objęte testy jednostkowe i tego, czy testy, które obejmują go kończy się sukcesem.  Na poniższej ilustracji przedstawiono wierszy kodu za pomocą zarówno się powodzeniem i niepowodzeniem testy, a także wierszy kodu, które nie są obejmowane przez testy. Wiersze ozdobione zielony "✓" są objęte przekazując testy, wiersze ozdobione czerwony symbol "x", są objęte zakończone niepowodzeniem testy i wiersze dekorowane przez niebieski "➖" nie są obejmowane przez dowolny test.

  ![Obraz](./media/lut-codewindow.png)

Live Unit Testing pokrycia wizualizacji jest aktualizowany bezpośrednio modyfikować kodu w edytorze kodu. Podczas przetwarzania zmiany, wizualizacja zmienia, aby wskazać, że dane nie są aktualne, dodając round czasomierza obraz poniżej przekazywanie, kończy się niepowodzeniem, a nie pasuje do symboli, jak przedstawiono na poniższym rysunku.

  ![Obraz](./media/lut-codeupdating.png)

## <a name="get-information-on-successful-or-failed-tests"></a>Uzyskiwanie informacji na temat testy powodzeniem lub niepowodzeniem

Ustawiając kursor zakończyło się powodzeniem lub niepowodzeniem symboli w oknie kodu, możesz zobaczyć, ile testów osiągnięcia tego wiersza. Po kliknięciu symbolu można wyświetlić stan poszczególnych testów, jak przedstawiono na poniższym rysunku:

  ![Obraz](./media/lut-failedinfo.png)

Oprócz nazwy i wyniki testów, umożliwia etykietki narzędzia można uruchomić ponownie zestaw testów, a także uruchomić zestaw testów przy użyciu debugera. Wybranie jednego lub więcej testów w etykietce narzędzia, można również uruchomić lub debugować tylko te testy. Pozwala na debugowanie testów bez konieczności opuszczania okna kodu. Podczas debugowania, oprócz obserwowania żadnych punktów przerwania, może zostały już ustawione, wstrzymuje działanie wykonywania programu, gdy debuger wykonuje [ `Assert` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) metodę, która zwraca nieoczekiwany wynik.

Po umieszczeniu testów zakończonych niepowodzeniem w etykietce narzędzia rozwija zapewnienie dodatkowych informacji na temat błędu, jak pokazano na poniższej ilustracji. Jeśli klikniesz dwukrotnie na test zakończony niepowodzeniem w etykietce narzędzia, można przejść bezpośrednio do niego.

  ![Obraz](./media/lut-failedmsg.png)

Po przejściu do sekcji testów zakończonych niepowodzeniem Live Unit Testing również wizualnie wskazuje w podpisie metody testów, które upłynęły (wskazane zlewce pełnej połowie wraz z zielony "✓"), nie powiodło się (zlewce pół pełny oraz czerwonego "🞩"), lub które nie są zaangażowane w Live Unit Testing (pół pełny zlewce wraz z niebieski "➖"). Metody testowe inne niż nie są oznaczone symbolem. Na poniższym rysunku przedstawiono cztery rodzaje metod.

  ![Obraz](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Zdiagnozować i rozwiązać niepowodzeń testów

Od test zakończony niepowodzeniem można łatwo debugować kod produktu, wprowadź zmiany i kontynuować tworzenie aplikacji. Ponieważ Live Unit Testing działa w tle, nie trzeba zatrzymać i ponownie uruchomić funkcję Live Unit Testing podczas debugowania, Edytuj i Kontynuuj cyklu.

Na przykład awaria testu zostało pokazane na poprzedniej ilustracji zostało spowodowane przez nieprawidłowe założenie w metodzie testowej, która zwraca znaki niealfabetyczne `true` przy przekazywaniu do <xref:System.Char.IsLower%2A?displayProperty=fullName> metody. Gdy możemy poprawić metody testowej, uważamy, że kod przechodzi wszystkie testy. Gdy firma Microsoft jest w ten sposób nie mamy wstrzymać lub zatrzymać Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing i Eksplorator testów

Zazwyczaj **Eksploratora testów** udostępnia interfejs, który umożliwia uruchamianie, debugowanie i analizowanie wyników testu. Live Unit Testing integruje się z **Eksplorator testów**. Live Unit Testing nie jest włączona lub jest zatrzymana, **Eksploratora testów** wyświetlany jest stan testów jednostkowych czasu ostatniego wykonywania testu. Zmiany kodu źródłowego wymagają, ponownie uruchom testy. Natomiast po włączeniu Live Unit Testing sprawdza stan jednostki w **Eksplorator testów** natychmiast zaktualizować. Nie trzeba jawnie Uruchamianie testów jednostkowych.

> [!NOTE]
> Możesz otworzyć **Eksplorator testów** , wybierając **testu** > **Windows** > **Eksplorator testów** z menu najwyższego poziomu programu Visual Studio.

Można zauważyć w **Eksplorator testów** okno, które są wygasić niektóre testy. Na przykład po włączeniu Live Unit Testing po otwarciu projektu wcześniej zapisany, **Eksploratora testów** okna miał wygasić połączenie z wszystkich pól poza testu nie powiodło się, jak przedstawiono na poniższym rysunku. W tym przypadku Live Unit Testing została ponownie uruchomić test zakończony niepowodzeniem, ale nie została uruchomiona ponownie testy zakończone powodzeniem, ponieważ Live Unit Testing firmy utrwalone dane wskazują, że nie wprowadzono żadnych zmian, ponieważ testy zostały ostatnio uruchomione pomyślnie.

  ![Obraz](media/lut-test-explorer.png)

Możesz ponownie uruchomić wszystkie testy, które pojawiają się pojawił, wybierając **Uruchom wszystkie** lub **Uruchom** opcje z **Eksplorator testów** menu lub wybierając jeden lub więcej testów w **Eksplorator testów** menu, kliknij prawym przyciskiem myszy i wybierając opcję **Uruchom wybrane testy** lub **Debuguj wybrane testy** z menu podręcznego. Jak są uruchamiane testy, mogą się pojawiać z góry.

Istnieją pewne różnice między Live Unit Testing automatyczne uruchamianie i aktualizowanie wyników testów oraz jawnie Uruchamianie testów z **Eksploratora testów**. Różnice te obejmują:

- Uruchamianie i debugowanie testów z okna Eksploratora testów uruchamia regularne plików binarnych, a Live Unit Testing są uruchamiane instrumentowanych danych binarnych.
- Live Unit Testing nie powoduje utworzenia nowej domeny aplikacji, aby uruchomić testy, ale raczej uruchamia testy z domyślnej domeny. Testy uruchamiane z **Eksplorator testów** okna Tworzenie nowej domeny aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testów po kolei. Po uruchomieniu wielu testów z **Eksplorator testów** okna i **Uruchom testy równolegle** przycisk jest zaznaczony, testy są uruchamiane równolegle.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing i dużych rozwiązań

Jeśli rozwiązanie ma projekty, co najmniej 10, podczas uruchamiania Live Unit Testing and nie ma żadnych utrwalonych danych lub po wybraniu **testu** > **Live Unit Testing**  >  **Resetowania czyste** opcję z menu najwyższego poziomu programu Visual Studio, Visual Studio wyświetla następujące okno dialogowe i ostrzega o tym, że dynamiczne wykonywanie dużej liczby testów w dużych projektów może poważnie obniżyć wydajność. Jeśli wybierzesz **OK**, Live Unit Testing uruchamia wszystkie testy w rozwiązaniu. Jeśli wybierzesz **anulować**, możesz wybrać testy do wykonania. Aby uzyskać informacje, jak to zrobić, zobacz następującą sekcję [Dołączanie i wykluczanie projekty testowe i metod testowych](#include-and-exclude-test-projects-and-test-methods).

 ![Live Unit Testing okno dialogowe dla dużych projektów](media/lut-large-project.png)

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Dołączyć i wykluczyć projekty testowe i metod testowych

W przypadku rozwiązań z wieloma projektami testowymi można kontrolować, projekty i jakie poszczególne metody w projekcie uczestniczyć w operacji Live Unit Testing. Na przykład jeśli masz rozwiązanie z setek projektów testów, można wybrać docelowego zestawu projektów testowych do wzięcia udziału w Live Unit Testing. Istnieje wiele sposobów, aby to zrobić, w zależności od tego, czy chcesz wykluczyć wszystkie testy w projekcie lub rozwiązaniu, czy chcesz uwzględnić lub wykluczyć większości testów lub tego, czy chcesz wykluczyć testy indywidualnie. Live Unit Testing zapisuje stan dołączania lub wykluczania jako ustawienia użytkownika i pamięta, gdy rozwiązanie jest zamykany i ponownie otwarty.

**Z wyjątkiem wszystkich testów w projekcie lub rozwiązaniu**

Po uruchomieniu Live Unit Testing, aby wybrać poszczególnych projektów testów jednostkowych, wykonaj następujące czynności:

1.  Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz polecenie **testów na żywo** > **wykluczyć** wyłączenie całego rozwiązania.
1.  Kliknij prawym przyciskiem myszy każdy projekt testowy, który chcesz uwzględnić w testach, a następnie wybierz **testów na żywo** > **Include**.

**Wykluczanie indywidualnych testów z oknem edytora kodu**

Do dołączania lub wykluczania metody poszczególnych testach, można użyć okna edytora kodu. Kliknij prawym przyciskiem myszy na sygnaturze metody testowej w oknie edytora kodu, a następnie wybierz pozycję **testów na żywo** > **obejmują [wybranej metody]**, **testów na żywo**  >  **Wykluczyć [wybranej metody]**, lub **testów na żywo** > **wykluczyć wszystkie elementy oprócz [wybranej metody]**, gdzie "wybrane metody" to nazwa Metoda wybrane w oknie kodu.

**Programowe wykluczanie testów**

Można zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybutu programowe wykluczanie metody, klasy lub struktury z raportowania ich pokrycia w Live Unit Testing.

Aby wyłączyć poszczególne metody z Live Unit Testing umożliwia także następujące atrybuty:

- Aby uzyskać xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Aby uzyskać NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Aby uzyskać MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz także

- [Narzędzia do testowania kodu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blog](https://go.microsoft.com/fwlink/?linkid=842514)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)
- [Wideo Channel 9: Live Unit Testing w programie Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
