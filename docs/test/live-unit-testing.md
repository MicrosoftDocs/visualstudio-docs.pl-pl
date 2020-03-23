---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 1e1a0ec1fd6f2fbdf4f016b1d22db5a6929b5e24
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75851443"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Jak skonfigurować i używać live unit testing

Podczas tworzenia aplikacji live unit testing automatycznie uruchamia wszelkie testy jednostkowe wpływ w tle i przedstawia wyniki i pokrycie kodu w czasie rzeczywistym. Podczas modyfikowania kodu live unit testing zawiera informacje zwrotne na temat wpływu zmian na istniejące testy i czy nowy kod, który został dodany jest objęty co najmniej jednym istniejącym testem. To delikatnie przypomina, aby napisać testy jednostkowe, jak robisz poprawki błędów lub dodawanie nowych funkcji.

> [!NOTE]
> Testowanie jednostek na żywo jest dostępne dla projektów języka C# i Visual Basic, które są przeznaczone dla programu .NET Core lub .NET Framework w wersji Enterprise programu Visual Studio.

Podczas korzystania z live unit testing dla testów, utrzymuje się dane o stanie testów. Za pomocą danych utrwalonych umożliwia live unit testing do zaoferowania najwyższej wydajności podczas uruchamiania testów dynamicznie w odpowiedzi na zmiany kodu.

## <a name="supported-test-frameworks"></a>Obsługiwane struktury testów

Testowanie jednostek na żywo współpracuje z trzema popularnymi strukturami testowania jednostek wymienionymi w poniższej tabeli. Pokazano również minimalną obsługiwaną wersję ich kart i struktur. Struktury testowania jednostkowego są dostępne od NuGet.org.

|Struktura testów  |Minimalna wersja karty programu Visual Studio  |Minimalna wersja ramowa  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio wersja 2.2.0-beta3-build1187 |xjedna 1.9.2 |
|Nunit |NUnit3TestAdapter wersja 3.5.1 |NUnit w wersji 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-podgląd |MSTest.TestFramework 1.0.5-podgląd |

Jeśli masz starsze projekty testowe oparte na mstest, które odwołują się do microsoft.VisualStudio.QualityTools.UnitTestFramework i nie chcesz przenieść do nowszych pakietów MSTest NuGet, uaktualnij do programu Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołuje się projekt, aby testy jednostek na żywo działały. Można to zrobić, wykonując jawną kompilację rozwiązania (wybierz **Build** > **Rebuild Solution** z menu programu Visual Studio najwyższego poziomu) lub przywracając pakiety w rozwiązaniu (kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Przywróć pakiety NuGet).**

## <a name="configure"></a>Konfigurowanie

Skonfiguruj testowanie jednostek na żywo, wybierając**opcje** **narzędzi** > z paska menu programu Visual Studio najwyższego poziomu, a następnie wybierając pozycję **Testowanie jednostek na żywo** w lewym okienku okna dialogowego **Opcje.**

