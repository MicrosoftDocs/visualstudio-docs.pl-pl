---
title: Mapy kodu
description: Dowiedz się, jak mapy kodu pomagają zobaczyć, jak kod pasuje do siebie, bez odczytywania plików i wierszy kodu.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39b34bb124d663d81769c6d3086d6b36803d60eb
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362239"
---
# <a name="map-dependencies-with-code-maps"></a>Mapowanie zależności za pomocą map kodu

Możesz wizualizować zależności w kodzie przez utworzenie mapy kodu. Mapy kodu pomagają zobaczyć, jak kod pasuje do siebie, bez odczytywania plików i wierszy kodu.

![Wyświetlanie zależności za pomocą map kodu w programie Visual Studio](../modeling/media/codemapsmainintro.png)

Do tworzenia i edytowania map kodu potrzebna jest wersja Visual Studio Enterprise. W programie Visual Studio Community i wersje Professional można otwierać diagramy, które zostały wygenerowane w wersji Enterprise, ale nie można ich edytować.

> [!NOTE]
> Przed udostępnieniem map utworzonych w Visual Studio Enterprise z innymi osobami korzystającymi z Visual Studio Professional upewnij się, że są widoczne wszystkie elementy na mapie (takie jak elementy ukryte, rozwinięte grupy i linki między grupami).

Można mapować zależności dla kodu w następujących językach:

- Visual C# lub Visual Basic w rozwiązaniu lub zestawach (*. dll* lub *. exe*)

- Natywny lub zarządzany kod C lub C++ w Visual C++ projektach, plikach nagłówkowych (*. h* lub `#include` ) lub plików binarnych

- Projekty X + + i zestawy wykonane z modułów .NET dla systemu Microsoft Dynamics AX

> [!NOTE]
> W przypadku projektów innych niż C# lub Visual Basic istnieje mniej opcji uruchamiania mapy kodu lub dodawania elementów do istniejącej mapy kodu. Na przykład nie można kliknąć prawym przyciskiem myszy obiektu w edytorze tekstu projektu C++ i dodać go do mapy kodu. Można jednak przeciągać i upuszczać poszczególne elementy kodu lub pliki z **Eksplorator rozwiązań**, **Widok klasy** i **Przeglądarka obiektów**.

## <a name="install-code-map-and-live-dependency-validation"></a>Instalowanie mapy kodu i walidacji na żywo zależności

Aby utworzyć mapę kodu w programie Visual Studio, najpierw zainstaluj składniki **Mapa kodu** i **Walidacja aktywnej zależności** :

1. Otwórz **Instalator programu Visual Studio**. Możesz otworzyć ją z menu Start systemu Windows lub w programie Visual Studio, wybierając pozycję **Narzędzia**  >  **Pobierz narzędzia i funkcje**.

1. Wybierz kartę **poszczególne składniki** .

1. Przewiń w dół do sekcji **Narzędzia kodu** i wybierz pozycję **Mapa kodu** i **Walidacja na żywo**.

   ![Składniki mapy kodu i walidacji na żywo w Instalator programu Visual Studio](media/modeling-components.png)

1. Wybierz pozycję **Modyfikuj**.

   Trwa instalowanie składników **mapy kodu** i **walidacji na żywo** . Może zostać wyświetlony monit o zamknięcie programu Visual Studio.

## <a name="add-a-code-map"></a>Dodawanie mapy kodu

Można utworzyć pustą mapę kodu i przeciągnąć do niej elementy, takie jak odwołania do zestawów, pliki i foldery, lub można wygenerować mapę kodu dla całego rozwiązania lub jego części.

Aby dodać pustą mapę kodu:

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła rozwiązania najwyższego poziomu. Wybierz pozycję **Dodaj**  >  **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane** wybierz kategorię **Ogólne** .

3. Wybierz szablon **dokument wykresu bezpośredniego (. dgml)** , a następnie wybierz pozycję **Dodaj**.

   > [!TIP]
   > Ten szablon może nie być wyświetlany alfabetycznie, dlatego przewiń w dół do końca listy szablonów, jeśli go nie widzisz.

   Pusta mapa zostanie wyświetlona w folderze **elementów rozwiązania** rozwiązania.

Podobnie można utworzyć nowy plik mapy kodu bez dodawania go do rozwiązania, wybierając pozycję **Architektura**  >  **Nowa mapa kodu** lub **plik**  >  **Nowy**  >  **plik**.

## <a name="generate-a-code-map-for-your-solution"></a>Generuj mapę kodu dla rozwiązania

Aby wyświetlić wszystkie zależności w rozwiązaniu:

