---
title: Przeglądanie i zmienianie rozmieszczenia map kodu | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
ms.assetid: 08f65f77-6ca7-4b25-b060-3f6c9f5847a4
caps.latest.revision: 91
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ecdfb91beb4d844216a9c961830af336e9de15a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302358"
---
# <a name="browse-and-rearrange-code-maps"></a>Przeglądanie i rozmieszczanie map kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zmień kolejność elementów na mapach kodu, aby ułatwić ich odczytywanie i zwiększyć ich wydajność.

 Można dostosować mapy kodu bez wpływu na kod źródłowy w rozwiązaniu. Jest to przydatne, gdy chcesz skupić się na kluczowych elementów kodu lub komunikować pomysły dotyczące kodu. Na przykład, aby wyróżnić interesujące obszary, można wybrać elementy kodu na mapie i filtrować je, zmienić styl elementów kodu i łączy, ukryć lub usunąć elementy kodu oraz zorganizować elementy kodu przy użyciu właściwości, kategorii lub grup.

 **Wymagania**

- Aby utworzyć mapy kodu, musisz mieć program Visual Studio Enterprise.

- W programie Visual Studio Professional można wyświetlać mapy kodu i wprowadzać ograniczone zmiany w mapach kodu.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a>Rozpoczęcie pracy z mapami kodu
 Tworzenie mapy kodu (zobacz [Map zależności między rozwiązaniami, aby](../modeling/map-dependencies-across-your-solutions.md) uzyskać więcej informacji). Jeśli nie chcesz czekać na zakończenie generowania mapy, kliknij łącze **Anuluj** w dowolnym momencie, aby zatrzymać proces generowania. Jednak nie zobaczysz szczegółów wszystkich zależności i łączy, jeśli to zrobisz.

 Po wygenerowaniu mapy zapoznaj się z tymi wskazówkami dotyczącymi przeglądania kodu:

