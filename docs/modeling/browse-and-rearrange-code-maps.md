---
title: Przeglądanie i rozmieszczanie map kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e38308c5bb94028fa17e78740da2b0df2779447
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590608"
---
# <a name="browse-and-rearrange-code-maps"></a>Przeglądanie i rozmieszczanie map kodu

Zmień rozmieszczenie elementów na mapach kodu, aby ułatwić ich odczytywanie i ulepszanie ich wydajności.

Mapy kodu można dostosować bez wpływu na kod źródłowy w rozwiązaniu. Jest to przydatne w przypadku, gdy chcesz skupić się na elementach kodu najważniejszych lub poznać pomysły dotyczące kodu. Na przykład, aby wyróżnić interesujące obszary, można wybrać elementy kodu na mapie i filtrować je, zmienić styl elementów kodu i linków, ukryć lub usunąć elementy kodu i zorganizować elementy kodu przy użyciu właściwości, kategorii lub grup.

 **Requirements**

- Aby utworzyć mapy kodu, musisz mieć Visual Studio Enterprise.

- Można wyświetlić mapy kodu i wprowadzić ograniczone edycje map kodu w Visual Studio Professional.

## <a name="ManageLargeGraphs"></a>Wprowadzenie do pracy z mapami kodu

Utwórz mapę kodu (zobacz [zależności mapy w rozwiązaniach](../modeling/map-dependencies-across-your-solutions.md) , aby uzyskać więcej informacji). Jeśli nie chcesz czekać na zakończenie generowania mapy, kliknij link **Anuluj** w dowolnym momencie, aby zatrzymać proces generacji. Jeśli to zrobisz, nie będzie można zobaczyć szczegółów wszystkich zależności i linków.

Po wygenerowaniu mapy Rozpocznij z tymi wskazówkami dotyczącymi recenzowania kodu:

