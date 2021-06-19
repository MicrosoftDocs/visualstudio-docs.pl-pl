---
title: Wizualizowanie zależności za pomocą map kodu
description: Dowiedz się, jak mapy kodu pomagają zobaczyć, jak kod pasuje do siebie bez konieczności odczytywania plików i wierszy kodu.
ms.custom: SEO-VS-2020
ms.date: 05/16/2021
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d33e3d882d25045802f2c015c88b87b970d9d04e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390440"
---
# <a name="map-dependencies-with-code-maps"></a>Mapowanie zależności za pomocą map kodu

W tym artykule dowiesz się, jak wizualizować zależności w kodzie za pomocą map kodu.

## <a name="what-are-code-maps"></a>Co to są mapy kodu?

W Visual Studio mapy kodu pomagają szybciej zobaczyć, jak kod programu pasuje do siebie bez konieczności odczytywania plików i wierszy kodu.  Za pomocą tych map można zobaczyć organizację i relacje w kodzie, w tym jego strukturę i zależności, sposób jej aktualizowania oraz oszacować koszt proponowanych zmian.

![Wyświetlanie zależności za pomocą map kodu w Visual Studio](../modeling/media/codemapsmainintro.png)

Zależności dla kodu można mapować w tych językach:

- Visual C# lub Visual Basic w rozwiązaniu lub zestawach *(*.dlllub *.exe*)

- Natywny lub zarządzany kod C lub C++ w projektach Visual C++, plikach nagłówkowych *(h* lub `#include` ) lub plikach binarnych

- Projekty i zestawy języka X++ wykonane z modułów platformy .NET dla programu Microsoft Dynamics AX

> [!NOTE]
> W przypadku projektów innych niż C# lub Visual Basic dostępnych jest mniej opcji uruchamiania mapy kodu lub dodawania elementów do istniejącej mapy kodu. Na przykład nie można kliknąć prawym przyciskiem myszy obiektu w edytorze tekstów projektu języka C++ i dodać go do mapy kodu. Można jednak przeciągać i upuszczać poszczególne elementy kodu lub pliki z Eksplorator rozwiązań **,** **Widok klasy** i **Przeglądarki obiektów**.

## <a name="prerequisites"></a>Wymagania wstępne

Aby utworzyć mapę kodu w Visual Studio, najpierw zainstaluj [składniki **Code Map** i **Live Dependency Validation**](install-architecture-tools.md)

Aby tworzyć i edytować mapy kodu, musisz **Visual Studio Enterprise wersji**. Jednak w Visual Studio Community i Professional można otwierać diagramy wygenerowane w wersji Enterprise, ale nie można ich edytować.

> [!NOTE]
> Przed udostępnieniem map utworzonych w programie Visual Studio Enterprise innym osobom, które używają usługi Visual Studio Professional, upewnij się, że wszystkie elementy na mapie (takie jak ukryte elementy, rozwinięte grupy i linki między grupami) są widoczne.

## <a name="add-a-code-map"></a>Dodawanie mapy kodu

Możesz utworzyć pustą mapę kodu i przeciągnąć na nie elementy, w tym odwołania do zestawu, pliki i foldery, lub wygenerować mapę kodu dla całej lub części rozwiązania.

Aby dodać pustą mapę kodu:

1. W **Eksplorator rozwiązań** otwórz menu skrótów dla węzła rozwiązania najwyższego poziomu. Wybierz **pozycję Dodaj** nowy  >  **element**.

2. W **oknie dialogowym Dodawanie nowego** elementu w **obszarze Zainstalowane** wybierz **kategorię** Ogólne.

3. Wybierz szablon **Directed Graph Document(.dgml),** a następnie wybierz pozycję **Dodaj**.

   > [!TIP]
   > Ten szablon może nie pojawiać się w porządku alfabetycznym, dlatego przewiń listę szablonów w dół, jeśli jej nie widzisz.

   W folderze Elementy rozwiązania rozwiązania zostanie wyświetlona **pusta** mapa.

Podobnie możesz utworzyć nowy plik mapy kodu bez dodawania go do rozwiązania, wybierając pozycję **Architektura** Nowa mapa  >  **kodu** lub **Plik**  >  **Nowy**  >  **plik**.

Więcej informacji:
- [Udostępnianie map kodu](share-code-maps.md)
- [Tworzenie map kodu dla języka C++](code-maps-for-cpp.md)
- [Poprawianie wydajności mapy kodu](code-maps-performance.md)

## <a name="generate-a-code-map-for-your-solution"></a>Generowanie mapy kodu dla rozwiązania

Aby wyświetlić wszystkie zależności w rozwiązaniu:

