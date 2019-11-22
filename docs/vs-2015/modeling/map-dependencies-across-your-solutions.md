---
title: Mapowanie zależności między rozwiązaniami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b25d23b7c65742ffddadbe178d7550dc1794414a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296333"
---
# <a name="map-dependencies-across-your-solutions"></a>Zależności mapy w ramach rozwiązań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zrozumieć zależności w kodzie, wizualizuj je poprzez tworzenie map kodu. Dzięki temu można zobaczyć, jak kod pasuje do siebie bez odczytywania plików i wierszy kodu.

 ![Wyświetlanie zależności między rozwiązaniami](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

 **Oto kilka filmów wideo**:

- [Poznanie zależności kodu za poorednictwem wizualizacji](https://go.microsoft.com/fwlink/?LinkID=252065)

- [Wizualizuj wpływ zmiany](https://go.microsoft.com/fwlink/?LinkID=252068)

- [Zrozumienie złożonego kodu za pomocą map kodu](https://go.microsoft.com/fwlink/?LinkID=259869)

## <a name="GetStarted"></a>Wprowadzenie do map kodu
 **Aby korzystać z map kodu, musisz wykonać**następujące:

- Visual Studio Enterprise: Tworzenie map kodu za pomocą edytora kodu, Eksplorator rozwiązań, Widok klasy lub Przeglądarka obiektów.

- Visual Studio Professional: otwieranie map kodu, wykonywanie ograniczonych edycji i nawigowanie po kodzie.

> [!WARNING]
> Przed udostępnieniem map utworzonych w Visual Studio Enterprise z innymi osobami korzystającymi z Visual Studio Professional upewnij się, że wszystkie elementy na mapie (takie jak elementy ukryte, rozwinięte grupy i linki między grupami) są widoczne.

 **Można mapować zależności dla kodu w następujących językach**:

- Visual C# .net lub Visual Basic .NET w rozwiązaniu lub zestawach (. dll lub. exe)

- Natywna lub zarządzana C++ C lub kod C++ w projektach wizualnych, pliki nagłówkowe (. h lub `#include`) lub pliki binarne

- Projekty X + + i zestawy wykonane z modułów .NET dla systemu Microsoft Dynamics AX

  **Uwaga:** W przypadku projektów innych C# niż lub Visual Basic .NET istnieje mniej opcji uruchamiania mapy kodu lub dodawania elementów do istniejącej mapy kodu. Na przykład nie można kliknąć prawym przyciskiem myszy obiektu w edytorze tekstu C++ projektu i dodać go do mapy kodu. Można jednak przeciągać i upuszczać poszczególne elementy kodu lub pliki z Eksplorator rozwiązań, Widok klasy i Przeglądarka obiektów.

#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Aby wyświetlić ogólne zależności w rozwiązaniu

1. Otwórz menu **Architektura** .

2. Jeśli rozwiązanie zostało właśnie otwarte i nie zostało jeszcze skompilowane, lub jeśli kod zmienił się od czasu ostatniego skompilowania, wybierz opcję **Generuj mapę kodu dla rozwiązania**.

3. Jeśli Twój kod nie zmienił się od czasu ostatniej kompilacji, wybierz opcję **Generuj mapę kodu dla rozwiązania bez kompilowania** , aby zwiększyć wydajność podczas tworzenia mapy.

4. Zapoznaj się z [ogólnymi zależnościami](#SeeOverviewSource) , aby zrozumieć, jak można użyć map kodu do wyświetlania ogólnych zależności w rozwiązaniu.

#### <a name="to-see-specific-dependencies-within-your-solution"></a>Aby wyświetlić określone zależności w ramach rozwiązania

1. Po załadowaniu rozwiązania Otwórz **Eksplorator rozwiązań**.

2. Zaznacz wszystkie projekty, odwołania do zestawów, foldery, pliki, typy lub elementy członkowskie, które chcesz zmapować.

3. Na pasku narzędzi **Eksplorator rozwiązań** wybierz przycisk **Pokaż na mapie kodu**![Utwórz nowy Graf z wybranych węzłów](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton"). Lub Otwórz menu skrótów i wybierz **Pokaż na mapie kodu**. Możesz również przeciągać elementy z Widok klasy lub Przeglądarka obiektów do nowej lub istniejącej mapy kodu.

4. Zapoznaj się z [określonymi zależnościami](#SeeSpecificSource) , aby zrozumieć, jak można użyć map kodu do wyświetlania określonych zależności w ramach rozwiązania.

### <a name="CreateEmptyMap"></a>Aby dodać nową pustą mapę kodu do rozwiązania

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązania najwyższego poziomu. Wybierz pozycję **Dodaj** , a następnie wybierz pozycję **nowy element**.

2. W obszarze **zainstalowane**wybierz pozycję **Ogólne**.

3. W okienku po prawej stronie wybierz pozycję **ukierunkowany dokument wykresu** , a następnie wybierz pozycję **Dodaj**.

     Masz teraz pustą mapę, która jest wyświetlana w folderze **elementy rozwiązania** rozwiązania.

#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Aby utworzyć nową pustą mapę kodu bez dodawania jej do rozwiązania

1. Otwórz menu **Architektura** i wybierz pozycję **Nowa mapa kodu**.

     \- lub —

2. Otwórz menu **plik** i wybierz polecenie **Nowy** , a następnie wybierz **plik**.

3. W obszarze **zainstalowane**wybierz pozycję **Ogólne**.

4. W okienku po prawej stronie wybierz pozycję **ukierunkowany dokument wykresu** , a następnie wybierz polecenie **Otwórz**.

     Masz teraz pustą mapę, która nie jest wyświetlana w folderach rozwiązania.

## <a name="SeeOverviewSource"></a>Zobacz Ogólne zależności

### <a name="OverviewSource"></a>Zobacz zależności w rozwiązaniu

1. W menu **Architektura** wybierz polecenie **Generuj mapę kodu dla rozwiązania**.

    ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")

    Uzyskasz mapę pokazującą zestawy najwyższego poziomu i zagregowane łącza między nimi. Im szerszy link zagregowany, tym więcej zależności reprezentuje.

2. Użyj przycisku **Legenda** na pasku narzędzi Mapa kodu, aby pokazać lub ukryć listę ikon typu projektu (na przykład projektu testowego, sieci Web i telefonu), elementów kodu (takich jak klasy, metody i właściwości), a także typy relacji (na przykład dziedziczone z, implementacje i wywołania).

    ![Wykres&#45;zależności najwyższego poziomu dla zestawów](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")

    To przykładowe rozwiązanie zawiera foldery rozwiązań (**testy** i **składniki**), projekty testowe, projekty sieci Web i zestawy. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grupy*, które można rozwijać i zwijać. Grupa **zewnętrzna** zawiera wszystkie elementy spoza rozwiązania, w tym zależności platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie typy podstawowe systemu są ukryte na mapie, aby zmniejszyć ilość bałaganu.

3. Aby przejść do szczegółów mapy, rozwiń grupy reprezentujące projekty i zespoły. Możesz rozwinąć wszystko, naciskając **klawisze Ctrl + A** , aby zaznaczyć wszystkie węzły, a następnie wybrać **grupę**, **Rozwiń** z menu skrótów.

    ![Rozszerzanie wszystkich grup na mapie kodu](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")

4. Jednak może to nie być przydatne w przypadku dużych rozwiązań. W rzeczywistości ograniczenia pamięci mogą uniemożliwiać rozszerzanie wszystkich grup. Zamiast tego, aby zobaczyć wewnątrz pojedynczego węzła, rozwiń go. Przesuń wskaźnik myszy na górny węzeł, a następnie kliknij cudzysłów ostrokątny (Strzałka w dół), gdy zostanie wyświetlony.

    ![Rozszerzanie węzła na mapie kodu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

    Możesz też użyć klawiatury, zaznaczając element, a następnie naciskając klawisz plus ( **+** ). Aby zapoznać się z bardziej szczegółowymi poziomami kodu, wykonaj te same czynności dla obszarów nazw, typów i elementów członkowskich.

   > [!TIP]
   > Aby uzyskać szczegółowe informacje na temat pracy z mapami kodu przy użyciu myszy, klawiatury i dotyku, zobacz [przeglądanie i zmiana kolejności map kodu](../modeling/browse-and-rearrange-code-maps.md).

5. Aby uprościć mapę i skoncentrować się na poszczególnych częściach, wybierz **filtry** na pasku narzędzi Mapa kodu i wybierz tylko wybrane typy węzłów i linków. Można na przykład ukryć wszystkie kontenery i foldery rozwiązań.

    ![Uproszczenie mapy przez filtrowanie kontenerów](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")

    Możesz również uprościć mapę przez ukrycie lub usunięcie poszczególnych grup i elementów z mapy, bez wpływu na podstawowy kod rozwiązania.

6. Aby wyświetlić relacje między elementami, zaznacz je na mapie. Kolory linków wskazują typy relacji, jak pokazano w okienku **Legenda** .

    ![Wyświetlanie zależności między rozwiązaniami](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

    W tym przykładzie purpurowe łącza to wywołania, linki kropkowane są odwołaniami, a niebieskie linki są dostępem do pól. Zielone linki mogą być dziedziczenia lub mogą być *zagregowanymi łączami* , które wskazują więcej niż jeden typ relacji (lub *kategorii*).

   > [!TIP]
   > Jeśli zobaczysz zielony link, może nie oznaczać, że istnieje tylko relacja dziedziczenia. Mogą również wystąpić wywołania metody, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy łączy, Użyj pól wyboru w okienku **filtry** w celu ukrycia nieinteresujących typów.

7. Aby uzyskać więcej informacji na temat elementu lub łącza, przesuń wskaźnik na wierzchu do momentu wyświetlenia etykietki narzędzia. Przedstawia szczegóły elementu kodu lub kategorie reprezentowane przez łącze.

    ![Pokaż kategorie relacji](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")

8. Aby przejrzeć elementy i zależności reprezentowane przez łącze zagregowane, najpierw zaznacz łącze, a następnie otwórz jego menu skrótów. Wybierz **Pokaż linki** do współtworzenia (lub **Pokaż linki do współtworzenia na nowej mapie kodu**). Rozszerza to grupy na obu końcach łącza i pokazuje tylko te elementy i zależności, które uczestniczą w łączu.

9. Aby skoncentrować się na określonych częściach mapy, możesz kontynuować usuwanie nieinteresujących elementów. Na przykład aby przejść do szczegółów w widoku klasy i elementu członkowskiego, wystarczy odfiltrować wszystkie węzły przestrzeni nazw w okienku **filtry** .

     ![Przechodzenie do szczegółów na poziomie klasy i elementu członkowskiego](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")

10. Innym sposobem skoncentrowania się na złożonej mapie rozwiązań jest wygenerowanie nowej mapy zawierającej wybrane elementy z istniejącej mapy. Przytrzymaj klawisz **Ctrl** podczas zaznaczania elementów, na których chcesz się skoncentrować, otwórz menu skrótów i wybierz polecenie **Nowy wykres z zaznaczenia**.

     ![Pokaż zaznaczone elementy na nowej mapie kodu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

11. Kontekst zawierający jest przenoszony do nowej mapy. Ukryj foldery rozwiązań i inne kontenery, które nie mają być wyświetlane za pomocą okienka **filtry** .

     ![Filtrowanie kontenerów w celu uproszczenia widoku](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")

12. Rozwiń grupy i wybierz elementy na mapie, aby wyświetlić relacje.

     ![Wybierz elementy, aby wyświetlić relacje](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")

    Zobacz również:

- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)

- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

- Znajdź potencjalne problemy w kodzie, [uruchamiając Analizator](../modeling/find-potential-problems-using-code-map-analyzers.md).

### <a name="OverviewCompiled"></a>Zobacz zależności w zestawach lub plikach binarnych

1. [Utwórz pustą mapę kodu](#GetStarted)lub Otwórz istniejącą mapę kodu (plik. dgml).

2. Przeciągnij zestawy lub pliki binarne, które chcesz zmapować z zewnątrz programu Visual Studio na mapę. Na przykład przeciągnij zestawy lub pliki binarne z Eksploratora Windows lub Eksploratora plików.

> [!NOTE]
> Możesz przeciągać zestawy lub pliki binarne z Eksploratora Windows lub Eksploratora plików tylko wtedy, gdy używasz go i programu Visual Studio na tym samym poziomie uprawnień użytkownika Access Control (UAC). Na przykład jeśli kontrola konta użytkownika jest włączona i używasz programu Visual Studio jako administrator, Eksplorator Windows lub Eksplorator plików zablokuje operację przeciągania. Aby obejść ten sposób, upewnij się, że oba działają z tym samym poziomem uprawnień, lub wyłącz funkcję Kontrola konta użytkownika.

## <a name="SeeSpecificSource"></a>Zobacz określone zależności
 Załóżmy na przykład, że masz przegląd kodu do wykonania w niektórych plikach z oczekującymi zmianami. Aby wyświetlić zależności w tych zmianach, można utworzyć mapę kodu z tych plików.

 ![Pokaż określone zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

### <a name="see-specific-dependencies-in-your-solution"></a>Wyświetlanie określonych zależności w rozwiązaniu

1. Otwórz **Eksplorator rozwiązań**. Wybierz projekty, odwołania do zestawów, foldery, pliki, typy i członków, które Cię interesują. Aby znaleźć elementy z zależnościami dotyczącymi typów lub elementów członkowskich, otwórz menu skrótów typu lub elementu członkowskiego z **Eksplorator rozwiązań**. Wybierz typ zależności, a następnie wybierz wyniki.

2. Mapowanie elementów i ich członków. Na pasku narzędzi **Eksplorator rozwiązań** kliknij przycisk **Pokaż na mapie kodu**![Utwórz nowy wykres z wybranych węzłów](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").

     ![Wybierz elementy, które chcesz zmapować](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")

3. Mapa pokazuje wybrane elementy w ich zestawach zawierających.

     ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")

     Możesz również przeciągać elementy z Eksplorator rozwiązań, Widok klasy lub Przeglądarka obiektów do pustej lub istniejącej mapy kodu. Aby utworzyć pustą mapę, zobacz [Tworzenie pustej mapy kodu](#GetStarted). Aby uwzględnić hierarchię nadrzędną dla elementów, naciśnij i przytrzymaj klawisz **Ctrl** podczas przeciągania elementów lub użyj przycisku **Dołącz obiekty nadrzędne** na pasku narzędzi Mapa kodu, aby określić akcję domyślną.

    > [!NOTE]
    > Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Sklep Windows, elementy te są widoczne na mapie z projektem aktualnie aktywnych aplikacji. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

4. Aby eksplorować elementy, rozwiń je. Przesuń wskaźnik myszy nad elementem, a następnie kliknij ikonę cudzysłów ostrokątny (Strzałka w dół), gdy zostanie wyświetlona.

     ![Rozszerzanie węzła na mapie kodu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

     Aby rozwinąć wszystkie elementy, zaznacz je za pomocą **kombinacji klawiszy Ctrl + A**, a następnie otwórz menu skrótów dla mapy i wybierz **grupę**, **Rozwiń**. Jednak ta opcja jest niedostępna, jeśli rozszerzanie wszystkich grup tworzy niezdatną mapę lub problemy z pamięcią.

5. Kontynuuj rozwijanie interesujących Cię elementów, a jeśli to konieczne, na poziomie klasy i elementu członkowskiego.

     ![Rozwiń grupy do poziomu klasy i elementu członkowskiego](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")

     Aby wyświetlić elementy członkowskie, które znajdują się w kodzie, ale nie są wyświetlane na mapie, kliknij ikonę ponownie **Pobierz elementy podrzędne** ikona ponownie ![Pobierz elementy podrzędne](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") w lewym górnym rogu grupy.

6. Aby wyświetlić więcej elementów związanych z tymi elementami na mapie, wybierz jeden z nich i wybierz **Pokaż powiązane** z paskiem narzędzi Mapa kodu, a następnie wybierz typ powiązanych elementów do dodania do mapy. Alternatywnie wybierz co najmniej jeden element, otwórz menu skrótów, a następnie wybierz polecenie **Pokaż...** opcja dla typu elementów pokrewnych, które mają zostać dodane do mapy. Na przykład:

     Dla **zestawu**wybierz:

    |||
    |-|-|
    |**Pokaż zestawy te odwołania**|Dodaj zestawy, do których odwołuje się ten zestaw. Zestawy zewnętrzne pojawiają się w grupie **zewnętrzne** .|
    |**Pokaż zestawy odwołujące się do tego**|Dodaj zestawy w rozwiązaniu odwołującym się do tego zestawu.|

     W przypadku **przestrzeni nazw**wybierz pozycję **Pokaż zawierający zestaw**, jeśli nie jest ona widoczna.

     Dla **klasy** lub **interfejsu**, wybierz:

    |||
    |-|-|
    |**Pokaż typy podstawowe**|Dla klasy dodaj klasę bazową i implementowane interfejsy.<br /><br /> Dla interfejsu dodaj interfejsy podstawowe.|
    |**Pokaż typy pochodne**|Dla klasy dodaj klasy pochodne.<br /><br /> Dla interfejsu dodaj interfejsy pochodne i implementujące klasy lub struktury.|
    |**Pokaż typy te odwołania**|Dodaj wszystkie klasy i używane przez nie składowe.|
    |**Pokaż typy przywołujące ten element**|Dodaj wszystkie klasy oraz ich składowe, które używają tej klasy.|
    |**Pokaż zawierającą przestrzeń nazw**|Dodaj nadrzędną przestrzeń nazw.|
    |**Pokaż zawierającą przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|
    |**Pokaż wszystkie typy podstawowe**|Dodaj cyklicznie klasę bazową lub hierarchię interfejsu.|
    |**Pokaż wszystkie typy pochodne**|Dla klasy dodaj wszystkie klasy pochodne cyklicznie.<br /><br /> Dla interfejsu, dodaj wszystkie interfejsy pochodne i cyklicznie implementujące klasy lub struktury.|

     Dla **metody**należy wybrać:

    |||
    |-|-|
    |**Pokaż metody tego wywołania**|Dodaj metody, które wywołuje ta metoda.|
    |**Pokaż pola te odwołania**|Dodaj pola, do których odwołuje się ta metoda.|
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|
    |**Pokaż zawierający typ, przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|
    |**Pokaż przesłonięte metody**|Dla metody, która zastępuje inne metody lub implementuje metodę interfejsu, należy dodać wszystkie metody abstrakcyjne lub wirtualne w klasach bazowych, które są zastępowane, oraz — jeśli istnieje — implementowaną metodę interfejsu.|

     Dla **pola** lub **Właściwości**wybierz:

    |||
    |-|-|
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|
    |**Pokaż zawierający typ, przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|

     ![Pokaż metody wywoływane przez ten element członkowski](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")

7. Mapa pokazuje relacje. W tym przykładzie metody wywoływane przez metodę `Find` i ich lokalizacja w rozwiązaniu lub zewnętrznie.

     ![Pokaż określone zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

8. Aby uprościć mapę i skoncentrować się na poszczególnych częściach, wybierz **filtry** na pasku narzędzi Mapa kodu i wybierz tylko wybrane typy węzłów i linków. Na przykład Wyłącz wyświetlanie folderów rozwiązań, zestawów i przestrzeni nazw.

     ![Używanie okienka filtru do uproszczenia wyświetlania](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")

## <a name="SeeSourceHeader"></a>Zobacz zależności między plikami C C++ i Source a plikami nagłówkowymi
 Jeśli chcesz utworzyć dokładniejsze mapy dla C++ projektów, ustaw dla tych projektów opcję **/fr**(przeglądanie informacji kompilatora). Zobacz [/fr,/fr (Create. Plik SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. Jeśli wybierzesz **OK**, spowoduje to ustawienie opcji tylko dla bieżącej mapy. Możesz wybrać opcję ukrycia komunikatu dla wszystkich późniejszych map. Jeśli ten komunikat zostanie ukryty, można go ponownie wyświetlić. Ustaw następujący klucz rejestru, aby `0` lub usunąć klucz:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**

 Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie może nie być możliwe utworzenie map kodu dla plików nagłówkowych (. h lub `#include`), dopóki nie zakończy się aktualizowanie bazy danych IntelliSense. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio. Aby rozwiązać problemy lub komunikaty wyświetlane z powodu wyłączenia niektórych ustawień IntelliSense, zobacz artykuł [Rozwiązywanie problemów z mapami C++ dla języka C i kodu](#Troubleshooting).

- Aby wyświetlić zależności między wszystkimi plikami źródłowymi i plikami nagłówkowymi w rozwiązaniu, w menu **Architektura** wybierz polecenie **Generuj Graf plików dołączanych**.

     ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")

- Aby wyświetlić zależności między aktualnie otwartym plikiem i powiązanymi plikami źródłowymi i plikami nagłówkowymi, Otwórz plik źródłowy lub plik nagłówkowy. Otwórz menu skrótów pliku w dowolnym miejscu w pliku. Wybierz pozycję **Generuj Graf plików dołączanych**.

     ![Wykres&#45;zależności pierwszego poziomu dla pliku h](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")

### <a name="Troubleshooting"></a>Rozwiązywanie problemów z mapami C++ dla języka C i kodu
 Te elementy nie są obsługiwane w języku C++ C i kodzie:

- Typy podstawowe nie są wyświetlane na mapach, które zawierają hierarchię nadrzędną.

- Większość elementów menu **Pokaż** nie jest dostępnych dla języków C++ C i Code.

  Te problemy mogą wystąpić podczas tworzenia map kodu dla języka C i C++ kodu:

|**Wykonaj**|**Możliwa przyczyna**|**Rozdzielczość**|
|---------------|------------------------|--------------------|
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Napraw błędy kompilacji, które wystąpiły, a następnie ponownie Wygeneruj mapę.|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przestaje odpowiadać przy próbie wygenerowania mapy kodu z menu **architektury** .|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia IntelliSense można wyłączyć w oknie dialogowym **opcje** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|Włącz te ustawienia.<br /><br /> Zobacz [Opcje, Edytor tekstu, C/C++, zaawansowane](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Komunikat **nieznane metody** pojawi się w węźle metody.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz opcję **/FIXED: No** w konsolidatorze.<br /><br /> Zobacz [/FIXED (stały adres podstawowy)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz opcję **/Debug** w konsolidatorze.<br /><br /> Zobacz [/debug (generowanie informacji o debugowaniu)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli w konsolidatorze użyto opcji **/PDBSTRIPPED** , Dołącz do niej kompletny plik. pdb.<br /><br /> Zobacz [/PDBSTRIPPED (symbole prywatne)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Gdy obiekt wywołujący jest thunk, spróbuj użyć `_declspec(dllimport)`, aby uniknąć thunk.<br /><br /> Zobacz:<br /><br /> -   [ogólne reguły i ograniczenia](https://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [importowania wywołań funkcji przy użyciu __declspec (dllimport)](https://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](https://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|

## <a name="RenderMoreQuickly"></a>Szybsze renderowanie map kodu
 Po wygenerowaniu mapy po raz pierwszy, program Visual Studio indeksuje wszystkie zależności, które znajdzie. Ten proces może zająć trochę czasu, szczególnie w przypadku dużych rozwiązań, ale poprawi wydajność później. Jeśli kod ulegnie zmianie, program Visual Studio ponownie indeksuje tylko zaktualizowany kod. Aby zminimalizować czas potrzebny na zakończenie renderowania mapy, należy wziąć pod uwagę następujące kwestie:

- [Mapuj tylko zależności, które Cię interesują.](#SeeSpecificSource)

- Przed wygenerowaniem mapy dla całego rozwiązania, Zmniejsz zakres rozwiązania.

- Wyłącz automatyczne Kompilowanie rozwiązania za pomocą przycisku **Pomiń kompilację** na pasku narzędzi mapy kodu.

- Wyłącz automatyczne dodawanie elementów nadrzędnych za pomocą przycisku **Dołącz rodziców** na pasku narzędzi mapy kodu.

- Edytuj plik mapy kodu bezpośrednio, aby usunąć węzły i linki, które nie są potrzebne. Zmiana mapy nie ma wpływu na kod źródłowy. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

  ![Pomiń kompilację i Dołącz przyciski nadrzędne](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")

  Mimo że program Visual Studio może działać z 1 GB pamięci, zalecamy, aby komputer miał co najmniej 2 GB pamięci, aby uniknąć długotrwałych opóźnień, podczas gdy program Visual Studio tworzy indeks kodu i generuje mapę.

  Utworzenie map lub dodanie elementów do mapy z Eksplorator rozwiązań może zająć więcej czasu, gdy właściwość **Kopiuj do katalogu wyjściowego** elementu projektu jest ustawiona na wartość **Kopiuj zawsze**. Może to spowodować problemy z kompilacjami przyrostowymi i każdorazowe ponowne kompilowanie projektu przez program Visual Studio. Aby zwiększyć wydajność, należy zmienić tę właściwość na **Kopiuj, jeśli nowszy** lub `PreserveNewest`. Zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md).

  Zakończona mapa będzie wyświetlać zależności tylko dla kodu skompilowanego pomyślnie. Jeśli wystąpią błędy kompilacji dla niektórych składników, te błędy są wyświetlane na mapie. Upewnij się, że składnik rzeczywiście kompiluje i ma zależności od tego przed podjęciem decyzji o architekturze na podstawie mapy.

## <a name="SavingExporting"></a>Udostępnianie map kodu

### <a name="share-the-map-with-other-visual-studio-users"></a>Udostępnianie mapy innym użytkownikom programu Visual Studio
 Użyj menu **plik** , aby zapisać mapę.

 —lub—

 Aby zapisać mapę jako część określonego projektu, na pasku narzędzi Mapa wybierz pozycję **Udostępnij**, **przenieś** \<*CodeMapName*> **. dgml do**, a następnie wybierz projekt, w którym chcesz zapisać mapę.

 ![Przenoszenie mapy do innego projektu](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")

 Program Visual Studio zapisuje mapę jako plik. dgml, który można udostępniać innym użytkownikom Visual Studio Enterprise i Visual Studio Professional.

> [!NOTE]
> Przed udostępnieniem mapy z tymi, które używają Visual Studio Professional, pamiętaj, aby rozwinąć wszystkie grupy, pokazać ukryte węzły i linki między grupami i pobrać wszystkie usunięte węzły, które mają być widoczne dla innych użytkowników na mapie. W przeciwnym razie inni użytkownicy nie będą mogli zobaczyć tych elementów.
>
> Następujący błąd może wystąpić, gdy zapisujesz mapę, która znajduje się w projekcie modelowania lub został skopiowany z projektu modelowania do innej lokalizacji:
>
> "Nie można zapisać *pliku* poza katalogiem projektu. Elementy połączone nie są obsługiwane”.
>
> Program Visual Studio pokazuje błąd, ale mimo to tworzy zapisaną wersję. Aby uniknąć tego błędu, Utwórz mapę poza projektem modelowania. Można następnie zapisać go w dowolnej lokalizacji. Skopiowanie pliku do innej lokalizacji w rozwiązaniu, a następnie próba zapisu zakończą się niepowodzeniem.

### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Wyeksportuj mapę jako obraz, aby można było skopiować ją do innych aplikacji, takich jak Microsoft Word lub PowerPoint

1. Na pasku narzędzi Mapa kodu wybierz opcję **Udostępnij**, **wiadomości e-mail jako obraz** lub **Kopiuj obraz**.

2. Wklej obraz do innej aplikacji.

### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Eksportowanie mapy jako pliku XPS, aby można ją było zobaczyć w przeglądarkach XML lub XAML, takich jak Internet Explorer

1. Na pasku narzędzi Mapa kodu wybierz opcję **Udostępnij**, **Wyślij wiadomość e-mail jako przenośny dokument XPS** lub **Zapisz jako przenośny plik XPS**.

2. Przejdź do lokalizacji, w której chcesz zapisać plik.

3. Nazwij mapę kodu. Upewnij się, że pole **Zapisz jako typ** jest ustawione na **pliki XPS (\*. XPS)** . Wybierz pozycję **Zapisz**.

## <a name="what-else-can-i-do"></a>Co jeszcze można zrobić?

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)

- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
