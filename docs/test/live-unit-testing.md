---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: gewarren
ms.author: gewarren
ms.workload:
- dotnet
ms.openlocfilehash: 646a8680211d7d79ea24a1b5b62d78eb6955b5f7
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262325"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Jak skonfigurować i używać Live Unit Testing

Podczas tworzenia aplikacji Live Unit Testing automatycznie uruchamia wszystkie testy jednostkowe, których to dotyczy, w tle i przedstawia wyniki i pokrycie kodu w czasie rzeczywistym. Jak można zmodyfikować kod, Live Unit Testing zapewnia informacje zwrotne na wpływ zmiany na istniejące testy i czy nowego kodu po dodaniu zgodnie z co najmniej jeden z istniejących testów. To delikatnie przypomina, aby napisać testy jednostkowe podczas tworzenia poprawek błędów lub dodawania nowych funkcji.

> [!NOTE]
> Live Unit Testing jest dostępny dla C# i Visual Basic projektów przeznaczonych dla platformy .NET Core lub .NET Framework w wersji Enterprise programu Visual Studio.

W przypadku korzystania z Live Unit Testing dla testów są zachowywane dane o stanie testów. Użycie utrwalonych danych umożliwia Live Unit Testing oferowanie najwyższej wydajności podczas jednoczesnego uruchamiania testów w odpowiedzi na zmiany kodu.

## <a name="supported-test-frameworks"></a>Platformy obsługiwane testowe

Live Unit Testing działa z trzech struktur testowania jednostek popularne, wymienione w poniższej tabeli. Wyświetlana jest również minimalna obsługiwana wersja ich kart i struktur. Struktur testowania jednostek są dostępne w witrynie NuGet.org.

|Struktury testowej  |Minimalna wersja programu Visual Studio karty  |Minimalna wersja Framework  |
|---------|---------|---------|
|xUnit.net |2\.2.0-beta3-build1187 wersji xunit.Runner.VisualStudio |xunit 1.9.2 |
|Rozszerzenie NUnit |NUnit3TestAdapter wersji 3.5.1 |Wersja 3.5.0 NUnit |
|MSTest |MSTest.TestAdapter 1.1.4-preview |1\.0.5-preview rozwiązań MSTest.TestFramework |

Jeśli masz starsze projekty testowe oparte na MSTest, które odwołują się do Microsoft. VisualStudio. QualityTools. UnitTestFramework, i nie chcesz przenosić do nowszych pakietów NuGet MSTest, przeprowadź uaktualnienie do programu Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołuje się projekt, aby Live Unit Testing działała. Możesz to zrobić, wykonując jawną kompilację rozwiązania (wybierz opcję **kompiluj** > **Skompiluj ponownie rozwiązanie** z menu programu Visual Studio najwyższego poziomu) lub przez przywrócenie pakietów w rozwiązaniu (kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie Przywróć pakiet NuGet).  **Pakiety**).

## <a name="configure"></a>Konfigurowanie

Skonfiguruj Live Unit Testing, wybierając**Opcje** **Narzędzia** >  z paska menu najwyższego poziomu programu Visual Studio, a następnie wybierając pozycję **Live Unit Testing** w lewym okienku okna dialogowego **Opcje** .