1. Na pasku menu wybierz pozycję **Architektura**  >  **Generuj mapę kodu dla rozwiązania.** Jeśli kod nie zmienił się od czasu ostatniego sbudowania, możesz zamiast tego wybrać pozycję Architektura Generuj mapę kodu dla rozwiązania  >  **bez budowania.**

   ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png)

   Generowana jest mapa, która pokazuje zestawy najwyższego poziomu i zagregowane łącza między nimi. Im szerszy jest link agregowania, tym więcej zależności reprezentuje.

2. Użyj **przycisku Legenda** na pasku narzędzi mapy kodu, aby wyświetlić lub ukryć listę ikon typu projektu (takich jak Test, Internet i Projekt na telefon), elementów kodu (takich jak klasy, metody i właściwości) oraz typów relacji (takich jak dziedziczy z, implementuje i wywołuje).

   ![Graf zależności najwyższego poziomu zestawów](../modeling/media/dependencygraph_toplevelassemblies.png)

   To przykładowe rozwiązanie zawiera foldery rozwiązań **(testy** i **składniki),** projekty testowe, projekty sieci Web i zestawy. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grupy*, które można rozwijać i zwijać. Grupa **Externals (Elementy zewnętrzne)** zawiera wszystkie elementy spoza rozwiązania, w tym zależności platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie podstawowe typy systemowe są ukryte na mapie w celu zmniejszenia zaśmiecania.

3. Aby przejść do szczegółów mapy, rozwiń grupy reprezentujące projekty i zestawy. Możesz rozwinąć wszystko, naciskając klawisze **CTRL+A,** aby zaznaczyć wszystkie węzły, a następnie wybierając pozycję **Grupuj,** **Rozwiń** z menu skrótów.

   ![Rozszerzanie wszystkich grup na mapie kodu](../modeling/media/codemapsexpandallgroups.png)

4. Jednak może to nie być przydatne w przypadku dużego rozwiązania. W przypadku złożonych rozwiązań ograniczenia pamięci mogą uniemożliwić rozszerzanie wszystkich grup. Zamiast tego, aby zobaczyć wewnątrz pojedynczego węzła, rozwiń go. Przesuń wskaźnik myszy na górę węzła, a następnie kliknij strzałkę w dół, gdy pojawi się.

   ![Rozwijanie węzła na mapie kodu](../modeling/media/dependencygraph_containment.png)

   Możesz też użyć klawiatury, wybierając element, a następnie naciskając klawisz plus ( **+** ). Aby poznać więcej poziomów kodu, zrób to samo dla przestrzeni nazw, typów i elementów członkowskich.

   > [!TIP]
   > Aby uzyskać więcej informacji na temat pracy z mapami kodu przy użyciu myszy, klawiatury i dotyku, zobacz Przeglądanie i zmiana [układu map kodu](../modeling/browse-and-rearrange-code-maps.md).

5. Aby uprościć mapę i skoncentrować  się na poszczególnych częściach, wybierz pozycję Filtry na pasku narzędzi mapy kodu i wybierz tylko typy węzłów i linków, które Cię interesują. Można na przykład ukryć wszystkie kontenery Folder rozwiązania i Zestaw.

   ![Upraszczanie mapy przez filtrowanie kontenerów](../modeling/media/codemapsfilterfoldersassemblies.png)

   Możesz również uprościć mapę, ukrywając lub usuwając poszczególne grupy i elementy z mapy bez wpływu na podstawowy kod rozwiązania.

6. Aby wyświetlić relacje między elementami, wybierz je na mapie. Kolory linków wskazują typy relacji, jak pokazano w **okienku Legenda.**

   ![Wyświetlanie zależności między rozwiązaniami](../modeling/media/codemapsmainintro.png)

   W tym przykładzie fioletowe linki to wywołania, linki kropkowane są odwołaniami, a jasnoniebieskie to linki z polami. Zielone linki mogą być dziedziczeniem lub mogą być linkami *agregowania* wskazującymi więcej niż jeden typ relacji (lub *kategorię*).

   > [!TIP]
   > Jeśli zostanie wyświetlony zielony link, może to nie oznaczać, że istnieje tylko relacja dziedziczenia. Mogą również wystąpić wywołania metod, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy linków, użyj  pól wyboru w okienku Filtry, aby ukryć typy, które Cię nie interesują.

7. Aby uzyskać więcej informacji na temat elementu lub linku, przesuń wskaźnik na jego górę do momentu, gdy pojawi się etykietka narzędzia. To pokazuje szczegóły elementu kodu lub kategorii, które reprezentuje łącze.

   ![Wyświetlanie kategorii relacji](../modeling/media/codemapsshowlinkcatgories.png)

