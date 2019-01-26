---
title: Mapy kodu
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9d7f438b125e492069073675609757dd9d484427
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950484"
---
# <a name="map-dependencies-with-code-maps"></a>Mapowanie zależności z mapami kodu

Można wizualizować zależności w kodzie przez utworzenie mapy kodu. Mapy kodu pomogą Ci sprawdzić, jak kod dopasowuje się ze sobą przed odczytaniem za pośrednictwem plików i wierszy kodu.

![Wyświetlanie zależności Dzięki mapom kodu w programie Visual Studio](../modeling/media/codemapsmainintro.png)

Aby tworzyć i edytować map kodu, należy programu Visual Studio Enterprise edition. W Visual Studio Community i Professional może otwierać diagramy, które były generowane w wersji Enterprise edition, ale nie można ich edytować.

> [!NOTE]
> Przed udostępnieniem map utworzone w programie Visual Studio Enterprise z innymi osobami, którzy korzystają z programu Visual Studio Professional, upewnij się, że wszystkie elementy na mapie (takich jak elementy ukryte, rozwinięte grupy i łącza grupy współzależności) są widoczne.

Można mapować zależności dla kodu w tych językach:

- Visual C# lub Visual Basic z rozwiązaniem lub zestawy (*.dll* lub *.exe*)

- Macierzysty lub zarządzany kod C lub C++ w projektach języka Visual C++, pliki nagłówkowe (*.h* lub `#include`), lub pliki binarne

- Projekty X ++ i zestawy wykonane z modułów .NET dla systemu Microsoft Dynamics AX

> [!NOTE]
> Dla projektów innych niż C# lub Visual Basic istnieją mniej opcji do uruchamiania mapę kodu i dodawania elementów do istniejącej mapy kodu. Nie można na przykład, kliknij prawym przyciskiem myszy obiekt w edytorze tekstów projektu w języku C++ i dodać go do mapy kodu. Jednak możesz przeciągać i upuszczać elementy poszczególnych kodu lub pliki z **Eksploratora rozwiązań**, **Widok klas**, i **przeglądarki obiektów**.

## <a name="install-code-map-and-live-dependency-validation"></a>Mapa kodu instalacja i weryfikacja zależności na żywo

Aby utworzyć mapę kodu w programie Visual Studio 2017, należy najpierw zainstalować **mapy kodu** i **walidację aktywnych zależności** składników:

1. Otwórz **Instalatora programu Visual Studio**. Możesz go otworzyć w menu Windows Start lub w programie Visual Studio, wybierając **narzędzia** > **Pobierz narzędzia i funkcje**.

1. Wybierz **poszczególne składniki** kartę.

1. Przewiń w dół do **kodu narzędzia** i wybierz pozycję **mapy kodu** i **walidację aktywnych zależności**.

   ![Mapa kodu i walidację aktywnych zależności składników w Instalatorze programu Visual Studio](media/modeling-components.png)

1. Wybierz **zmodyfikować**.

   **Mapy kodu** i **walidację aktywnych zależności** składniki rozpoczęcie instalacji. Może być konieczne zamknięcie programu Visual Studio.

## <a name="add-a-code-map"></a>Dodaj mapę kodu

Można utworzyć mapę pusty kod i przeciągnij elementy na nim, odwołania do zestawów, pliki i foldery, lub możesz wygenerować mapę kodu dla wszystkich lub część rozwiązania.

Aby dodać mapę pusty kod:

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła najwyższego poziomu rozwiązania. Wybierz **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okna dialogowego, w obszarze **zainstalowane**, wybierz **ogólne** kategorii.

3. Wybierz **Document(.dgml) wykres kierowany** szablonu, a następnie wybierz **Dodaj**.

   > [!TIP]
   > Ten szablon nie może występować w kolejności alfabetycznej, więc przewiń w dół do dolnej części listy szablonów, jeśli jej nie widzisz.

   Pusta Mapa pojawia się w swoim rozwiązaniu **elementy rozwiązania** folderu.

Podobnie, można utworzyć nowy plik mapy kodu bez dodawania go do rozwiązania, wybierając **architektury** > **nowej mapy kodu** lub **pliku**  >  **Nowe** > **pliku**.

## <a name="generate-a-code-map-for-your-solution"></a>Generuj mapę kodu dla rozwiązania

Aby wyświetlić wszystkie zależności w rozwiązaniu:

1. Na pasku menu wybierz **architektury** > **Generuj mapę kodu dla rozwiązania**. Jeśli Twój kod nie została zmieniona od czasu ostatniego utworzoną go, możesz wybrać **architektury** > **Generuj mapę kodu dla rozwiązania bez kompilowania** zamiast tego.

   ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png)

   Mapa jest generowany, pokazujący zestawy najwyższego poziomu i zagregowane łącza między nimi. Szerszy łącze zagregowane, więcej zależności reprezentuje.

