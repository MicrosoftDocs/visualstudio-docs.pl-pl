---
title: Mapowanie zależności w ramach rozwiązań | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cb62c82722cbfc76264e760e117c828a6dc3bef0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687158"
---
# <a name="map-dependencies-across-your-solutions"></a>Zależności mapy w ramach rozwiązań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz poznać zależności w kodzie, utwórz ich wizualizację przez utworzenie map kodów. Dzięki temu można zobaczyć, jak kod dopasowuje się ze sobą przed odczytaniem za pośrednictwem plików i wierszy kodu.  
  
 ![Wyświetlanie zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **Poniżej przedstawiono niektóre filmy wideo**:  
  
- [Poznanie zależności w kodzie za pomocą wizualizacji](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
- [Wizualizacja wpływu zmian](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
- [Opis złożonego kodu za pomocą map kodu](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
## <a name="GetStarted"></a> Rozpoczynanie pracy z mapami kodu  
 **Aby używać mapy kodu, należy albo**:  
  
- Visual Studio Enterprise: Tworzenie map kodu z edytora kodu, w Eksploratorze rozwiązań, widoku klas lub przeglądarki obiektów.  
  
- Visual Studio Professional: Otwieranie map kodu, wprowadzanie ograniczonych zmian edycyjnych i przechodzenie do kodu.  
  
> [!WARNING]
> Przed udostępnieniem map utworzone w programie Visual Studio Enterprise z innymi osobami, którzy korzystają z programu Visual Studio Professional, upewnij się, że wszystkie elementy na mapie (takich jak elementy ukryte, rozwinięte grupy i łącza grupy współzależności) są widoczne.  
  
 **Można mapować zależności dla kodu w tych językach**:  
  
- Visual C# .NET lub Visual Basic .NET z rozwiązaniem lub zestawy (.dll lub .exe)  
  
- Macierzysty lub zarządzany kod C lub C++ w projektach języka Visual C++, pliki nagłówkowe (.h lub `#include`), lub pliki binarne  
  
- Projekty X ++ i zestawy wykonane z modułów .NET dla systemu Microsoft Dynamics AX  
  
  **Uwaga:** Dla projektów innych niż C# lub Visual Basic .NET, dostępnych jest mniej opcji Uruchamianie mapy kodu lub dodawania elementów do istniejącej mapy kodu. Nie można na przykład, kliknij prawym przyciskiem myszy obiekt w edytorze tekstów projektu w języku C++ i dodać go do mapy kodu. Jednak możesz przeciągać i upuszczać elementy poszczególnych kodu lub pliki w Eksploratorze rozwiązań, widoku klas i przeglądarki obiektów.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Aby wyświetlić ogólne zależności między rozwiązania  
  
1. Otwórz **architektury** menu.  
  
2. Czy po prostu otworzyć rozwiązanie i jeszcze nie zostało utworzone, czy kod został zmieniony od czasu ostatniego utworzoną go, wybierz polecenie **Generuj mapę kodu dla rozwiązania**.  
  
3. Jeśli Twój kod nie została zmieniona od czasu ostatniego utworzoną go, wybierz opcję **Generuj mapę kodu dla rozwiązania bez kompilowania** można pobrać zwiększa wydajność podczas tworzenia mapy.  
  
4. [Zobacz ogólne zależności](#SeeOverviewSource) Aby dowiedzieć się jak możesz użyć mapy kodu, aby wyświetlić ogólne zależności w rozwiązaniu.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>Aby wyświetlić konkretne zależności w ramach rozwiązania usługi  
  
1. Twoje rozwiązanie zostało załadowane, otwórz **Eksploratora rozwiązań**.  
  
2. Wybierz wszystkie projekty, odwołania do zestawów, folderów, pliki, typy lub elementy członkowskie, które ma być mapowany.  
  
3. Na **Eksploratora rozwiązań** narzędzi, wybierz **Pokaż na mapie kodu**![Utwórz nowy wykres z wybrane węzły przycisk](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Otwórz menu skrótów i wybierając polecenie lub **Pokaż na mapie kodu**. Można również przeciągać elementy z widoku klas lub przeglądarki obiektów do nowej lub istniejącej mapy kodu.  
  
4. [Zobacz określonych zależności](#SeeSpecificSource) Aby dowiedzieć się jak możesz użyć mapy kodu, aby wyświetlić konkretne zależności w ramach rozwiązania usługi.  
  
### <a name="CreateEmptyMap"></a> Aby dodać nowej mapy kodu puste do rozwiązania  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła najwyższego poziomu rozwiązania. Wybierz **Dodaj** wybierz **nowy element**.  
  
2. W obszarze **zainstalowane**, wybierz **ogólne**.  
  
3. W okienku po prawej stronie wybierz **dokument kierowanego wykresu** , a następnie wybierz **Dodaj**.  
  
     Masz teraz pusta mapa, która pojawia się w swoim rozwiązaniu **elementy rozwiązania** folderu.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Aby utworzyć nowej mapy kodu puste bez dodawania go do rozwiązania  
  
1. Otwórz **architektury** menu i wybrać **nowej mapy kodu**.  
  
     \- lub —  
  
2. Otwórz **pliku** menu i wybierz polecenie **New** wybierz **pliku**.  
  
3. W obszarze **zainstalowane**, wybierz **ogólne**.  
  
4. W okienku po prawej stronie wybierz **dokument kierowanego wykresu** , a następnie wybierz **Otwórz**.  
  
     Teraz masz mapę puste nie są wyświetlane w folderach tego rozwiązania.  
  
## <a name="SeeOverviewSource"></a> Zobacz ogólne zależności  
  
### <a name="OverviewSource"></a> Wyświetlanie zależności w rozwiązaniu  
  
1. Na **architektury** menu, wybierz **Generuj mapę kodu dla rozwiązania**.  
  
    ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
    Możesz uzyskać mapę, pokazujący zestawy najwyższego poziomu i zagregowane łącza między nimi. Szerszy łącze zagregowane, więcej zależności reprezentuje.  
  
2. Użyj **legendy** znajdujący się na pasku narzędzi mapy kodu, aby pokazać lub ukryć listy ikony typu projektu (na przykład Test sieci Web i projekt telefonu), elementy kodu (na przykład klas, metod i właściwości) i typy relacji (np. dziedziczy z Implementuje i wywołania).  
  
    ![TOP&#45;wykres zależności na poziomie zestawów](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
    To przykładowe rozwiązanie zawiera foldery rozwiązania (**testy** i **składniki**), projekty testowe, projekty sieci Web i zestawów. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grup*, które można rozwijać i zwijać. **Zewnętrzne** grupa zawiera wszystkie rozwiązania, w tym zależności platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie system typów podstawowych są ukryte na mapie, aby zwiększyć czytelność.  
  
3. Aby przejść do mapy, rozwiń węzeł grupy, które reprezentują projektów i zespołów. Można rozwinąć wszystko, naciskając klawisz **CTRL + A** zaznacz wszystkie węzły jak i następnie wybierając **grupy**, **rozwiń** z menu skrótów.  
  
    ![Rozwinięcie wszystkich grup w mapie kodu](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4. Jednak może to nie być przydatne w przypadku dużych rozwiązań. W rzeczywistości złożonych rozwiązań ograniczenia pamięci może uniemożliwić rozwinięcie wszystkich grup. Zamiast tego aby wyświetlić wewnątrz jednego węzła, je rozwinąć. Umieść wskaźnik myszy na węzeł, a następnie kliknij przycisk cudzysłów ostrokątny (strzałkę), gdy pojawia się.  
  
    ![Rozwinięcie węzła w mapie kodu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
    Lub za pomocą klawiatury, wybierając element, a następnie naciskając klawisz znaku plus (**+**). Aby zapoznać się z bardziej poziomy kodu, zrób to samo dla przestrzeni nazw, typów i elementów członkowskich.  
  
   > [!TIP]
   > Aby uzyskać więcej informacji o pracy z kodem mapy za pomocą myszy, klawiatury i dotyku, zobacz [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).  
  
5. Aby uprościć mapy i skupić się na poszczególnych częściach, wybierz opcję **filtry** na pasku narzędzi Mapa kodu i po prostu wybierz typy węzłów i łączy Cię interesuje. Na przykład można ukryć kontenerów w folderze rozwiązania i zestawu.  
  
    ![Uprość mapy, filtrując kontenery](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
    Aby uprościć mapy, możesz również ukrywać lub usuwanie poszczególne grupy i elementy z mapy, bez wywierania wpływu na podstawowy kod rozwiązania.  
  
6. Aby wyświetlić relacje między elementami, zaznacz je w mapie. Kolory łącza typy relacji wskazują, jak pokazano w **legendy** okienka.  
  
    ![Wyświetlanie zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
    W tym przykładzie purpurowy łącza są wywołania kropkowana łącza są odwołaniami i dostęp do pola są światła łącza niebieski. Zielony mogą to być dziedziczenie lub mogą one być *zagregowane łącza* wskazujące więcej niż jeden typ relacji (lub *kategorii*).  
  
   > [!TIP]
   > Jeśli zostanie wyświetlony link zielony, nie może oznaczać jest po prostu relacji dziedziczenia. Może również być wywołania metody, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy łączy, użyj pól wyboru w **filtry** okienko, aby ukryć typy nie są zainteresowani.  
  
7. Aby uzyskać więcej informacji dotyczących łącza lub elementu, umieść kursor na on, aż pojawi się etykietka narzędzia. To pokazuje szczegóły elementu kodu lub kategorii, które reprezentuje łącze.  
  
    ![Pokaż kategorie relacji](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8. Aby sprawdzić elementy i zależności reprezentowane przez łącze zagregowane, najpierw zaznacz łącze, a następnie otwórz jego menu skrótów. Wybierz **Pokaż linki** (lub **Pokaż linki na nowej mapie kodu**). To rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które uczestniczą w linku.  
  
9. Chcesz się skupić w określonych części mapy, możesz w dalszym ciągu usunąć elementy, których nie chcesz. Na przykład, aby przejść do widoku klas i składowych, po prostu filtrować wszystkie węzły przestrzeni nazw w **filtry** okienka.  
  
     ![Przechodzenie do szczegółów do klas i składowych poziomu](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Innym sposobem, aby skoncentrować się na mapie złożone rozwiązanie jest generowanie nowej mapy zawierająca wybrane elementy z istniejącej mapy. Przytrzymaj **CTRL** podczas wybierania elementów chcesz skupić się na, otwórz menu skrótów i wybierz polecenie **nowy wykres na podstawie wyboru**.  
  
     ![Pokaż wybrane elementy na nowej mapie kodu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. Kontekst zawierający są przenoszone do nowej mapy. Ukryj foldery rozwiązania i innych kontenerów nie chcesz, aby zobaczyć, za pomocą **filtry** okienka.  
  
     ![Filtruj kontener, aby uprościć widok](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Rozwiń grupy, a następnie wybierz elementy na mapie, aby wyświetlać relacje.  
  
     ![Wybierz elementy, aby wyświetlać relacje](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
    Zobacz też:  
  
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)  
  
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
- Wyszukiwanie potencjalnych problemów w kodzie, poprzez [uruchomiony analizator](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
### <a name="OverviewCompiled"></a> Wyświetlanie zależności w zestawy lub pliki binarne  
  
1. [Utwórz mapę kodu pusty](#GetStarted), lub otworzyć istniejącej mapy kodu (plik .dgml).  
  
2. Przeciągnij zestawy lub pliki binarne, które chcesz mapować z poza programem Visual Studio na mapę. Na przykład przeciągać zestawy lub pliki binarne z Eksploratora Windows lub Eksploratora plików.  
  
> [!NOTE]
> Tylko wtedy, gdy na tym samym poziomie uprawnień kontroli dostępu użytkownika (UAC) są uruchomione i programu Visual Studio można przeciągnąć z zestawy lub pliki binarne z Eksploratora Windows lub Eksploratora plików. Na przykład jeśli jest włączona funkcja Kontrola konta użytkownika i korzystasz z programu Visual Studio jako Administrator, Eksplorator Windows lub Eksploratora plików zablokuje operację przeciągania. Aby obejść ten problem, upewnij się, że zarówno są uruchomione na tym samym poziomie uprawnień lub wyłączyć funkcji Kontrola konta użytkownika.  
  
## <a name="SeeSpecificSource"></a> Zobacz określonych zależności  
 Na przykład załóżmy, że Przegląd kodu do wykonania w niektórych plików z oczekującymi zmianami. Aby wyświetlić zależności w tych zmian, można utworzyć mapy kodu z tych plików.  
  
 ![Pokaż określonych zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Zobacz określonych zależności w rozwiązaniu  
  
1. Otwórz **Eksploratora rozwiązań**. Wybierz projekty, odwołania do zestawów, folderów, plików, typów i elementów członkowskich, które Cię interesują. Aby znaleźć elementy z zależnościami dotyczącymi typów lub członków, otwórz typ lub menu skrótów elementu członkowskiego z **Eksploratora rozwiązań**. Wybierz typ zależności, a następnie wybierz wyniki.  
  
2. Mapowanie elementów i ich elementów członkowskich. Na **Eksploratora rozwiązań** kliknij pasek narzędzi **Pokaż na mapie kodu**![Utwórz nowy wykres z wybrane węzły przycisk](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Wybierz elementy, którą chcesz zamapować](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3. Mapy zawiera wybrane elementy w ramach ich zawierającego zestawów.  
  
     ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     Można również przeciągać elementy z Eksploratora rozwiązań, widoku klas lub przeglądarki obiektów do pustego lub istniejącą mapę kodu. Aby utworzyć pustą mapę, zobacz [utworzyć mapę kodu pusty](#GetStarted). Aby dołączyć hierarchię nadrzędną elementów, naciśnij i przytrzymaj **CTRL** klucza podczas przeciągania elementów lub użyj **obejmują elementy nadrzędne** przycisk na pasku narzędzi mapy kodu, aby określić domyślną akcję.  
  
    > [!NOTE]
    > Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Sklep Windows, elementy te są widoczne na mapie z projektem aktualnie aktywnych aplikacji. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.  
  
4. Aby sprawdzić elementy, je rozwinąć. Przesuń wskaźnik myszy na górze elementu, a następnie kliknij ikonę cudzysłów ostrokątny (strzałkę), gdy się pojawi.  
  
     ![Rozwinięcie węzła w mapie kodu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     Aby rozwinąć wszystkie elementy, zaznacz je przy użyciu **CTRL + A**, a następnie otwórz menu skrótów dla mapy i wybierz **grupy**, **rozwiń**. Jednak ta opcja jest niedostępna, jeśli rozwinięcie wszystkich grup tworzy bezużyteczny mapy lub problemy z pamięcią.  
  
5. W dalszym ciągu rozwijanie elementów, które Cię interesują, schodząc poziom klas i składowych, jeśli jest to wymagane.  
  
     ![Rozwiń grupy na poziomie klas i składowych](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Aby wyświetlić elementy członkowskie, które są w kodzie, ale nie są wyświetlane na mapie, kliknij **ponownie Pobierz elementy podrzędne** ikonę ![ikonę ponownie Pobierz elementy podrzędne](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") u góry lewym rogu grupy.  
  
6. Aby wyświetlić więcej elementów związanych z tymi na mapie, wybierz jedną, a następnie wybierz **Pokaż powiązane** na pasku narzędzi mapy kodu, a następnie wybierz typ elementy pokrewne, aby dodać do mapy. Alternatywnie, wybierz jeden lub więcej elementów, otwórz menu skrótów, a następnie wybierz **Pokaż...** Opcja typu powiązane elementy do dodania do mapy. Na przykład:  
  
     Aby uzyskać **zestawu**, wybierz opcję:  
  
    |||  
    |-|-|  
    |**Pokaż zestawy przywoływane przez ten element**|Dodaj zestawy, do których odwołuje się ten zestaw. Zestawy zewnętrzne pojawiają się w **zewnętrzne** grupy.|  
    |**Pokaż zestawy PRZYWOŁUJĄCE ten element**|Dodaj zestawy w rozwiązaniu odwołującym się do tego zestawu.|  
  
     Dla **przestrzeni nazw**, wybierz **Pokaż zawierający zestaw**, jeśli nie jest widoczna.  
  
     Aby uzyskać **klasy** lub **interfejsu**, wybierz opcję:  
  
    |||  
    |-|-|  
    |**Pokaż typy podstawowe**|Dla klasy dodaj klasę bazową i implementowane interfejsy.<br /><br /> Dla interfejsu dodaj interfejsy podstawowe.|  
    |**Pokaż typy pochodne**|Dla klasy dodaj klasy pochodne.<br /><br /> Dla interfejsu dodaj interfejsy pochodne i implementujące klasy lub struktury.|  
    |**Pokaż typy przywoływane przez ten element**|Dodaj wszystkie klasy i używane przez nie składowe.|  
    |**Pokaż typy PRZYWOŁUJĄCE ten element**|Dodaj wszystkie klasy oraz ich składowe, które używają tej klasy.|  
    |**Pokaż zawierający Namespace**|Dodaj nadrzędna przestrzeń nazw.|  
    |**Pokaż zawierający Namespace i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|  
    |**Pokaż wszystkie typy podstawowe**|Dodaj cyklicznie klasę bazową lub hierarchię interfejsu.|  
    |**Pokaż wszystkie typy pochodne**|Dla klasy dodaj wszystkie klasy pochodne cyklicznie.<br /><br /> Dla interfejsu, dodaj wszystkie interfejsy pochodne i cyklicznie implementujące klasy lub struktury.|  
  
     Aby uzyskać **metoda**, wybierz opcję:  
  
    |||  
    |-|-|  
    |**Pokaż metody, które powoduje to wywołanie**|Dodaj metody, które wywołuje ta metoda.|  
    |**Pokaż pola przywoływane przez ten element**|Dodaj pola, do których odwołuje się ta metoda.|  
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|  
    |**Pokaż zawierający typ, Namespace i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|  
    |**Pokaż przesłonięte metody**|Dla metody, która zastępuje inne metody lub implementuje metodę interfejsu, należy dodać wszystkie metody abstrakcyjne lub wirtualne w klasach bazowych, które są zastępowane, oraz — jeśli istnieje — implementowaną metodę interfejsu.|  
  
     Aby uzyskać **pola** lub **właściwość**, wybierz opcję:  
  
    |||  
    |-|-|  
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|  
    |**Pokaż zawierający typ, Namespace i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|  
  
     ![Pokaż metody wywoływane przez ten element członkowski](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7. Mapa przedstawiono relacje. W tym przykładzie metody wywoływane przez `Find` metoda i ich lokalizacji w rozwiązaniu lub zewnętrznie.  
  
     ![Pokaż określonych zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8. Aby uprościć mapy i skupić się na poszczególnych częściach, wybierz opcję **filtry** na pasku narzędzi Mapa kodu i po prostu wybierz typy węzłów i łączy Cię interesuje. Na przykład Wyłącz wyświetlanie folderów rozwiązania, zestawy i przestrzenie nazw.  
  
     ![Używanie okienka filtru można uproszczenie wyświetlania](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
## <a name="SeeSourceHeader"></a> Zobacz zależności między plikami źródłowymi C i C++ a plikami nagłówkowymi  
 Jeśli chcesz utworzyć pełniejsze mapy dla projektów w języku C++, należy ustawić opcji Przeglądaj informacje kompilatora (**/FR**) w tych projektach. Zobacz [/FR, /Fr (Utwórz. Plik SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. Jeśli wybierzesz **OK**, to ustawienie opcji dla bieżącej mapy. Można ukryć komunikat dla wszystkich nowszych mapy. Możesz ukryć ten komunikat, można wyświetlić ją ponownie. Ustaw następujący klucz rejestru `0` lub Usuń klucz:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**  
  
 Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie nie można utworzyć mapy kodu dla nagłówka (.h lub `#include`) plików, dopóki nie zakończy się aktualizowania bazy danych IntelliSense. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio. Aby rozwiązać problemy i komunikaty, które pojawiają się, ponieważ niektóre ustawienia opcji IntelliSense są wyłączone, zobacz [Rozwiązywanie problemów z mapami kodu C i C++](#Troubleshooting).  
  
- Aby wyświetlić zależności między wszystkie pliki źródłowe i pliki nagłówkowe w rozwiązaniu na **architektury** menu, wybierz **generowania wykresu z pliki dołączane**.  
  
     ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")  
  
- Aby wyświetlić zależności między aktualnie otwarty plik oraz pokrewne pliki źródłowe i pliki nagłówkowe, otwórz plik źródłowy lub plik nagłówkowy. Otwórz menu skrótów plików w dowolne miejsce wewnątrz pliku. Wybierz **Generowanie grafu plików dołączanych**.  
  
     ![Pierwszy&#45;wykres zależności na poziomie pliku .h](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
### <a name="Troubleshooting"></a> Rozwiązywanie problemów z mapami kodu C i C++  
 Te elementy nie są obsługiwane dla kodu C i C++:  
  
- Typy podstawowe nie pojawiają się na mapach, zawierających hierarchię nadrzędną.  
  
- Większość **Pokaż** elementów menu nie są dostępne dla kodu C i C++.  
  
  Te problemy mogą się zdarzyć, gdy tworzone mapy kodu dla kodu C i C++:  
  
|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|  
|---------------|------------------------|--------------------|  
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Napraw błędy kompilacji, które wystąpiły, a następnie ponownie wygenerować mapę.|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przestaje odpowiadać przy próbie wygenerowania mapy kodu z **architektury** menu.|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|  
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia opcji IntelliSense mogą być wyłączone w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **opcje** okno dialogowe.|Włącz te ustawienia.<br /><br /> Zobacz [opcje, Edytor tekstu, C/C++, zaawansowane](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Komunikat **nieznane metody** w węźle metody zostanie wyświetlony.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz **/Fixed: No** opcji w konsolidatorze.<br /><br /> Zobacz [/Fixed (stały adres podstawowy)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|  
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz **/DEBUG** opcji w konsolidatorze.<br /><br /> Zobacz [/DEBUG (generowanie informacji o debugowaniu)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|  
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|  
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli **/pdbstripped** w konsolidatorze użyto opcji, zamiast dołączyć kompletny plik .pdb.<br /><br /> Zobacz [/pdbstripped (Usuń symbole prywatne)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Jeśli element wywołujący jest sekcją thunk, spróbuj użyć `_declspec(dllimport)` Aby uniknąć osadzenia.<br /><br /> Zobacz:<br /><br /> -   [Ograniczenia i reguły ogólne](https://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)](https://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](https://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|  
  
## <a name="RenderMoreQuickly"></a> Wprowadź kod, który map render szybciej  
 Podczas generowania mapy po raz pierwszy, program Visual Studio indeksuje wszystkie zależności, które znajdzie. Ten proces może zająć trochę czasu, szczególnie w przypadku dużych rozwiązań, ale poprawi wydajność później. Jeśli kod ulegnie zmianie, program Visual Studio indeksuje ponownie tylko zaktualizowany kod. Aby zminimalizować czas potrzebny na mapie, aby zakończyć renderowania, należy rozważyć następujące kwestie:  
  
- [Mapowanie zależności, które Cię interesują.](#SeeSpecificSource)  
  
- Przed wygenerowaniem mapy dla całego rozwiązania Zmniejsz zakres rozwiązania.  
  
- Wyłącz automatyczne kompilacji w celu rozwiązania obejmującego **pominięcia kompilacji** przycisk na pasku narzędzi mapy kodu.  
  
- Wyłącz opcję automatycznego dodawania elementów nadrzędnych za pomocą **obejmują elementy nadrzędne** przycisk na pasku narzędzi mapy kodu.  
  
- Edytuj plik mapy kodu bezpośrednio po to, aby usunąć węzły i łącza, które nie są potrzebne. Zmiana na mapie nie ma wpływu na odpowiedni kod. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
  ![Przyciski pominięcia kompilacji i obejmują elementy nadrzędne](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
  Mimo że program Visual Studio można uruchomić z 1 GB pamięci, zalecane jest, aby komputer miał co najmniej 2 GB pamięci, aby uniknąć opóźnień, podczas gdy program Visual Studio tworzy indeks kodu i generuje mapy.  
  
  Może upłynąć więcej czasu na tworzenie map lub dodawanie elementów do mapy za pomocą Eksploratora rozwiązań, gdy element projektu **Kopiuj do katalogu wyjściowego** właściwość jest ustawiona na **zawsze Kopiuj**. Może to spowodować problemy z kompilacjami przyrostowymi i każdorazowe ponowne kompilowanie projektu przez program Visual Studio. Aby zwiększyć wydajność, należy zmienić tę właściwość na **Kopiuj Jeśli nowszy** lub `PreserveNewest`. Zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).  
  
  Ukończone mapy pokażą zależności tylko w przypadku kodu pomyślnie skompilowane. Jeśli wystąpią błędy kompilacji dla niektórych składników, te błędy są wyświetlane na mapie. Upewnij się, że składnik rzeczywiście kompiluje i ma zależności od tego, przed wprowadzeniem decyzji architektury oparte na mapie.  
  
## <a name="SavingExporting"></a> Udostępnianie map kodu  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Dzielić się mapami z innymi użytkownikami programu Visual Studio  
 Użyj **pliku** menu, aby zapisać na mapie.  
  
 —lub—  
  
 Aby zapisać mapy jako część określonego projektu, na pasku narzędzi mapy, wybierz **udziału**, **przenieść** \< *CodeMapName*>**.dgml do**, a następnie wybierz projekt, gdzie chcesz zapisać na mapie.  
  
 ![Przenieś mapę do innego projektu](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Program Visual Studio zapisuje mapy jako plik .dgml, który można udostępniać innym użytkownikom programu Visual Studio Enterprise i Visual Studio Professional.  
  
> [!NOTE]
> Przed udostępnieniem map użytkownikom korzystającym z programu Visual Studio Professional, pamiętaj Rozwiń wszystkie grupy, Pokaż ukryte węzły i łącza między grupami i Pobierz wszelkie usunięte węzły, które inni mają zobaczyć na mapie. W przeciwnym razie inni użytkownicy nie będą mogli zobaczyć tych elementów.  
>   
> Po zapisaniu mapę, która znajduje się w projekcie modelowania lub został skopiowany z projektu modelowania w inne miejsce, mógł wystąpić następujący błąd:  
>   
> "Nie można zapisać *fileName* poza katalogiem projektu. Elementy połączone nie są obsługiwane”.  
>   
> Program Visual Studio pokazuje błąd, ale mimo to tworzy zapisaną wersję. Aby uniknąć tego błędu, należy utworzyć mapy poza projektem modelowania. Można następnie zapisać go w dowolnej lokalizacji. Skopiowanie pliku do innej lokalizacji w rozwiązaniu, a następnie próba zapisu zakończą się niepowodzeniem.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Eksportuj mapy jako obraz, aby można było skopiować do innych aplikacji, takich jak Microsoft Word lub PowerPoint  
  
1. Na pasku narzędzi mapy kodu Wybierz **udziału**, **poczty E-mail jako obraz** lub **Kopiuj obraz**.  
  
2. Wklej obraz do innej aplikacji.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Eksportuj mapy jako plik XPS, tak aby był widoczny w XML lub XAML przeglądarki, takich jak Internet Explorer  
  
1. Na pasku narzędzi mapy kodu Wybierz **udziału**, **wiadomości E-mail jako przenośny dokument XPS** lub **Zapisz jako przenośny dokument XPS**.  
  
2. Przejdź do której chcesz zapisać plik.  
  
3. Nazwa mapy kodu. Upewnij się, że **Zapisz jako typ** pole jest ustawiona na **pliki XPS (\*.xps)**. Wybierz polecenie **Zapisz**.  
  
## <a name="what-else-can-i-do"></a>Co jeszcze można zrobić?  
  
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)  
  
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)  
  
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