8. Aby zbadać elementy i zależności reprezentowane przez link agregowania, najpierw wybierz link, a następnie otwórz jego menu skrótów. Wybierz **pozycję Pokaż linki do współtworowania** (lub Pokaż linki do **współtworowania na nowej mapie kodu).** Rozwija grupy na obu końcach linku i pokazuje tylko te elementy i zależności, które uczestniczą w linku.

9. Aby skoncentrować się na określonych częściach mapy, możesz nadal usuwać elementy, które Cię nie interesują. Aby na przykład przejść do szczegółów widoku klasy i elementu członkowskiego, wystarczy przefiltrować wszystkie węzły przestrzeni nazw w **okienku** Filtry.

   ![Przechodzenie do przechodzenia do poziomu klasy i członka](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Innym sposobem skoncentrowania się na złożonej mapie rozwiązania jest wygenerowanie nowej mapy zawierającej wybrane elementy z istniejącej mapy. Przytrzymaj **klawisz Ctrl** podczas zaznaczania elementów, na których chcesz skupić uwagę, otwórz menu skrótów i wybierz pozycję **Nowy graf z listy Wybór.**

    ![Pokazywanie wybranych elementów na nowej mapie kodu](../modeling/media/codemapsshowonnewmap.png)

11. Kontekst zawierający jest przekierowyny do nowej mapy. Ukrywaj foldery rozwiązań i inne kontenery, których nie chcesz widzieć, za pomocą **okienka** Filtry.

    ![Filtrowanie kontenerów w celu uproszczenia widoku](../modeling/media/codemapsexpandnewgroups.png)

12. Rozwiń grupy i wybierz elementy na mapie, aby wyświetlić relacje.

    ![Wybieranie elementów w celu wyświetlenia relacji](../modeling/media/codemapsviewnewrelationships.png)

Zobacz również:

- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Znajdowanie potencjalnych problemów w kodzie przez [uruchomienie analizatora](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-dependencies"></a>Wyświetlanie zależności

Załóżmy, że masz przegląd kodu do wykonania w niektórych plikach z oczekującymi zmianami. Aby wyświetlić zależności w tych zmianach, możesz utworzyć mapę kodu na ich pomocą.

   ![Wyświetlanie określonych zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

1. W **Eksplorator rozwiązań** wybierz projekty, odwołania do zestawu, foldery, pliki, typy lub elementy członkowskie, które chcesz mapować.

   ![Wybierz elementy, które chcesz mapować](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na pasku **Eksplorator rozwiązań** wybierz pozycję Pokaż na **mapie** kodu Przycisk Utwórz ![ nowy graf z wybranych węzłów. ](../modeling/media/createnewgraphfromselectedbutton.gif) Możesz też otworzyć menu skrótów dla jednego lub grupy elementów i wybrać pozycję **Pokaż na mapie kodu**.

   Możesz również przeciągać elementy **z** Eksplorator rozwiązań , **Widok klasy** lub **Przeglądarki obiektów** do [nowej lub](#add-a-code-map) istniejącej mapy kodu. Aby uwzględnić hierarchię nadrzędną elementów, naciśnij i przytrzymaj klawisz **Ctrl**  podczas przeciągania elementów lub użyj przycisku Dołącz elementy nadrzędne na pasku narzędzi mapy kodu, aby określić akcję domyślną. Można również przeciągać pliki zestawu spoza Visual Studio, na przykład z **Eksplorator Windows**.

   > [!NOTE]
   > Po dodaniu elementów z projektu, który jest udostępniany w wielu aplikacjach, takich jak Windows Phone lub Microsoft Store, te elementy są wyświetlane na mapie z aktualnie aktywnym projektem aplikacji. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

3. Mapa przedstawia wybrane elementy w ramach ich zawierających zestawy.

   ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Aby eksplorować elementy, rozwiń je. Przesuń wskaźnik myszy na górę elementu, a następnie kliknij ikonę strzałki w dół, gdy zostanie wyświetlony.

   ![Rozwijanie węzła na mapie kodu](../modeling/media/dependencygraph_containment.png)

   Aby rozwinąć wszystkie elementy, zaznacz je za pomocą **klawisza Ctrl** A, a następnie otwórz menu skrótów mapy i + wybierz polecenie **Grupuj**  >  **Rozwiń**. Ta opcja nie jest jednak dostępna, jeśli rozwinięcie wszystkich grup powoduje problemy z mapą lub pamięcią, które nie mogą być używane.

5. W razie potrzeby rozwiń elementy, które Cię interesują, aż do poziomu klasy i członka.

   ![Rozwijanie grup do poziomu klasy i członka](../modeling/media/codemapsexpandtoclassandmember.png)

   Aby wyświetlić elementy członkowskie, które znajdują się w kodzie,  ale nie są wyświetlane na mapie, kliknij ikonę Pobieranie ponownie elementów członkowskich Ikona pobieranie elementów children w lewym górnym rogu ![ ](../modeling/media/dependencygraph_deletednodesicon.png) grupy.

6. Aby wyświetlić więcej elementów powiązanych z elementami  na mapie, wybierz jeden z nich i wybierz pozycję Pokaż powiązane na pasku narzędzi mapy kodu, a następnie wybierz typ powiązanych elementów do dodania do mapy. Alternatywnie wybierz co najmniej jeden element, otwórz menu  skrótów, a następnie wybierz opcję Pokaż dla typu powiązanych elementów do dodania do mapy. Na przykład:

    W przypadku **zestawu** wybierz:

    |Opcja|Opis|
    |-|-|
    |**Pokaż zestawy, do których odwołuje się to**|Dodaj zestawy, do których odwołuje się ten zestaw. Zestawy zewnętrzne są wyświetlane w **grupie Externals (Zewnętrzne).**|
    |**Pokaż zestawy odwołujące się do tego**|Dodaj zestawy w rozwiązaniu odwołującym się do tego zestawu.|

    W przypadku **przestrzeni nazw** wybierz pozycję Pokaż **zawierający zestaw**, jeśli nie jest widoczna.

    Dla klasy **lub** **interfejsu** wybierz:

    |Opcja|Opis|
    |-|-|
    |**Pokaż typy podstawowe**|Dla klasy dodaj klasę bazową i implementowane interfejsy.<br /><br /> Dla interfejsu dodaj interfejsy podstawowe.|
    |**Pokaż typy pochodne**|Dla klasy dodaj klasy pochodne.<br /><br /> Dla interfejsu dodaj interfejsy pochodne i implementujące klasy lub struktury.|
    |**Pokaż typy, do których odwołuje się to**|Dodaj wszystkie klasy i używane przez nie składowe.|
    |**Pokaż typy odwołujące się do tego**|Dodaj wszystkie klasy oraz ich składowe, które używają tej klasy.|
    |**Pokaż zawierającą przestrzeń nazw**|Dodaj nadrzędną przestrzeń nazw.|
    |**Pokaż zawierającą przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|
    |**Pokaż wszystkie typy podstawowe**|Dodaj cyklicznie klasę bazową lub hierarchię interfejsu.|
    |**Pokaż wszystkie typy pochodne**|Dla klasy dodaj wszystkie klasy pochodne cyklicznie.<br /><br /> Dla interfejsu, dodaj wszystkie interfejsy pochodne i cyklicznie implementujące klasy lub struktury.|

     W przypadku **metody** wybierz:

    |Opcja|Opis|
    |-|-|
    |**Pokaż metody, które wywołuje**|Dodaj metody, które wywołuje ta metoda.|
    |**Pokaż pola, do których ta odwołania się odwołuje**|Dodaj pola, do których odwołuje się ta metoda.|
    |**Show Containing Type**|Dodaj typ nadrzędny.|
    |**Wyświetlanie zawierającego typu, przestrzeni nazw i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|
    |**Pokaż metody przesłonięć**|Dla metody, która zastępuje inne metody lub implementuje metodę interfejsu, należy dodać wszystkie metody abstrakcyjne lub wirtualne w klasach bazowych, które są zastępowane, oraz — jeśli istnieje — implementowaną metodę interfejsu.|

     Dla pola **lub** **właściwości wybierz:**

    |Opcja|Opis|
    |-|-|
    |**Show Containing Type**|Dodaj typ nadrzędny.|
    |**Wyświetlanie zawierającego typu, przestrzeni nazw i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|

    ![Pokaż metody wywoływane przez ten członek](../modeling/media/codemapsshowrelatedmethods.png)

7. Mapa przedstawia relacje. W tym przykładzie mapa przedstawia metody wywoływane przez metodę i ich lokalizację `Find` w rozwiązaniu lub na zewnątrz.

   ![Wyświetlanie określonych zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Aby uprościć mapę i skoncentrować  się na poszczególnych częściach, wybierz pozycję Filtry na pasku narzędzi mapy kodu i wybierz tylko typy węzłów i linków, które Cię interesują. Na przykład wyłącz wyświetlanie folderów rozwiązań, zestawów i przestrzeni nazw.

   ![Korzystanie z okienka Filtr w celu uproszczenia wyświetlania](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Zobacz też

- [Udostępnianie map kodu](share-code-maps.md)
- [Tworzenie map kodu dla języka C++](code-maps-for-cpp.md)
- [Poprawianie wydajności mapy kodu](code-maps-performance.md)
- [Wideo: Understand design from code with Visual Studio 2015 code maps (Zrozumienie projektowania na Visual Studio 2015 r.](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Wideo: Understand design from code with Visual Studio 2015 code maps (Zrozumienie projektowania na Visual Studio 2015 r.](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