2. Użyj **legendy** znajdujący się na pasku narzędzi mapy kodu, aby pokazać lub ukryć listy ikony typu projektu (na przykład Test sieci Web i projekt telefonu), elementy kodu (na przykład klas, metod i właściwości) i typy relacji (np. dziedziczy z Implementuje i wywołania).

   ![Wykres zależności najwyższego poziomu zestawów](../modeling/media/dependencygraph_toplevelassemblies.png)

   To przykładowe rozwiązanie zawiera foldery rozwiązania (**testy** i **składniki**), projekty testowe, projekty sieci Web i zestawów. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grup*, które można rozwijać i zwijać. **Zewnętrzne** grupa zawiera wszystkie rozwiązania, w tym zależności platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie system typów podstawowych są ukryte na mapie, aby zwiększyć czytelność.

3. Aby przejść do mapy, rozwiń węzeł grupy, które reprezentują projektów i zespołów. Można rozwinąć wszystko, naciskając klawisz **CTRL + A** zaznacz wszystkie węzły jak i następnie wybierając **grupy**, **rozwiń** z menu skrótów.

   ![Rozwinięcie wszystkich grup w mapie kodu](../modeling/media/codemapsexpandallgroups.png)

4. Jednak może to nie być przydatne w przypadku dużych rozwiązań. W rzeczywistości złożonych rozwiązań ograniczenia pamięci może uniemożliwić rozwinięcie wszystkich grup. Zamiast tego aby wyświetlić wewnątrz jednego węzła, je rozwinąć. Umieść wskaźnik myszy na węzeł, a następnie kliknij przycisk cudzysłów ostrokątny (strzałkę), gdy pojawia się.

   ![Rozwinięcie węzła w mapie kodu](../modeling/media/dependencygraph_containment.png)

   Lub za pomocą klawiatury, wybierając element, a następnie naciskając klawisz znaku plus (**+**). Aby zapoznać się z bardziej poziomy kodu, zrób to samo dla przestrzeni nazw, typów i elementów członkowskich.

   > [!TIP]
   > Aby uzyskać więcej informacji na temat pracy z kodem mapy za pomocą myszy, klawiatury i dotyku, zobacz [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

5. Aby uprościć mapy i skupić się na poszczególnych częściach, wybierz opcję **filtry** na pasku narzędzi Mapa kodu i po prostu wybierz typy węzłów i łączy Cię interesuje. Na przykład można ukryć kontenerów w folderze rozwiązania i zestawu.

   ![Uprość mapy, filtrując kontenerów](../modeling/media/codemapsfilterfoldersassemblies.png)

   Aby uprościć mapy, możesz również ukrywać lub usuwanie poszczególne grupy i elementy z mapy, bez wywierania wpływu na podstawowy kod rozwiązania.

6. Aby wyświetlić relacje między elementami, zaznacz je w mapie. Kolory łącza typy relacji wskazują, jak pokazano w **legendy** okienka.

   ![Wyświetlanie zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png)

   W tym przykładzie purpurowy łącza są wywołania kropkowana łącza są odwołaniami i dostęp do pola są światła łącza niebieski. Zielony mogą to być dziedziczenie lub mogą one być *zagregowane łącza* wskazujące więcej niż jeden typ relacji (lub *kategorii*).

   > [!TIP]
   > Jeśli zostanie wyświetlony link zielony, nie może oznaczać jest po prostu relacji dziedziczenia. Może również być wywołania metody, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy łączy, użyj pól wyboru w **filtry** okienko, aby ukryć typy nie są zainteresowani.

7. Aby uzyskać więcej informacji dotyczących łącza lub elementu, umieść kursor na on, aż pojawi się etykietka narzędzia. To pokazuje szczegóły elementu kodu lub kategorii, które reprezentuje łącze.

   ![Pokaż kategorie relacji](../modeling/media/codemapsshowlinkcatgories.png)

8. Aby sprawdzić elementy i zależności reprezentowane przez łącze zagregowane, najpierw zaznacz łącze, a następnie otwórz jego menu skrótów. Wybierz **Pokaż linki** (lub **Pokaż linki na nowej mapie kodu**). To rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które uczestniczą w linku.

9. Chcesz się skupić w określonych części mapy, możesz w dalszym ciągu usunąć elementy, których nie chcesz. Na przykład, aby przejść do widoku klas i składowych, po prostu filtrować wszystkie węzły przestrzeni nazw w **filtry** okienka.

   ![Przechodzenie do szczegółów do poziomu klas i składowych](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Innym sposobem, aby skoncentrować się na mapie złożone rozwiązanie jest generowanie nowej mapy zawierająca wybrane elementy z istniejącej mapy. Przytrzymaj **Ctrl** podczas wybierania elementów chcesz skupić się na, otwórz menu skrótów i wybierz polecenie **nowy wykres na podstawie wyboru**.

    ![Pokaż wybrane elementy na nowej mapie kodu](../modeling/media/codemapsshowonnewmap.png)

11. Kontekst zawierający są przenoszone do nowej mapy. Ukryj foldery rozwiązania i innych kontenerów nie chcesz, aby zobaczyć, za pomocą **filtry** okienka.

    ![Filtruj kontener, aby uprościć widok](../modeling/media/codemapsexpandnewgroups.png)

12. Rozwiń grupy, a następnie wybierz elementy na mapie, aby wyświetlać relacje.

    ![Wybierz elementy, aby wyświetlać relacje](../modeling/media/codemapsviewnewrelationships.png)

Zobacz też:

- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Wyszukiwanie potencjalnych problemów w kodzie, poprzez [uruchamiania analizatora](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Wyświetlanie określonych zależności na mapie kodu

Załóżmy, że Przegląd kodu do wykonania w niektórych plików z oczekującymi zmianami. Aby wyświetlić zależności w tych zmian, można utworzyć mapy kodu z tych plików.

   ![Pokaż określonych zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

1. W **Eksploratora rozwiązań**, wybierz projekty, odwołania do zestawów, folderów, plików, typów lub elementów członkowskich, które ma być mapowany.

   ![Wybierz elementy, które chcesz mapować](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na **Eksploratora rozwiązań** narzędzi, wybierz **Pokaż na mapie kodu** ![Utwórz nowy wykres z wybrane węzły przycisk](../modeling/media/createnewgraphfromselectedbutton.gif). Lub, otwórz menu skrótów dla jednego lub grupę elementów i wybierz polecenie **Pokaż na mapie kodu**.

   Można również przeciągać elementy z **Eksploratora rozwiązań**, **Widok klas**, lub **przeglądarki obiektów**, do [nowe](#add-a-code-map) lub istniejącego kodu mapy. Aby dołączyć hierarchię nadrzędną elementów, naciśnij i przytrzymaj **Ctrl** klucza podczas przeciągania elementów lub użyj **obejmują elementy nadrzędne** przycisk na pasku narzędzi mapy kodu, aby określić domyślną akcję. Można również przeciągać pliki zestawu z poza programem Visual Studio, takie jak, z **Eksplorator Windows**.

   > [!NOTE]
   > Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Microsoft Store, elementy te są widoczne na mapie z projektem aktualnie aktywnych aplikacji. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

3. Mapy zawiera wybrane elementy w ramach ich zawierającego zestawów.

   ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Aby sprawdzić elementy, je rozwinąć. Przesuń wskaźnik myszy na górze elementu, a następnie kliknij ikonę cudzysłów ostrokątny (strzałkę), gdy się pojawi.

   ![Rozwiń węzeł na mapie kodu](../modeling/media/dependencygraph_containment.png)

   Aby rozwinąć wszystkie elementy, zaznacz je przy użyciu **Ctrl**+**A**, a następnie otwórz menu skrótów dla mapy i wybierz **grupy**  >   **Rozwiń**. Jednak ta opcja jest niedostępna, jeśli rozwinięcie wszystkich grup tworzy bezużyteczny mapy lub problemy z pamięcią.

5. W dalszym ciągu rozwijanie elementów, które Cię interesują, schodząc poziom klas i składowych, jeśli to konieczne.

   ![Rozwiń grupy na poziomie klas i składowych](../modeling/media/codemapsexpandtoclassandmember.png)

   Aby wyświetlić elementy członkowskie, które są w kodzie, ale nie są wyświetlane na mapie, kliknij **ponownie Pobierz elementy podrzędne** ikonę ![ikonę ponownie Pobierz elementy podrzędne](../modeling/media/dependencygraph_deletednodesicon.png) w lewym górnym rogu grupy.

6. Aby wyświetlić więcej elementów związanych z tymi na mapie, wybierz jedną, a następnie wybierz **Pokaż powiązane** na pasku narzędzi mapy kodu, a następnie wybierz typ elementy pokrewne, aby dodać do mapy. Alternatywnie, wybierz jeden lub więcej elementów, otwórz menu skrótów, a następnie wybierz **Pokaż** opcję dla typu powiązanych elementów, aby dodać do mapy. Na przykład:

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

    ![Pokaż metody wywoływane przez ten element członkowski](../modeling/media/codemapsshowrelatedmethods.png)

7. Mapa przedstawiono relacje. W tym przykładzie mapy zawiera metody wywoływane przez `Find` metody i ich lokalizacji w rozwiązaniu lub zewnętrznie.

   ![Pokaż określonych zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Aby uprościć mapy i skupić się na poszczególnych częściach, wybierz opcję **filtry** na pasku narzędzi Mapa kodu i po prostu wybierz typy węzłów i łączy Cię interesuje. Na przykład Wyłącz wyświetlanie folderów rozwiązania, zestawy i przestrzenie nazw.

   ![Używanie okienka filtru można uproszczenie wyświetlania](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Zobacz także

- [Wideo: Poznawanie projektu na podstawie kodu dzięki mapom kodu w programie Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)]
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