> [!TIP]
> Po włączeniu testowania jednostek na żywo (patrz następna sekcja [Start, wstrzymanie i zatrzymanie testowania jednostek na żywo)](#start-pause-and-stop)można również otworzyć okno dialogowe **Opcje,** wybierając opcję **Opcje testowania** > **na żywo** > **.**

Na poniższym obrazie przedstawiono opcje konfiguracji testowania jednostek na żywo dostępne w oknie dialogowym:

![Opcje konfiguracji testowania jednostek na żywo](./media/lut-options.png)

Konfigurowalne opcje obejmują:

- Czy live unit testing wstrzymuje, gdy rozwiązanie jest zbudowany i debugowane.

- Czy testowanie jednostek na żywo jest wstrzymywało się, gdy poziom naładowania baterii systemu spadnie poniżej określonego progu.

- Czy testowanie jednostek na żywo jest uruchamiane automatycznie po otwarciu rozwiązania.

- Czy włączyć generowanie symbolu debugowania i dokumentacji XML.

- Katalog, w którym mają być przechowywane dane utrwalone.

- Możliwość usunięcia wszystkich utrwalonych danych. Jest to przydatne, gdy testowanie jednostek na żywo zachowuje się w sposób nieprzewidywalny lub nieoczekiwany, co sugeruje, że utrwalone dane uległy uszkodzeniu.

- Interwał, po którym przesądmiały przekreśla czas przypadku testowego. Wartość domyślna to 30 sekund.

- Maksymalna liczba procesów testowych, które tworzy testowanie jednostek na żywo.

- Maksymalna ilość pamięci, jaką mogą zużywać procesy testowania jednostek na żywo.

- Poziom informacji zapisanych w oknie **Dane wyjściowe** testowania jednostek na żywo.

   Opcje obejmują brak rejestrowania (**Brak**), tylko komunikaty o**błędach**( Błąd ), komunikaty o błędzie i informacyjne **(Informacje**,**domyślne)** lub wszystkie szczegóły ( Pełne ).

   Można również wyświetlić pełne dane wyjściowe w oknie **Dane wyjściowe** testowania jednostek na żywo, `VS_UTE_DIAGNOSTICS`przypisując wartość "1" do zmiennej środowiskowej na poziomie użytkownika o nazwie , a następnie ponownie uruchamiając program Visual Studio.

   Aby przechwycić szczegółowe komunikaty dziennika MSBuild `LiveUnitTesting_BuildLog` z live unit testing w pliku, ustaw zmienną środowiskową na poziomie użytkownika na nazwę pliku zawierającego dziennik.

## <a name="start-pause-and-stop"></a>Uruchamianie, wstrzymywanie i zatrzymywanie

Aby włączyć testowanie jednostek na żywo, wybierz **test** > **testowania jednostek na** > żywo**start** z menu programu Visual Studio najwyższego poziomu. Gdy włączone jest testowanie jednostek na żywo, opcje dostępne w menu **Live Unit Testing** zmieniają się z jednego elementu, **Start**, na **Pauza** i **Zatrzymaj:**

- **Wstrzymaj** tymczasowo zawiesza testy jednostek na żywo.

  Gdy testowanie jednostek na żywo jest wstrzymana, wizualizacja pokrycia nie pojawia się w edytorze, ale wszystkie dane, które zostały zebrane, są zachowywane. Aby wznowić testowanie jednostek na żywo, wybierz polecenie **Kontynuuj** z menu Testowanie jednostek na żywo. Live Unit Testing wykonuje niezbędną pracę, aby nadrobić zaległości ze wszystkimi zmianami, które zostały wprowadzone podczas wstrzymania i odpowiednio aktualizuje glify.

- **Zatrzymaj** całkowicie zatrzymuje live unit testing. Testy jednostek na żywo odrzuca wszystkie dane, które zostały zebrane.

> [!NOTE]
> Jeśli rozpoczniesz testowanie jednostek na żywo w rozwiązaniu, które nie zawiera projektu testu jednostkowego, opcje **Wstrzymaj** i **Zatrzymaj** pojawią się w menu **Testowanie jednostek na żywo,** ale testowanie jednostek na żywo nie zostanie uruchomiony. Okno **Dane wyjściowe** wyświetla komunikat, który rozpoczyna się" Żadne obsługiwane karty testowe nie są odwoływane przez to rozwiązanie...".

W dowolnym momencie można tymczasowo wstrzymać lub całkowicie zatrzymać testowanie jednostek na żywo. Możesz to zrobić, na przykład, jeśli jesteś w środku refaktoryzacji i wiem, że testy zostaną przerwane na chwilę.

## <a name="view-coverage-visualization"></a>Wyświetlanie wizualizacji pokrycia

Po włączeniu live unit testing aktualizuje każdy wiersz kodu w edytorze programu Visual Studio, aby pokazać, czy kod, który piszesz jest objęty testów jednostkowych i czy testy, które obejmują go są przekazywania. Na poniższej ilustracji przedstawiono wiersze kodu z testów przekazywania i niepowodzenia, a także wiersze kodu, które nie są objęte testów. Linie ozdobione zielonym "✓" są objęte jedynie przejściami, linie ozdobione czerwonym "x" są objęte jednym lub kilkoma nieudanymi testami, a linie ozdobione niebieskim "➖" nie są objęte żadnym testem.

![Pokrycie kodu w programie Visual Studio](./media/lut-codewindow.png)

Wizualizacja relacji Live Unit Testing jest aktualizowana natychmiast po zmodyfikowaniu kodu w edytorze kodu. Podczas przetwarzania zmian wizualizacja zmienia się, aby wskazać, że dane nie są aktualne, dodając obraz czasomierza okrągłego poniżej symboli przechodzących, nieprzestrzeliwalnych i nieobjętych, jak pokazano na poniższej ilustracji.

![Pokrycie kodu w programie Visual Studio z ikoną czasomierza](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Uzyskaj informacje o stanie testu

Po najechaniu kursorem na symbol, który odniósł sukces lub nie powiódł się w oknie kodu, można zobaczyć, ile testów uderza w ten wiersz. Aby zobaczyć stan poszczególnych testów, wybierz symbol:

![Stan testu symbolu w programie Visual Studio](./media/lut-failedinfo.png)

Oprócz podawania nazw i wyników testów, etykietka narzędzia umożliwia ponowne uruchomienie lub debugowanie zestawu testów. Jeśli wybierzesz jeden lub więcej testów w etykietce narzędzia, można również uruchomić lub debugować tylko te testy. Dzięki temu można debugować testy bez konieczności opuszczania okna kodu. Podczas debugowania, oprócz obserwowania punktów przerwania, które mogą być już ustawione, wykonanie programu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> wstrzymuje się, gdy debuger wykonuje metodę, która zwraca nieoczekiwany wynik.

Po umieszczeniu wskaźnika myszy na test nie powiodło się w etykietce narzędzia, rozszerza się, aby zapewnić dodatkowe informacje o awarii, jak pokazano na poniższej ilustracji. Aby przejść bezpośrednio do testu, który nie powiódł się, kliknij go dwukrotnie w etykietce narzędzia.

![Informacje o narzędziach testu nie powiodły się w programie Visual Studio](./media/lut-failedmsg.png)

Po przejściu do testu nie powiodło się, Live Unit Testing wizualnie wskazuje w podpisie metody testy, które mają:

- (wskazywany przez pół-pełną zlewkę wraz z zielonym "✓")
- nie powiodła się (pół-pełna zlewka🞩wraz z czerwonym " ")
- nie biorą udziału w testach jednostkowych na żywo (półuprawna zlewka wraz z niebieskim "➖")

Metody nietestowe nie są ozdobione symbolem. Na poniższej ilustracji przedstawiono wszystkie cztery typy metod.

![Metody testowania w programie Visual Studio z symbolem przebiegu lub niepowodzenia](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnozowanie i korygowanie błędów testów

Z testu nie powiodło się, można łatwo debugować kod produktu, wprowadzić zmiany i kontynuować tworzenie aplikacji. Ponieważ testowanie jednostek na żywo działa w tle, nie trzeba zatrzymywać i ponownie uruchamiać testowania jednostek na żywo podczas cyklu debugowania, edycji i kontynuowania.

Na przykład błąd testu pokazany w poprzednim obrazie został spowodowany przez niepoprawne założenie `true` w metodzie <xref:System.Char.IsLower%2A?displayProperty=fullName> testowej, że znaki niealfabetyczne zwracają po przekazaniu do metody. Po skorygowaniu metody testowej wszystkie testy powinny przejść. Nie trzeba wstrzymywać ani zatrzymywać testowania jednostek na żywo.

## <a name="test-explorer"></a>Eksplorator testów

**Eksplorator testów** udostępnia interfejs, który umożliwia uruchamianie i debugowanie testów oraz analizowanie wyników testów. Live Unit Testing integruje się z **Eksploratorem testów**. Gdy testowanie jednostkowe na żywo nie jest włączone lub jest zatrzymane, **Eksplorator testów** wyświetla stan testów jednostkowych podczas ostatniego uruchomienia testu. Zmiany kodu źródłowego wymagają ponownego uruchomienia testów. Natomiast gdy aktywne testowanie jednostkowe jest włączone, stan testów jednostkowych w **Eksploratorze testów** jest aktualizowany natychmiast. Nie trzeba jawnie uruchamiać testy jednostkowe.

> [!TIP]
> Otwórz **Eksploratora testów,** wybierając **pozycję Test** > **Windows** > **Test Explorer** z menu programu Visual Studio najwyższego poziomu.

W oknie **Eksploratora testów** można zauważyć, że niektóre testy są wyblakłe. Na przykład po włączeniu live unit testing po otwarciu wcześniej zapisanego projektu, okno **Eksploratora testów** wyblakło wszystkie, ale test nie powiodło się, jak pokazano na poniższej ilustracji. W takim przypadku live unit testing ma ponownie uruchomić test nie powiodło się, ale nie ma ponownie pomyślne testy. Jest tak, ponieważ utrwalone dane utrwalonych testów jednostkowych na żywo wskazują, że nie było żadnych zmian, ponieważ testy zostały pomyślnie uruchomione.

![Nieudany test w Eksploratorze testów](media/lut-test-explorer.png)

Można ponownie uruchomić wszystkie testy, które wydają się wyblakłe, wybierając opcje **Uruchom wszystko** lub **Uruchom** z menu **Eksploratora testów.** Możesz też wybrać jeden lub więcej testów w menu **Eksploratora testów,** kliknąć prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom wybrane testy** lub **Debugowanie wybranych testów** z menu podręcznego. Jak testy są uruchamiane, oni bańki na górze.

Istnieją pewne różnice między live unit testing automatycznie uruchomiony i aktualizowanie wyników testów i jawnie uruchomiony testów z **Eksploratora testów.** Różnice te obejmują:

- Uruchamianie lub debugowanie testów z okna Eksploratora testów uruchamia regularne pliki binarne, podczas gdy testowanie jednostek na żywo uruchamia instrumentowane pliki binarne.
- Testowanie jednostek na żywo nie tworzy nowej domeny aplikacji do uruchamiania testów, ale uruchamia testy z domeny domyślnej. Testy uruchamiane z okna **Eksploratora testów** tworzą nową domenę aplikacji.
- Live Unit Testing uruchamia testy w każdym zestawie testowym sekwencyjnie. W oknie **Eksploratora testów** można uruchomić wiele testów równolegle.

## <a name="large-solutions"></a>Duże rozwiązania

Jeśli rozwiązanie ma 10 lub więcej projektów, visual studio wyświetla następujące okno dialogowe podczas:

- uruchamianie testów jednostkowych na żywo i nie ma utrwalonych danych
- wybieranie opcji **narzędzia** > **Na** > **żywo testowanie jednostek Usuwanie** > **utrwalonych danych**

![Okno dialogowe Testowanie jednostek na żywo dla dużych projektów](media/lut-large-project.png)

Okno dialogowe ostrzega, że dynamiczne wykonywanie dużej liczby testów w dużych projektach może poważnie wpłynąć na wydajność. Jeśli wybierzesz **OK,** live unit testing wykonuje wszystkie testy w rozwiązaniu. Jeśli wybierzesz **anuluj,** możesz wybrać testy do wykonania. W poniższej sekcji wyjaśniono, jak to zrobić.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Uwzględnianie i wykluczanie projektów testowych i metod testowych

W przypadku rozwiązań z wieloma projektami testowymi można kontrolować, które projekty i poszczególne metody w projekcie uczestniczą w testach jednostek na żywo. Na przykład jeśli masz rozwiązanie z setkami projektów testowych, możesz wybrać zestaw testów do udziału w testach jednostek na żywo. Istnieje wiele sposobów, aby to zrobić, w zależności od tego, czy chcesz wykluczyć wszystkie testy w projekcie lub rozwiązaniu, uwzględnić lub wykluczyć większość testów lub wykluczyć poszczególne testy. Live Unit Testing zapisuje podać/wykluczyć stan jako ustawienie użytkownika i zapamiętuje go, gdy rozwiązanie jest zamknięte i ponownie otwarte.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Wykluczanie wszystkich testów w projekcie lub rozwiązaniu

Aby wybrać poszczególne projekty w testach jednostkowych, wykonaj następujące czynności po uruchomieniu testów jednostkowych na żywo:

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz opcję**Wyklucz** **testy** > na żywo, aby wykluczyć całe rozwiązanie.
1. Kliknij prawym przyciskiem myszy każdy projekt testowy, który chcesz uwzględnić w testach, i wybierz polecenie**Uwzględnij** **testy** > na żywo .

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Wykluczanie poszczególnych testów z okna edytora kodu

Można użyć okna edytora kodu, aby uwzględnić lub wykluczyć poszczególne metody testowania. Kliknij prawym przyciskiem myszy podpis metody testowej w oknie edytora kodu, a następnie wybierz jedną z następujących opcji:

- **Testy na żywo** > ** \<Uwzględnij wybraną metodę>**
- **Testy na żywo** > ** \<Wykluczyć wybraną metodę>**
- **Testy na żywo** > **wykluczają wszystkie, ale \<wybrana metoda>**

### <a name="exclude-tests-programmatically"></a>Wykluczanie testów programowo

Można zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybut do programowo wykluczyć metody, klasy lub struktury z raportowania ich zasięgu w live unit testing.

Użyj następujących atrybutów, aby wykluczyć poszczególne metody z testów jednostek na żywo:

- Dla jednostki xUnit:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Dla NUnit:`[Category("SkipWhenLiveUnitTesting")]`
- Dla MSTest:`[TestCategory("SkipWhenLiveUnitTesting")]`

Użyj następujących atrybutów, aby wykluczyć cały zestaw testów z testów jednostkowych na żywo:

- Dla jednostki xUnit:`[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Dla NUnit:`[assembly: Category("SkipWhenLiveUnitTesting")]`
- Dla MSTest:`[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz też

- [Narzędzia do testowania kodu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog testowania jednostek na żywo](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)
- [Klip wideo z kanału 9: Testowanie jednostek na żywo w programie Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
