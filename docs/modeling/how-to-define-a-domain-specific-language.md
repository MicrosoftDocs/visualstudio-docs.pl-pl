---
title: 'Porady: definiowanie języka właściwego dla domeny'
description: Dowiedz się, jak utworzyć Visual Studio na podstawie szablonu, aby zdefiniować język specyficzny dla domeny (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51717e4bdbf12478e22bb825a9c84cfc82815f98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387362"
---
# <a name="how-to-define-a-domain-specific-language"></a>Porady: definiowanie języka właściwego dla domeny
Aby zdefiniować język specyficzny dla domeny (DSL), należy utworzyć Visual Studio na podstawie szablonu. Kluczową częścią rozwiązania jest diagram definicji DSL, który jest przechowywany w dslDefinition.dsl. Definicja DSL definiuje klasy i kształty DSL. Po zmodyfikowaniu i dodaniu do tych elementów można dodać kod programu, aby bardziej szczegółowo dostosować DSL.

Jeśli nie masz jeszcze dostępu do języka DSL, zalecamy zapoznanie się z laboratorium **narzędzi DSL Tools Lab,** które można znaleźć w tej witrynie: Zestaw SDK wizualizacji [i modelowania](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Wybieranie rozwiązania szablonu

Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:

- Visual Studio
- Visual Studio tworzenia rozszerzeń (w tym zestaw SDK Visual Studio)
- Modeling SDK (zainstaluj go jako pojedynczy składnik w programie Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Aby utworzyć nowy język specyficzny dla domeny, należy utworzyć nowe rozwiązanie Visual Studio przy użyciu szablonu Domain-Specific language.

### <a name="to-create-a-dsl-solution"></a>Aby utworzyć rozwiązanie DSL

1. Utwórz nowy **projekt Języka specyficznego dla** domeny.

   ::: moniker range="vs-2017"

    ![Okno dialogowe Tworzenie DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

    Zostanie **otwarty Kreator języka specyficznego** dla domeny z wyświetloną listą szablonów rozwiązań DSL.

2. Kliknij każdy szablon, aby wyświetlić opis. Wybierz rozwiązanie, które najlepiej przypomina to, co chcesz utworzyć.

    Każdy szablon DSL definiuje podstawowy roboczy DSL. Będziesz edytować ten język DSL, aby dopasować go do własnych wymagań.

    Kliknij każdy przykład, aby uzyskać więcej informacji.

   - Wybierz **pozycję Przepływ zadań,** aby utworzyć DSL, który ma tory. Tory to pionowe lub poziome partycje diagramu.

   - Wybierz **pozycję Modele składników,** aby utworzyć DSL z portami. Porty są małymi kształtami na krawędzi większego kształtu.

   - Wybierz **pozycję Diagramy klas,** aby zdefiniować DSL, który ma kształty przedziałów. Kształty przedziałów zawierają listy elementów.

   - Wybierz **pozycję Minimalny język** w innych przypadkach lub jeśli nie masz pewności.

   - Wybierz **pozycję Minimal WinForm Designer** lub Minimal **WPF Designer,** aby utworzyć DSL wyświetlany na powierzchni Windows Forms lub WPF. Aby zdefiniować edytor, musisz napisać kod. Aby uzyskać więcej informacji, zobacz następujące tematy:

        [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Wprowadź rozszerzenie nazwy pliku dla DSL na odpowiedniej stronie kreatora. Jest to rozszerzenie, które będzie używać plików zawierających wystąpienia DSL.

   - Wybierz rozszerzenie nazwy pliku, które nie jest skojarzone z żadnej aplikacji na komputerze lub na dowolnym komputerze, na którym chcesz zainstalować DSL. Na przykład rozszerzenia **docx** i **htm** byłyby nieakceptowalnymi rozszerzeniami nazw plików.

   - Kreator ostrzega, jeśli wprowadzone rozszerzenie jest używane jako DSL. Rozważ użycie innego rozszerzenia nazwy pliku. Można również zresetować wystąpienie eksperymentalne zestawu SDK Visual Studio, aby wyczyścić starych projektantów eksperymentalnych. Kliknij **przycisk Start**, kliknij pozycję Wszystkie **programy,** **Microsoft Visual Studio 2010 SDK,** **Narzędzia**, a następnie zresetuj **Microsoft Visual Studio 2010 Eksperymentalne wystąpienie** programu .

4. Możesz dostosować ustawienia na innych stronach lub pozostawić wartości domyślne.

5. Kliknij przycisk **Finish** (Zakończ).

    Kreator tworzy rozwiązanie, które zawiera dwa lub trzy projekty i generuje kod na podstawie definicji DSL.

   Interfejs użytkownika jest teraz podobny do poniższego obrazu.

   ![dsl designer](../modeling/media/dsl_designer.png)

   To rozwiązanie definiuje język specyficzny dla domeny. Aby uzyskać więcej informacji, [zobacz Overview of the Domain-Specific Language Tools Interfejs użytkownika](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testowanie rozwiązania
 Rozwiązanie szablonu udostępnia roboczy DSL, który można modyfikować lub używać bez zmian.

 Aby przetestować rozwiązanie, naciśnij klawisz F5 lub CTRL+F5. Nowe wystąpienie usługi Visual Studio zostanie otwarte w trybie eksperymentalnym.

 W nowym wystąpieniu Visual Studio w Eksplorator rozwiązań otwórz plik Przykład. Zostanie on otwarty jako diagram z przybornikiem.

 Jeśli uruchamiasz rozwiązanie utworzone na podstawie szablonu **Minimalny** język, twój szablon eksperymentalny Visual Studio podobny do następującego przykładu:

 ![Drzewo przykładowe języka specyficznego dla domeny w Visual Studio](../modeling/media/dsl_min.png)

 Poeksperymentuj z narzędziami. Tworzenie elementów i łączenie ich.

 Zamknij eksperymentalne wystąpienie Visual Studio.

> [!NOTE]
> Po zmodyfikowaniu DSL nie będzie już można zobaczyć kształtów w przykładowym pliku testowym. Będzie można jednak tworzyć nowe elementy.

### <a name="modifying-the-template-dsl"></a>Modyfikowanie DSL szablonu
 Zmień nazwę i zachowaj niektóre lub wszystkie klasy domeny i klasy kształtów w definicji DSL szablonu. Nazwy nowych klas powinny być prawidłowymi nazwami CLR, bez spacji ani znaków interpunkcji.

 Szczególnie przydatne jest zachowanie tych klas:

- Klasa główna jest wyświetlana w lewym górnym rogu diagramu definicji DSL w obszarze **Klasy i relacje**. Zmień jego nazwę na inną niż DSL. Na przykład DSL o nazwie **MusicLibrary** może mieć klasę główną o nazwie **Music**.

- Klasa diagramu jest wyświetlana w prawym dolnym rogu diagramu definicji DSL w kolumnie **Elementy diagramu.** W celu jej zobaczenia może być konieczne przewinięcie w prawo. Zazwyczaj nosi on nazwę _YourDsl_**Diagram**.

- Jeśli używasz szablonu **przepływu zadań** i chcesz tworzyć diagramy z torami, zachowaj klasę domeny Aktor i kształt ActorSwimlane oraz zmień ich nazwę.

  Usuń lub zmień nazwy innych klas odpowiednio do swoich wymagań.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> Wzorce definiowania DSL
 Zalecamy opracowanie DSL przez dodanie lub dostosowanie jednej lub dwóch funkcji na raz. Dodaj funkcję, uruchom DSL i przetestuj ją, a następnie dodaj co najmniej jedną funkcję. Typową funkcją DSL może być:

- Klasa domeny, relacja osadzania łącząca element z modelem, kształt wymagany do wyświetlania elementów tej klasy na diagramie oraz narzędzie elementu, które umożliwia użytkownikom tworzenie elementów.

- Właściwości domeny klasy domeny i dekoratory, które wyświetlają je na kształcie.

- Relacja referencyjna i łącznik, który wyświetla je na diagramie, oraz narzędzie łącznika, które umożliwia użytkownikom tworzenie linków.

- Dostosowanie, które wymaga kodu programu, takiego jak ograniczenie walidacji lub polecenie menu.

  W poniższych sekcjach opisano sposób konstruowania najbardziej przydatnych rodzajów funkcji DSL. Istnieje wiele innych wzorców, za pomocą których można utworzyć DSL, ale są one najczęściej używane.

> [!NOTE]
> Po dodaniu funkcji nie zapomnij  kliknąć przycisk Przekształć wszystkie szablony na pasku narzędzi Eksplorator rozwiązań przed skompilowanie i uruchomienie DSL.

 Na poniższej ilustracji przedstawiono klas i relacji część DSL, który jest używany jako przykład w tym temacie.

 ![Osadzanie i odwołania do relacji](../modeling/media/music_classes.png)

 Następny rysunek jest przykładowym modelem tego DSL:

 ![Model wystąpienia wygenerowanego DSL](../modeling/media/music_instance.png)

> [!NOTE]
> "Model" odnosi się do wystąpienia DSL, które użytkownicy tworzą i zwykle jest wyświetlany jako diagram. W tym temacie omówiono zarówno diagram definicji DSL, jak i diagramy modelu, które są wyświetlane, gdy jest używany dsl.

## <a name="defining-domain-classes"></a><a name="classes"></a> Definiowanie klas domeny
 Klasy domen reprezentują pojęcia DSL. Wystąpienia są *elementami modelu*. Na przykład w DSL **MusicLibrary** możesz mieć klasy domen o nazwach **Aad** i **Song.**

 Aby utworzyć klasę domeny, możesz przeciągnąć z narzędzia **Nazwana klasa domeny** do diagramu, a następnie zmienić nazwę klasy.

 Aby uzyskać więcej informacji, [zobacz Właściwości klas domeny](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Tworzenie relacji osadzania dla każdej klasy domeny
 Każda klasa domeny z wyjątkiem klasy głównej musi być obiektem docelowym co najmniej jednej relacji osadzania lub musi dziedziczyć z klasy, która jest obiektem docelowym relacji osadzania.

 W modelu każdy element modelu jest węzłem w jednym drzewie osadzania relacji. Źródło i element docelowy relacji osadzania są często określane jako element nadrzędny i podrzędny.

 Wybór elementu nadrzędnego dla klasy domeny zależy od tego, jak okresy istnienia jej elementów mają zależeć od innych elementów. Jeśli węzeł drzewa zostanie usunięty, jego drzewo podrzędne jest zwykle również usuwane. Klasy elementów, które mają niezależne istnienie, są w związku z tym osadzone bezpośrednio w klasie głównej.

 Zazwyczaj, jeśli element jest wyświetlany wewnątrz innego elementu, chcesz wskazać relację właściciela. W takim przypadku najbardziej odpowiednią klasą nadrzędną jest klasa kontenera. Wyjątek występuje, gdy element, który widzisz wewnątrz kontenera, jest w rzeczywistości tylko linkiem odwołania do niezależnego elementu. W takim przypadku usunięcie kontenera powoduje usunięcie odwołania, ale nie jego obiektu docelowego.

 We wzorcach definicji DSL opisanych w tym temacie założono, że elementy wyświetlane wewnątrz kontenera zostaną usunięte po usunięciu kontenera. Bardziej złożone schematy są możliwe i można je osiągnąć przez zdefiniowanie reguł.

|Sposób wyświetlania elementu|Klasa nadrzędna (osadzanie)|Przykład w szablonie rozwiązania DSL|
|-|-|-|
|Kształtowanie na diagramie.<br /><br /> Tor.|Klasa główna DSL.|Minimalny język.<br /><br /> Przepływ zadań: klasa aktora.|
|Kształtowanie na torysach.|Klasa domeny elementów, które są wyświetlane jako torów.|Przepływ zadań: Klasa zadania.|
|Element na liście w kształcie, gdzie element jest usuwany w przypadku usunięcia kontenera.<br /><br /> Port na krawędzi kształtu.|Klasa domeny zamapowana na kształt kontenera.|Diagram klas: Klasa atrybutu.<br /><br /> Diagram składników: klasa portu.|
|Element na liście, a nie usunięty, jeśli kontener zostanie usunięty.|Klasa główna DSL.<br /><br /> Na liście zostaną wyświetlone linki odwołania.||
|Nie są wyświetlane bezpośrednio.|Klasa, której stanowi część.||

 W przykładzie z biblioteką muzyki Są wyświetlane prostokąty, w których są wyświetlane tytuły utworów. W związku z tym elementem nadrzędnym Zespołu jest główna klasa Music, a elementem nadrzędnym utworu jest Jednak.

 Aby utworzyć klasę domeny i jej osadzanie w  tym samym czasie, kliknij narzędzie Relacja osadzania, a następnie kliknij klasę nadrzędną, a następnie kliknij pustą część diagramu.

 Zazwyczaj nie trzeba dostosowywać nazwy relacji osadzania i jej ról, ponieważ będą one automatycznie śledzić nazwy klas.

 Aby uzyskać więcej informacji, [zobacz Właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i właściwości ról [domeny.](../modeling/properties-of-domain-roles.md)

> [!NOTE]
> Osadzanie to nie to samo co dziedziczenie. Elementy children w relacji osadzania nie dziedziczą cech po ich elementach rodziców.

### <a name="add-domain-properties-to-each-domain-class"></a>Dodawanie właściwości domeny do każdej klasy domeny
 Właściwości domeny przechowują wartości. Przykłady to: Nazwa, Tytuł, Data publikacji.

 Kliknij **pozycję Właściwości** domeny w klasie, naciśnij klawisz ENTER, a następnie wpisz nazwę właściwości. Domyślnym typem właściwości domeny jest Ciąg. Jeśli chcesz zmienić typ, wybierz właściwość domeny i ustaw **typ** w **oknie** Właściwości. Jeśli typ, którego chcesz użyć, nie znajduje się na liście rozwijanej, zobacz [Dodawanie typów właściwości](#addTypes).

 **Ustaw właściwość Nazwa elementu.** Wybierz właściwość domeny, która może służyć do identyfikowania elementów w eksploratorze języka. Na przykład w klasie domeny Song można wybrać właściwość domeny Tytuł. W **oknie Właściwości** ustaw wartość **właściwości Jest nazwą elementu** na `true` .

### <a name="create-derived-domain-classes"></a>Tworzenie klas domen pochodnych
 Jeśli chcesz, aby klasa domeny zawierała warianty dziedziczące jej właściwości i relacje, utwórz klasy, które pochodzą z tej klasy. Na przykład Może mieć klas pochodnych WMA i MP3.

 Utwórz klasę pochodną za pomocą **narzędzia Klasy domeny.**

 Kliknij narzędzie **Dziedziczenie,** kliknij klasę pochodną, a następnie kliknij klasę bazową.

 Rozważ ustawienie **modyfikatora dziedziczenia** klasy bazowej w celu **abstrakcji**. Jeśli uważasz, że mogą być potrzebne wystąpienia klasy bazowej, rozważ utworzenie oddzielnej klasy pochodnej.

 Klasy pochodne dziedziczą właściwości i role klas bazowych.

### <a name="tidy-the-dsl-definition-diagram"></a>Uporządkowanie diagramu definicji DSL
 Po dodaniu relacji niektóre klasy będą wyświetlane w więcej niż jednym miejscu. Aby zmniejszyć liczbę wystąpień i szerszego diagramu, kliknij prawym przyciskiem myszy klasę docelową relacji, a następnie kliknij pozycję Bring Tree Here (Przynieź **drzewo tutaj).** Aby uzyskać odwrotny efekt, kliknij prawym przyciskiem myszy klasę docelową relacji, a następnie kliknij pozycję **Podziel drzewo**. Jeśli nie widzisz tych poleceń menu, upewnij się, że wybrano tylko klasę domeny.

 Użyj klawiszy CTRL+Up i CTRL+Down, aby przenieść klasy domen i klasy kształtów.

### <a name="test-the-domain-classes"></a>Testowanie klas domeny

##### <a name="to-test-the-new-domain-classes"></a>Aby przetestować nowe klasy domeny

1. **Kliknij pozycję Przekształć** wszystkie szablony na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL. Ten krok można zautomatyzować. Aby uzyskać więcej informacji, zobacz How to Automate Transform All Templates (Jak [zautomatyzować przekształcanie wszystkich szablonów).](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

2. **Skompilowanie i uruchomienie DSL.** Naciśnij klawisz F5 lub CTRL+F5, aby uruchomić nowe wystąpienie Visual Studio w trybie eksperymentalnym. W eksperymentalnym wystąpieniu Visual Studio otwórz lub utwórz plik z rozszerzeniem nazwy pliku DSL.

3. **Otwórz Eksploratora.** Na stronie diagramu znajduje się okno eksploratora języka, które zazwyczaj nosi nazwę *YourLanguage* Explorer. Jeśli to okno nie jest widzisz, może ono być na karcie poniżej Eksplorator rozwiązań. Jeśli nie możesz go znaleźć, w menu **Widok** wskaż pozycję **Inne okna,** a następnie kliknij *pozycję YourLanguage* **Explorer**.

     Eksplorator przedstawia widok drzewa modelu.

4. **Tworzenie nowych elementów.** Kliknij prawym przyciskiem myszy węzeł główny u góry, a następnie kliknij polecenie **Dodaj nową**_klasę_.

     W Eksploratorze języka zostanie wyświetlone nowe wystąpienie klasy.

5. Sprawdź, czy każde wystąpienie ma inną nazwę podczas tworzenia nowych wystąpień. Nastąpi to tylko wtedy, gdy ustawiono flagę **Is Nazwa elementu** we właściwości domeny.

6. **Sprawdź właściwości domeny. Po wybraniu wystąpienia klasy sprawdź,** czy okno Właściwości. Powinny być w nim wyświetlane właściwości domeny zdefiniowane w tej klasie domeny.

7. **Zapisz plik, zamknij go i otwórz go ponownie.** Wszystkie utworzone wystąpienia powinny być widoczne w eksploratorze po rozwinięciu węzłów.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Definiowanie kształtów na diagramie
 Klasy elementów wyświetlanych na diagramie można definiować jako prostokąty, wielokropki lub ikony.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Aby zdefiniować klasę elementów, które są wyświetlane jako kształty na diagramie

1. **Zdefiniuj i przetestuj klasę domeny zgodnie z opisem** w [teście Definiowanie klas domeny](#classes) **.**  

   - Element nadrzędny klasy powinien być klasą główną. Oznacza to, że powinna być relacja osadzania między klasą główną a nową klasą domeny.

   - Jeśli diagram zawiera tory, elementem nadrzędnym może być klasa domeny zamapowana na tor. Przed kontynuowaniem tej procedury, zobacz [Definiowanie DSL, który ma torów](#swimlanes).

2. **Dodaj klasę kształtu reprezentującą** elementy na diagramie modelu. Przeciągnij z jednego z następujących narzędzi na diagram definicji DSL:

   - **Kształt geometrii** zawiera prostokąt lub wielokropek.

   - **W polu Image Shape** (Kształt obrazu) jest wyświetlany obraz, który został przez Ciebie wyświetlony.

   - **Kształt przedziału** to prostokąt zawierający co najmniej jedną listę elementów.

     Zmień nazwę klasy shape, która będzie wyświetlana po prawej stronie diagramu definicji DSL, w obszarze Kształty i łączniki.

3. **Zdefiniuj obraz, jeśli utworzono kształt obrazu**.

   1. Utwórz plik obrazu o dowolnym rozmiarze. Obsługiwane są formaty BMP, JPEG, GIF i EMF.

   2. W Eksplorator rozwiązań dodaj plik do rozwiązania w obszarze Dsl\Resources.

   3. Wróć do diagramu definicji DSL i wybierz nową klasę kształtu obrazu.

   4. W okno Właściwości kliknij właściwość **Image.**

   5. W **oknie dialogowym** Wybieranie obrazu kliknij menu rozwijane w obszarze **Nazwa pliku** i wybierz obraz.

4. **Dodaj dekoratory tekstu do kształtu, aby wyświetlić właściwości domeny.**

    Aby wyświetlić nazwę lub tytuł elementu modelu, prawdopodobnie będziesz potrzebować co najmniej jednego dekoratora tekstu.

    Kliknij prawym przyciskiem myszy nagłówek klasy kształtu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Dekorator tekstu.** Ustaw nazwę dekoratora, a w okno Właściwości ustaw jego **pozycję**.

5. **Połącz każdy kształt za pomocą mapy elementu diagramu z klasą domeny, która powinna wyświetlać** element .

    Kliknij narzędzie **Mapowanie elementu diagramu,** a następnie kliknij klasę domeny, a następnie kliknij klasę kształtu.

6. **Zamapuj właściwości na dekoratory tekstu.**

   1. Wybierz szarą linię między klasą domeny a klasą kształtu, która reprezentuje mapę elementu diagramu.

   2. W **oknie Szczegóły DSL** kliknij **kartę Decorator Maps.** Jeśli nie widzisz okna **Szczegóły DSL,** w menu **Widok** wskaż pozycję **Inne okna,** a następnie kliknij pozycję **Szczegóły DSL.** Często konieczne jest podniesienie górnej części tego okna, aby wyświetlić całą jego zawartość.

   3. Wybierz nazwę dekoratora. W **obszarze Właściwość wyświetlania** wybierz nazwę właściwości klasy domeny. Powtórz to dla każdego dekoratora.

       Jeśli chcesz wyświetlić właściwość powiązanego elementu, kliknij nawigator drzewa listy rozwijanej w obszarze **Ścieżka, aby wyświetlić właściwość**.

   4. Upewnij się, że obok każdej nazwy dekoratora jest wyświetlany znacznik wyboru.

      ![Mapowanie kształtów i okno szczegółów DSL](../modeling/media/dsldetailswindow.png)

7. **Tworzenie elementu przybornika do tworzenia elementów klasy domeny.**

   1. W **Eksploratorze DSL** rozwiń węzeł **Edytor** i wszystkie jego węzły podrzędne.

   2. Kliknij prawym przyciskiem myszy węzeł w obszarze **Karty przybornika** o takiej samej nazwie jak DSL, na przykład MusicLibrary. Kliknij **pozycję Add Element Tool (Dodaj element Tool).**

       > [!NOTE]
       > Jeśli klikniesz prawym przyciskiem myszy **węzeł Narzędzia,** nie zobaczysz narzędzia **Dodaj element**. Zamiast tego kliknij węzeł nad nim.

   3. W okno Właściwości z wybranym narzędziem nowego elementu ustaw opcję **Klasa** na nowo dodaną klasę domeny.

   4. Ustaw **podpis i** **etykietkę narzędzia.**

   5. Ustaw **ikonę przybornika** na ikonę, która będzie wyświetlana w przyborniku. Możesz ustawić ją na nową ikonę lub ikonę używaną już dla innego narzędzia.

        Aby utworzyć nową ikonę, otwórz katalog Dsl\Resources w **Eksplorator rozwiązań**. Skopiuj i wklej jeden z istniejących plików BMP narzędzia elementu. Zmień nazwę wklejonych kopii, a następnie kliknij dwukrotnie, aby ją edytować.

        Wróć do diagramu definicji DSL, wybierz narzędzie, a następnie na okno Właściwości **przycisk [...]** w **ikonie przybornika**. W **oknie dialogowym Wybieranie** mapy bitowej wybierz .BMP z menu rozwijanego.

   Aby uzyskać więcej informacji, [zobacz Właściwości kształtów geometrycznych](../modeling/properties-of-geometry-shapes.md) i [właściwości kształtów obrazu](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Aby przetestować kształty

1. **Kliknij pozycję Przekształć** wszystkie szablony na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL.

2. **Skompilowanie i uruchomienie DSL.** Naciśnij klawisz F5 lub CTRL+F5, aby uruchomić nowe wystąpienie Visual Studio w trybie eksperymentalnym. W eksperymentalnym wystąpieniu Visual Studio otwórz lub utwórz plik z rozszerzeniem nazwy pliku DSL.

3. **Sprawdź, czy narzędzia elementów są wyświetlane w przyborniku.**

4. **Twórz kształty,** przeciągając je z narzędzia do diagramu modelu.

5. **Sprawdź, czy każdy dekorator tekstu jest wyświetlany i** czy:

   1. Można go edytować, chyba że ustawiono flagę **Tylko** do odczytu interfejsu użytkownika we właściwości domeny.

   2. Podczas edytowania właściwości w okno Właściwości lub w dekoratorze zostanie zaktualizowany drugi widok.

   Po pierwszym przetestowaniu kształtu warto dostosować jego właściwości i dodać bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-reference-relationships"></a><a name="references"></a> Definiowanie relacji odwoływać
 Można zdefiniować relację odwołania między dowolną klasą domeny źródłowej i dowolną docelową klasą domeny. Relacje referencyjne są zwykle wyświetlane na diagramie jako łączniki, które są liniami między kształtami.

 Jeśli na diagramie na diagramie są wyświetlane kształty music (Amis i Artists), można zdefiniować relację o nazwie ArtistsAppearedOnAlbums,która łączy artystów z negocjami, nad którymi pracowali. Zobacz przykład na rysunku.

 ![Model wystąpienia wygenerowanego DSL](../modeling/media/music_instance.png)

 Relacje odwoływać mogą również łączyć elementy tego samego typu. Na przykład w DSL reprezentującym drzewo rodziny relacja między rodziców i ich dzieci jest relacją referencyjną z osoby do osoby.

### <a name="define-a-reference-relationship"></a>Definiowanie relacji odwołania
 Kliknij narzędzie Relacja referencyjna, kliknij klasę domeny źródłowej relacji, a następnie kliknij docelową klasę domeny. Klasa docelowa może być taka sama jak klasa źródłowa.

 Każda relacja ma dwie role reprezentowane przez wiersz po każdej stronie pola relacji. Możesz wybrać każdą rolę i ustawić jej właściwości w okno Właściwości.

 **Rozważ zmianę nazw ról**. Na przykład w relacji między osobami i osobami można zmienić nazwy domyślne na Rodziców i dzieci, Menedżer i Podrzędne, Nauczyciel i Uczeń i tak dalej.

 **Dostosuj mnożenia poszczególnych ról,** jeśli jest to konieczne. Jeśli chcesz, aby każda osoba zawierała co najwyżej jednego Menedżera, ustaw liczebność wyświetlaną poniżej etykiety Menedżer na diagramie na wartość 0..1.

 **Dodaj właściwości domeny do relacji.** Na rysunku relacja Artist-Album ma właściwość roli.

 **Ustaw właściwość Zezwala na duplikaty relacji,** jeśli między tymi samymi dwiema elementami modelu może istnieć więcej niż jedno łącze tej samej klasy. Na przykład możesz zezwolić nauczycielowi na nauczanie więcej niż jednego tematu dla tego samego ucznia.

 ![Mapy kształtów dla łączników](../modeling/media/music_connector.png)

 Aby uzyskać więcej informacji, [zobacz Właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i właściwości ról [domeny.](../modeling/properties-of-domain-roles.md)

### <a name="define-a-connector-to-display-the-relationship"></a>Definiowanie łącznika w celu wyświetlenia relacji
 Łącznik wyświetla linię między dwoma kształtami na diagramie modelu.

 Przeciągnij narzędzie **Łącznik** na diagram definicji DSL.

 Dodaj dekoratory tekstu, jeśli chcesz wyświetlać etykiety w łączniku. Ustaw ich pozycje. Aby pozwolić użytkownikowi na przeniesienie dekoratora tekstu, ustaw jego **właściwość Is Moveable.**

 Użyj narzędzia **Mapy elementu diagramu,** aby połączyć łącznik z relacją referencyjną.

 Po wybraniu mapy elementu diagramu otwórz okno **Szczegóły DSL** i otwórz **kartę Decorator Maps.**

 Wybierz każdą **właściwość Decorator** i ustaw **właściwość Display** na poprawną właściwość domeny.

 Upewnij się, że obok każdego elementu na liście **Decorators** jest wyświetlany znacznik wyboru.

### <a name="define-a-connection-builder-tool"></a>Definiowanie narzędzia Connection Builder
 W **oknie Eksplorator DSL** rozwiń węzeł **Edytor** i wszystkie jego podwęzy.

 Kliknij prawym przyciskiem myszy węzeł, który ma taką samą nazwę jak DSL, a następnie kliknij polecenie **Dodaj nowe narzędzie połączenia.**

 Po wybraniu nowego narzędzia na okno Właściwości:

- Ustaw podpis **i** **etykietkę narzędzia**.

- Kliknij **pozycję Konstruktor połączeń** i wybierz odpowiedniego konstruktora dla nowej relacji.

- Ustaw **ikonę przybornika** na ikonę, która ma być wyświetlana w przyborniku. Możesz ustawić ją na nową ikonę lub ikonę używaną już dla innego narzędzia.

     Aby utworzyć nową ikonę, otwórz katalog Dsl\Resources w **Eksplorator rozwiązań**. Skopiuj i wklej jeden z istniejących plików BMP narzędzia elementu. Zmień nazwę wklejonych kopii, a następnie kliknij dwukrotnie, aby ją edytować.

     Wróć do diagramu definicji DSL, wybierz narzędzie, a następnie na okno Właściwości **przycisk [...]** w **ikonie przybornika**. W **oknie dialogowym Wybieranie** mapy bitowej wybierz .BMP z menu rozwijanego.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Aby przetestować relację odwołania i łącznik

1. **Kliknij pozycję Przekształć** wszystkie szablony na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL.

2. **Skompilowanie i uruchomienie DSL.** Naciśnij klawisz F5 lub CTRL+F5, aby uruchomić nowe wystąpienie Visual Studio w trybie eksperymentalnym. W eksperymentalnym wystąpieniu Visual Studio otwórz lub utwórz plik z rozszerzeniem nazwy pliku DSL.

3. **Sprawdź, czy narzędzie połączenia jest wyświetlane w przyborniku.**

4. **Twórz kształty,** przeciągając je z narzędzia na diagram modelu.

5. **Tworzenie połączeń** między kształtami. Kliknij narzędzie łącznika, kliknij kształt, a następnie kliknij inny kształt.

6. **Sprawdź, czy nie można utworzyć połączeń między nieodpowiednimi klasami.** Jeśli na przykład twoja relacja znajduje się między Miastami i Artystów, sprawdź, czy nie możesz połączyć artystów z artystów.

7. **Sprawdź, czy mnożenia są poprawne. Sprawdź na przykład, czy nie można połączyć osoby z więcej niż jednym menedżerem.**

8. **Sprawdź, czy każdy dekorator tekstu jest wyświetlany i** czy:

   1. Można go edytować, chyba że dla właściwości domeny ustawiono flagę **Tylko** do odczytu interfejsu użytkownika.

   2. Podczas edytowania właściwości w okno Właściwości lub w dekoratorze jest aktualizowany drugi widok.

   Po pierwszym przetestowaniu łącznika możesz dostosować jego właściwości i dodać bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Definiowanie kształtów zawierających listy: kształty przedziałów
 Kształt przedziału zawiera co najmniej jedną listę elementów. Na przykład w bibliotece muzyki DSL można użyć kształtów przedziałów do reprezentowania muzyki Dosyć. W każdym z nich znajduje się lista Songs (Utwory).

 ![Kształt przedziału](../modeling/media/compartmentshape.png)

 W najprostszej metodzie osiągnięcia tego efektu w definicji DSL należy zdefiniować jedną klasę domeny dla kontenera i jedną klasę domeny dla każdej listy. Klasa kontenera jest mapowana na kształt przedziału.

 ![Mapa kształtów](../modeling/media/music_mapcomp.png)

 Aby uzyskać więcej informacji, [zobacz Właściwości kształtów przedziałów](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Aby zdefiniować kształt przedziału

1. **Utwórz klasę domeny kontenera**. Kliknij narzędzie **Relacja osadzania,** kliknij klasę główną modelu, a następnie kliknij pustą część diagramu definicji DSL. Powoduje to utworzenie klasy domeny o nazwie Na rysunku przykładu.

     Alternatywnie zamiast osadzania w klasie głównej można osadzić kontener w klasie domeny, która jest mapowana na tor.

     Dodaj właściwość domeny, taką jak Name, do klasy i ustaw jej flagę **Is Element Name** w okno Właściwości.

2. **Utwórz klasę domeny elementu listy**. Kliknij narzędzie **Embedding Relationship (Relacja** osadzania), kliknij klasę kontenera (Hack), a następnie kliknij pustą część diagramu. Powoduje to utworzenie klasy domeny o nazwie Song na przykładowej ilustracji.

     Dodaj właściwość domeny, taką jak Title, do klasy i ustaw jej **flagę Is Element Name.**

     Dodaj inne właściwości domeny.

     Dodaj kolejną klasę domeny elementu listy dla każdej listy, która ma być wyświetlana.

3. **Aby pomieszać kilka typów elementów na liście, utwórz** klasy dziedziczące z klasy listy. Uatrakcyjniaj klasę listy, ustawiając **jej modyfikator dziedziczenia**.

     Jeśli na przykład chcesz sortować muzyka klasyczną według kompozytorów, a nie artystów, możesz utworzyć dwie podklasy Utworu, KlasycznySong i NonClassicalSong.

4. **Utwórz kształt przedziału**. Przeciągnij element z narzędzia **Kształt przedziału** na diagram definicji DSL.

     Dodaj dekorator tekstu i ustaw jego nazwę.

     Dodaj przedział i ustaw jego nazwę.

5. Aby pozwolić użytkownikowi ukryć przedziały listy, kliknij prawym przyciskiem myszy klasę kształtu przedziału, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Expand/Collapse Decorator**. W okno Właściwości ustaw pozycję dekoratora.

6. Kliknij narzędzie **Mapa elementu diagramu,** kliknij klasę domeny kontenera, a następnie kliknij kształt przedziału.

7. Wybierz link mapy elementu diagramu między klasą domeny i kształtem. W **oknie Szczegóły DSL:**

    1. Kliknij **kartę Decorators (Dekoratory).** Kliknij nazwę dekoratora, a następnie wybierz odpowiedni element w obszarze **Display Property (Właściwość wyświetlania).** Upewnij się, że obok nazwy dekoratora jest widoczny znacznik wyboru.

    2. Kliknij **kartę Mapy przedziałów.**

         Kliknij nazwę przedziału.

         W **obszarze Ścieżka kolekcji Wyświetlane elementy** przejdź do klasy elementów listy (Song). Kliknij strzałkę listy rozwijanej, aby użyć narzędzia nawigatora.

         W **obszarze Display Property**(Właściwość wyświetlania) wybierz właściwość, która powinna być wyświetlana na liście. W tym przykładzie jest to Tytuł.

> [!NOTE]
> Korzystając z pól Ścieżki w polach mapy Decorator Map i Przedział, można utworzyć bardziej złożone relacje między klasami domeny i kształtem przedziału.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Aby zdefiniować narzędzie do tworzenia kształtu

1. **Tworzenie elementu przybornika do tworzenia elementów klasy domeny.**

2. W **Eksploratorze DSL** rozwiń węzeł **Edytor** i wszystkie jego węzły podrzędne.

3. Kliknij prawym przyciskiem myszy węzeł w obszarze **Karty przybornika,** który ma taką samą nazwę jak DSL, na przykład MusicLibrary. Kliknij **pozycję Add Element Tool (Dodaj element Tool).**

    > [!NOTE]
    > Jeśli klikniesz prawym przyciskiem myszy **węzeł Narzędzia,** narzędzie Dodaj element nie **będzie dostępne.** Zamiast tego kliknij węzeł nad nim.

4. W okno Właściwości z wybranym narzędziem nowego elementu ustaw opcję **Klasa** na klasę domeny, która została ostatnio dodana.

5. Ustaw **podpis i** **etykietkę narzędzia.**

6. Ustaw **ikonę przybornika** na ikonę, która będzie wyświetlana w przyborniku. Możesz ustawić nową ikonę lub ikonę używaną już dla innego narzędzia.

     Aby utworzyć nową ikonę, otwórz folder Dsl\Resources w **Eksplorator rozwiązań**. Skopiuj i wklej jeden z istniejących plików .BMP elementu. Zmień nazwę wklejonych kopii, a następnie kliknij dwukrotnie, aby ją edytować.

     Wróć do diagramu definicji DSL, wybierz narzędzie, a następnie na okno Właściwości **przycisk [...]** w **przyborniku Ikona**. W **oknie dialogowym Wybieranie** mapy bitowej wybierz plik BMP z menu rozwijanego.

#### <a name="to-test-a-compartment-shape"></a>Aby przetestować kształt przedziału

1. **Kliknij pozycję Przekształć** wszystkie szablony na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL.

2. **Skompilowanie i uruchomienie DSL.** Naciśnij klawisz F5 lub CTRL+F5, aby uruchomić nowe wystąpienie Visual Studio w trybie eksperymentalnym. W eksperymentalnym wystąpieniu Visual Studio otwórz lub utwórz plik z rozszerzeniem nazwy pliku DSL.

3. **Sprawdź, czy narzędzie jest wyświetlane w przyborniku.**

4. Przeciągnij narzędzie na diagram modelu. Zostanie utworzony kształt.

    Sprawdź, czy nazwa elementu jest wyświetlana i jest automatycznie ustawiana na wartość domyślną.

5. Kliknij prawym przyciskiem myszy nagłówek nowego kształtu, a następnie kliknij pozycję Dodaj *element listy.* W tym przykładzie polecenie to Dodaj utwór.

    Sprawdź, czy element znajduje się na liście i ma nową nazwę.

6. Kliknij jeden z elementów listy, a następnie sprawdź, okno Właściwości. Powinny zostać wyświetlony właściwości elementów listy.

7. Otwórz Eksploratora języka. Sprawdź, czy widzisz węzły kontenera z węzłami elementów listy wewnątrz.

   ![Wygenerowany eksplorator DSL](../modeling/media/music_explorer.png)

   Po pierwszym przetestowaniu kształtu przedziału warto dostosować niektóre z jego właściwości i dodać bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Wyświetlanie linku odwołania w przedziale
 Zazwyczaj element wyświetlany w przedziale jest elementem podrzędnym elementu reprezentowanego przez kształt przedziału. Jednak czasami chcesz wyświetlić element, który jest z nim połączony za pomocą relacji odwołania.

 Na przykład możemy dodać drugi przedział do aplikacji ListShape, który wyświetla listę artystów połączonych z Listą.

 W takim przypadku przedział powinien wyświetlać link, a nie element, do których się odwołuje. Dzieje się tak, ponieważ gdy użytkownik wybierze element w przedziale i naciśnie klawisz DELETE, chcesz usunąć link, a nie element, do którego się odwołuje.

 Niemniej jednak w przedziale może być wyświetlana nazwa przywołynego elementu.

 W poniższej procedurze przyjęto założenie, że utworzono już klasę domeny, relację odwołania, kształt przedziału i mapę elementu diagramu, zgodnie z opisem we wcześniejszej części tej sekcji.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Aby wyświetlić link odwołania w przedziale

1. **Dodaj przedział do kształtu przedziału**. Na diagramie definicji DSL kliknij prawym przyciskiem myszy klasę kształtu przedziału, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Przedział**.

2. Ustaw **ścieżkę kolekcji Wyświetlane elementy,** aby przejść do linku zamiast do jego elementu docelowego. Kliknij menu rozwijane i użyj widoku drzewa, aby wybrać relację odwołania zamiast jej elementu docelowego. W tym przykładzie relacja to **ArtistAppearedOnAlbums**.

3. Ustaw **właściwość Ścieżka na Display,** aby nawigować z linku do elementu docelowego. W tym przykładzie jest to **Artist**.

4. Ustaw **właściwość Display na** odpowiednią właściwość elementu docelowego, na przykład **Name**.

5. **Przekształć wszystkie** szablony, skompilować i uruchomić DSL, a następnie otwórz model testowy.

6. Na diagramie modelu utwórz odpowiednie klasy kształtu, ustaw ich nazwy i utwórz połączenie między nimi. W kształcie przedziału powinny pojawić się nazwy połączonych elementów.

7. Wybierz link lub element w kształcie przedziału. Zarówno link, jak i element powinny zniknąć.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Definiowanie portów na granicy innego kształtu
 Port to kształt, który znajduje się na granicy innego kształtu.

 Porty mogą również służyć do zapewnienia stałego punktu połączenia na innym kształcie, do którego użytkownik może rysować łączniki. W takim przypadku można sprawić, że kształt portu będzie przezroczysty.

 Aby wyświetlić przykład, który używa portów, wybierz szablon **Diagram składników** podczas tworzenia nowego rozwiązania DSL. W tym przykładzie przedstawiono główne kwestie, które można wziąć pod uwagę podczas definiowania portów:

- Istnieje klasa domeny, która reprezentuje kontener portów `Component` .

- Istnieje klasa domeny, która reprezentuje porty. w tym przykładzie jest to `ComponentPort`.

- Istnieje relacja osadzania z klasy domeny kontenera do klasy domeny portu. Aby uzyskać więcej informacji, zobacz [Definiowanie klas domeny](#classes).

- Jeśli chcesz, aby różne typy portów były mieszane w tym samym kontenerze, możesz utworzyć podklasy klasy domeny portu. W tym przykładzie `InPort` i `OutPort` dziedziczą po `ComponentPort` .

- Klasę domeny kontenera można mapować na dowolny kształt. W tym przykładzie jest to `ComponentShape` . Aby uzyskać więcej informacji, zobacz [Definiowanie kształtów](#shapes).

- Klasy domen portów są mapowane na kształty portów. Klasy pochodne można mapować w celu oddzielenia klas kształtów portów lub zamapować klasę bazową na jedną klasę kształtu portu.

  Pod innymi względami kształty portów zachowują się zgodnie z opisem w [definiowaniu kształtów](#shapes).

  Aby uzyskać więcej informacji, [zobacz Właściwości kształtów portów](../modeling/properties-of-port-shapes.md).

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Definiowanie DSL, który ma tory
 Tory to pozioma lub pionowa partycja diagramu. Każdy tor odpowiada elementowi modelu. Definicja DSL wymaga jednej klasy domeny dla elementów torów.

 Najlepszym sposobem utworzenia DSL z torami jest utworzenie nowego rozwiązania DSL i wybranie szablonu rozwiązania przepływu zadań. W definicji DSL klasa Aktor jest klasą domeny zamapowana na tor. Zmień nazwę tej klasy i innych klas na dopasowane do projektu.

 Aby dodać klasę, która będzie wyświetlana jako kształt wewnątrz torów, utwórz relację osadzania między klasą torów a nową klasą. Użytkownicy będą mogli przeciągać elementy z jednego toru do innego, ale każdy element zawsze będzie się znajduje w określonym torysie. W szablonie rozwiązania przepływu zadań FlowElement jest elementem podrzędnym klasy torów.

 Aby dodać klasę, która będzie wyświetlana jako kształt niezależnie od torów, utwórz relację osadzania między klasą główną a nową klasą. Użytkownicy będą mogli umieszczać te kształty w dowolnym miejscu na diagramie, w tym w granicach torów i poza torami. W szablonie rozwiązania przepływu zadań komentarz jest podrzędnym klasy głównej.

 Aby uzyskać więcej informacji, [zobacz Właściwości torów](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Dodawanie typów właściwości

### <a name="domain-enumerations-and-literals"></a>Wyliczenia i literały domeny
 Wyliczenie domeny jest typem z kilkoma wartościami literału.

 Aby dodać wyliczenie domeny, kliknij prawym przyciskiem myszy katalog główny modelu w Eksploratorze **DSL,** a następnie kliknij polecenie **Dodaj nowe wyliczenie domeny.** Element pojawi się w Eksploratorze **DSL w** **węźle Typy** domen. Ten element nie jest wyświetlany na diagramie.

 Aby dodać literały wyliczenia do wyliczenia domeny, kliknij prawym przyciskiem myszy wyliczenie domeny w Eksploratorze **DSL,** a następnie kliknij polecenie Dodaj nowy **literał wyliczenia**.

 Domyślnie właściwość, która ma typ wyliczenia, może być ustawiona na tylko jedną wartość wyliczenia na raz. Jeśli chcesz, aby użytkownicy i programiści mogli ustawić dowolną kombinację wartości — "pole bitowe" — ustaw właściwość **IsFlags** wyliczenia.

### <a name="external-types"></a>Typy zewnętrzne
 Jeśli ustawisz typ właściwości domeny, jeśli nie znajdziesz typu,  który ma być na liście rozwijanej Typ, możesz dodać typ zewnętrzny. Na przykład można dodać typ **System.Drawing.Color** do listy.

 Aby dodać typ, kliknij prawym przyciskiem myszy katalog główny modelu w Eksploratorze DSL, a następnie kliknij polecenie **Dodaj nowy typ zewnętrzny.** W okno Właściwości ustaw nazwę na **Color,** a przestrzeń nazw na **System.Drawing**. Ten typ jest teraz wyświetlany w Eksploratorze DSL w **obszarze Typy domen.** Możesz wybrać ją za każdym razem, gdy ustawisz typ właściwości domeny.

## <a name="customizing-the-dsl"></a><a name="custom"></a> Dostosowywanie DSL
 Korzystając z technik opisanych w tym temacie, można szybko utworzyć DSL z notacją diagramu, czytelnym formularzem XML i podstawowymi narzędziami, które są wymagane do generowania kodu i innych artefaktów.

 Istnieją dwie metody rozszerzania definicji DSL:

1. Dostosuj DSL przy użyciu więcej funkcji definicji DSL. Można na przykład utworzyć jedno narzędzie łącznika, które może utworzyć kilka typów łączników, i kontrolować reguły, za pomocą których usunięcie jednego elementu powoduje również usunięcie powiązanych elementów. Te techniki są osiągane głównie przez ustawienie wartości w definicji DSL, a niektóre wymagają kilku wierszy kodu programu.

     Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Rozszerzanie narzędzi modelowania przy użyciu kodu programu w celu osiągnięcia bardziej zaawansowanych efektów. Można na przykład tworzyć polecenia menu, które mogą zmieniać model, oraz narzędzia, które integrują co najmniej dwa pliki DSL. VmSDK zaprojektowano specjalnie, aby ułatwić integrowanie rozszerzeń z kodem wygenerowanym na podstawie definicji DSL.  Aby uzyskać więcej informacji, zobacz Writing Code to Customize a Domain-Specific Language (Pisanie kodu [w celu dostosowania Domain-Specific języku ).](../modeling/writing-code-to-customise-a-domain-specific-language.md)

### <a name="changing-the-dsl-definition"></a>Zmienianie definicji DSL
 Podczas tworzenia dowolnego elementu w definicji DSL wiele wartości domyślnych jest ustawianych automatycznie. Po ich skonfigurowaniu można je zmienić. Upraszcza to tworzenie DSL, jednocześnie umożliwiając zaawansowane dostosowania.

 Na przykład podczas mapowania kształtu na element ścieżka elementu nadrzędnego mapowania jest ustawiana automatycznie zgodnie z relacją osadzania klasy domeny. Jeśli jednak później zmienisz relację osadzania, ścieżka elementu nadrzędnego nie zostanie zmieniona automatycznie.

 W związku z tym należy pamiętać, że w przypadku zmiany niektórych relacji w definicji DSL nie jest niczym niezwykłym, że błędy będą zgłaszane podczas zapisywania definicji lub przekształcania wszystkich szablonów. Większość tych błędów można łatwo naprawić. Kliknij dwukrotnie raport o błędach, aby wyświetlić lokalizację błędu.

 Zobacz również [temat Jak zmienić przestrzeń nazw Domain-Specific języku](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="troubleshooting"></a><a name="trouble"></a> Rozwiązywanie problemów
 W poniższej tabeli wymieniono niektóre z najbardziej typowych problemów, które występują podczas projektowania DSL, wraz z sugestiami dla ich rozwiązania. Więcej porad można uzyskać na forum rozszerzalności narzędzi [wizualizacji](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

| Problem | Sugestia |
|-|-|
| Zmiany wprowadzone w pliku definicji DSL nie mają żadnego efektu. | Kliknij **pozycję Przekształć wszystkie** szablony na pasku narzędzi powyżej Eksplorator rozwiązań, a następnie ponownie skompilować rozwiązanie. |
| Kształty pokazują nazwę dekoratora zamiast wartości właściwości. | Skonfiguruj mapowanie dekoratora. Na diagramie definicji DSL kliknij mapę elementu diagramu, która jest szarą linią między klasą domeny i klasą kształtu.<br /><br /> Otwórz okno **Szczegóły DSL.** Jeśli go nie widzisz, w menu Widok wskaż pozycję **Inne okna,** a następnie kliknij pozycję **Szczegóły DSL.**<br /><br /> Kliknij **kartę Decorator Maps (Mapy** dekoratora). Wybierz nazwę dekoratora. Upewnij się, że pole obok niego jest zaznaczone. W **obszarze Właściwość** wyświetlania wybierz nazwę właściwości domeny.<br /><br /> Aby uzyskać więcej informacji, zobacz [Kształty na diagramie](#shapes). |
| W Eksploratorze DSL nie mogę dodać do kolekcji. Na przykład po kliknięciu prawym przyciskiem myszy pozycji Narzędzia w menu nie ma polecenia "Dodaj narzędzie".<br /><br /> W eksploratorze dla mojego DSL nie mogę dodać elementu do listy. | Kliknij prawym przyciskiem myszy element nad węzłem, który próbujesz. Jeśli chcesz dodać do listy, dodaj polecenie nie znajduje się w węźle listy, ale w jego właścicielu. |
| Utworzono klasę domeny, ale nie można utworzyć wystąpień w eksploratorze języka. | Każda klasa domeny z wyjątkiem głównej musi być elementem docelowym relacji osadzania. |
| W eksploratorze dla mojego DSL elementy są wyświetlane tylko z ich nazwami typów. | W definicji DSL wybierz właściwość domeny klasy , a w okno Właściwości ustaw wartość True dla właściwości **Is Element Name.** |
| Mój DSL zawsze otwiera się w edytorze XML. | Może się to zdarzyć z powodu błędu podczas odczytywania pliku. Jednak nawet po naprawieniu tego błędu musisz jawnie zresetować edytor, aby był projektantem DSL.<br /><br /> Kliknij prawym przyciskiem myszy element projektu, kliknij polecenie **Otwórz za pomocą** i wybierz pozycję *YourLanguage* Designer **(Domyślnie)**. |
| Przybornik mojego DSL nie jest wyświetlany po zmianie nazw zestawu. | Sprawdź i zaktualizuj **pakiet DslPackage\GeneratedCode\Package.tt** Aby uzyskać więcej informacji, zobacz Jak zmienić przestrzeń nazw [Domain-Specific języku](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| Przybornik mojego DSL nie jest wyświetlany, ale nie zmieniono nazwy zestawu.<br /><br /> Lub zostanie wyświetlone okno komunikatu z raportem o niepowodzeniu załadowania rozszerzenia. | Zresetuj wystąpienie eksperymentalne i ponownie skompilować rozwiązanie.<br /><br /> 1. Na stronie Menu Start Windows w obszarze Wszystkie programy rozwiń pozycję , a następnie pozycję Narzędzia, a następnie kliknij [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] pozycję  **Resetuj Microsoft Visual Studio wystąpienie eksperymentalne.**<br />2. W menu **Build (Kompilacja)** kliknij pozycję **Rebuild Solution (Skompilowanie rozwiązania).** |

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do języków specyficznych dla domeny](../modeling/getting-started-with-domain-specific-languages.md)
- [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)