- Przyjrzyj się naturalnym Klastrom zależności w kodzie. Na pasku narzędzi mapy wybierz pozycję **Układ**, **szybkie klastry**![przycisk Szybkie klastry na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif). Zobacz [Zmiana układu mapy](#Selecting).

     ![Układ szybkich klastrów wykresu &#45; zależności](../modeling/media/dependencygraph_quickclusters.png)

- Uporządkuj mapę w mniejsze obszary, grupując powiązane węzły. Zwiń te grupy, aby wyświetlić tylko zależności międzygrupowe, które są wyświetlane automatycznie. Zobacz [węzły grupy](#OrganizeGroups).

- Użyj filtrów, aby uprościć mapę i skupić się na typach węzłów lub linków, które Cię interesują. Zobacz [filtrowanie węzłów i linków](#FilterNodes).

- Maksymalizuj wydajność dużych map. Aby uzyskać więcej informacji, zobacz [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md) . Na przykład Włącz opcję **Pomiń kompilację** na pasku narzędzi mapy, aby program Visual Studio nie odbudowuje Twojego rozwiązania podczas aktualizacji elementów na mapie.

## <a name="Selecting"></a>Zmienianie układu mapy

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Rozmieść przepływ zależności dla całej mapy w określonym kierunku. Może to pomóc w wyświetleniu warstw architektury w kodzie.|Na pasku narzędzi Mapa wybierz **Układ**, a następnie:<br /><br /> -   **od góry do dołu** ![górnego do dolnego przycisku wykresu](../modeling/media/topbottomgraphbutton.gif)<br />-   **od dołu do góry** ![z dołu do górnego przycisku wykresu](../modeling/media/bottomtopgraphbutton.gif)<br />-   **od lewej do prawej** ![przycisku z układem do prawej](../modeling/media/leftrightgraphbutton.gif)<br />-   **od prawej do lewej** ![przycisk z prawej strony do lewego wykresu](../modeling/media/rightleftgraphbutton.gif)|
|Zobacz naturalne klastry zależności w kodzie z najbardziej zależnymi węzłami w centrum klastrów i najniższymi węzłami zależnymi znajdującymi się poza tymi klastrami.|Na pasku narzędzi mapy wybierz pozycję **Układ**, a następnie pozycję **szybkie klastry**![przycisk Szybkie klastry na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif).|
|Wybierz co najmniej jeden węzeł na mapie.|Kliknij węzeł, aby go zaznaczyć. Aby wybrać lub usunąć zaznaczenie więcej niż jednego węzła, przytrzymaj klawisz **Ctrl** podczas klikania.<br /><br /> Klawiatura: naciśnij klawisz **Tab** lub użyj klawiszy strzałek, aby przesunąć prostokątny fokus do węzła, a następnie naciśnij klawisz **spacji** , aby go zaznaczyć. Naciśnij klawisz **CTRL** + **miejsce** na wiele zaznaczeń lub usuń zaznaczenie węzłów.|
|Przenieś określone węzły wokół mapy.|Przeciągnij węzły, aby je przenieść. Aby przenieść inne węzły i linki w sposób, w jaki przeciągniesz węzły, naciśnij i przytrzymaj klawisz **SHIFT** .<br /><br /> Klawiatura: przytrzymaj klawisz **Ctrl** i naciśnij klawisze strzałek.|
|Zmień układ wewnątrz grupy niezależnie od innych węzłów i grup na mapie.|Wybierz węzeł i otwórz menu skrótów. Wybierz **Układ** i wybierz styl układu.<br /><br /> — lub —<br /><br /> Wybierz węzeł i rozwiń go, aby wyświetlić węzły podrzędne. Kliknij tytuł węzła, aby wyświetlić podręczny pasek narzędzi grupy, a następnie otwórz pozycję **Zmień styl układu** paska narzędzi &#45; &#45; grupy wykresów![zależność grupy](../modeling/media/dependencygraph_grouptoolbar.gif). Wybierz jeden z układów drzewa, **szybkie klastry**lub **Widok listy** , który organizuje zawartość grupy w postaci listy.<br /><br /> Aby uzyskać więcej informacji, zobacz [węzły grup](#OrganizeGroups) .|
|Cofnij akcję na mapie.|Naciśnij klawisz **CTRL** + **Z** lub użyj polecenia **Cofnij** programu Visual Studio.|

## <a name="Explore"></a>Przeglądaj mapę

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Zeskanuj mapę.|Przeciągnij mapę w dowolnym kierunku przy użyciu myszy.<br /><br /> — lub —<br /><br /> Przytrzymaj klawisz **SHIFT** i obróć kółko myszy, aby przewinąć w poziomie. Przytrzymaj klawisz **SHIFT** + **Ctrl** i obróć kółko myszy, aby przewinąć w poziomie.|
|Powiększ lub Zmniejsz mapę.|Obróć kółko myszy.<br /><br /> — lub —<br /><br /> Użyj listy rozwijanej **powiększenie** na pasku narzędzi mapy kodu.<br /><br /> — lub —<br /><br /> Użyj skrótów klawiaturowych. Aby powiększyć, naciśnij **klawisze Ctrl + Shift +.** (kropka). Aby pomniejszyć, naciśnij **klawisze CTRL + SHIFT +,** (przecinek).|
|Powiększ dla określonego obszaru za pomocą myszy.|Przytrzymaj prawy przycisk myszy podczas rysowania prostokąta wokół tego obszaru, który Cię interesuje.|
|Zmień rozmiar i Dopasuj mapę w oknie.|Wybierz pozycję **Powiększ, aby dopasować ją do** listy **powiększenie** na pasku narzędzi mapy kodu.<br /><br /> — lub —<br /><br /> Kliknij ikonę **Powiększ do dopasowania** , ![ikonę powiększenia na pasku narzędzi mapy](../modeling/media/almcodemapzoomicon.png) na pasku narzędzi Mapa kodu. Klawiatura: Naciśnij **Ctrl + 0** (zero).|
|Znajdź węzeł na mapie według jego nazwy. **Porada:**  Działa to tylko dla elementów na mapie. Aby znaleźć elementy w rozwiązaniu, ale nie na mapie, Znajdź je w **Eksplorator rozwiązań**, a następnie przeciągnij je do mapy. (Przeciągnij zaznaczenie lub na pasku narzędzi **Eksplorator rozwiązań** kliknij pozycję **Pokaż na mapie kodu**).|1. Wybierz ikonę **znajdź** ![ikonę Znajdź na pasku narzędzi mapy](../modeling/media/almcodemapfindicon.png) na pasku narzędzi Mapa kodu (klawiatura: Naciśnij **klawisze CTRL + F**), aby wyświetlić pole wyszukiwania w prawym górnym rogu mapy.<br />2. Wpisz nazwę elementu, a następnie naciśnij klawisz **Return** lub kliknij ikonę "Lupa". Pierwszy element, który jest zgodny z wyszukiwaniem, zostanie wyświetlony na mapie.<br />3. Aby dostosować wyszukiwanie, Otwórz listę rozwijaną i wybierz opcję wyszukiwania. Dostępne są opcje **Znajdź następny**, **Znajdź poprzedni**i **Zaznacz wszystko**. Następnie kliknij odpowiedni przycisk obok pola tekstowego wyszukiwania.<br />     Lista rozwijana&#45;opcji wyszukiwania ![](../modeling/media/almcodemapssearchdropdown.png)<br />     Alternatywnie możesz użyć klawiatury: naciśnij klawisz **F3** , aby wybrać następny pasujący węzeł lub **Shift + F3** , aby wybrać poprzedni pasujący węzeł.<br />4. Wybierz jedną z opcji, które określają sposób obsługi warunków wyszukiwania, klikając ikony poniżej pola tekstowego wyszukiwania.<br />     Opcje dopasowania wyszukiwania ![](../modeling/media/almcodemapssearchmatchicons.png)<br />     Dostępne opcje to, od lewej do prawej, dopasowanie do wielkości liter, dopasowuje tylko całe wyrazy, użyj składni wyrażeń regularnych programu .NET, automatycznie Rozwiń grupy, aby pokazać dopasowania do zamkniętych elementów. **Ważne:**  Możesz użyć pola wyszukiwania, aby znaleźć dopasowania w zwiniętych grupach tylko wtedy, gdy te grupy zostały wcześniej rozwinięte. Aby znaleźć te dopasowania i automatycznie rozwinąć ich grupy nadrzędne, wybierz tę opcję w polu wyszukiwania.|
|Zaznacz wszystkie niewybrane węzły.|Otwórz menu skrótów dla wybranych węzłów. Wybierz pozycję **zaznacz**, **Odwróć zaznaczenie**.|
|Wybierz dodatkowe węzły, które łączą się z wybranymi.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **pozycję Wybierz** i jedną z następujących opcji:<br /><br /> -Aby zaznaczyć dodatkowe węzły, które łączą się bezpośrednio z wybranym węzłem, wybierz pozycję **zależności przychodzące**.<br />-Aby wybrać dodatkowe węzły, które łączą się bezpośrednio z wybranego węzła, wybierz pozycję **zależności wychodzące**.<br />-Aby wybrać dodatkowe węzły, które łączą się bezpośrednio z i z wybranego węzła, wybierz **oba**te elementy.<br />-Aby zaznaczyć wszystkie węzły, które łączą się z wybranym węzłem i z niego wybierz opcję **połączony wykres**podrzędny.<br />-Aby zaznaczyć wszystkie elementy podrzędne wybranego węzła, wybierz pozycję **elementy podrzędne**.|

## <a name="FilterNodes"></a>Filtruj węzły i linki

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Pokaż lub Ukryj okienko filtry.|Wybierz przycisk **filtry** na pasku narzędzi mapy kodu. Domyślnie okienko **filtry** jest wyświetlane jako strona z kartami w **Eksplorator rozwiązań**.|
|Filtrowanie typów węzłów, które są wyświetlane na mapie.|Ustaw lub wyczyść pola wyboru na liście **elementy kodu** w okienku filtry.|
|Filtruj typy łączy, które są wyświetlane na mapie.|Ustaw lub wyczyść pola wyboru na liście **relacje** w okienku filtry.|
|Pokaż lub Ukryj węzły projektu testowego na mapie.|Ustaw lub wyczyść pole wyboru **zasoby testowe** na liście **różne** w okienku filtry.|

Ikony wyświetlane w panelu legendy mapy odzwierciedlają ustawienia wprowadzone na liście. Aby pokazać lub ukryć panel legenda, kliknij przycisk **Legenda** na pasku narzędzi mapy kodu.

## <a name="Inspect"></a>Sprawdzanie węzłów i linków

Mapy kodu pokazują następujące rodzaje łączy:

- Pojedyncze łącze reprezentuje pojedynczą relację między dwoma węzłami.

- Łącze między grupami reprezentuje relację między dwoma węzłami w różnych grupach.

- Łącze zagregowane reprezentuje wszystkie relacje, które wskazują w tym samym kierunku między dwiema grupami.

> [!TIP]
> Domyślnie mapa pokazuje linki między grupami tylko dla wybranych węzłów. Aby zmienić to zachowanie, aby pokazać lub ukryć zagregowane łącza między grupami, kliknij przycisk **Układ** na pasku narzędzi Mapa kodu i wybierz pozycję **Zaawansowane**, a następnie **Wyświetl wszystkie linki między grupami** lub **Ukryj wszystkie linki między grupami**. Aby uzyskać więcej informacji, zobacz [ukrywanie lub pokazywanie węzłów i linków](#HidingShowing) .

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Zobacz więcej informacji na temat węzła lub łącza.|Przesuń wskaźnik myszy nad węzłem lub linkiem do momentu wyświetlenia etykietki narzędzia.<br /><br /> Etykietka narzędzia dla łącza zagregowanego zawiera listę poszczególnych zależności, które reprezentuje.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla węzła lub łącza. Wybierz kolejno opcje **Edytuj**i **Właściwości**.|
|Pokaż lub Ukryj zawartość grupy.|-Aby rozwinąć grupę, otwórz menu skrótów dla węzła, a następnie wybierz pozycję **Grupa**, **Rozwiń**.<br />     — lub —<br />     Przesuń wskaźnik myszy nad węzłem do momentu, gdy zostanie wyświetlony przycisk cudzysłów ostrokątny (Strzałka w dół). Kliknij ten przycisk, aby rozwinąć grupę. Klawiatura: aby rozwinąć lub zwinąć wybraną grupę, naciśnij klawisz **Plus** ( **+** ) lub **znak minus** ( **-** ).<br />— Aby zwinąć grupę, otwórz menu skrótów dla węzła, a następnie wybierz pozycję **Grupa**, **Zwiń**.<br />     — lub —<br />     Przesuń wskaźnik myszy na górną grupę do momentu, gdy zostanie wyświetlony przycisk Pagon (Strzałka w górę). Kliknij ten przycisk, aby zwinąć grupę.<br />-Aby rozwinąć wszystkie grupy, naciśnij klawisz **CTRL** + **A** , aby zaznaczyć wszystkie węzły. Otwórz menu skrótów dla mapy i wybierz pozycję **Grupa**, **Rozwiń**. **Uwaga:**      To polecenie jest niedostępne, jeśli rozwinięcie wszystkich grup generuje niezdatną mapę lub problemy z pamięcią. Zaleca się, aby rozszerzyć mapę tylko na poziom szczegółowości, który Cię interesuje.<br />-Aby zwinąć wszystkie grupy, otwórz menu skrótów dla węzła lub dla mapy. Wybierz kolejno pozycje **Grupa**i **Zwiń wszystko**.|
|Zobacz definicję kodu dla przestrzeni nazw, typu lub składowej.|Otwórz menu skrótów dla węzła i wybierz polecenie **Przejdź do definicji**.<br /><br /> lub<br /><br /> Kliknij dwukrotnie węzeł. W przypadku rozwiniętych grup kliknij dwukrotnie nagłówek w grupie.<br /><br /> lub<br /><br /> Wybierz węzeł i naciśnij klawisz **F12**.<br /><br /> Na przykład:<br /><br /> — W przypadku przestrzeni nazw zawierającej jedną klasę plik kodu dla klasy zostanie otwarty w celu wyświetlenia definicji tej klasy. W innych przypadkach okno **Znajdź wyniki symboli** zawiera listę plików kodu. **Uwaga:**      Po wykonaniu tego zadania w Visual Basic przestrzeni nazw plik kodu za przestrzenią nazw nie jest otwarty. Ten problem występuje również w przypadku wykonywania tego zadania w grupie wybranych węzłów, które zawierają przestrzeń nazw Visual Basic. Aby obejść ten problem, przejrzyj ręcznie plik z kodem znajdujący się za przestrzenią nazw lub Pomiń ten węzeł dla przestrzeni nazw.<br />— W przypadku klasy lub klasy częściowej plik kodu dla tej klasy zostanie otwarty w celu wyświetlenia definicji klasy.<br />-Dla metody, plik kodu dla klasy nadrzędnej otwiera się, aby wyświetlić definicję metody.|
|Sprawdzanie zależności i elementów, które uczestniczą w łączu agregującym.|Wybierz interesujące Cię linki i otwórz menu skrótów dla zaznaczenia. Wybierz pozycję **Pokaż linki** do współtworzenia lub **Pokaż linki współautorów na nowej mapie kodu**.<br /><br /> Program Visual Studio rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które w nim uczestniczą. **Uwaga:**  Podczas badania zależności między elementami w grupach częściowych może zostać wyświetlone następujące zachowanie: <ul><li>Linki do elementów, które nie uczestniczą w badaniu, znikają z mapy, mimo że te linki nadal istnieją.</li><li>Załóżmy, że analizujesz link do elementu w grupie częściowej, a następnie przebadasz inny link do tego samego elementu. Podczas drugiego badania Grupa docelowa częściowa zawiera tylko elementy z pierwszego badania. Linki i elementy docelowe, które nie uczestniczyły w pierwszej analizie, ale uczestniczą w drugim badaniu nie są wyświetlane.</li></ul> Aby wyświetlić brakujące elementy z grupy, wybierz opcję ponownie **Pobierz elementy podrzędne**![ponownie Pobierz elementy podrzędne](../modeling/media/dependencygraph_deletednodesicon.png) (które wskazuje, że nie wszystkie elementy członkowskie grupy są wyświetlane na mapie). Możesz również spróbować cofać akcje (klawiatura: Naciśnij **klawisze Ctrl + Z**) i sprawdź zależności na nowej mapie.|
|Sprawdzanie zależności między wieloma węzłami w różnych grupach.|Rozwiń grupy, aby zobaczyć wszystkie ich elementy podrzędne. Zaznacz wszystkie węzły, które Cię interesują, w tym ich elementy podrzędne. Mapa pokazuje linki między grupami między wybranymi węzłami.<br /><br /> Aby zaznaczyć wszystkie węzły w grupie, naciśnij i przytrzymaj klawisz **SHIFT** oraz lewy przycisk myszy podczas rysowania prostokąta wokół tej grupy. Aby zaznaczyć wszystkie węzły na mapie, naciśnij klawisz **CTRL**+**a**. **Porada:**  Aby wyświetlić linki między grupami przez cały czas, wybierz pozycję **Układ** na pasku narzędzi Mapa, **Zaawansowane**, **Pokaż wszystkie linki między grupami**.|
|Zobacz elementy, do których odwołuje się węzeł lub link.|Otwórz menu skrótów dla węzła i wybierz polecenie **Znajdź wszystkie odwołania**. **Uwaga:**  Ma to zastosowanie tylko wtedy, gdy atrybut `Reference` jest ustawiony dla węzła lub łącza w pliku DGML mapy. Aby dodać odwołania do elementów z węzłów lub linków, zobacz [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="HidingShowing"></a>Ukrywanie lub pokazywanie węzłów i linków

Ukrywanie węzłów wyklucza je z udziału w układzie algorytmów. Domyślnie łącza między grupami są ukryte. Łącza grupy współzależności są poszczególnymi łączami połączenia między grupami węzłów. Gdy grupy są zwinięte, Mapa agreguje wszystkie linki między grupami do pojedynczych linków między grupami. Gdyby rozwinąć grupę i wybrać węzły wewnątrz grupy, łącza grupy współzależności pojawiają się i pokażą zależności w tej grupie.

> [!CAUTION]
> Przed udostępnieniem mapy, która została utworzona w Visual Studio Enterprise z tymi, które używają Visual Studio Professional, pamiętaj, aby odkryć wszystkie węzły lub linki między grupami, które mają być widoczne dla innych użytkowników. W przeciwnym razie użytkownicy nie mogą odkryć tych elementów.

### <a name="to-hide-or-show-nodes"></a>Aby ukryć lub pokazać węzły

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Ukryj wybrane węzły.|1. Wybierz węzły, które chcesz ukryć.<br />2. Otwórz menu skrótów dla wybranych węzłów lub dla mapy. Wybierz pozycję **zaznacz**, **Ukryj zaznaczone**.|
|Ukryj niewybrane węzły.|1. Wybierz węzły, które mają pozostać widoczne.<br />2. Otwórz menu skrótów dla wybranych węzłów lub dla mapy. Wybierz pozycję **zaznacz**, **Ukryj niezaznaczone**.|
|Pokaż ukryte węzły.|-Aby pokazać wszystkie ukryte węzły wewnątrz grupy, najpierw upewnij się, że grupa jest rozwinięta. Otwórz menu skrótów i wybierz polecenie **Wybierz**, **odkryj elementy podrzędne**.<br />     — lub —<br />     Kliknij ikonę **odkryj elementy podrzędne**![Ukryj elementy podrzędne](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) ikona w lewym górnym rogu grupy (jest to widoczne tylko wtedy, gdy istnieją ukryte węzły podrzędne).<br />— Aby pokazać wszystkie ukryte węzły, otwórz menu skrótów dla mapy lub węzła, a następnie wybierz **Wybierz**, **Odkryj wszystkie**.|

### <a name="to-hide-or-show-links"></a>Aby ukryć lub pokazać linki

|**To**|**Na pasku narzędzi mapy wybierz pozycję Układ, zaawansowane, a następnie wybierz pozycję**|
|-|-|
|Pokaż linki między grupami przez cały czas.|**Pokaż wszystkie linki między grupami**. Powoduje to ukrycie agregowanych łącz między grupami.|
|Ukryj linki między grupami przez cały czas.|**Ukryj wszystkie linki między grupami**|
|Pokaż tylko linki międzygrupowe dla wybranych węzłów.|**Pokaż linki między grupami w wybranych węzłach**|
|Ukryj wszystkie linki.|**Ukryj wszystkie linki**. Aby wyświetlić linki ponownie, wybierz jedną z opcji wymienionych powyżej.|

## <a name="OrganizeGroups"></a>Grupuj węzły

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Pokaż węzły kontenera jako węzły grupy lub węzły liścia.|Aby wyświetlić węzły kontenera jako węzły liścia: Zaznacz węzły, otwórz menu skrótów dla zaznaczenia, a następnie wybierz pozycję **Grupuj**, **Konwertuj na liść**.<br /><br /> Aby wyświetlić węzły kontenera jako węzły grupy: Zaznacz węzły, otwórz menu skrótów dla zaznaczenia, a następnie wybierz pozycję **Grupuj**, **Konwertuj na grupę**.|
|Zmień układ wewnątrz grupy.|Wybierz grupę, otwórz menu skrótów, wybierz **Układ**i wybierz styl układu.<br /><br /> — lub —<br /><br /> 1. Wybierz grupę i upewnij się, że została rozwinięta.<br />2. Kliknij ponownie nagłówek grupy, a zostanie wyświetlony pasek narzędzi grupy.<br />     ![pasek narzędzi &#45; grupy grafów zależności](../modeling/media/dependencygraph_group.png)<br />3. Otwórz pozycję **Zmień styl układu na liście grup** ![układ paska narzędzi &#45; &#45; grupy grafów zależności](../modeling/media/dependencygraph_grouptoolbar.gif) a następnie wybierz odpowiedni styl układu.<br /><br /> **Widok listy** rozdziela członków grupy na listę. **Domyślnie program Graph** resetuje układ grupy do domyślnego układu mapy. Aby poznać inne opcje, zobacz [Zmiana układu mapy](#Selecting).|
|Dodaj węzeł do grupy.|Przeciągnij węzeł na grupę.<br /><br /> Podczas przeciągania węzła program Visual Studio wyświetla wskaźnik, aby pokazać, że przenosisz węzeł.<br /><br /> Można również przeciągać węzły na zewnątrz grupy.|
|Dodaj węzeł do węzła, który nie jest grupą.|Przeciągnij węzeł na węzeł docelowy. Można przekonwertować dowolny węzeł docelowy na grupę, dodając do niego węzły.|
|Grupuj wybrane węzły.|1. Wybierz węzły, które chcesz zgrupować. Zostanie wyświetlony podręczny pasek narzędzi nad ostatnim zaznaczonym węzłem.<br />     ![pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)<br />2. na pasku narzędzi wybierz czwartą ikonę **grupy wybrane węzły** (Jeśli węzeł jest rozwinięty, będzie miał pięć zamiast czterech ikon). Wpisz nazwę nowej grupy, a następnie naciśnij klawisz **Return**.<br />     — lub —<br />     Wybierz węzły, które chcesz zgrupować, i otwórz menu skrótów dla zaznaczenia. Wybierz pozycję **Grupa**, **Dodaj grupę nadrzędną**, wpisz nazwę nowej grupy, a następnie naciśnij klawisz **Return**.<br /><br /> Można zmienić nazwę grupy. Otwórz menu skrótów dla grupy i wybierz polecenie **Edytuj**, **Właściwości** , aby otworzyć program Visual Studio okno właściwości. We właściwości **etykieta** Zmień nazwę grupy zgodnie z wymaganiami.|
|Usuń grupy.|Zaznacz jedną grupę lub kilka, które chcesz usunąć. Otwórz menu skrótów dla zaznaczenia, a następnie wybierz pozycję **Grupa**, **Usuń grupę**.|
|Usuń węzły z grupy nadrzędnej.|Zaznacz węzły, które chcesz przenieść. Otwórz menu skrótów dla zaznaczenia, a następnie wybierz pozycję **Grupa**, **Usuń z elementu nadrzędnego**. Spowoduje to usunięcie węzłów do ich nadrzędnego lub spoza grupy, jeśli nie mają grupy nadrzędnych.<br /><br /> — lub —<br /><br /> Wybierz węzły i przeciągnij je poza grupę.|

## <a name="AddRemoveNodesLinks"></a>Dodawanie, usuwanie lub zmienianie nazw węzłów, linków i komentarzy

Możesz wyświetlić więcej lub mniej elementów na mapie, aby przechodzenie do szczegółów lub uprościć mapę. Możesz również zmienić nazwy elementów i dodać komentarze do elementów.

> [!CAUTION]
> Przed udostępnieniem mapy, która została utworzona przy użyciu Visual Studio Enterprise z osobami, które korzystają z programu Visual Professional, upewnij się, że wszystkie elementy kodu, które mają być widoczne dla innych, są wyświetlane na mapie. W przeciwnym razie użytkownicy nie będą mogli pobierać usuniętych elementów kodu.

### <a name="add-a-node-for-a-code-element"></a>Dodawanie węzła dla elementu kodu

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Dodaj nowy węzeł ogólny w bieżącej lokalizacji wskaźnika myszy.|1. Przenieś wskaźnik myszy do miejsca na mapie, w której chcesz umieścić nowy element kodu, a następnie naciśnij klawisz **INSERT**.<br />     — lub —<br />     Otwórz menu skrótów dla mapy i wybierz polecenie **Edytuj**, **Dodaj**, **węzeł generyczny**.<br />2. Wpisz nazwę nowego węzła i naciśnij przycisk **Return**.|
|Dodaj konkretny typ węzła elementu kodu w bieżącej lokalizacji wskaźnika myszy.|1. Przenieś wskaźnik myszy do położenia na mapie, w której chcesz umieścić nowy element kodu, a następnie otwórz menu skrótów dla mapy.<br />2. Wybierz pozycję **Edytuj**, **Dodaj**i wybierz żądany typ węzła.<br />3. Wpisz nazwę nowego węzła i naciśnij przycisk **Return**.|
|Dodaj ogólny lub określony typ węzła elementu kodu do grupy.|1. Wybierz węzeł grupy, a następnie otwórz menu skrótów.<br />2. Wybierz pozycję **Edytuj**, **Dodaj**i wybierz żądany typ węzła.<br />3. Wpisz nazwę nowego węzła i naciśnij przycisk **Return**.|
|Dodaj nowy węzeł tego samego typu i połączony z, istniejący węzeł.|1. Wybierz element Code. Nad nim zostanie wyświetlony podręczny pasek narzędzi.<br />     ![pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)<br />2. na pasku narzędzi wybierz drugą ikonę **Utwórz węzeł o tej samej kategorii co ten węzeł i Dodaj do niego nowy link**.<br />3. Wybierz miejsce na mapie, aby umieścić nowy element kodu, a następnie kliknij lewym przyciskiem myszy.<br />4. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|
|Dodaj nowy węzeł ogólny, który jest połączony z istniejącym elementem kodu, który ma fokus.|1. przy użyciu klawiatury Naciskaj klawisz **Tab** , aż element kodu do linku ma fokus (prostokąt kropkowany).<br />2. Naciśnij **kombinację klawiszy Alt**+**INSERT**.<br />3. Wpisz nazwę nowego węzła i naciśnij przycisk **Return**.|
|Dodaj nowy węzeł ogólny, który łączy się z istniejącym elementem kodu, który ma fokus.|1. przy użyciu klawiatury Naciskaj klawisz **Tab** , aż element kodu do linku ma fokus (prostokąt kropkowany).<br />2. Naciśnij **kombinację klawiszy Alt**+**SHIFT**+**Wstaw**.<br />3. Wpisz nazwę nowego węzła i naciśnij przycisk **Return**.|

|**Aby dodać elementy kodu dla**|**Wykonaj następujące kroki**|
|-|-|
|Elementy kodu w rozwiązaniu.|1. Znajdź element Code w **Eksplorator rozwiązań**. Użyj pola wyszukiwania **Eksplorator rozwiązań** lub Przeglądaj rozwiązanie. **Porada:**      Aby znaleźć elementy kodu, które mają zależności od typu lub elementu członkowskiego, otwórz menu skrótów dla typu lub elementu członkowskiego w **Eksplorator rozwiązań**. Wybierz odpowiednią relację. **Eksplorator rozwiązań** pokazuje tylko te elementy kodu z określonymi zależnościami.<br />2. Przeciągnij elementy kodu, które interesują się powierzchnią mapy. Można również przeciągać elementy kodu z Widok klasy lub Przeglądarka obiektów.<br />     — lub —<br />     W **Eksplorator rozwiązań**wybierz elementy kodu, które chcesz zmapować. Następnie na **Eksplorator rozwiązań** pasku narzędzi kliknij pozycję **Pokaż na mapie kodu**.<br /><br /> Domyślnie nadrzędna hierarchia kontenerów dla nowych elementów kodu jest pokazywana na mapie. Aby zmienić to zachowanie, użyj przycisku **Dołącz obiekty nadrzędne** na pasku narzędzi mapy kodu. Po wyłączeniu tylko sam element kodu zostanie dodany do mapy. Aby wycofać to zachowanie tylko dla jednej akcji przeciągania i upuszczania, naciśnij i przytrzymaj klawisz **Ctrl** podczas przeciągania elementów kodu do mapy.<br /><br /> Program Visual Studio dodaje do zaznaczenia elementy kodu najwyższego poziomu. Aby sprawdzić, czy element kodu zawiera inne elementy kodu, przesuń wskaźnik myszy nad element Code, aby pojawił się podwójna strzałka w dół. Wybierz cudzysłów ostrokątny, aby rozwinąć element kodu. Aby rozwinąć wszystkie elementy kodu, naciśnij klawisz **CTRL**+**A** , aby zaznaczyć wszystkie elementy, otwórz menu skrótów dla mapy, a następnie wybierz **grupę**, **Rozwiń**. To polecenie jest niedostępne, jeśli rozwinięcie wszystkich grup spowoduje utworzenie nieużytecznej mapy lub spowodowanie braku problemów z pamięcią.|
|Elementy kodu związane z elementami kodu na mapie.|Kliknij przycisk **Pokaż powiązane** na pasku narzędzi Mapa kodu i wybierz typ powiązanych elementów, które Cię interesują.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla elementu Code. Wybierz jeden z elementów **wyświetlanych** w menu w zależności od rodzaju relacji, która Cię interesuje. Na przykład można zobaczyć elementy, do których odwołuje się bieżący element, elementy, które odwołują się do bieżącego elementu, bazowego i pochodnego, dla klas, metod wywołujących i zawierających klasy, przestrzenie nazw i zestawy.<br /><br /> Aby uzyskać więcej informacji, zobacz [ten temat](../modeling/map-dependencies-across-your-solutions.md).|
|Skompilowane zestawy .NET (. dll lub. exe) lub pliki binarne.|Przeciągnij zestawy lub pliki binarne z zewnątrz programu Visual Studio do mapy.<br /><br /> Można przeciągać z Eksploratora Windows lub Eksploratora plików tylko wtedy, gdy działa i program Visual Studio na tym samym poziomie uprawnień użytkownika Access Control (UAC). Na przykład jeśli kontrola konta użytkownika jest włączona i używasz programu Visual Studio jako administrator, Eksplorator Windows lub Eksplorator plików zablokuje operację przeciągania.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Dodaj łącze między istniejącymi elementami kodu

1. Wybierz element kodu źródłowego. Pasek narzędzi jest wyświetlany powyżej elementu kodu.

    ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)

2. Na pasku narzędzi wybierz pierwszą ikonę, **Utwórz nowy link z tego węzła, do którego węzeł zostanie kliknięty dalej**.

3. Wybierz docelowy element kodu. Zostanie wyświetlony link między dwoma elementami kodu.

**OR**

1. Wybierz element kodu źródłowego na mapie.

2. Jeśli masz zainstalowaną myszą, przesuń wskaźnik myszy poza granice mapy.

3. Otwórz menu skrótów elementu kodu i wybierz polecenie **edytuj** > **Dodaj** > **Ogólne**.

4. I wybierz docelowy element kodu dla linku.

5. Naciśnij klawisz **wprowadź**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Dodawanie komentarza do istniejącego węzła na mapie

1. Wybierz element kodu. Nad nim pojawia się pasek narzędzi.

     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)

2. Na pasku narzędzi wybierz trzecią ikonę, **Utwórz nowy węzeł komentarza z nowym linkiem do wybranego węzła**.

     \- lub —

     Otwórz menu skrótów dla elementu Code i wybierz polecenie **edytuj** > **Nowy komentarz**.

3. Wpisz swoje komentarze. Aby wpisać nowy wiersz, naciśnij klawisz **Shift** + **Enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Dodaj komentarz do samego mapy

1. Otwórz menu skrótów dla mapy i wybierz polecenie **edytuj** > **Nowy komentarz**.

2. Wpisz swoje komentarze. Aby wpisać nowy wiersz, naciśnij klawisz **Shift** + **Enter**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Zmień nazwę elementu lub linku kodu

1. Wybierz element kodu lub łącze, którego nazwę chcesz zmienić.

2. Naciśnij klawisz **F2**lub Otwórz menu skrótów i wybierz polecenie **Edytuj** > **Zmień nazwę**.

3. Gdy pole edycji pojawia się na mapie, Zmień nazwę elementu kodu lub łącza.

**OR**

1. Otwórz menu skrótów i wybierz polecenie **edytuj** > **Właściwości**.

2. Edytuj Właściwość **Label** w okno właściwości programu Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Usuń element kodu lub łącze z mapy

1. Wybierz element kodu lub łącze, a następnie naciśnij klawisz **delete** .

     \- lub —

     Otwórz menu skrótów dla elementu kodu lub łącza, a następnie wybierz polecenie **edytuj** > **Usuń**.

2. Jeśli element lub łącze jest częścią grupy, przycisk ponownie **Pobierz elementy podrzędne** ![ikonę ponownie Pobierz elementy podrzędne](../modeling/media/dependencygraph_deletednodesicon.png) pojawia się wewnątrz grupy. Kliknij, aby pobrać brakujące elementy i linki.

- Można usunąć elementy kodu i linki z mapy bez wpływu na kod źródłowy. Po ich usunięciu definicje są usuwane z pliku DGML (. dgml).

- Mapy utworzone przez edytowanie DGML, przez dodawanie niezdefiniowanych elementów kodu lub przy użyciu niektórych wcześniejszych wersji programu Visual Studio, nie obsługują tej funkcji.

#### <a name="flag-a-code-element-for-follow-up"></a>Oflaguj element kodu na potrzeby monitowania

1. Wybierz element kodu lub link, dla którego chcesz oflagować monit.

2. Otwórz menu skrótów i wybierz polecenie **edytuj** > **flagę, aby zaobserwować**.

- Domyślnie element kodu uzyskuje czerwone tło. Rozważ [dodanie do niego komentarza](#AddComments) z odpowiednimi informacjami monitu.

- Zmień kolor tła elementu lub wyczyść flagę monitującej, wybierając **edytuj** > **inne kolory flagi**.

## <a name="ChangeStyleCodeOrLink"></a>Zmień styl elementu lub linku kodu

Można zmienić ikony elementów kodu oraz kolory elementów kodu i linków przy użyciu wstępnie zdefiniowanych ikon i kolorów. Na przykład można wybrać kolor, aby wyróżnić elementy kodu i linki z określoną kategorią lub właściwością. Pozwala to na identyfikację i skoncentrowanie się na określonych obszarach mapy. Możesz określić niestandardowe ikony i kolory, edytując plik. dgml mapy; Aby dowiedzieć [się, jak dostosować mapy kodu, edytuj pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Aby zastosować wstępnie zdefiniowany kolor lub ikonę do elementów kodu lub linków z określoną kategorią lub właściwością

1. Na pasku narzędzi mapy wybierz pozycję **Legenda**.

2. W polu **Legenda** Sprawdź, czy Kategoria elementu kodu lub właściwość już występuje na liście.

3. Jeśli lista nie zawiera kategorii lub właściwości, wybierz **+** w polu **Legenda** , a następnie wybierz pozycję **Właściwość węzła**, **Kategoria węzła**, **Właściwość link**lub **Kategoria łącza**. Następnie wybierz właściwość lub kategorię. Kategoria lub właściwość pojawi się w polu **Legenda** .

    > [!NOTE]
    > Aby utworzyć i przypisać kategorię lub właściwość do elementu kodu, można edytować plik. dgml mapy; Aby dowiedzieć [się, jak dostosować mapy kodu, edytuj pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. W polu **Legenda** kliknij ikonę obok dodawanej kategorii lub właściwości lub chcesz zmienić.

5. Skorzystaj z poniższej tabeli, aby wybrać styl, który ma zostać zmieniony:

    |**Aby zmienić**|**Następnie**|
    |-|-|
    |Kolor tła|**Tło**|
    |Kolor konturu|**Linii**|
    |Kolor tekstu (zostanie wyświetlony litera "f", aby pokazać wynik)|**Pierwszego planu**|
    |Ikona|**Ikony**|

     **Selektor zestawu kolorów** lub **Selektor zestawu ikon** zostanie wyświetlony, aby wybrać kolor lub ikonę.

6. W oknie dialogowym Selektor **zestawu kolorów** lub **Selektor zestawu ikon** wykonaj jedną z następujących czynności:

    |**Aby zastosować**|**Wykonaj następujące kroki**|
    |-|-|
    |Zestaw kolorów lub ikon|Otwórz listę **Wybierz** **zestaw** kolorów (lub **ikon**). Wybierz zestaw kolorów lub ikon.|
    |Określony kolor lub ikona|Otwórz listę wartości kategorii lub właściwości. Wybierz kolor lub ikonę.|

    > [!NOTE]
    > Można zmienić rozmieszczenie, usunąć lub tymczasowo dezaktywować style w polu **Legenda** . Zobacz [Edytowanie pola legendy](#ModifyLegend).

## <a name="ModifyLegend"></a>Edytuj pole legendy

Można zmienić rozmieszczenie, usunąć lub tymczasowo dezaktywować style w polu **Legenda** :

1. Otwórz menu skrótów dla stylu w polu **Legenda** .

2. Wykonaj jedno z następujących zadań:

    |**To**|**Następnie**|
    |-|-|
    |Dezaktywuj element kodu|**Wyłącz**|
    |Usuń element kodu|**Delete**|
    |Przenieś styl w górę|**Przenieś w górę**|
    |Przenieś element kodu w dół|**Przenieś w dół**|

## <a name="CopyLegend"></a>Kopiuj style z jednej mapy do innej

1. Upewnij się, że pole **Legenda** jest widoczne na mapie źródłowej. Jeśli nie jest widoczny, na pasku narzędzi Mapa kliknij pozycję **Legenda**.

2. Otwórz menu skrótów dla pola **Legenda** . Wybierz **Kopiuj legendę**.

3. Wklej legendę do mapy docelowej.

## <a name="MergeMaps"></a>Scalanie map kodu

Mapy można scalać przez kopiowanie i wklejanie elementów kodu między mapami. Jeśli identyfikatory elementów kodu są zgodne, wklejanie elementów kodu funkcjonuje podobnie jak operacja scalania. Aby ułatwić to zadanie, należy umieścić wszystkie zestawy lub pliki binarne, które chcesz wizualizować w tym samym folderze, aby pełna ścieżka każdego zestawu lub pliku binarnego była taka sama dla każdej mapy, która ma zostać scalona.

Alternatywnie możesz przeciągnąć te zestawy lub pliki binarne na tę samą mapę z tego folderu.

## <a name="see-also"></a>Zobacz także

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