1. Na pasku menu wybierz **Architektura**  >  **Generuj mapę kodu dla rozwiązania**. Jeśli Twój kod nie zmienił się od czasu ostatniego skompilowania, możesz wybrać **architekturę**  >  **Generuj mapę kodu dla rozwiązania bez kompilowania** .

   ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png)

   Jest generowana mapa, która pokazuje zestawy najwyższego poziomu i zagregowane łącza między nimi. Im szerszy link zagregowany, tym więcej zależności reprezentuje.

2. Użyj przycisku **Legenda** na pasku narzędzi Mapa kodu, aby pokazać lub ukryć listę ikon typu projektu (na przykład projektu testowego, sieci Web i telefonu), elementów kodu (takich jak klasy, metody i właściwości), a także typy relacji (na przykład dziedziczone z, implementacje i wywołania).

   ![Wykres zależności najwyższego poziomu dla zestawów](../modeling/media/dependencygraph_toplevelassemblies.png)

   To przykładowe rozwiązanie zawiera foldery rozwiązań (**testy** i **składniki**), projekty testowe, projekty sieci Web i zestawy. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grupy*, które można rozwijać i zwijać. Grupa **zewnętrzna** zawiera wszystkie elementy spoza rozwiązania, w tym zależności platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie typy podstawowe systemu są ukryte na mapie, aby zmniejszyć ilość bałaganu.

3. Aby przejść do szczegółów mapy, rozwiń grupy reprezentujące projekty i zespoły. Możesz rozwinąć wszystko, naciskając **klawisze Ctrl + A** , aby zaznaczyć wszystkie węzły, a następnie wybrać **grupę**, **Rozwiń** z menu skrótów.

   ![Rozszerzanie wszystkich grup na mapie kodu](../modeling/media/codemapsexpandallgroups.png)

4. Jednak może to nie być przydatne w przypadku dużych rozwiązań. W rzeczywistości ograniczenia pamięci mogą uniemożliwiać rozszerzanie wszystkich grup. Zamiast tego, aby zobaczyć wewnątrz pojedynczego węzła, rozwiń go. Przesuń wskaźnik myszy na górny węzeł, a następnie kliknij cudzysłów ostrokątny (Strzałka w dół), gdy zostanie wyświetlony.

   ![Rozszerzanie węzła na mapie kodu](../modeling/media/dependencygraph_containment.png)

   Możesz też użyć klawiatury, zaznaczając element, a następnie naciskając klawisz plus ( **+** ). Aby zapoznać się z bardziej szczegółowymi poziomami kodu, wykonaj te same czynności dla obszarów nazw, typów i elementów członkowskich.

   > [!TIP]
   > Aby uzyskać więcej informacji na temat pracy z mapami kodu przy użyciu myszy, klawiatury i dotyku, zobacz [przeglądanie i zmiana kolejności map kodu](../modeling/browse-and-rearrange-code-maps.md).

5. Aby uprościć mapę i skoncentrować się na poszczególnych częściach, wybierz **filtry** na pasku narzędzi Mapa kodu i wybierz tylko wybrane typy węzłów i linków. Można na przykład ukryć wszystkie kontenery i foldery rozwiązań.

   ![Uproszczenie mapy przez filtrowanie kontenerów](../modeling/media/codemapsfilterfoldersassemblies.png)

   Możesz również uprościć mapę przez ukrycie lub usunięcie poszczególnych grup i elementów z mapy, bez wpływu na podstawowy kod rozwiązania.

6. Aby wyświetlić relacje między elementami, zaznacz je na mapie. Kolory linków wskazują typy relacji, jak pokazano w okienku **Legenda** .

   ![Wyświetlanie zależności między rozwiązaniami](../modeling/media/codemapsmainintro.png)

   W tym przykładzie purpurowe łącza to wywołania, linki kropkowane są odwołaniami, a niebieskie linki są dostępem do pól. Zielone linki mogą być dziedziczenia lub mogą być *zagregowanymi łączami* , które wskazują więcej niż jeden typ relacji (lub *kategorii*).

   > [!TIP]
   > Jeśli zobaczysz zielony link, może nie oznaczać, że istnieje tylko relacja dziedziczenia. Mogą również wystąpić wywołania metody, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy łączy, Użyj pól wyboru w okienku **filtry** w celu ukrycia nieinteresujących typów.

7. Aby uzyskać więcej informacji na temat elementu lub łącza, przesuń wskaźnik na wierzchu do momentu wyświetlenia etykietki narzędzia. Przedstawia szczegóły elementu kodu lub kategorie reprezentowane przez łącze.

   ![Pokaż kategorie relacji](../modeling/media/codemapsshowlinkcatgories.png)