> [!TIP]
> Po włączeniu Live Unit Testing (zobacz następną sekcję, [Uruchamianie, wstrzymywanie i zatrzymywanie Live Unit Testing](#start-pause-and-stop)), możesz również otworzyć okno dialogowe **Opcje** , wybierając pozycję **Test** > **Live Unit Testing** > **opcji**.

Na poniższej ilustracji przedstawiono opcje konfiguracji Live Unit Testing dostępne w oknie dialogowym:

![Opcje konfiguracji Live Unit Testing](./media/lut-options.png)

Można skonfigurować opcje:

- Czy Live Unit Testing wstrzymuje, gdy rozwiązanie jest skompilowane i debugowania.

- Czy Live Unit Testing wstrzymuje, gdy system baterii spadnie poniżej określonego progu.

- Czy Live Unit Testing działa automatycznie po otwarciu rozwiązania.

- Czy włączyć debugowanie symboli i generowanie komentarzy dokumentacji XML.

- Katalog do przechowywania danych.

- Możliwość usunięcia wszystkich danych. Jest to przydatne, gdy Live Unit Testing zachowuje się w nieprzewidywalny lub nieoczekiwany sposób, co sugeruje, że utrwalone dane uległy uszkodzeniu.

- Interwał, po którym przypadek testowy przeprowadzi limit czasu. Wartość domyślna to 30 sekund.

- Maksymalna liczba procesów testu, utworzone przez funkcję Live Unit Testing.

- Maksymalna ilość pamięci, którą może wykorzystać funkcję Live Unit Testing procesów.

- Poziom informacji zapisywane Live Unit Testing **dane wyjściowe** okna.

   Dostępne są następujące opcje bez rejestrowania (**Brak**), tylko komunikaty o błędach (**błąd**), błędów i komunikaty informacyjne (**informacje**, wartość domyślna), lub wszystkie szczegóły (**pełne** ).

   Można również wyświetlić pełne dane wyjściowe w Live Unit Testing **dane wyjściowe** okna, przypisując wartość "1" do zmiennej środowiska na poziomie użytkownika o nazwie `VS_UTE_DIAGNOSTICS`, a następnie ponownie uruchom program Visual Studio.

   Aby przechwycić szczegółowe komunikaty dziennika MSBuild z Live Unit Testing w pliku, należy ustawić `LiveUnitTesting_BuildLog` zmiennej środowiskowej poziomie użytkownika, aby nazwa pliku zawiera dziennik.

## <a name="start-pause-and-stop"></a>Uruchamianie, wstrzymywanie i zatrzymywanie

Aby włączyć Live Unit Testing, wybierz pozycję **testuj** > **Live Unit Testing** > **Rozpocznij** od menu programu Visual Studio najwyższego poziomu. Po włączeniu Live Unit Testing opcje dostępne w menu **Live Unit Testing** zmieniają się z jednego elementu, **zaczynają**, aby **wstrzymywać**, **zatrzymywać**i **resetować czyszczenie**:

- **Wstrzymuje** tymczasowo wstrzymywanie Live Unit Testing.

  Gdy Live Unit Testing jest wstrzymana, Wizualizacja pokrycia nie jest wyświetlana w edytorze, ale wszystkie zebrane dane są zachowywane. Aby wznowić działanie Live Unit Testing, wybierz **Kontynuuj** menu Live Unit Testing. Live Unit Testing wykonuje czynności, które należy wykonać, aby przechwycić wszystkie zmiany, które zostały wprowadzone, gdy została wstrzymana, i odpowiednio aktualizuje symbole.

- **Zatrzymaj** całkowicie zatrzymuje Live Unit Testing. Live Unit Testing odrzuca wszystkie dane, które zostały zebrane.

- **Resetowanie Live Unit Testing czyszczenia** powoduje usunięcie danych utrwalonych, a następnie ponowne uruchomienie Live Unit Testing.

> [!NOTE]
> Jeśli uruchamiasz Live Unit Testing w rozwiązaniu, który nie zawiera projekt testu jednostkowego **Wstrzymaj**, **zatrzymać**, i **resetowania czyste** opcje są wyświetlane na **na żywo Testowanie jednostkowe** menu, ale Live Unit Testing nie rozpoczyna się. W oknie **danych wyjściowych** zostanie wyświetlony komunikat o rozpoczęciu "Brak obsługiwanych adapterów testowych, do których odwołuje się to rozwiązanie...".

W dowolnym momencie możesz czasowo wstrzymać lub całkowite zatrzymanie Live Unit Testing. Można to zrobić na przykład, jeśli jesteś w trakcie refaktoryzacji i wiadomo, że testy zostaną przerwane przez pewien czas.

## <a name="view-coverage-visualization"></a>Wyświetl wizualizację pokrycia

Po włączeniu Live Unit Testing aktualizuje każdy wiersz kodu w edytorze programu Visual Studio, aby pokazać, czy kod, który jest pisany jest objęty testami jednostkowymi, oraz czy testy, które je obejmują, są przekazywane. Na poniższej ilustracji przedstawiono wiersze kodu z testami przechodzącymi i zakończonymi niepowodzeniem, a także wierszy kodu, które nie są objęte testami. Wiersze ozdobione zielony "✓" są objęte przekazując testy, wiersze ozdobione czerwony symbol "x", są objęte zakończone niepowodzeniem testy i wiersze dekorowane przez niebieski "➖" nie są obejmowane przez dowolny test.

![Pokrycie kodu w programie Visual Studio](./media/lut-codewindow.png)

Wizualizacja pokrycia Live Unit Testing jest aktualizowana natychmiast po zmodyfikowaniu kodu w edytorze kodu. Podczas przetwarzania zmian wizualizacji w celu wskazania, że dane nie są aktualne przez dodanie obrazu czasomierza okrągłego poniżej symboli zakończonych niepowodzeniem i nie pokrytych, jak pokazano na poniższej ilustracji.

![Pokrycie kodu w programie Visual Studio przy użyciu ikony czasomierza](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Pobierz informacje o stanie testu

Ustawiając kursor zakończyło się powodzeniem lub niepowodzeniem symboli w oknie kodu, możesz zobaczyć, ile testów osiągnięcia tego wiersza. Aby wyświetlić stan poszczególnych testów, wybierz symbol:

![Stan testu dla symbolu w programie Visual Studio](./media/lut-failedinfo.png)

Oprócz podawania nazw i wyników testów, etykietka narzędzia umożliwia ponowne uruchomienie lub debugowanie zestawu testów. Wybranie jednego lub więcej testów w etykietce narzędzia, można również uruchomić lub debugować tylko te testy. Pozwala na debugowanie testów bez konieczności opuszczania okna kodu. Podczas debugowania, oprócz obserwowania wszystkich punktów przerwania, które można już ustawić, wykonanie programu jest wstrzymywane, gdy debuger wykonuje metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>, która zwraca nieoczekiwany wynik.

Po umieszczeniu testów zakończonych niepowodzeniem w etykietce narzędzia rozwija zapewnienie dodatkowych informacji na temat błędu, jak pokazano na poniższej ilustracji. Aby przejść bezpośrednio do testu zakończonego niepowodzeniem, kliknij go dwukrotnie w etykietce narzędzia.

![Nie można przetestować informacji o etykietce narzędzia w programie Visual Studio](./media/lut-failedmsg.png)

Gdy przejdziesz do testu zakończonego niepowodzeniem, Live Unit Testing wizualnie wskazuje, że w metodzie podpisuje testy, które mają:

- zakończony zakończono (wskazywanym przez pół zlewki i zieloną "✓")
- Niepowodzenie (połowa-pełna zlewka wraz z czerwonym "🞩")
- nie są wykorzystywane w Live Unit Testing (połowa-pełna zlewka wraz z niebieską "➖")

Metody testowe inne niż nie są oznaczone symbolem. Na poniższej ilustracji przedstawiono wszystkie cztery typy metod.

![Metody testowe w programie Visual Studio z symbolem powodzenia lub niepowodzenia](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Zdiagnozować i rozwiązać niepowodzeń testów

W teście zakończonym niepowodzeniem można łatwo debugować kod produktu, wprowadzać zmiany i kontynuować tworzenie aplikacji. Ponieważ Live Unit Testing działa w tle, nie trzeba przerywać ani ponownie uruchamiać Live Unit Testing podczas debugowania, Edytuj i Kontynuuj.

Na przykład niepowodzenie testu pokazane na poprzednim obrazie zostało spowodowane przez nieprawidłowe założenie w metodzie testowej, że znaki niealfabetyczne zwracają `true` po przesłaniu do metody <xref:System.Char.IsLower%2A?displayProperty=fullName>. Po naprawieniu metody testowej należy przekazać wszystkie testy. Nie musisz wstrzymywać ani zatrzymywać Live Unit Testing.

## <a name="test-explorer"></a>Eksplorator testów

**Eksplorator testów** udostępnia interfejs, który umożliwia uruchamianie i debugowanie testów oraz analizowanie wyników testów. Live Unit Testing integruje się z **Eksplorator testów**. Live Unit Testing nie jest włączona lub jest zatrzymana, **Eksploratora testów** wyświetlany jest stan testów jednostkowych czasu ostatniego wykonywania testu. Zmiany kodu źródłowego wymagają, ponownie uruchom testy. Natomiast po włączeniu Live Unit Testing sprawdza stan jednostki w **Eksplorator testów** natychmiast zaktualizować. Nie musisz jawnie uruchamiać testów jednostkowych.

> [!TIP]
> Otwórz **Eksploratora testów** , wybierając **test** > **Windows** > **Test Explorer** z menu programu Visual Studio najwyższego poziomu.

Można zauważyć w **Eksplorator testów** okno, które są wygasić niektóre testy. Na przykład po włączeniu Live Unit Testing po otwarciu wcześniej zapisanego projektu okno **Eksplorator testów** zostało podpięte wszystkie oprócz testu zakończonego niepowodzeniem, jak pokazano na poniższej ilustracji. W takim przypadku Live Unit Testing ponownie uruchamia test zakończony niepowodzeniem, ale nie uruchamia ponownie testów zakończonych powodzeniem. Wynika to z faktu, że dane utrwalone Live Unit Testing wskazują, że nie zostały wprowadzone żadne zmiany, ponieważ testy zostały ostatnio wykonane pomyślnie.

![Test zakończony niepowodzeniem w Eksploratorze testów](media/lut-test-explorer.png)

Wszystkie testy, które są wyświetlane, można uruchomić ponownie, wybierając opcję **Uruchom wszystkie** lub **Uruchom** z menu **Eksplorator testów** . Lub wybierz jeden lub więcej testów w menu **Eksploratora testów** , kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom wybrane testy** lub **Debuguj wybrane testy** z menu podręcznego. Jak są uruchamiane testy, mogą się pojawiać z góry.

Istnieją pewne różnice między Live Unit Testing automatyczne uruchamianie i aktualizowanie wyników testów oraz jawnie Uruchamianie testów z **Eksploratora testów**. Różnice te obejmują:

- Uruchamianie i debugowanie testów z okna Eksploratora testów uruchamia regularne plików binarnych, a Live Unit Testing są uruchamiane instrumentowanych danych binarnych.
- Live Unit Testing nie powoduje utworzenia nowej domeny aplikacji, aby uruchomić testy, ale raczej uruchamia testy z domyślnej domeny. Testy uruchamiane z **Eksplorator testów** okna Tworzenie nowej domeny aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testów po kolei. W oknie **Eksplorator testów** można uruchomić wiele testów równolegle.

## <a name="large-solutions"></a>Duże rozwiązania

Jeśli rozwiązanie ma 10 lub więcej projektów, program Visual Studio wyświetli następujące okno dialogowe:

- Rozpocznij Live Unit Testing i nie ma żadnych utrwalonych danych
- Wybierz **Test** > **Live Unit Testing** > **Zresetuj czyste**

![Live Unit Testing okno dialogowe dla dużych projektów](media/lut-large-project.png)

Okno dialogowe ostrzega o tym, że dynamiczne wykonywanie dużej liczby testów w dużych projektach może poważnie wpłynąć na wydajność. Jeśli wybierzesz **OK**, Live Unit Testing uruchamia wszystkie testy w rozwiązaniu. Jeśli wybierzesz **anulować**, możesz wybrać testy do wykonania. W poniższej sekcji wyjaśniono, jak to zrobić.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Dołączyć i wykluczyć projekty testowe i metod testowych

W przypadku rozwiązań z wieloma projektami testowymi można kontrolować, które projekty i poszczególne metody w projekcie biorą udział w Live Unit Testing. Na przykład jeśli masz rozwiązanie z setek projektów testów, można wybrać docelowego zestawu projektów testowych do wzięcia udziału w Live Unit Testing. Istnieje kilka sposobów, w zależności od tego, czy chcesz wykluczyć wszystkie testy w projekcie lub rozwiązaniu, dołączyć lub wykluczyć większość testów lub wykluczyć poszczególne testy. Live Unit Testing zapisuje stan dołączania lub wykluczania jako ustawienia użytkownika i pamięta, gdy rozwiązanie jest zamykany i ponownie otwarty.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Wyklucz wszystkie testy w projekcie lub rozwiązaniu

Po uruchomieniu Live Unit Testing, aby wybrać poszczególnych projektów testów jednostkowych, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz polecenie **testów na żywo** > **wykluczyć** wyłączenie całego rozwiązania.
1. Kliknij prawym przyciskiem myszy każdy projekt testowy, który chcesz uwzględnić w testach, a następnie wybierz **testów na żywo** > **Include**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Wyklucz pojedyncze testy z okna edytora kodu

Do dołączania lub wykluczania metody poszczególnych testach, można użyć okna edytora kodu. Kliknij prawym przyciskiem myszy podpis metody testowej w oknie Edytor kodu, a następnie wybierz jedną z następujących opcji:

- **Testy na żywo** > **obejmują metodę \<selected >**
- **Testy na żywo** > **wykluczać metodę \<selected >**
- **Testy na żywo** > **Wyklucz wszystko, ale metoda \<selected >**

### <a name="exclude-tests-programmatically"></a>Programowe wykluczanie testów

Można zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybutu programowe wykluczanie metody, klasy lub struktury z raportowania ich pokrycia w Live Unit Testing.

Użyj następujących atrybutów, aby wykluczyć poszczególne metody z Live Unit Testing:

- Aby uzyskać xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Aby uzyskać NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Aby uzyskać MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Użyj następujących atrybutów, aby wykluczyć cały zestaw testów z Live Unit Testing:

- Aby uzyskać xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Aby uzyskać NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Aby uzyskać MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz także

- [Narzędzia do testowania kodu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blog](https://go.microsoft.com/fwlink/?linkid=842514)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)
- film wideo @no__t 0Channel 9: Live Unit Testing w programie Visual Studio @ no__t-0
