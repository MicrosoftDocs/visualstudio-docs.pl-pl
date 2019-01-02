---
title: 'Porady: definiowanie języka właściwego dla domeny'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 7e99e37f99d067356d24e2808754696dc233e50f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959498"
---
# <a name="how-to-define-a-domain-specific-language"></a>Porady: definiowanie języka właściwego dla domeny
Aby zdefiniować języka specyficznego dla domeny (DSL), należy utworzyć rozwiązanie programu Visual Studio z szablonu. Kluczowym elementem rozwiązania jest diagramem definicji DSL, który jest przechowywany w DslDefinition.dsl. W definicji DSL definiuje klasy i kształty język DSL. Po zmodyfikowaniu i dodawane do tych elementów, można dodać kod programu, aby dostosować DSL bardziej szczegółowo.

Jeśli jesteś nowym użytkownikiem językami DSL, firma Microsoft zaleca pracy za pośrednictwem **laboratorium narzędzia DSL**, która znajduje się w tej lokacji: [Visualizaton i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Wybieranie szablonu rozwiązania
 Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| Visual Studio Visualisation i Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Aby utworzyć nowego języka specyficznego dla domeny, należy utworzyć nowe rozwiązanie Visual Studio przy użyciu szablonu projektu języka specyficznego dla domeny.

#### <a name="to-create-a-dsl-solution"></a>Aby utworzyć rozwiązanie DSL

1. Tworzenie rozwiązań za pomocą **Domain-Specific Language** szablonu, który znajduje się w obszarze **inne typy/rozszerzalności projektów** w **nowy projekt** okno dialogowe.

    ![Tworzenie okna dialogowego DSL](../modeling/media/create_dsldialog.png)

    Po kliknięciu **OK**, **kreatora języka specyficznego dla domeny** otwiera i wyświetla listę rozwiązań DSL szablonu.

2. Kliknij każdy szablon, aby wyświetlić opis. Wybierz rozwiązanie, które najbardziej przypomina ma zostać utworzona.

    Każdy szablon DSL definiuje działającego podstawowe DSL. Trzeba edytować tego języka DSL w celu dopasowania do własnych wymagań.

    Kliknij każdy przykład, aby uzyskać więcej informacji.

   -   Wybierz **przepływu zadań** utworzyć DSL, który ma ścieżek. Tory są pionowych lub poziomych partycji diagramu.

   -   Wybierz **modeli składnika** utworzyć DSL, który ma portów. Porty są małe kształty na krawędzi większy kształt.

   -   Wybierz **diagramów klas** do definiowania DSL, który ma kształtów przedziałów. Kształty przedziału zawierają listy elementów.

   -   Wybierz **minimalny języka** w innych przypadkach lub sprawdzić.

   -   Wybierz **minimalny projektanta formularza systemu Windows** lub **minimalny WPF Designer** utworzyć DSL, który jest wyświetlany na powierzchni Windows Forms i WPF. Należy napisać kod, aby zdefiniować edytora. Więcej informacji znajduje się w następujących tematach:

        [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Wprowadź rozszerzenie nazwy pliku DSL w odpowiedniej strony w kreatorze. To rozszerzenie, używanego przez pliki zawierające wystąpienia elementu DSL.

   -   Wybierz rozszerzenie nazwy pliku, który nie jest skojarzony z każdą aplikacją na komputerze lub w dowolnym komputerze, na którym chcesz zainstalować język DSL. Na przykład **docx** i **htm** będzie niedopuszczalne pliku rozszerzenia nazw.

   -   Kreator wyświetli ostrzeżenie, jeśli jest używane rozszerzenie, które zostały wprowadzone jako języka DSL. Należy rozważyć użycie innym rozszerzeniem nazwy pliku. Możesz także zresetować Visual Studio SDK eksperymentalne wystąpienie wyczyszczenie stare projektantów eksperymentalne. Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, a następnie **resetowania firmy Microsoft Wystąpienie programu Visual Studio 2010 eksperymentalne**.

4. Możesz dostosować ustawienia na innych stronach lub pozostaw wartości domyślne.

5. Kliknij przycisk **Zakończ**.

    Kreator utworzy rozwiązanie, które zawiera dwa lub trzy projekty i generuje kod w definicji DSL.

   Interfejs użytkownika jest teraz podobny do poniższej ilustracji.

   ![Projektant DSL](../modeling/media/dsl_designer.png)

   To rozwiązanie definiuje języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [omówienie interfejsu użytkownika narzędzi języka specyficznego dla domeny](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testowanie rozwiązania
 Szablon rozwiązania zawiera działającego DSL, który można zmodyfikować lub użyć, ponieważ jest.

 Aby przetestować rozwiązanie, naciśnij klawisz F5 lub CTRL + F5. Nowe wystąpienie programu Visual Studio zostanie otwarty w trybie doświadczalnym.

 Nowe wystąpienie programu Visual Studio w Eksploratorze rozwiązań Otwórz plik przykładowy. Spowoduje to otwarcie jako diagram, za pomocą przybornika.

 Jeśli uruchamianie rozwiązania, które utworzono z **minimalny języka** szablonu, eksperymentalne programu Visual Studio będzie wyglądać następująco:

 ![](../modeling/media/dsl_min.png)

 Poeksperymentuj z narzędzia. Tworzenie elementów i łączyć je.

 Zamknij wystąpienie doświadczalne programu Visual Studio.

> [!NOTE]
>  Nie będzie można wyświetlić kształty, na przykład plik testu, modyfikacji język DSL. Jednak można utworzyć nowych elementów.

### <a name="modifying-the-template-dsl"></a>Modyfikowanie szablonu DSL
 Zmień nazwę i zachować niektóre lub wszystkie z klasami domeny i kształt klasy w szablonie definicji DSL. Nowe nazwy klasy powinna być prawidłowych nazw środowiska CLR, bez spacji i znaków przestankowych.

 Jest to szczególnie przydatne zachować te klasy:

- Klasa główna pojawia się w lewym górnym rogu z diagramem definicji DSL, w obszarze **klasy i relacje**. Zmień jej nazwę na inny niż język DSL. Na przykład DSL o nazwie **MusicLibrary** może być klasą główną o nazwie **utworów muzycznych**.

- Klasa diagram jest wyświetlany w prawym dolnym rogu z diagramem definicji DSL w **elementów diagramu** kolumny. Trzeba będzie przewinąć w prawo, aby zobaczyć, że. Jest typowo nazwana _YourDsl_**Diagram**.

- Jeśli użyto **przepływu zadań** szablonu i chcesz utworzyć diagramy za pomocą ścieżek, przechowywać i Zmień nazwę klasy domeny aktora i kształt ActorSwimlane.

  Usuń lub zmień innych klas ze swoimi potrzebami.

## <a name="patterns"></a> Wzorce do definiowania języka DSL
 Firma Microsoft zaleca tworzenie DSL, dodając lub dostosowania jednego lub dwóch funkcji w danym momencie. Dodaj funkcję, uruchom język DSL i przetestować go, a następnie dodaj jeden lub dwa więcej funkcji. Typowa funkcja DSL może być:

- Klasy domeny relacji osadzania, która łączy elementu modelu, kształt, wymagany, aby wyświetlić elementy tej klasy w diagramie i narzędzia elementu, który umożliwia użytkownikom tworzenie elementów.

- Właściwości domeny klasy domeny i dekoratory, zawierające je na kształcie.

- Relacja odwołania i łącznik, który wyświetla na diagramie i narzędzia łącznika, który pozwala użytkownikom tworzyć łącza.

- Możliwość dostosowania, który wymaga kod programu, takie jak polecenie menu lub ograniczenia sprawdzania poprawności.

  Poniżej opisano sposób tworzenia najbardziej przydatne rodzaju funkcje języka DSL. Istnieje wiele innych wzorców za pomocą których można skonstruować DSL, ale są one używane najczęściej.

> [!NOTE]
>  Po dodaniu funkcji, nie zapomnij kliknąć **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań, przed kompilowanie i uruchamianie DSL.

 Na poniższej ilustracji przedstawiono klasy i relacje część DSL, który służy jako przykład w tym temacie.

 ![Relacji osadzania i dokumentacja](../modeling/media/music_classes.png)

 Następny rysunek jest przykładowy model tego języka DSL:

 ![Wystąpienie modelu DSL wygenerowany](../modeling/media/music_instance.png)

> [!NOTE]
>  "Model" odnosi się do wystąpienia użytkownikom tworzenie, która zwykle jest wyświetlany jako diagram DSL. W tym temacie omówiono diagramem definicji DSL i diagramy modelu, które są wyświetlane, gdy jest używana DSL.

## <a name="classes"></a> Definiowanie klas domeny
 Klasy domeny reprezentują koncepcji DSL. Wystąpienia są *elementów modelu*. Na przykład w **MusicLibrary** DSL może być klasami domeny o nazwie **albumu** i **utworu**.

 Aby utworzyć klasę domeny, można przeciągnąć z **klasy domeny o nazwie** narzędzia do diagramu, a następnie zmień nazwę klasy.

 Aby uzyskać więcej informacji, zobacz [właściwości klas domeny](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Tworzenie relacji osadzania dla każdej klasy domeny
 Każda klasa domeny, z wyjątkiem klasy głównego musi być elementem docelowym co najmniej jedna relacja osadzania lub ten typ musi dziedziczyć z klasy, która jest lokalizacją docelową relacji osadzania.

 W modelu każdy element modelu jest węzłem w jedno drzewo relacji osadzania. Źródłowy i docelowy relacji osadzania są często nazywane nadrzędnymi i podrzędnymi.

 Wybór elementu nadrzędnego dla klasy domeny zależy od tego, jak mają okresy istnienia jego elementy, aby była zależna od innych elementów. Jeśli węzeł drzewa zostanie usunięty, jego poddrzewa zwykle jest również usunięte. W związku z tym osadzono klas elementów, które mają niezależne istnienia bezpośrednio w ramach klasy głównej.

 Zwykle jeśli element wewnątrz innego elementu są wyświetlane, chcesz wskazać relacji właściciela. W takiej sytuacji najbardziej odpowiedniej klasie nadrzędnej jest klasą kontenera. Wyjątek to w rzeczywistości po prostu łącze odwołania do elementu niezależnie od elementu, który zostanie wyświetlony w kontenerze. W takim przypadku usunięcie kontenera spowoduje usunięcie odwołania, ale nie jego element docelowy.

 We wzorcach definicji DSL opisane w tym temacie założono spowoduje, że elementów wyświetlanych w kontenerze zostaną usunięte po usunięciu kontenera. Bardziej złożone są możliwe i schematy można osiągnąć, definiując zasady.

|Sposób wyświetlania elementu|Klasa nadrzędna (osadzanie)|Przykład szablonu rozwiązania dotyczącego języka DSL|
|-|-|-|
|Kształt na diagramie.<br /><br /> Swimlane.|Klasa główna DSL.|Minimalny język.<br /><br /> Przepływ zadań: Klasa aktora.|
|Kształt w toru.|Klasa domeny elementów, które są wyświetlane jako ścieżek.|Przepływ zadań: Klasa zadania.|
|Element na liście w kształcie, gdy element zostanie usunięty po usunięciu kontenera.<br /><br /> Port na krawędzi kształtu.|Klasa domeny, która jest mapowana na kształt kontenera.|Diagram klasy: Klasy atrybutu.<br /><br /> Diagram składników: Klasa portu.|
|Element na liście, nie zostanie usunięty po usunięciu kontenera.|Klasa główna DSL.<br /><br /> Na liście zostaną wyświetlone linki odwołań.||
|Nie bezpośrednio wyświetlane.|Klasy, które wchodzi w skład części.||

 W tym przykładzie biblioteka utworów muzycznych albumy są wyświetlane jako prostokątów, w których tytuły utwory są wyświetlane. W związku z tym elementem nadrzędnym albumu jest klasą głównego utworów muzycznych, a element nadrzędny utwór jest albumu.

 Aby utworzyć klasę domeny i osadzanie w tym samym czasie, kliknij przycisk **relacji osadzania** narzędzia, a następnie kliknij klasy nadrzędnej, a następnie kliknij pustą część diagramu.

 Nie jest zazwyczaj konieczne dopasować nazwę relacji osadzania i jego role, ponieważ ich będzie automatycznie śledzić nazwy klas.

 Aby uzyskać więcej informacji, zobacz [właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i [ról właściwości domeny](../modeling/properties-of-domain-roles.md).

> [!NOTE]
>  Osadzanie nie jest taka sama jak dziedziczenie. Elementy podrzędne w relacji osadzania dziedziczy funkcje z obiektów nadrzędnych.

### <a name="add-domain-properties-to-each-domain-class"></a>Dodawanie właściwości domeny do każdej klasy domeny
 Właściwości domeny przechowywać wartości. Oto przykłady: Nazwa, nazwa, Data publikacji.

 Kliknij przycisk **właściwości domeny** w klasie, naciśnij klawisz ENTER, a następnie wpisz nazwę właściwości. Domyślny typ właściwości domeny jest ciąg. Jeśli chcesz zmienić typ, wybierz właściwość domeny i ustaw **typu** w **właściwości** okna. Jeśli typ, który ma nie znajduje się na liście rozwijanej, zobacz [dodanie typów właściwości](#addTypes).

 **Ustaw właściwość nazwy elementu.** Wybierz właściwość domeny, który może służyć do identyfikowania elementów w Eksploratorze języka. Na przykład w klasie utworu domeny, możesz określić właściwości domain tytuł. W **właściwości** oknie **jest nazwa elementu** do `true`.

### <a name="create-derived-domain-classes"></a>Tworzenie klas pochodnych domeny
 Klasy domeny mają wariantów, które dziedziczą jej właściwości i relacje, utworzyć klasy, które wynikają z niego. Na przykład albumu może mieć klasy pochodne WMA i MP3.

 Tworzenie przy użyciu klasy pochodnej **klasy domeny** narzędzia.

 Kliknij przycisk **dziedziczenia** narzędzia, kliknij przycisk klasy pochodnej, a następnie kliknij klasy bazowej.

 Rozważ ustawienie **modyfikator dziedziczenia** klasy bazowej do **abstrakcyjne**. Jeśli Twoim zdaniem, możesz potrzebować wystąpień klasy bazowej, należy wziąć pod uwagę zamiast tworzenia oddzielnego pochodne klasy dla nich.

 Klasy pochodne dziedziczą właściwości i ról z ich klasami podstawowymi.

### <a name="tidy-the-dsl-definition-diagram"></a>Porządek diagramem definicji DSL
 Po dodaniu relacje, niektóre z Twoich zajęciach pojawi się w więcej niż jednym miejscu. Aby zmniejszyć liczbę wystąpień i szersze diagramu, kliknij prawym przyciskiem myszy klasę docelową relacji, a następnie kliknij przycisk **przenieść drzewa w tym miejscu**. Przeciwny efektu, kliknij prawym przyciskiem myszy klasę docelową relacji i kliknij przycisk **Podziel drzewo**. Jeśli nie ma tych poleceń menu, upewnij się, że wybrano tylko klasy domeny.

 Aby przesunąć kształt klasy i klas domeny, należy użyć klawiszy CTRL + Strzałka w górę i CTRL + Strzałka w dół.

### <a name="test-the-domain-classes"></a>Testowanie klas domeny

##### <a name="to-test-the-new-domain-classes"></a>Aby przetestować nowe klasy domeny

1.  **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań, aby wygenerować kod projektanta DSL. Możesz zautomatyzować ten krok. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować Przekształć wszystkie szablony](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2.  **Twórz i uruchamiaj język DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie doświadczalnym. W doświadczalnym wystąpieniu programu Visual Studio Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3.  **Otwórz Eksploratora.** Na stronie diagramu jest okna Eksploratora języka, który zazwyczaj jest on nazywany *YourLanguage* Explorer. Jeśli nie widzisz tego okna, może to być na karcie poniżej obszaru Eksploratora rozwiązań. Jeśli nie możesz znaleźć go na **widoku** menu, wskaż **Windows inne**, a następnie kliknij przycisk *YourLanguage* **Explorer**.

     Eksplorator usługi przedstawia widok drzewa modelu.

4.  **Tworzenie nowych elementów.** Kliknij prawym przyciskiem myszy węzeł główny u góry, a następnie kliknij przycisk **Dodaj nowe**_YourClass_.

     Nowe wystąpienie klasy pojawia się w Twoim języku Eksploratora.

5.  Sprawdź, czy każde wystąpienie ma pod inną nazwą, podczas tworzenia nowych wystąpień. Będzie to miało miejsce tylko wtedy, gdy zostały ustawione **jest nazwa elementu** flagi na właściwością domeny.

6.  **Sprawdź właściwości domeny. Przy użyciu wystąpienia klasy zaznaczone** Sprawdź okno właściwości. Właściwości domeny, które zostały zdefiniowane dla tej klasy domeny powinny być widoczne.

7.  **Zapisz plik, zamknij go i otwórz go ponownie**. Wszystkie wystąpienia utworzone powinny być widoczne w Eksploratorze, po rozwinięciu węzłów.

## <a name="shapes"></a> Definiowanie kształtów na diagramie
 Można zdefiniować klasy elementy, które pojawiają się na diagramie jako prostokątów, wielokropek lub ikony.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Aby zdefiniować klasę elementów, które są wyświetlane jako kształtów na diagramie

1. **Definiowanie i przetestować klasy domeny, zgodnie z opisem w**[Definiowanie klas domeny](#classes) **.**

   -   Element nadrzędny klasy powinna być klasy głównego. Oznacza to powinien istnieć relacja osadzania między klasą głównego i nową klasę domeny.

   -   Jeśli diagramu ma torów, element nadrzędny może być klasy domeny, który jest mapowany tor. Przed kontynuowaniem tej procedury, zobacz [Definiowanie DSL, który ma torów](#swimlanes).

2. **Dodaj klasę kształtu** reprezentujące elementy na diagram modelu. Przeciągnij jeden z następujących narzędzi na diagramem definicji DSL:

   - **Kształt geometryczny** zapewnia prostokąta lub elipsy.

   - **Obraz kształtu** Wyświetla obraz, który należy podać.

   - **Przedział kształtu** jest prostokąt, który zawiera jedną lub więcej list elementów.

     Zmień nazwę klasy kształtu, który pojawi się po prawej stronie diagramem definicji DSL, w obszarze kształtów i łączników.

3. **Zdefiniuj obraz, jeśli utworzono kształt obrazu**.

   1.  Utwórz plik obrazu, o dowolnym rozmiarze. BMP, JPEG, GIF i EMF formaty są obsługiwane.

   2.  W Eksploratorze rozwiązań Dodaj plik do rozwiązania w folderze Dsl\Resources.

   3.  Wróć do diagramem definicji DSL i wybierz nową klasę kształtu obrazu.

   4.  W oknie dialogowym właściwości kliknij **obraz** właściwości.

   5.  W **wybierz obraz** okna dialogowego kliknij menu rozwijane w obszarze **nazwy pliku**i wybierz obraz.

4. **Dodaj dekoratorów tekstu do kształtu, aby wyświetlić właściwości domeny.**

    Aby wyświetlić nazwę lub tytuł elementu modelu, niezbędny będzie co najmniej jeden dekorator tekstu.

    Kliknij prawym przyciskiem myszy nagłówek klasę kształtu, wskaż opcję **Dodaj**, a następnie kliknij przycisk **Dekoratora tekstu**. Ustaw nazwę dekoratora, a w zestawie okna właściwości jego **pozycji**.

5. **Połącz wszystkie kształty z mapowanie elementu diagramu, do klasy domeny, która powinna zostać wyświetlona**.

    Kliknij przycisk **mapowanie elementu diagramu** narzędzia, a następnie kliknij klasy domeny, a następnie klasy kształtu.

6. **Właściwości są mapowane na dekoratorów tekstu.**

   1. Wybierz szara linia między klasą domeny i Klasa kształtu, która reprezentuje mapowanie elementu diagramu.

   2. W **szczegóły języka DSL** okna, kliknij przycisk **mapy Dekoratora** kartę. Jeśli nie widzisz **szczegóły języka DSL** okna na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **szczegóły języka DSL**. Jest to często konieczne zgłoszenie górnej części tego okna, aby wyświetlić jego zawartość.

   3. Wybierz nazwę dekoratora. W obszarze **Właściwość wyświetlania**, wybierz nazwę właściwości klasy domeny. Powtórz tę czynność dla każdego elementu decorator.

       Jeśli chcesz wyświetlić właściwości elementu powiązane, kliknij przycisk Nawigator drzewo listy rozwijanej w obszarze **cieżka do właściwości wyświetlania**.

   4. Upewnij się, że jest wyświetlany znacznik wyboru obok nazwy dekoratora.

      ![W oknie mapowań kształtów i szczegóły języka DSL](../modeling/media/dsldetailswindow.png)

7. **Ustaw element przybornika do tworzenia elementów klasy domeny.**

   1.  W **Eksplorator DSL**, rozwiń węzeł **edytora** węzła i wszystkich jego węzłów podrzędnych.

   2.  Kliknij prawym przyciskiem myszy węzeł w węźle **karty przybornika** który ma taką samą nazwę jak DSL, na przykład MusicLibrary. Kliknij przycisk **narzędzie elementu Dodawanie**.

       > [!NOTE]
       >  Kliknięcie prawym przyciskiem myszy **narzędzia** węzła, nie będzie mógł przeglądać **narzędzia elementu Dodawanie**. Zamiast tego kliknij węzeł powyżej.

   3.  W oknie dialogowym właściwości nowego elementu wybierz narzędzie, należy ustawić **klasy** do klasy domeny, która została ostatnio dodana.

   4.  Ustaw **podpis** i **etykietki narzędzia**.

   5.  Ustaw **ikonę przybornika** ikonę, która będzie wyświetlana w przyborniku. Można ustawić go na nową ikonę lub ikony już używana dla innego narzędzia.

        Aby utworzyć nową ikonę, otwórz Dsl\Resources w **Eksploratora rozwiązań**. Skopiuj i Wklej jeden z istniejących plików BMP narzędzia elementu. Zmień nazwę kopii wklejonych, a następnie kliknij dwukrotnie, aby go edytować.

        Wróć do diagramem definicji DSL, wybierz narzędzie i w oknie dialogowym właściwości kliknij **[...]**  w **ikonę przybornika**. W **Wybierz mapę bitową** okno dialogowe, wybierz użytkownika. Plik BMP z menu rozwijanego.

   Aby uzyskać więcej informacji, zobacz [właściwości kształtów geometrycznych](../modeling/properties-of-geometry-shapes.md) i [właściwości kształtów obrazu](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Aby przetestować kształtów

1. **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań, aby wygenerować kod projektanta DSL.

2. **Twórz i uruchamiaj język DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie doświadczalnym. W doświadczalnym wystąpieniu programu Visual Studio Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Sprawdź, czy narzędzia elementu są wyświetlane w przyborniku.**

4. **Tworzyć kształty** , przeciągając przy użyciu narzędzia na diagram modelu.

5. **Sprawdź, czy każdy dekorator tekst jest wyświetlany,** oraz że:

   1.  Można edytować go, o ile nie zostało ustawione **jest interfejs użytkownika tylko do odczytu** flagi dla właściwości domeny.

   2.  Podczas edytowania właściwości w oknie dialogowym właściwości lub w dekoratorze innych widokach jest aktualizowana.

   Po przetestowaniu najpierw kształtu, można dostosować niektóre jej właściwości i dodać niektóre bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Definiowanie relacji odwołania
 Można zdefiniować relacji między wszystkie klasy domeny źródłowej, a wszystkie klasy domeny docelowej. Relacje odniesienia zazwyczaj są wyświetlane na diagramie jako łączniki, które linie między kształtami.

 Na przykład jeśli utworów muzycznych albumy i artystów są wyświetlane jako kształtów na diagramie, można zdefiniować relacji o nazwie ArtistsAppearedOnAlbums, który stanowi łącze artystów do albumów, na których mający doświadczenie. Zobacz przykład pokazany na rysunku.

 ![Wystąpienie modelu DSL wygenerowany](../modeling/media/music_instance.png)

 Relacje odniesienia można też połączyć elementy tego samego typu. Na przykład w DSL, reprezentujący drzewa rodziny, relacja elementów nadrzędnych i podrzędnych ich jest relacja odwołania różnych osób.

### <a name="define-a-reference-relationship"></a>Definiowanie relacji
 Kliknij narzędzie relacja odwołania, a następnie kliknij przycisk klasy domeny źródła relacji, a następnie kliknij klasy domeny docelowej. Klasa docelowa może być taka sama jak klasa źródłowa.

 Każda relacja ma dwie role, reprezentowany przez linię na każdej stronie okno relacji. Można wybrać poszczególnych ról i ustaw jego właściwości w oknie dialogowym właściwości.

 **Rozważ zmianę nazwy ról**. Na przykład w relacji między osoby i osoby, możesz chcieć zmienić domyślne nazwy do elementów nadrzędnych i podrzędnych, Menedżer i elementów podrzędnych dla nauczycieli i uczniów i tak dalej.

 **Dostosuj Liczebność punktów każdej roli**, jeśli jest to konieczne. Jeśli chcesz, aby każda osoba miała co najwyżej jednego z kierowników, należy ustawić liczebności, która pojawia się poniżej Menedżer etykiety na diagramie aby od 0 do 1.

 **Dodaj właściwości domeny do relacji.** Na rysunku relacja Wykonawca Album ma właściwości roli.

 **Ustaw właściwość umożliwia duplikuje tę relację,** Jeśli więcej niż jednego połączenia w tej samej klasy może istnieć między tej samej pary elementów modelu. Na przykład można zezwolić nauczyciel nauczenie więcej niż jeden z zastrzeżeniem tych samych uczniów.

 ![Mapowania kształtów dla łączników](../modeling/media/music_connector.png)

 Aby uzyskać więcej informacji, zobacz [właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i [ról właściwości domeny](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definiowanie łącznika do wyświetlania relacji
 Łącznik wyświetla linię między dwoma kształtami na diagram modelu.

 Przeciągnij **łącznika** narzędzia na diagramem definicji DSL.

 Dodaj dekoratorów tekstu, jeśli chcesz wyświetlić etykiety w łączniku. Ustaw ich pozycji. Aby umożliwić użytkownikowi przenoszenie dekoratora tekstu, ustaw jego **to ruchoma** właściwości.

 Użyj **mapowanie elementu diagramu** narzędzie do łączenia łącznik do relacji odwołania.

 Wybrane mapowanie elementu diagramu Otwórz **szczegóły języka DSL** okna, a następnie otwórz **mapy Dekoratora** kartę.

 Wybierz poszczególne **Dekoratora** i ustaw **Właściwość wyświetlania** właściwości prawidłowej domenie.

 Upewnij się, że jest wyświetlany znacznik wyboru obok każdego elementu w **Dekoratory** listy.

### <a name="define-a-connection-builder-tool"></a>Zdefiniuj narzędzie konstruktora połączeń
 W **Eksplorator DSL** okna, rozwiń węzeł **edytora** węzła i jego węzłami podrzędnymi.

 Kliknij prawym przyciskiem myszy węzeł, który ma taką samą nazwę jak DSL, a następnie kliknij przycisk **dodać nowe narzędzie połączenia**.

 Gdy nowe narzędzie jest zaznaczony w oknie dialogowym właściwości:

-   Ustaw **podpis** i **etykietki narzędzia**.

-   Kliknij przycisk **konstruktora połączeń** i wybierz odpowiedniego konstruktora dla nowej relacji.

-   Ustaw **ikonę przybornika** ikony, które mają być wyświetlane w przyborniku. Można ustawić go na nową ikonę lub ikony już używana dla innego narzędzia.

     Aby utworzyć nową ikonę, otwórz Dsl\Resources w **Eksploratora rozwiązań**. Skopiuj i Wklej jeden z istniejących plików BMP narzędzia elementu. Zmień nazwę kopii wklejonych, a następnie kliknij dwukrotnie, aby go edytować.

     Wróć do diagramem definicji DSL, wybierz narzędzie i w oknie dialogowym właściwości kliknij **[...]**  w **ikonę przybornika**. W **Wybierz mapę bitową** okno dialogowe, wybierz użytkownika. Plik BMP z menu rozwijanego.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Aby przetestować relacji i łącznik

1. **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań, aby wygenerować kod projektanta DSL.

2. **Twórz i uruchamiaj język DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie doświadczalnym. W doświadczalnym wystąpieniu programu Visual Studio Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Sprawdź, czy narzędzie połączenia jest wyświetlany w przyborniku.**

4. **Tworzyć kształty** , przeciągając przy użyciu narzędzia na diagram modelu.

5. **Tworzenie połączeń** między kształtów. Kliknij narzędzie łącznik, kliknij kształt, a następnie kliknij przycisk innego kształtu.

6. **Upewnij się, że nie można utworzyć połączenia między klasami nieodpowiednie.** Na przykład w przypadku relacji między ze zdjęciami i artystów, sprawdź, że nie można połączyć artystów artystów.

7. **Sprawdź, czy liczebność punktów są poprawne. Na przykład sprawdzić, że nie można nawiązać połączenia osoby więcej niż jednego z kierowników.**

8. **Sprawdź, czy każdy dekorator tekst jest wyświetlany,** oraz że:

   1.  Można edytować go, o ile nie zostało ustawione **jest interfejs użytkownika tylko do odczytu** flagi dla właściwości domeny.

   2.  Podczas edytowania właściwości w oknie dialogowym właściwości lub w dekoratorze innych widokach jest aktualizowana.

   Po przetestowaniu najpierw łącznik, możesz chcieć dostosować niektóre jej właściwości i dodać niektóre bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Definiowanie kształtów, które zawierają listy: Kształtów przedziałów
 Kształt przedziału zawiera jedną lub więcej list elementów. Na przykład w języku DSL biblioteki utworów muzycznych wystarczą kształtów przedziałów do reprezentowania utworów muzycznych albumy. W przypadku każdego albumu ma listę utworów.

 ![Kształt przedziału](../modeling/media/compartmentshape.png)

 Najprostszą metodą osiągnięcia w tym celu w definicji DSL służy do definiowania jedną klasę domeny dla kontenera i jedną klasę domeny dla każdej listy. Klasa kontenera jest mapowany kształt przedziału.

 ![Mapowanie kształtów](../modeling/media/music_mapcomp.png)

 Aby uzyskać więcej informacji, zobacz [właściwości kształtów przedziałów](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Aby zdefiniować kształt przedziału

1.  **Utwórz klasę domeny kontenera**. Kliknij przycisk **relacji osadzania** narzędzia, kliknij odpowiednią klasę głównego modelu, a następnie kliknij pustą część diagramem definicji DSL. Spowoduje to utworzenie klasy domeny o nazwie albumu na ilustracji przykład.

     Alternatywnie zamiast osadzania w klasie głównego, mogą osadzać kontenera w klasę domeny, który jest mapowany tor.

     Dodaj właściwość domeny, takie jak nazwa klasy i ustaw jego **jest nazwa elementu** flagi w oknie dialogowym właściwości.

2.  **Utwórz klasę domeny elementu listy**. Kliknij przycisk **relacji osadzania** narzędzia, kliknij klasy kontenera (albumu), a następnie kliknij pustą część diagramu. Spowoduje to utworzenie klasy domeny o nazwie utworu na ilustracji przykład.

     Dodaj właściwość domeny, takich jak tytuł, klasy i ustaw jego **jest nazwa elementu** flagi.

     Dodaj inne właściwości domeny.

     Dodaj inną klasę domeny elementu listy dla każdej listy, które mają być wyświetlane.

3.  **Aby utworzyć kilka typów elementów na liście**, zostaną utworzone klasy, które dziedziczą z klasy list. Upewnij list — klasa abstrakcyjna, ustawiając jego **modyfikator dziedziczenia**.

     Na przykład chcąc muzyki być sortowane według Composer (kompozytor) zamiast wykonawcy, można utworzyć dwa podklasy utworu, ClassicalSong i NonClassicalSong.

4.  **Utwórz kształt przedziału**. Przeciągnij z **kształt przedziału** narzędzia na diagramem definicji DSL.

     Dodaj dekoratora tekstu i ustaw jego nazwę.

     Dodawanie przedziału i ustaw jego nazwę.

5.  Aby zezwolić użytkownikom na ukrywanie przedziałów listy, kliknij prawym przyciskiem myszy klasę kształtu przedziału, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **Dekoratora Rozwiń/Zwiń**. W oknie właściwości ustaw pozycji dekoratora.

6.  Kliknij przycisk **mapowanie elementu diagramu** narzędzia, kliknij kontener klasy domeny, a następnie kliknij kształt przedziału.

7.  Wybierz łącze mapy elementu diagramu między klasą domeny i kształt. W **szczegóły języka DSL** okna:

    1.  Kliknij przycisk **Dekoratory** kartę. Kliknij nazwę dekoratora, a następnie wybierz odpowiedni element, w obszarze **Właściwość wyświetlania**. Upewnij się, że jest wyświetlany znacznik wyboru obok nazwy dekoratora.

    2.  Kliknij przycisk **mapowania przedziałów** kartę.

         Kliknij nazwę przedziału.

         W obszarze **ścieżkę kolekcji elementy wyświetlane**, przejdź do klasy elementu listy (utworu). Kliknij strzałkę listy rozwijanej, aby użyć narzędzia navigator.

         W obszarze **Właściwość wyświetlania**, wybierz właściwość, która powinna być wyświetlana na liście. W tym przykładzie jest tytuł.

> [!NOTE]
>  Za pomocą pól ścieżki w mapowaniu Dekoratora i przedziału Mapuj pola, można tworzyć bardziej złożone relacje między klasami domeny i kształt przedziału.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Aby zdefiniować narzędzie do tworzenia kształtu

1.  **Ustaw element przybornika do tworzenia elementów klasy domeny.**

2.  W **Eksplorator DSL**, rozwiń węzeł **edytora** węzła i wszystkich jego węzłów podrzędnych.

3.  Kliknij prawym przyciskiem myszy węzeł w węźle **karty przybornika** który ma taką samą nazwę jak DSL, na przykład MusicLibrary. Kliknij przycisk **narzędzie elementu Dodawanie**.

    > [!NOTE]
    >  Kliknięcie prawym przyciskiem myszy **narzędzia** węzła, nie będzie mógł przeglądać **narzędzia elementu Dodawanie**. Zamiast tego kliknij węzeł powyżej.

4.  W oknie dialogowym właściwości nowego elementu wybierz narzędzie, należy ustawić **klasy** do klasy domeny, która została ostatnio dodana.

5.  Ustaw **podpis** i **etykietki narzędzia**.

6.  Ustaw **ikonę przybornika** ikonę, która będzie wyświetlana w przyborniku. Można ustawić go na nową ikonę lub ikony już używana dla innego narzędzia.

     Aby utworzyć nową ikonę, otwórz Dsl\Resources w **Eksploratora rozwiązań**. Skopiuj i Wklej jeden z istniejących narzędzi elementu. Pliki BMP. Zmień nazwę kopii wklejonych, a następnie kliknij dwukrotnie, aby go edytować.

     Wróć do diagramem definicji DSL, wybierz narzędzie i w oknie dialogowym właściwości kliknij **[...]**  w **ikonę przybornika**. W **Wybierz mapę bitową** okna dialogowego Wybierz swój plik BMP z menu rozwijanego.

#### <a name="to-test-a-compartment-shape"></a>Aby przetestować kształt przedziału

1. **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań, aby wygenerować kod projektanta DSL.

2. **Twórz i uruchamiaj język DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie doświadczalnym. W doświadczalnym wystąpieniu programu Visual Studio Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Sprawdź, czy narzędzie znajduje się w przyborniku.**

4. Przeciągnij narzędzie na diagram modelu. Kształt jest tworzony.

    Sprawdź, czy nazwa elementu jest wyświetlany i jest automatycznie ustawiana na wartość domyślną.

5. Kliknij prawym przyciskiem myszy nagłówek nowy kształt, a następnie kliknij przycisk Dodaj *Your elementu listy.* W tym przykładzie polecenie jest dodać utworu.

    Sprawdź, czy element jest wyświetlany na liście i że jego nazwa została zmieniona.

6. Kliknij jeden z elementów listy, a następnie sprawdź w oknie właściwości. Właściwości elementów listy powinny być widoczne.

7. Otwórz Eksplorator języka. Upewnij się, widoczne węzły kontenerów z węzłami elementu listy wewnątrz.

   ![Wygenerowany Eksploratorze DSL](../modeling/media/music_explorer.png)

   Po przetestowaniu najpierw kształt przedziału, możesz chcieć dostosować niektóre jej właściwości i dodać niektóre bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Wyświetlanie tematami w przedziale
 Zazwyczaj wyświetlanych w przedziale element jest elementem podrzędnym elementu, który jest reprezentowany przez kształt przedziału. Jednak czasami chcesz wyświetlić element, który jest połączony do niej przy użyciu relacji odwołania.

 Na przykład możemy dodać drugi przedział, do AlbumShape, który wyświetla listę artyści, które są połączone z albumu.

 W tym przypadku przedziału powinien być wyświetlany w linku zamiast odnośny element. To dlatego, gdy użytkownik wybierze element w przedziale i naciska klawisz DELETE, chcesz, aby łącze do usunięcia, nie odnośny element.

 Jednakże może mieć nazwę odnośny element pojawiają się w przedziale.

 W poniższej procedurze przyjęto, że utworzono już klasy domeny, relacja odwołania, kształt przedziału i mapowanie elementu diagramu, zgodnie z wcześniejszym opisem w tej sekcji.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Aby wyświetlić łącza w przedziale

1.  **Dodawanie przedziału do kształtu przedziału**. Na diagramie w definicji DSL, kliknij prawym przyciskiem myszy klasę kształtu przedziału, wskaż opcję **Dodaj**, a następnie kliknij przycisk **przedziału**.

2.  Ustaw **ścieżkę kolekcji elementy wyświetlane** można przejść do łącza, a nie jego element docelowy. Kliknij menu rozwijane, a następnie wybierz relacja odwołania, a nie jego element docelowy za pomocą widoku drzewa. W tym przykładzie, jest relacja **ArtistAppearedOnAlbums**.

3.  Ustaw **ścieżka do właściwości wyświetlania** można przejść z linku do elementu docelowego. W tym przykładzie jest to **wykonawcy**.

4.  Ustaw **Właściwość wyświetlania** do odpowiedniej właściwości elementu docelowego, na przykład **nazwa**.

5.  **Transformuj wszystkie szablony**, tworzenie i uruchamianie język DSL i Otwieranie modelu testu.

6.  Diagramu modelu tworzenie odpowiednich klas kształtu, ustawianie ich nazwy i Utwórz łącze między nimi. Przedział kształtu nazwy elementów połączonych powinna zostać wyświetlona.

7.  Wybierz element lub linku w kształt przedziału. Łącza i element powinien zniknąć.

## <a name="ports"></a> Definiowanie porty na granicy innego kształtu
 Port jest kształtu, który znajduje się na granicy innego kształtu.

 Porty mogą również służyć do zapewnienia punktu połączenia stały innego kształtu, do którego użytkownik może narysować łączników. W takim przypadku można wprowadzić kształt portu przezroczysty.

 Aby zobaczyć przykład, który korzysta z portów, wybierz **Diagram składników** szablonu podczas tworzenia nowego rozwiązania języka DSL. Ten przykład przedstawia główne punkty, które należy rozważyć podczas definiowania portów:

- Brak klasy domeny, który reprezentuje kontener, portów, `Component`.

- Brak klasy domeny, który reprezentuje portów. W tym przykładzie jest to `ComponentPort`.

- Istnieje relacja osadzania z klasy domeny kontenera do portu klasy domeny. Aby uzyskać więcej informacji, zobacz [Definiowanie klas domeny](#classes).

- Różnego rodzaju port była mieszana na tym samym kontenerze, można utworzyć podklasy klasy domeny portu. W tym przykładzie `InPort` i `OutPort` dziedziczyć `ComponentPort`.

- Klasa domeny mogą być mapowane do dowolnego rodzaju kształtu. W tym przykładzie jest `ComponentShape`. Aby uzyskać więcej informacji, zobacz [Definiowanie kształtów](#shapes).

- Klasy domeny portu są mapowane na port kształtów. Możesz mapować klas pochodnych do rozdzielania klas kształt portu lub mapowania klasy bazowej do klasy kształt jeden port.

  Pod innymi względami kształtów portu zachowują się zgodnie z opisem w [Definiowanie kształtów](#shapes).

  Aby uzyskać więcej informacji, zobacz [właściwości kształtów portu](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Definiowanie DSL, który ma torów
 Tory są poziomej lub pionowej partycji diagramu. Każdego toru odnosi się do elementu modelu. Definicji DSL wymaga jednej klasy domeny dla elementów toru.

 Najlepszym sposobem tworzenia DSL za pomocą ścieżek jest Utwórz nowe rozwiązanie języka DSL, a następnie wybierz szablon przepływu zadań rozwiązania. W definicji DSL Klasa aktora jest mapowany do toru klasy domeny. Zmień nazwę tego i innych klas, w zależności od projektu.

 Aby dodać klasę, która będzie wyświetlana jako kształt wewnątrz tor, Utwórz relacja osadzania między klasą toru i nowej klasie. Użytkownicy będą mogli przeciągnij elementy z jednego tor, ale każdy element zawsze będzie znajdować się w szczególności toru. W szablonie przepływu zadań rozwiązania FlowElement jest elementem podrzędnym klasy toru.

 Aby dodać klasę, która będzie wyświetlana jako kształt, niezależnie od ścieżek, Utwórz relacja osadzania między klasą głównego i nowej klasie. Użytkownicy będą mogli umieścić te kształty w dowolnym miejscu na diagramie, w tym w granicach torów i na zewnątrz torów. W szablonie przepływu zadań rozwiązania komentarz jest element podrzędny klasy głównej.

 Aby uzyskać więcej informacji, zobacz [właściwości torów](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Dodawanie typów właściwości

### <a name="domain-enumerations-and-literals"></a>Literały i wyliczenia domeny
 Wyliczenia domeny jest typem z kilku wartości literału.

 Aby dodać wyliczenia domeny, kliknij prawym przyciskiem myszy korzeń modelu w **Eksplorator DSL** a następnie kliknij przycisk **Dodaj nowe wyliczenie domeny**. Element pojawi się w **Eksplorator DSL** w obszarze **typy domen** węzła. Ten element nie jest wyświetlana na diagramie.

 Aby dodać wyliczenie literały do wyliczenia domeny, kliknij prawym przyciskiem myszy wyliczenia domena w **Eksplorator DSL** a następnie kliknij przycisk **Dodaj nowe wyliczenie literału**.

 Domyślnie tylko jednej wartości wyliczenia w danym momencie można ustawić właściwości, która ma typ wyliczenia. Użytkownicy i programistów, aby można było ustawić dowolną kombinację wartości — "polem bitowym" - ustawić **IsFlags** właściwości wyliczenia.

### <a name="external-types"></a>Typy zewnętrzne
 Po ustawieniu typ własności domeny, jeśli nie zostanie znaleziony typ chcesz w **typu** listy rozwijanej, można dodać typu zewnętrznego. Na przykład można dodać **System.Drawing.Color** typu do listy.

 Aby dodać typ, kliknij prawym przyciskiem myszy korzeń modelu w Eksplorator DSL, a następnie kliknij przycisk **dodać nowy typ zewnętrzny**. W oknie właściwości ustaw nazwę na **kolor** oraz przestrzeń nazw **System.Drawing**. Ten typ jest teraz wyświetlany w Eksplorator DSL w obszarze **typy domen**. Można go zawsze wtedy, gdy ustawiony typ właściwości domeny.

## <a name="custom"></a> Dostosowywanie języka DSL
 Korzystając z metod opisanych w tym temacie, można szybko utworzyć DSL za pomocą notacji diagramowy, czytelny formularza XML i podstawowe narzędzia, które są wymagane do generowania kodu i innych artefaktów.

 Istnieją dwie metody rozszerzania definicji DSL:

1.  Dostosuj język DSL za pomocą więcej funkcji w definicji DSL. Na przykład może być narzędziem pojedynczy łącznik, które można utworzyć kilka typów łącznika i kontrolowania zasad, które usuwając jeden element spowoduje również usunięcie powiązanych elementów. Te techniki najczęściej są wykonywane przez ustawienie wartości w definicji DSL, a niektóre wymagają kilku wierszy kodu programu.

     Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

2.  Rozszerzanie narzędzi do modelowania przy użyciu kodu programu, aby uzyskać więcej informacji o zaawansowanych efekty. Na przykład można utworzyć polecenia menu, które można zmienić modelu i narzędzia, które integrują się co najmniej dwóch języków DSL. VMSDK jest zaprojektowany specjalnie w celu ułatwiają integrowanie rozszerzeń z kodem, który jest generowany na podstawie definicji DSL.  Aby uzyskać więcej informacji, zobacz [pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Zmiana definicji DSL
 Wiele wartości domyślne są ustawiane automatycznie po utworzeniu każdego elementu w definicji DSL. Po ustawieniu, można je zmienić. Upraszcza to rozwoju DSL, umożliwiając jednocześnie zaawansowanych dostosowań.

 Na przykład kiedy mapujesz kształtu do elementu ścieżka elementu nadrzędnego mapowania automatycznie ustawiono zgodnie z relacji osadzania klasy domeny. Jednak w przypadku późniejszej zmiany relacji osadzania, ścieżka elementu nadrzędnego nie jest zmieniany automatycznie.

 Dlatego należy pamiętać, że zmiana niektórych relacji w definicji DSL, nie jest niczym niezwykłym, błędy, należy podać podczas zapisywania definicji lub gdy Transformuj wszystkie szablony. Większość z tych błędów jest łatwo rozwiązać. Kliknij dwukrotnie raport o błędach, aby zobaczyć pozycję Lokalizacja błędu.

 Zobacz też [jak: Zmień Namespace języka specyficznego dla domeny](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Rozwiązywanie problemów
 Poniższa lista zawiera niektóre z najczęściej występujących problemów napotkanych podczas projektowania DSL, wraz z sugestie dotyczące ich rozwiązania. Więcej porad jest dostępny na [Extensibililty Forum narzędzia wizualizacji](http://go.microsoft.com/fwlink/?LinkId=186074).


| Problem | Sugestia |
|-|-|
| Zmiany wprowadzone w pliku definicji DSL przyniosło żadnego skutku. | Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi powyżej Eksploratora rozwiązań, a następnie ponownej kompilacji rozwiązania. |
| Kształty Pokaż nazwę elementu decorator zamiast wartości właściwości. | Skonfiguruj mapowanie dekoratora. Wybierz polecenie mapowanie elementu diagramu, czyli szara linia między klasą domeny i klasa kształt z diagramem definicji DSL.<br /><br /> Otwórz **szczegóły języka DSL** okna. Jeśli nie jest widoczna, w menu Widok, wskaż **Windows inne**, a następnie kliknij przycisk **szczegóły języka DSL**.<br /><br /> Kliknij przycisk **mapy Dekoratora** kartę. Wybierz nazwę dekoratora. Upewnij się, że zaznaczono pole wyboru obok tej pozycji. W obszarze **Właściwość wyświetlania**, wybierz nazwę właściwości domeny.<br /><br /> Aby uzyskać więcej informacji, zobacz [kształtów na diagramie](#shapes). |
| W Eksploratorze DSL nie można dodać do kolekcji. Na przykład gdy klikam prawym przyciskiem myszy narzędzia istnieje żadne polecenie "Dodaj narzędzie" w menu.<br /><br /> W Eksploratorze dla mojego języka DSL nie można dodać elementu do listy. | Kliknij prawym przyciskiem myszy element nad węzłem, który ma. Jeśli chcesz dodać do listy polecenia Dodaj jest nie znajduje się w węźle listy, ale w jego właściciel. |
| Po utworzeniu klasy domeny, ale nie można utworzyć wystąpienia w Eksploratorze języka. | Każda klasa domeny, z wyjątkiem głównego musi być elementem docelowym relacji osadzania. |
| W Eksploratorze dla mojego języka DSL elementy są wyświetlane tylko w przypadku ich nazwy typu. | W definicji DSL wybierz właściwość domeny klasy, a w oknie właściwości ustaw oknie **jest nazwa elementu** na wartość true. |
| Moje DSL zawsze zostanie otwarty w edytorze XML. | Może to nastąpić z powodu błędu podczas odczytu pliku. Jednak mimo należy naprawić ten błąd, możesz jawnie zresetować edytora projektanta DSL.<br /><br /> Kliknij prawym przyciskiem myszy element projektu, kliknij przycisk **Otwórz za pomocą** i wybierz pozycję * YourLanguage ***projektanta (ustawienie domyślne)**. |
| Przybornik Moje DSL nie pojawia się po zmianie nazwy zestawu. | Sprawdzanie i zaktualizuj **DslPackage\GeneratedCode\Package.tt** Aby uzyskać więcej informacji, zobacz [jak: Zmień Namespace języka specyficznego dla domeny](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| Przybornik Moje DSL nie pojawia się, ale nie uległy zmianie nazwy zestawu.<br /><br /> Lub pojawia się komunikat z raportowania błędów, które można załadować rozszerzenia. | Zresetuj wystąpienie eksperymentalne programu i ponownie skompiluj rozwiązanie.<br /><br /> 1.  Windows — w menu Start, w obszarze **wszystkie programy**, rozwiń węzeł [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)], następnie **narzędzia**, a następnie kliknij przycisk **Zresetuj Microsoft Visual Studio wystąpienie eksperymentalne programu**.<br />2.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. |

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do języków specyficznych dla domeny](../modeling/getting-started-with-domain-specific-languages.md)
- [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)