8. Aby przejrzeć elementy i zależności reprezentowane przez łącze zagregowane, najpierw zaznacz łącze, a następnie otwórz jego menu skrótów. Wybierz **Pokaż linki** do współtworzenia (lub **Pokaż linki do współtworzenia na nowej mapie kodu**). Rozszerza to grupy na obu końcach łącza i pokazuje tylko te elementy i zależności, które uczestniczą w łączu.

9. Aby skoncentrować się na określonych częściach mapy, możesz kontynuować usuwanie nieinteresujących elementów. Na przykład aby przejść do szczegółów w widoku klasy i elementu członkowskiego, wystarczy odfiltrować wszystkie węzły przestrzeni nazw w okienku **filtry** .

   ![Przechodzenie do szczegółów na poziomie klasy i elementu członkowskiego](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Innym sposobem skoncentrowania się na złożonej mapie rozwiązań jest wygenerowanie nowej mapy zawierającej wybrane elementy z istniejącej mapy. Przytrzymaj klawisz **Ctrl** podczas zaznaczania elementów, na których chcesz się skoncentrować, otwórz menu skrótów i wybierz polecenie **Nowy wykres z zaznaczenia**.

    ![Pokaż zaznaczone elementy na nowej mapie kodu](../modeling/media/codemapsshowonnewmap.png)

11. Kontekst zawierający jest przenoszony do nowej mapy. Ukryj foldery rozwiązań i inne kontenery, które nie mają być wyświetlane za pomocą okienka **filtry** .

    ![Filtrowanie kontenerów w celu uproszczenia widoku](../modeling/media/codemapsexpandnewgroups.png)

12. Rozwiń grupy i wybierz elementy na mapie, aby wyświetlić relacje.

    ![Wybierz elementy, aby wyświetlić relacje](../modeling/media/codemapsviewnewrelationships.png)

Zobacz również:

- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Znajdowanie potencjalnych problemów w kodzie przez [uruchomienie analizatora](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Wyświetlanie określonych zależności na mapie kodu

Załóżmy, że masz przegląd kodu do wykonania w niektórych plikach z oczekującymi zmianami. Aby wyświetlić zależności w tych zmianach, można utworzyć mapę kodu z tych plików.

   ![Pokaż określone zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

1. W **Eksplorator rozwiązań** wybierz projekty, odwołania do zestawów, foldery, pliki, typy lub elementy członkowskie, które mają być mapowane.

   ![Wybierz elementy, które chcesz zmapować](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na pasku narzędzi **Eksplorator rozwiązań** wybierz przycisk **Pokaż na mapie kodu** ![ Utwórz nowy Graf z wybranych węzłów ](../modeling/media/createnewgraphfromselectedbutton.gif) . Lub Otwórz menu skrótów dla jednej lub grupy elementów i wybierz **Pokaż na mapie kodu**.

   Możesz również przeciągać elementy z **Eksplorator rozwiązań**, **Widok klasy** lub **Przeglądarka obiektów** do [nowej](#add-a-code-map) lub istniejącej mapy kodu. Aby uwzględnić hierarchię nadrzędną dla elementów, naciśnij i przytrzymaj klawisz **Ctrl** podczas przeciągania elementów lub użyj przycisku **Dołącz obiekty nadrzędne** na pasku narzędzi Mapa kodu, aby określić akcję domyślną. Możesz również przeciągać pliki zestawu spoza programu Visual Studio, na przykład z **Eksploratora Windows**.

   > [!NOTE]
   > Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Microsoft Store, te elementy są wyświetlane na mapie z aktualnie aktywnym projektem aplikacji. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

3. Mapa pokazuje wybrane elementy w ich zestawach zawierających.

   ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Aby eksplorować elementy, rozwiń je. Przesuń wskaźnik myszy nad elementem, a następnie kliknij ikonę cudzysłów ostrokątny (Strzałka w dół), gdy zostanie wyświetlona.

   ![Rozszerzanie węzła na mapie kodu](../modeling/media/dependencygraph_containment.png)

   Aby rozwinąć wszystkie elementy, zaznacz je za pomocą **klawisza Ctrl** + **a**, a następnie otwórz menu skrótów dla mapy i wybierz pozycję **Grupuj**  >  **rozwinięte**. Jednak ta opcja jest niedostępna, jeśli rozszerzanie wszystkich grup tworzy niezdatną mapę lub problemy z pamięcią.

5. Kontynuuj rozwijanie interesujących Cię elementów, a jeśli to konieczne, na poziomie klasy i elementu członkowskiego.

   ![Rozwiń grupy do poziomu klasy i elementu członkowskiego](../modeling/media/codemapsexpandtoclassandmember.png)

   Aby wyświetlić elementy członkowskie, które znajdują się w kodzie, ale nie są wyświetlane na mapie, kliknij ikonę ponownie **Pobierz elementy podrzędne** ikona ponownie ![ Pobierz elementy podrzędne ](../modeling/media/dependencygraph_deletednodesicon.png) w lewym górnym rogu grupy.

6. Aby wyświetlić więcej elementów związanych z tymi elementami na mapie, wybierz jeden z nich i wybierz **Pokaż powiązane** z paskiem narzędzi Mapa kodu, a następnie wybierz typ powiązanych elementów do dodania do mapy. Alternatywnie wybierz co najmniej jeden element, otwórz menu skrótów, a następnie wybierz opcję **Pokaż** dla typu elementów pokrewnych, które mają zostać dodane do mapy. Na przykład:

    Dla **zestawu** wybierz:

    |Opcja|Opis|
    |-|-|
    |**Pokaż zestawy te odwołania**|Dodaj zestawy, do których odwołuje się ten zestaw. Zestawy zewnętrzne pojawiają się w grupie **zewnętrzne** .|
    |**Pokaż zestawy odwołujące się do tego**|Dodaj zestawy w rozwiązaniu odwołującym się do tego zestawu.|

    W przypadku **przestrzeni nazw** wybierz pozycję **Pokaż zawierający zestaw**, jeśli nie jest ona widoczna.

    Dla **klasy** lub **interfejsu**, wybierz:

    |Opcja|Opis|
    |-|-|
    |**Pokaż typy podstawowe**|Dla klasy dodaj klasę bazową i implementowane interfejsy.<br /><br /> Dla interfejsu dodaj interfejsy podstawowe.|
    |**Pokaż typy pochodne**|Dla klasy dodaj klasy pochodne.<br /><br /> Dla interfejsu dodaj interfejsy pochodne i implementujące klasy lub struktury.|
    |**Pokaż typy te odwołania**|Dodaj wszystkie klasy i używane przez nie składowe.|
    |**Pokaż typy przywołujące ten element**|Dodaj wszystkie klasy oraz ich składowe, które używają tej klasy.|
    |**Pokaż zawierającą przestrzeń nazw**|Dodaj nadrzędną przestrzeń nazw.|
    |**Pokaż zawierającą przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|
    |**Pokaż wszystkie typy podstawowe**|Dodaj cyklicznie klasę bazową lub hierarchię interfejsu.|
    |**Pokaż wszystkie typy pochodne**|Dla klasy dodaj wszystkie klasy pochodne cyklicznie.<br /><br /> Dla interfejsu, dodaj wszystkie interfejsy pochodne i cyklicznie implementujące klasy lub struktury.|

     Dla **metody** należy wybrać:

    |Opcja|Opis|
    |-|-|
    |**Pokaż metody tego wywołania**|Dodaj metody, które wywołuje ta metoda.|
    |**Pokaż pola te odwołania**|Dodaj pola, do których odwołuje się ta metoda.|
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|
    |**Pokaż zawierający typ, przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|
    |**Pokaż przesłonięte metody**|Dla metody, która zastępuje inne metody lub implementuje metodę interfejsu, należy dodać wszystkie metody abstrakcyjne lub wirtualne w klasach bazowych, które są zastępowane, oraz — jeśli istnieje — implementowaną metodę interfejsu.|

     Dla **pola** lub **Właściwości** wybierz:

    |Opcja|Opis|
    |-|-|
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|
    |**Pokaż zawierający typ, przestrzeń nazw i zestaw**|Dodaj hierarchię kontenera nadrzędnego.|

    ![Pokaż metody wywoływane przez ten element członkowski](../modeling/media/codemapsshowrelatedmethods.png)

7. Mapa pokazuje relacje. W tym przykładzie mapa pokazuje metody wywoływane przez `Find` metodę i ich lokalizację lub zewnętrznie.

   ![Pokaż określone zależności na mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Aby uprościć mapę i skoncentrować się na poszczególnych częściach, wybierz **filtry** na pasku narzędzi Mapa kodu i wybierz tylko wybrane typy węzłów i linków. Na przykład Wyłącz wyświetlanie folderów rozwiązań, zestawów i przestrzeni nazw.

   ![Używanie okienka filtru do uproszczenia wyświetlania](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Zobacz też

- [Wideo: zrozumienie projektu na podstawie kodu za pomocą map kodu programu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