- Spójrz na klastry zależności naturalne w kodzie. Na pasku narzędzi mapy wybierz pozycję **Przycisk Układ**, **Szybkie klastry**![Szybkie klastry na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif "QuickClustersIcon (QuickClustersIcon)"). Zobacz [Zmienianie układu mapy](#Selecting).

     ![Wykres zależności &#45; układ szybkich klastrów](../modeling/media/dependencygraph-quickclusters.png "DependencyGraph_QuickClusters")

- Zorganizuj mapę na mniejsze obszary, grupując powiązane węzły. Zwiń te grupy, aby wyświetlić tylko zależności międzygrupami, które pojawiają się automatycznie. Zobacz [Węzły grupy](#OrganizeGroups).

- Użyj filtrów, aby uprościć mapę i skupić się na typach węzłów lub łączy, które Cię interesują. Zobacz [Filtrowanie węzłów i łączy](#FilterNodes).

- Maksymalizuj wydajność dużych map. Aby uzyskać więcej [informacji, zobacz Zależności mapowania między rozwiązaniami.](../modeling/map-dependencies-across-your-solutions.md) Na przykład włącz **Pomiń kompilację** na pasku narzędzi mapy, aby program Visual Studio nie odbudował rozwiązania podczas aktualizowania elementów na mapie.

## <a name="change-the-map-layout"></a><a name="Selecting"></a>Zmienianie układu mapy

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Rozmieść przepływ zależności dla całej mapy w określonym kierunku. Może to pomóc w wyświetleniu warstw architektonicznych w kodzie.|Na pasku narzędzi mapy wybierz pozycję **Układ**, a następnie:<br /><br /> -   Przycisk wykresu od góry **do dołu** ![do dołu](../modeling/media/topbottomgraphbutton.gif "TopBottomGraphButton (TopBottomGraphButton)")<br />-   Przycisk wykresu **od dołu do** ![dołu do góry](../modeling/media/bottomtopgraphbutton.gif "Przycisk dołu topografu")<br />-   Przycisk układu **od lewej do prawej** do ![prawej](../modeling/media/leftrightgraphbutton.gif "Lewy przycisk")<br />-   **Right to Left** ![Przycisk wykresu](../modeling/media/rightleftgraphbutton.gif "Prawy przycisk") od prawej do lewej od prawej do lewej|
|Zobacz klastry zależności naturalnych w kodzie z najbardziej zależnych węzłów w centrum klastrów i najmniej zależnych węzłów na zewnątrz tych klastrów.|Na pasku narzędzi mapy wybierz pozycję **Układ**, a następnie przycisk **Szybkie klastry szybkich klastrów**![na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif "QuickClustersIcon (QuickClustersIcon)").|
|Wybierz jeden lub więcej węzłów na mapie.|Kliknij węzeł, aby go zaznaczyć. Aby zaznaczyć lub usunąć zaznaczenie więcej niż jednego węzła, przytrzymaj **klawisz CTRL** podczas klikania.<br /><br /> Klawiatura: naciśnij **klawisz TAB** lub użyj klawiszy strzałek, aby przenieść prostokąt ostrości kropkowanego do węzła i naciśnij **spację,** aby go zaznaczyć. Naciśnij **klawisz CTRL** + **SPACJA,** aby zaznaczyć wiele lub usunąć zaznaczenie węzłów.|
|Przenoszenie określonych węzłów na mapie.|Przeciągnij węzły, aby je przenieść. Aby przenieść inne węzły i łącza z drogi podczas przeciągania węzłów, naciśnij i przytrzymaj klawisz **SHIFT.**<br /><br /> Klawiatura: przytrzymaj **klawisz CTRL** i naciśnij klawisze strzałek.|
|Zmień układ wewnątrz grupy niezależnie od innych węzłów i grup na mapie.|Wybierz węzeł i otwórz menu skrótów. Wybierz **pozycję Układ** i wybierz styl układu.<br /><br /> — lub —<br /><br /> Wybierz węzeł i rozwiń go, aby wyświetlić węzły podrzędne. Kliknij tytuł![węzła,](../modeling/media/dependencygraph-grouptoolbar.gif "DependencyGraph_GroupToolbar") aby wyświetlić pas narzędzi podręcznych grupy, a następnie otwórz **styl opcji Zmienianie stylu układu wykresu**zależności grupy &#45; pasek narzędzi grupy &#45; na liście układu. Wybierz jeden z układów drzewa, **Szybkie klastry**lub **Widok listy** (który rozmieszcza zawartość grupy na liście).<br /><br /> Aby uzyskać więcej informacji, zobacz [węzły grupy.](#OrganizeGroups)|
|Cofnij akcję na mapie.|Naciśnij **klawisz CTRL** + **Z** lub użyj polecenia **Cofnij program** Visual Studio.|

## <a name="browse-the-map"></a><a name="Explore"></a>Przeglądanie mapy

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Zeskanuj mapę.|Przeciągnij mapę w dowolnym kierunku za pomocą myszy.<br /><br /> — lub —<br /><br /> Przytrzymaj **klawisz SHIFT** i obróć kółko myszy, aby przewinąć w poziomie. Przytrzymaj **klawisz SHIFT** + **CTRL** i obróć kółko myszy, aby przewinąć w poziomie.|
|Powiększanie lub pomniejszanie mapy.|Obróć kółko myszy.<br /><br /> — lub —<br /><br /> Użyj listy rozwijanej **Powiększenie** na pasku narzędzi mapy kodu.<br /><br /> — lub —<br /><br /> Użyj skrótów klawiaturowych. Aby powiększyć, naciśnij **klawisze CTRL + SHIFT + .** (okres). Aby pomniejszyć widok, naciśnij **klawisze CTRL + SHIFT +** (przecinek).|
|Powiększ określony obszar za pomocą myszy.|Przytrzymaj prawy przycisk myszy podczas rysowania prostokąta wokół interesującego Cię obszaru.|
|Zmienić rozmiar i dopasować mapę w oknie.|Wybierz **pozycję Powiększ, aby dopasować** z listy **Powiększenie** na pasku narzędzi mapy kodu.<br /><br /> — lub —<br /><br /> Kliknij ikonę **Powiększenie, aby dopasować** ![ikonę Powiększenie ikony na pasku narzędzi mapy](../modeling/media/almcodemapzoomicon.png "ALMCodeMapZoomIcon") na pasku narzędzi mapy kodu. Klawiatura: naciśnij **klawisze CTRL + 0** (zero).|
|Znajdź węzeł na mapie według jego nazwy. **Wskazówka:**  Działa to tylko w przypadku elementów na mapie. Aby znaleźć elementy w rozwiązaniu, ale nie na mapie, znajdź je w **Eksploratorze rozwiązań,** a następnie przeciągnij je na mapę. (Przeciągnij zaznaczenie lub na pasku narzędzi Eksploratora rozwiązań kliknij pozycję **Pokaż na mapie kodu).**|1. Wybierz ikonę **Znajdź** ![znajdź na pasku narzędzi mapy](../modeling/media/almcodemapfindicon.png "ALMCodeMapFindIcon") na pasku narzędzi mapy kodu (klawiatura: naciśnij **klawisze CTRL + F**), aby wyświetlić pole wyszukiwania w prawym górnym rogu mapy.<br />2. Wpisz nazwę elementu i naciśnij **przycisk Powrót** lub kliknij ikonę "lupa". Pierwszy element zgodny z wyszukiwaniem pojawi się zaznaczony na mapie.<br />3. Aby dostosować wyszukiwanie, otwórz listę rozwijaną i wybierz opcję wyszukiwania. Dostępne opcje **to Znajdź następny**, Znajdź **poprzedni**i Wybierz **wszystko**. Następnie kliknij odpowiedni przycisk obok pola tekstowego wyszukiwania.<br />     ![Lista rozwijania opcji wyszukiwania&#45;w dół](../modeling/media/almcodemapssearchdropdown.png "ALMCodeMapsSearchDropDown")<br />     Możesz też użyć klawiatury: naciśnij klawisz **F3,** aby wybrać następny pasujący węzeł, lub **shift + F3,** aby wybrać poprzedni pasujący węzeł.<br />4. Wybierz jedną z opcji, które określają sposób obsługi wyszukiwanych haseł, klikając ikony pod polem tekstowym wyszukiwania.<br />     ![Opcje dopasowania wyszukiwania](../modeling/media/almcodemapssearchmatchicons.png "AlmCodeMapsSearchMatchIcons")<br />     Opcje to, od lewej do prawej, dopasowanie wielkości liter, dopasowanie tylko całych wyrazów, użycie składni wyrażenia regularnego .NET, automatyczne rozwijanie grup, aby wyświetlać dopasowania do ujętych elementów. **Ważne:**  Za pomocą pola wyszukiwania można wyszukiwać dopasowania w zwiniętych grupach tylko wtedy, gdy grupy te zostały rozwinięte wcześniej. Aby znaleźć te dopasowania i automatycznie rozwinąć grupy nadrzędne, wybierz tę opcję w polu wyszukiwania.|
|Zaznacz wszystkie niezaznaczone węzły.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **wybierz**, **odwróć zaznaczenie**.|
|Wybierz dodatkowe węzły, które łączą się z wybranymi.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **pozycję Wybierz,** a jeden z nich:<br /><br /> - Aby wybrać dodatkowe węzły, które łączą się bezpośrednio z wybranym węzłem, wybierz opcję **Zależności przychodzące**.<br />- Aby wybrać dodatkowe węzły, które łączą się bezpośrednio z wybranego węzła, wybierz opcję **Zależności wychodzące**.<br />- Aby wybrać dodatkowe węzły, które łączą się bezpośrednio z i z wybranego węzła, wybierz **opcję Oba**.<br />- Aby wybrać wszystkie węzły, które łączą się z i z wybranego węzła, wybierz pozycję **Połączony podkategow.**<br />- Aby wybrać wszystkie części podrzędne wybranego węzła, wybierz pozycję **Dzieci**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a>Filtrowanie węzłów i łączy

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Pokaż lub ukryj okienko Filtry.|Wybierz przycisk **Filtry** na pasku narzędzi mapy kodu. Okienko Filtry jest domyślnie wyświetlane jako strona z kartami w oknie Eksploratora rozwiązań.|
|Filtruj typy węzłów, które są wyświetlane na mapie.|Ustaw lub wyczyść pola wyboru na liście **Elementy kodu** w okienku Filtry.|
|Filtruj typy łączy wyświetlanych na mapie.|Ustaw lub wyczyść pola wyboru na liście **Relacje** w okienku Filtry.|
|Pokaż lub ukryj węzły projektu testowego na mapie.|Ustaw lub **wyczyść** pole wyboru Zasoby testowe na liście **Różne** w okienku Filtry.|

 Ikony wyświetlane w panelu Legenda mapy odzwierciedlają ustawienia na liście. Aby wyświetlić lub ukryć panel Legenda, kliknij przycisk **Legenda** na pasku narzędzi mapy kodu.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a>Sprawdzanie węzłów i łączy
 Mapy kodu pokazują tego rodzaju linki:

- Pojedyncze łącze reprezentuje pojedynczą relację między dwoma węzłami.

- Łącze międzygrupami reprezentuje relację między dwoma węzłami w różnych grupach.

- Łącze agregowane reprezentuje wszystkie relacje, które wskazują w tym samym kierunku między dwiema grupami.

> [!TIP]
> Domyślnie mapa pokazuje łącza między grupami tylko dla wybranych węzłów. Aby zmienić to zachowanie w celu wyświetlenia lub ukrycia zagregowanych łączy między grupami, kliknij pozycję **Układ** na pasku narzędzi mapy kodu i wybierz pozycję **Zaawansowane**, a następnie **pokaż wszystkie łącza między grupami** lub **Ukryj wszystkie łącza między grupami**. Aby uzyskać więcej informacji, zobacz [Ukrywanie lub pokazywalki węzłów i łączy.](#HidingShowing)

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Zobacz więcej informacji o węźle lub łączu.|Przesuwaj wskaźnik myszy na górze węzła lub łącza, aż pojawi się etykietka narzędzia.<br /><br /> Etykietka narzędzia dla zagregowanego łącza zawiera listę poszczególnych zależności, które reprezentuje.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla węzła lub łącza. Wybierz **polecenie Edytuj**właściwości . **Properties**|
|Pokazywania lub ukrywania zawartości grupy.|- Aby rozwinąć grupę, otwórz menu skrótów dla węzła i wybierz pozycję **Grupuj**, **Rozwiń**.<br />     — lub —<br />     Przesuwaj wskaźnik myszy na górze węzła, aż pojawi się przycisk szewronu (strzałka w dół). Kliknij ten przycisk, aby rozwinąć grupę. Klawiatura: aby rozwinąć lub zwinąć**+** wybraną grupę, naciśnij klawisz **PLUS** ( ) lub klawisz **MINUS** (**-**).<br />- Aby zwinąć grupę, otwórz menu skrótów dla węzła i wybierz pozycję **Grupuj**, **Zwiń**.<br />     — lub —<br />     Przesuwaj wskaźnik myszy na górze grupy, aż pojawi się przycisk szewronu (strzałka w górę). Kliknij ten przycisk, aby zwinąć grupę.<br />- Aby rozwinąć wszystkie grupy, naciśnij **klawisz CTRL** + **A,** aby wybrać wszystkie węzły. Otwórz menu skrótów dla mapy i wybierz pozycję **Grupuj**, **Rozwiń**. **Uwaga:**      To polecenie nie jest dostępne, jeśli rozwinięcie wszystkich grup powoduje problemy z mapą lub pamięcią niezrozumiaszaną do użyteczności. Zaleca się, aby rozwiać mapę tylko do poziomu szczegółowości, na których Ci zależy.<br />- Aby zwinąć wszystkie grupy, otwórz menu skrótów dla węzła lub mapy. Wybierz **pozycję Grupuj**, **Zwiń wszystkie**.|
|Zobacz definicję kodu dla obszaru nazw, typu lub elementu członkowskiego.|Otwórz menu skrótów dla węzła i wybierz pozycję **Przejdź do definicji**.<br /><br /> — lub —<br /><br /> Kliknij dwukrotnie węzeł. W przypadku grup rozwiniętych kliknij dwukrotnie nagłówek grupy.<br /><br /> — lub —<br /><br /> Wybierz węzeł i naciśnij klawisz **F12**.<br /><br /> Przykład:<br /><br /> - Dla obszaru nazw zawierającego jedną klasę, plik kodu dla klasy otwiera się, aby wyświetlić definicję tej klasy. W innych przypadkach w oknie **Znajdź wyniki symbolu** jest wyświetlana lista plików kodu. **Uwaga:**      Podczas wykonywania tego zadania w obszarze nazw Visual Basic .NET plik kodu znajdujący się za obszarem nazw nie jest otwierany. Ten problem występuje również podczas wykonywania tego zadania w grupie wybranych węzłów, które zawierają obszar nazw visual basic .NET. Aby obejść ten problem, przejdź ręcznie do pliku kodu znajdującego się za obszarem nazw lub pomiń węzeł obszaru nazw z zaznaczenia.<br />- Dla klasy lub klasy częściowej plik kodu dla tej klasy otwiera się, aby wyświetlić definicję klasy.<br />- Dla metody, plik kodu dla klasy nadrzędnej otwiera się, aby pokazać definicję metody.|
|Sprawdź zależności i elementy, które uczestniczą w łączu agregacji.|Wybierz interesujące Cię linki i otwórz menu skrótów do wyboru. Wybierz **pozycję Pokaż linki przyczyniające się** lub Pokaż linki **przyczyniające się na nowej mapie kodu**.<br /><br /> Program Visual Studio rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które w nim uczestniczą. **Uwaga:**  Podczas badania zależności między elementami w grupach częściowych może zostać wyświetlenie tego zachowania: <ul><li>Linki do przedmiotów, które nie biorą udziału w egzaminie, znikają z mapy, mimo że te linki nadal istnieją.</li><li>Załóżmy, że zbadać łącze do elementu w grupie częściowej, a następnie zbadać inne łącze do tego samego elementu. Podczas drugiego egzaminu docelowa grupa częściowa pokazuje tylko przedmioty z pierwszego egzaminu. Linki i przedmioty docelowe, które nie uczestniczyły w pierwszym egzaminie, ale biorą udział w drugim egzaminie, nie pojawiają się.</li></ul> Aby wyświetlić brakujące elementy z grupy, wybierz **ikonę Refetch Children**![Refetch Children (która](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") oznacza, że nie wszyscy członkowie grupy są obecni na mapie). Możesz również spróbować cofnąć swoje działania (Klawiatura: naciśnij **klawisze CTRL+Z**) i sprawdzić zależności na nowej mapie.|
|Sprawdź zależności między wieloma węzłami w różnych grupach.|Rozwiń grupy, aby zobaczyć wszystkie ich dzieci. Wybierz wszystkie węzły, które Cię interesują, w tym ich dzieci. Mapa pokazuje łącza między grupami między wybranymi węzłami.<br /><br /> Aby zaznaczyć wszystkie węzły w grupie, naciśnij i przytrzymaj **klawisz SHIFT** i lewy przycisk myszy podczas rysowania prostokąta wokół tej grupy. Aby zaznaczyć wszystkie węzły na mapie, naciśnij klawisz **CTRL**+**A**. **Wskazówka:**  Aby zawsze wyświetlać łącza między grupami, wybierz pozycję **Układ** na pasku narzędzi mapy, **Zaawansowane**, **Pokaż wszystkie łącza między grupami**.|
|Zobacz elementy, do których odwołuje się węzeł lub łącze.|Otwórz menu skrótów dla węzła i wybierz pozycję **Znajdź wszystkie odwołania**. **Uwaga:**  Dotyczy to tylko `Reference` wtedy, gdy atrybut jest ustawiony dla węzła lub łącza w pliku .dgml mapy. Aby dodać odwołania do elementów z węzłów lub łączy, zobacz [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a>Ukrywanie lub pokazywalki węzłów i łączy
 Ukrywanie węzłów wyklucza je z udziału w układzie algorytmów. Domyślnie łącza między grupami są ukryte. Łącza grupy współzależności są poszczególnymi łączami połączenia między grupami węzłów. Gdy grupy są zwinięte, mapa agreguje wszystkie łącza między grupami w pojedyncze łącza między grupami. Gdyby rozwinąć grupę i wybrać węzły wewnątrz grupy, łącza grupy współzależności pojawiają się i pokażą zależności w tej grupie.

> [!CAUTION]
> Przed udostępnieniem mapy utworzonej w programie Visual Studio Enterprise osobom korzystającym z programu Visual Studio Professional należy odkryć wszystkie węzły lub łącza między grupami, które mają być widoczne dla innych osób. W przeciwnym razie użytkownicy nie mogą odkryć tych elementów.

### <a name="to-hide-or-show-nodes"></a>Aby ukryć lub pokazać węzły

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Ukryj zaznaczone węzły.|1. Wybierz węzły, które chcesz ukryć.<br />2. Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **pozycję Wybierz**, **Ukryj zaznaczone**.|
|Ukryj niezaznaczone węzły.|1. Wybierz węzły, które mają pozostać widoczne.<br />2. Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **pozycję Wybierz**, **Ukryj niezaznaczone**.|
|Pokaż ukryte węzły.|- Aby wyświetlić wszystkie ukryte węzły wewnątrz grupy, najpierw upewnij się, że grupa jest rozwinięta. Otwórz menu skrótów i wybierz pozycję **Wybierz**, **Odkryj elementy podrzędne**.<br />     — lub —<br />     Kliknij ikonę **Odkryj**![ikonę Odkryjące dzieci](../modeling/media/dependencygraph-filtericon-hiddennodes.gif "DependencyGraph_FilterIcon_HiddenNodes") w lewym górnym rogu grupy (jest to widoczne tylko wtedy, gdy istnieją ukryte węzły podrzędne).<br />- Aby wyświetlić wszystkie ukryte węzły, otwórz menu skrótów dla mapy lub węzła i wybierz **wybierz Wybierz**, **Odkryj wszystko**.|

### <a name="to-hide-or-show-links"></a>Aby ukryć lub pokazać łącza

|**Do**|**Na pasku narzędzi mapy wybierz pozycję Układ, Zaawansowane, a następnie wybierz pozycję**|
|------------|----------------------------------------------------------------------|
|Pokaż łącza między grupami przez cały czas.|**Pokaż wszystkie łącza między grupami**. Powoduje to ukrycie agregowanych łącz między grupami.|
|Ukrywanie łączy między grupami przez cały czas.|**Ukryj wszystkie łącza między grupami**|
|Pokaż tylko łącza między grupami dla wybranych węzłów.|**Pokaż łącza międzygrupami w wybranych węzłach**|
|Ukryj wszystkie łącza.|**Ukryj wszystkie łącza**. Aby ponownie wyświetlić łącza, wybierz jedną z opcji wymienionych powyżej.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a>Węzły grupy

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Pokaż węzły kontenera jako węzły grupy lub węzły liścia.|Aby wyświetlić węzły kontenera jako węzły liścia: wybierz węzły, otwórz menu skrótów dla swojego zaznaczenia i wybierz polecenie **Grupuj**, **Konwertuj na liść**.<br /><br /> Aby wyświetlić węzły kontenera jako węzły grupy: wybierz węzły, otwórz menu skrótów dla swojego zaznaczenia i wybierz polecenie **Grupuj,** **Konwertuj na grupę**.|
|Zmienianie układu wewnątrz grupy.|Zaznacz grupę, otwórz menu skrótów, wybierz **pozycję Układ**i wybierz odpowiedni styl układu.<br /><br /> — lub —<br /><br /> 1. Wybierz grupę i upewnij się, że jest rozwinięta.<br />2. Ponownie kliknij nagłówek grupy i pojawi się pasek narzędzi grupy.<br />     ![Wykres zależności &#45; pasek narzędzi grupy](../modeling/media/dependencygraph-group.png "DependencyGraph_Group")<br />3. Otwórz **styl Zmień styl układu wykresu** zależności listy grup &#45; ![grupuj pasek narzędzi &#45; układ](../modeling/media/dependencygraph-grouptoolbar.gif "DependencyGraph_GroupToolbar") i wybierz odpowiedni styl układu.<br /><br /> **Widok listy** zmienia kolejność członków grupy na listę. **Domyślny wykres** resetuje układ grupy do domyślnego układu mapy. Aby uzyskać inne opcje, zobacz [Zmienianie układu mapy](#Selecting).|
|Dodawanie węzła do grupy.|Przeciągnij węzeł na grupę.<br /><br /> Podczas przeciągania węzła program Visual Studio wyświetla wskaźnik wskazujący, że przenosisz węzeł.<br /><br /> Można również przeciągać węzły na zewnątrz grupy.|
|Dodawanie węzła do węzła niebędącego grupą.|Przeciągnij węzeł na węzeł docelowy. Można przekonwertować dowolny węzeł docelowy do grupy, dodając do niego węzły.|
|Grupowanie wybranych węzłów.|1. Wybierz węzły, które chcesz zgrupować. Nad ostatnim wybranym węzłem pojawi się wyskakującym pasku narzędzi.<br />     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")<br />2. Na pasku narzędzi wybierz czwartą ikonę **Zgrupuj wybrane węzły** (jeśli węzeł zostanie rozwinięty, będzie miał pięć zamiast czterech ikon). Wpisz nazwę nowej grupy i naciśnij klawisz **Return**.<br />     — lub —<br />     Zaznacz węzły, które chcesz zgrupować, i otwórz menu skrótów dla wybranego. Wybierz **polecenie Grupuj,** **Dodaj grupę nadrzędną,** wpisz nazwę nowej grupy i naciśnij klawisz **Return**.<br /><br /> Można zmienić nazwę grupy. Otwórz menu skrótów dla grupy i wybierz polecenie **Edytuj** **właściwości,** aby otworzyć okno Właściwości programu Visual Studio. We właściwości **Label** zmień nazwę grupy zgodnie z wymaganiami.|
|Usuń grupy.|Zaznacz jedną grupę lub kilka, które chcesz usunąć. Otwórz menu skrótów dla swojego zaznaczenia i wybierz pozycję **Grupuj**, **Usuń grupę**.|
|Usuń węzły z grupy nadrzędnej.|Zaznacz węzły, które chcesz przenieść. Otwórz menu skrótów dla swojego zaznaczenia i wybierz pozycję **Grupuj**, **Usuń z rodzica**. Spowoduje to usunięcie węzłów do ich dziadków lub poza grupą, jeśli nie mają grupy dziadków.<br /><br /> — lub —<br /><br /> Zaznacz węzły i wyciągnij je z grupy.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a>Dodawanie, usuwanie lub zmienianie nazw węzłów, łączy i komentarzy
 Możesz wyświetlić więcej lub mniej elementów na mapie, aby przejść do szczegółów lub uprościć mapę. Można również zmieniać nazwy elementów i dodawać komentarze do elementów.

> [!CAUTION]
> Przed udostępnieniem mapy utworzonej przy użyciu programu Visual Studio Enterprise osobom korzystającym z programu Visual Professional upewnij się, że wszystkie elementy kodu, które mają być widoczne dla innych osób, są widoczne na mapie. W przeciwnym razie ci użytkownicy nie będą mogli pobrać usuniętych elementów kodu.

### <a name="add-a-node-for-a-code-element"></a>Dodawanie węzła dla elementu kodu

|**Do**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Dodaj nowy węzeł ogólny w bieżącym położeniu wskaźnika myszy.|1. Przesuń wskaźnik myszy do miejsca na mapie, w którym chcesz umieścić nowy element kodu i naciśnij **przycisk Wstaw**.<br />     — lub —<br />     Otwórz menu skrótów dla mapy i wybierz polecenie **Edytuj**, **Dodaj**, **Węzeł ogólny**.<br />2. Wpisz nazwę nowego węzła i naciśnij **klawisz Return**.|
|Dodaj określony typ węzła elementu kodu w bieżącej lokalizacji wskaźnika myszy.|1. Przesuń wskaźnik myszy do miejsca na mapie, w którym chcesz umieścić nowy element kodu i otwórz menu skrótów dla mapy.<br />2. Wybierz **pozycję Edytuj**, **Dodaj**i wybierz odpowiedni typ węzła.<br />3. Wpisz nazwę nowego węzła i naciśnij **klawisz Return**.|
|Dodaj ogólny lub określony typ węzła elementu kodu do grupy.|1. Wybierz węzeł grupy i otwórz menu skrótów.<br />2. Wybierz **pozycję Edytuj**, **Dodaj**i wybierz odpowiedni typ węzła.<br />3. Wpisz nazwę nowego węzła i naciśnij **klawisz Return**.|
|Dodaj nowy węzeł tego samego typu i połączony z istniejącym węzłem.|1. Wybierz element kodu. Nad nim pojawi się wyskakującym pasku narzędzi.<br />     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")<br />2. Na pasku narzędzi wybierz **drugą ikonę Utwórz węzeł o tej samej kategorii co ten węzeł i dodaj do niego nowe łącze**.<br />3. Wybierz miejsce na mapie, aby umieścić nowy element kodu i kliknij lewy przycisk myszy.<br />4. Wpisz nazwę nowego węzła i naciśnij **klawisz Return**.|
|Dodaj nowy węzeł ogólny, który jest połączony z istniejącym elementem kodu, który ma fokus.|1. Za pomocą klawiatury, naciśnij **klawisz Tab,** aż element kodu do łączenia z ma fokus (przerywany prostokąt).<br />2. **Alt**+Naciśnij**klawisz Alt Insert**.<br />3. Wpisz nazwę nowego węzła i naciśnij **klawisz Return**.|
|Dodaj nowy węzeł ogólny, który łączy się z istniejącym elementem kodu, który ma fokus.|1. Za pomocą klawiatury, naciśnij **klawisz Tab,** aż element kodu, aby połączyć się ma fokus (przerywany prostokąt).<br />2. Naciśnij klawisz **Alt**+**Shift**+**Insert**.<br />3. Wpisz nazwę nowego węzła i naciśnij **klawisz Return**.|

|**Aby dodać elementy kodu dla**|**Wykonaj te kroki**|
|----------------------------------|-----------------------------|
|Elementy kodu w rozwiązaniu.|1. Znajdź element kodu w **Eksploratorze rozwiązań**. Użyj pola wyszukiwania **Eksploratora rozwiązań** lub przejrzyj rozwiązanie. **Wskazówka:**      Aby znaleźć elementy kodu, które mają zależności od typu lub elementu członkowskiego, otwórz menu skrótów dla tego typu lub elementu członkowskiego w **Eksploratorze rozwiązań**. Wybierz odpowiednią relację. **Eksplorator rozwiązań** pokazuje tylko te elementy kodu o określonych zależnościach.<br />2. Przeciągnij elementy kodu, które Cię interesują, na powierzchnię mapy. Można również przeciągnąć elementy kodu z widoku klasy lub przeglądarki obiektów.<br />     — lub —<br />     W **Eksploratorze rozwiązań**wybierz elementy kodu, które chcesz zamapować. Następnie na pasku **narzędzi Eksploratora rozwiązań** kliknij pozycję **Pokaż na mapie kodu**.<br /><br /> Domyślnie nadrzędna hierarchia kontenera dla nowych elementów kodu jest wyświetlana na mapie. Użyj przycisku **Dołącz elementy bezużyteczne** na pasku narzędzi mapy kodu, aby zmienić to zachowanie. Po wyłączeniu do mapy jest dodawany tylko sam element kodu. Aby odwrócić to zachowanie tylko dla jednej akcji przeciągania i upuszczania, naciśnij i przytrzymaj klawisz **CTRL** podczas przeciągania elementów kodu na mapę.<br /><br /> Visual Studio dodaje elementy kodu dla elementów kodu najwyższego poziomu w zaznaczeniu. Aby sprawdzić, czy element kodu zawiera inne elementy kodu, przesuń wskaźnik myszy na górze elementu kodu, tak aby pojawiał się szewron (strzałka w dół). Wybierz szewron, aby rozwinąć element kodu. Aby rozwinąć wszystkie elementy kodu, naciśnij **klawisz CTRL**+**A,** aby zaznaczyć wszystkie elementy, otwórz menu skrótów dla mapy i wybierz pozycję **Grupuj**, **Rozwiń**. To polecenie nie jest dostępne, jeśli rozwinięcie wszystkich grup spowodowałoby nieużywanie mapy lub spowodowałoby brak problemów z pamięcią.|
|Elementy kodu związane z elementami kodu na mapie.|Kliknij przycisk **Pokaż powiązane** na pasku narzędzi mapy kodu i wybierz typ powiązanych elementów, które Cię interesują.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla elementu kodu. Wybierz jeden z **Show ...** pozycji w menu w zależności od rodzaju relacji, która Cię interesuje. Na przykład można zobaczyć elementy, które odwołuje się do bieżącego elementu, elementy, które odwołują się do bieżącego elementu, typy podstawowe i pochodne dla klas, wywoływania metody i zawierające klasy, przestrzenie nazw i zestawy.<br /><br /> Aby uzyskać więcej informacji, zobacz [ten temat](../modeling/map-dependencies-across-your-solutions.md).|
|Skompilowane zestawy .NET (dll lub exe) lub pliki binarne.|Przeciągnij zestawy lub pliki binarne spoza programu Visual Studio na mapę.<br /><br /> Możesz przeciągnąć z Eksploratora Windows lub Eksploratora plików tylko wtedy, gdy jest on uruchomiony i Visual Studio na tym samym poziomie uprawnień kontroli dostępu użytkownika (UAC). Na przykład jeśli funkcja Kontrola konta użytkownika jest włączona i jest uruchomiony program Visual Studio jako administrator, Eksplorator Windows lub Eksplorator plików zablokuje operację przeciągania.|

### <a name="AddNodes"></a>
##### <a name="add-a-link-between-existing-code-elements"></a>Dodawanie łącza między istniejącymi elementami kodu

1. Wybierz element kodu źródłowego. Nad elementem kodu pojawi się pasek narzędzi.

    ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")

2. Na pasku narzędzi wybierz pierwszą ikonę **Utwórz nowe łącze z tego węzła, do którego węzła, który klikniesz na następny**.

3. Wybierz docelowy element kodu. Pojawi się łącze między dwoma elementami kodu.

   \-lub -

4. Wybierz element kodu źródłowego na mapie.

5. Jeśli masz zainstalowaną mysz, przesuń wskaźnik myszy poza granice mapy.

6. Otwórz menu skrótów elementu kodu i wybierz polecenie **Edytuj,** **Dodaj**, **Łącze ogólne**.

7. Tab do i wybierz element kodu docelowego dla łącza.

8. Naciśnij **przycisk RETURN**.

### <a name="AddComments"></a>
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Dodawanie komentarza do istniejącego węzła na mapie

1. Wybierz element kodu. Nad nim pojawi się pasek narzędzi.

     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")

2. Na pasku narzędzi wybierz trzecią **ikonę, Utwórz nowy węzeł komentarza z nowym łączem do wybranego węzła**.

     \-lub -

     Otwórz menu skrótów dla elementu kodu i wybierz polecenie **Edytuj**, **Nowy komentarz**.

3. Wpisz swoje komentarze. Aby wpisać w nowym wierszu, naciśnij **klawisz SHIFT** + **RETURN**.

##### <a name="add-a-comment-to-the-map-itself"></a>Dodawanie komentarza do samej mapy

1. Otwórz menu skrótów dla mapy i wybierz polecenie **Edytuj**, **Nowy komentarz**.

2. Wpisz swoje komentarze. Aby wpisać w nowym wierszu, naciśnij **klawisz SHIFT** + **RETURN**.

### <a name="RenameNodes"></a>
##### <a name="rename-a-code-element-or-link"></a>Zmienianie nazwy elementu kodu lub łącza

1. Wybierz element kodu lub łącze, którego nazwę chcesz zmienić.

2. Naciśnij **klawisz F2**lub otwórz menu skrótów i wybierz polecenie **Edytuj**, **Zmień nazwę**.

3. Gdy na mapie pojawi się pole edycji, zmień nazwę elementu kodu lub łącza.

     \-lub -

4. Otwórz menu skrótów i wybierz polecenie **Edytuj** **właściwości**.

5. Edytuj **Label** właściwości w oknie Właściwości programu Visual Studio.

##### <a name="remove-a-code-element-or-link-from-the-map"></a>Usuwanie elementu kodu lub łącza z mapy

1. Wybierz element kodu lub łącze i naciśnij klawisz **Delete.**

     \-lub -

     Otwórz menu skrótów dla elementu kodu lub łącza i wybierz pozycję **Edytuj**, **Usuń**.

2. Jeśli element lub łącze jest częścią grupy, wewnątrz grupy pojawia się przycisk **Refetch Children** button ![Refetch Children Icon.](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") Kliknij tę opcję, aby pobrać brakujące elementy i łącza.

- Można usunąć elementy kodu i łącza z mapy bez wpływu na kod źródłowy. Po ich usunięciu ich definicje są usuwane z pliku DGML (dgml).

- Mapy utworzone przez edycję DGML, przez dodanie elementów kodu niezdefiniowanego lub przy użyciu niektórych wcześniejszych wersji programu Visual Studio, nie obsługują tej możliwości.

##### <a name="flag-a-code-element-for-follow-up"></a>Oflaguj element kodu dla działań następczych

1. Wybierz element kodu lub łącze, które chcesz oznaczyć do podjęcia działań następczych.

2. Otwórz menu skrótów i wybierz polecenie **Edytuj**, **Flaga dla kontynuacji**.

- Domyślnie element kodu zyskuje czerwone tło. Rozważ [dodanie](#AddComments) komentarza do niego wraz z odpowiednimi informacjami uzupełniającymi.

- Zmień kolor tła elementu lub wyczyść flagę uzupełniającą, wybierając pozycję **Edytuj**, **Inne kolory flag**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a>Zmienianie stylu elementu kodu lub łącza
 Można zmienić ikony elementów kodu oraz kolory elementów kodu i łączy za pomocą wstępnie zdefiniowanych ikon i kolorów. Na przykład można wybrać kolor, aby wyróżnić elementy kodu i łącza, które mają określoną kategorię lub właściwość. Dzięki temu można identyfikować i skupiać się na określonych obszarach mapy. Niestandardowe ikony i kolory można określić, edytując plik .dgml mapy; zobacz [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Aby zastosować wstępnie zdefiniowany kolor lub ikonę do elementów kodu lub łączy z określoną kategorią lub właściwością

1. Na pasku narzędzi mapy wybierz pozycję **Legenda**.

2. W polu **Legenda** sprawdź, czy kategoria lub właściwość elementu kodu jest już wyświetlana na liście.

3. Jeśli lista nie zawiera kategorii lub właściwości, wybierz **+** w polu **Legenda,** a następnie wybierz polecenie **Właściwość węzła,** Kategoria **węzła,** **Właściwość łącza**lub Kategoria **łącza**. Następnie wybierz właściwość lub kategorię. Kategoria lub właściwość pojawi się teraz w polu **Legenda.**

    > [!NOTE]
    > Aby utworzyć i przypisać kategorię lub właściwość do elementu kodu, można edytować plik .dgml mapy; zobacz [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. W polu **Legenda** kliknij ikonę obok dodanej kategorii lub właściwości lub chcesz zmienić.

5. Skorzystaj z poniższej tabeli, aby wybrać styl, który ma zostać zmieniony:

    |**Aby zmienić**|**Wybierz ikonę**|
    |-----------------------|----------------|
    |Kolor tła|**Tło**|
    |Kolor konturu|**Obrysu**|
    |Kolor tekstu (wyświetlana jest litera "f" pokazująca wynik)|**Pierwszy plan**|
    |Ikona|**Ikony**|

     Zostanie **wyświetlone** okno dialogowe Selektor zestawu kolorów lub **Selektor zestawu ikon,** aby wybrać kolor lub ikonę.

6. W oknie dialogowym **Selektor zestawu kolorów** lub Selektor zestawu **ikon** wykonaj jedną z następujących czynności:

    |**Aby zastosować**|**Wykonaj te kroki**|
    |--------------------|-----------------------------|
    |Zestaw kolorów lub ikon|Otwórz listę **zestawów** **Wybierz kolor** (lub **ikonę).** Wybierz zestaw kolorów lub ikon.|
    |Określony kolor lub ikona|Otwórz listę wartości kategorii lub właściwości. Wybierz kolor lub ikonę.|

    > [!NOTE]
    > Style można zmienić, usunąć lub tymczasowo zdezaktywować w polu **Legenda.** Zobacz [Pole Edytowanie legendy](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a>Edytowanie pola Legenda
 Style można zmienić, usunąć lub tymczasowo zdezaktywować w polu **Legenda:**

1. Otwórz menu skrótów dla stylu w polu **Legenda.**

2. Wykonaj jedno z następujących zadań:

    |**Do**|**Wybierz ikonę**|
    |------------|----------------|
    |Dezaktywacja elementu kodu|**Wyłączanie**|
    |Usuwanie elementu kodu|**Usuwanie**|
    |Przenieś styl w górę|**Przenieś w górę**|
    |Przenoszenie elementu kodu w dół|**Przenieś w dół**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a>Kopiowanie stylów z jednej mapy na drugą

1. Upewnij się, że na mapie źródłowej pojawi się pole **Legenda.** Jeśli nie jest widoczny, na pasku narzędzi mapy kliknij pozycję **Legenda**.

2. Otwórz menu skrótów dla pola **Legenda.** Wybierz **pozycję Kopiuj legendę**.

3. Wklej legendę na mapie docelowej.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a>Scalanie map kodu
 Mapy można scalać, kopiując i wklejając elementy kodu między mapami. Jeśli identyfikatory elementu kodu są zgodne, wklejanie elementów kodu działa jak operacja scalania. Aby ułatwić to zadanie, umieść wszystkie zestawy lub pliki binarne, które chcesz wizualizować w tym samym folderze, tak aby pełna ścieżka każdego zestawu lub pliku binarnego była taka sama dla każdej mapy, którą chcesz scalić.

 Alternatywnie można przeciągnąć te zestawy lub pliki binarne do tej samej mapy z tego folderu.

## <a name="see-also"></a>Zobacz też
 [Zależności map w rozwiązaniach](../modeling/map-dependencies-across-your-solutions.md) [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md) [Znajdowanie potencjalnych problemów przy użyciu analizatorów map kodu](../modeling/find-potential-problems-using-code-map-analyzers.md) Dostosowywanie map kodu przez edytowanie odwołania do języka [DGML (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md) [plików plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)