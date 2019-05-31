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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15b040ac69fbe581998850c3d8f56ad15d912a58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62995484"
---
# <a name="browse-and-rearrange-code-maps"></a>Przeglądanie i rozmieszczanie map kodu

Zmień kolejność elementów na mapach kodu, aby ułatwić ich do odczytywania i zwiększyć ich wydajność.

Możesz dostosować map kodu bez wywierania wpływu na podstawowy kod w rozwiązaniu. Jest to przydatne, gdy użytkownik chce skupić się na kod klucza elementów lub przedstawianiu pomysłów o kodzie. Na przykład wyróżnić interesujące obszary, możesz można wybierz elementy kodu na mapie i filtrować je, zmienianie stylu elementów kodu i linki, ukryć lub usuń elementy kodu i organizowanie elementów kodu za pomocą właściwości, kategorii lub grup.

 **Wymagania**

- Aby utworzyć map kodu, musi mieć program Visual Studio Enterprise.

- Można wyświetlać mapy kodu i wprowadzanie ograniczonych zmian edycyjnych dla map kodu w Visual Studio Professional.

## <a name="ManageLargeGraphs"></a> Rozpocznij pracę z mapami kodu

Utwórz mapę kodu (zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) Aby uzyskać więcej informacji). Jeśli nie chcesz czekać na mapę do ukończenia generowania, kliknij przycisk **anulować** łącze w dowolnym momencie można zatrzymać procesu tworzenia. Nie będzie jednak zobaczyć szczegółowe informacje o wszystkich zależności i łącza, jeśli to zrobisz.

Po wygenerowaniu mapy wprowadzenie porady dotyczące przeglądania kodu:

- Spójrz na klastry fizyczne zależności w kodzie. Na pasku narzędzi mapy wybierz **układ**, **szybkie klastry**![szybkie klastry przycisk na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif). Zobacz [zmienić układ mapy](#Selecting).

     ![Wykres zależności &#45; układ szybkie klastry](../modeling/media/dependencygraph_quickclusters.png)

- Organizuj mapy w mniejszych obszarów przez grupowanie powiązanych węzłów. Zwiń tych grup, aby wyświetlić tylko intergroup zależności, które pojawiają się automatycznie. Zobacz [węzły grup](#OrganizeGroups).

- Użyj filtrów w celu uproszczenia mapy i skoncentrować się na temat typów węzłów lub łączy, który Cię interesuje. Zobacz [Filtruj węzły i łącza](#FilterNodes).

- Maksymalizuj wydajność dużych mapy. Zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) Aby uzyskać więcej informacji. Na przykład włączyć **pominięcia kompilacji** na pasku narzędzi mapy, tak że program Visual Studio nie ponownie skompiluj rozwiązanie, gdy aktualizujesz elementy na mapie.

## <a name="Selecting"></a> Zmienianie układu mapy

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Rozmieść całą mapę w określonym kierunku przepływu zależności. To może pomóc warstwy architektury w kodzie.|Na pasku narzędzi mapy wybierz **układ**, a następnie:<br /><br /> -   **Od góry do dołu** ![od góry do dołu wykresu przycisku](../modeling/media/topbottomgraphbutton.gif)<br />-   **Od dołu do góry** ![dolny przycisk górnego wykresu](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Od lewej do prawej** ![od lewej do układu prawy przycisk](../modeling/media/leftrightgraphbutton.gif)<br />-   **Od prawej do lewej** ![bezpośrednio do przycisku po lewej stronie programu graph](../modeling/media/rightleftgraphbutton.gif)|
|Zobacz klastry fizyczne zależności w kodzie za pomocą najbardziej zależne węzły w środku klastrów i co najmniej zależne węzły na zewnątrz tych klastrów.|Na pasku narzędzi mapy wybierz **układ**, a następnie **szybkie klastry**![szybkie klastry przycisk na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif).|
|Wybierz co najmniej jeden węzeł na mapie.|Kliknij węzeł, aby go zaznaczyć. Aby zaznacz lub odznacz opcję więcej niż jeden węzeł, naciśnij i przytrzymaj **CTRL** podczas klikania.<br /><br /> Klawiatury: naciśnij **kartę** lub użyć klawiszy strzałek Aby przenieść prostokąt fokusu kropkowana węzła i naciśnij klawisz **miejsca** aby go zaznaczyć. Naciśnij klawisz **CTRL** + **miejsca** do wielokrotnego wyboru lub usuń zaznaczenie węzłów.|
|Poruszanie określonych węzłów na mapie.|Przeciągnij węzłów, aby przenieść je. Aby przejść do innych węzłów i łączy się z drogi podczas przeciągania węzłów, naciśnij i przytrzymaj klawisz **SHIFT** klucza.<br /><br /> Klawiatury: przytrzymaj **CTRL** i użyj klawiszy strzałek.|
|Zmień układ wewnątrz grupy, niezależnie od innych węzłów i grup na mapie.|Wybierz węzeł, a następnie otwórz menu skrótów. Wybierz **układ** i wybierz styl układu.<br /><br /> - lub -<br /><br /> Wybierz węzeł i rozwiń go, aby pokazać podrzędne węzły. Kliknij tytuł węzeł, aby wyświetlić grupy podręcznym pasku narzędzi, a następnie otwórz **Zmień styl układu grupy**![wykres zależności &#45; narzędzi grupy &#45; układ](../modeling/media/dependencygraph_grouptoolbar.gif) listy. Wybierz jeden z układów drzewa **szybkie klastry**, lub **widok listy** (który rozmieszcza zawartość grupy listy).<br /><br /> Zobacz [węzły grup](#OrganizeGroups) Aby uzyskać więcej informacji.|
|Cofnij akcję na mapie.|Naciśnij klawisz **CTRL** + **Z** lub za pomocą programu Visual Studio **Cofnij** polecenia.|

## <a name="Explore"></a> Przeglądaj mapy

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Skanowanie mapy.|Przeciągnij mapy w dowolnym kierunku, za pomocą myszy.<br /><br /> - lub -<br /><br /> Przytrzymaj **SHIFT** i obrót kółkiem myszy, aby przewijać w poziomie. Przytrzymaj **SHIFT** + **CTRL** i obrót kółkiem myszy, aby przewijać w poziomie.|
|Powiększanie lub pomniejszanie mapy.|Obrót kółkiem myszy.<br /><br /> - lub -<br /><br /> Użyj **powiększenia** listy rozwijanej na pasku narzędzi mapy kodu.<br /><br /> - lub -<br /><br /> Używanie skrótów klawiaturowych. Aby powiększyć, naciśnij klawisz **klawisze CTRL + SHIFT +.** (okres). Aby zmniejszyć, naciśnij klawisz **klawisze CTRL + SHIFT +,** (przecinek).|
|Powiększ określony obszar za pomocą myszy.|Przytrzymaj prawego przycisku myszy podczas rysowania prostokąt wokół tego obszaru, który Cię interesuje.|
|Zmień rozmiar i dopasować mapę w jego oknie.|Wybierz **Dopasuj widok do rozmiaru** z **powiększenia** listy na pasku narzędzi mapy kodu.<br /><br /> - lub -<br /><br /> Kliknij przycisk **Dopasuj do** ikonę ![powiększenia ikonę na pasku narzędzi Mapa](../modeling/media/almcodemapzoomicon.png) na pasku narzędzi mapy kodu. Klawiatury: naciśnij **CTRL + 0** (zero).|
|Znajdź węzeł na mapie, według jego nazwy. **Porada:**  Działa to tylko w przypadku elementów na mapie. Aby znaleźć elementy w Twoim rozwiązaniu, ale nie na mapie, je znaleźć w **Solution Explorer**, a następnie przeciągnij je do mapy. (Przeciągnij wybraną, lub na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Pokaż na mapie kodu**).|1.  Wybierz **znaleźć** ikonę ![Znajdź ikonę na pasku narzędzi Mapa](../modeling/media/almcodemapfindicon.png) na pasku narzędzi mapy kodu (klawiatura: naciśnij **CTRL + F**) do wyświetlenia w polu wyszukiwania w prawym górnym rogu mapy.<br />2.  Wpisz nazwę elementu i naciśnij klawisz **zwracają** lub kliknij ikonę "Lupa". Pierwszy element, który pasuje do wyszukiwania widoczny jako zaznaczony na mapie.<br />3.  Aby dostosować wyszukiwanie, otwórz listy rozwijanej, a następnie wybierz opcję wyszukiwania. W tabeli przedstawiono opcje **Znajdź następny**, **Find Previous**, i **Zaznacz wszystko**. Następnie kliknij odpowiedni przycisk obok polu tekstowym wyszukiwania.<br />     ![Listy opcji wyszukiwania&#45;listy rozwijanej](../modeling/media/almcodemapssearchdropdown.png)<br />     Można również użyć klawiatury: naciśnij **F3** wybrać kolejnego węzła pasującego lub **SHIFT + F3** wybrać poprzedniego węzła dopasowania.<br />4.  Wybierz dowolną spośród opcji, które określają, jak wyszukiwane terminy są obsługiwane, klikając ikony poniżej w polu tekstowym wyszukiwania.<br />     ![Opcje dopasowania wyszukiwania](../modeling/media/almcodemapssearchmatchicons.png)<br />     W tabeli przedstawiono opcje, od lewej do prawej strony, zamierzone, Zapisz poufnych dopasowania, dopasowywać całe wyrazy tylko wykorzystują składnię wyrażeń regularnych platformy .NET, automatycznie rozwiń grup do wyświetlenia dopasowania do zamkniętych elementów. **Ważne:**  Można użyć pola wyszukiwania, można znaleźć dopasowań w zwinięte grupy, tylko wtedy, gdy te grupy zostały wcześniej powiększone. Aby znaleźć te dopasowań i automatycznie rozwiń ich grupy nadrzędnej, należy wybrać tę opcję w polu wyszukiwania.|
|Zaznacz wszystkie węzły niezaznaczone.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **wybierz**, **Odwróć zaznaczenie**.|
|Zaznacz dodatkowe węzły, które łączą się z wybranymi.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **wybierz** i jeden z nich:<br /><br /> -Aby wybrać dodatkowe węzły, które łączą się bezpośrednio do wybranego węzła, wybierz **przychodzące zależności**.<br />-Aby zaznaczyć dodatkowe węzły, które łączą bezpośrednio z poziomu wybranego węzła, wybierz opcję **wychodzące zależności**.<br />-Aby wybrać dodatkowe węzły, które łączą się bezpośrednio do i z wybranego węzła, wybierz **zarówno**.<br />-Aby wybrać wszystkie węzły, które łączy do i od zaznaczonego węzła, wybierz **połączony wykres podrzędny**.<br />-Aby wybrać wszystkie elementy podrzędne wybranego węzła, wybierz **dzieci**.|

## <a name="FilterNodes"></a> Filtrowanie węzłów i łączy

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Pokaż lub Ukryj okienko filtry.|Wybierz **filtry** przycisk na pasku narzędzi mapy kodu. **Filtry** jako stronę z zakładkami w zostanie wyświetlone okienko **Eksploratora rozwiązań**, domyślnie.|
|Filtruj typy węzłów, które są wyświetlane na mapie.|Ustawianie lub wyczyść pola wyboru w **elementy kodu** na liście w okienku filtry.|
|Filtruj typy łączy, które są wyświetlane na mapie.|Ustawianie lub wyczyść pola wyboru w **relacje** na liście w okienku filtry.|
|Pokaż lub Ukryj węzły projektu testów na mapie.|Ustawić lub wyczyścić **zasobów testowych** pola wyboru w **różne** na liście w okienku filtry.|

Ikony wyświetlane w panelu legendy mapy odzwierciedlają ustawienia wprowadzone na liście. Aby pokazać lub ukryć panel legendy, kliknij przycisk **legendy** przycisk na pasku narzędzi mapy kodu.

## <a name="Inspect"></a> Sprawdź węzłów i łączy

Mapy kodu pokazują tego rodzaju łącza:

- Poszczególne linki odsyłają do jednej relacji między dwoma węzłami.

- Łącza grupy współzależności reprezentuje relację między dwoma węzłami w różnych grupach.

- Łącza zagregowanego reprezentuje wszystkie relacje, które wskazują, w tym samym kierunku, między dwiema grupami.

> [!TIP]
> Domyślnie mapy zawiera łącza grupy współzależności tylko dla wybranych węzłów. Aby zmienić to zachowanie, aby pokazać lub ukryć agregowanych łącz między grupami, kliknij przycisk **układ** na kodzie mapy paska narzędzi i wybierz polecenie **zaawansowane**, następnie **Pokaż wszystkie łącza grupy współzależności** lub **Ukryj wszystkie łącza grupy współzależności**. Zobacz [ukrywanie lub pokazywanie węzłów i łączy](#HidingShowing) Aby uzyskać więcej informacji.

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Zobacz więcej informacji na temat węzła lub łącza.|Przesuń wskaźnik myszy na węzeł lub łącze, aż pojawi się etykietka narzędzia.<br /><br /> Etykietka narzędzia dla zagregowane łącza zawiera listę poszczególnych zależności, które reprezentuje.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla węzła lub łącza. Wybierz **Edytuj**, **właściwości**.|
|Pokaż lub Ukryj zawartość grupy.|-Aby rozwinąć grupę, otwórz menu skrótów dla węzła, a następnie wybierz **grupy**, **rozwiń**.<br />     - lub -<br />     Przesuń wskaźnik myszy na węzeł, aż pojawi się przycisk cudzysłów ostrokątny (strzałkę). Kliknij ten przycisk, aby rozwinąć grupę. Klawiatury: Aby rozwinąć lub zwinąć wybraną grupę, naciśnij **oraz** klucza ( **+** ) lub **MINUS** klucza ( **-** ).<br />-Aby zwinąć grupy, otwórz menu skrótów dla węzła, a następnie wybierz **grupy**, **Zwiń**.<br />     - lub -<br />     Przesuń wskaźnik myszy na grupy, aż pojawi się przycisk cudzysłowu ostrokątnego (Strzałka w górę). Kliknij ten przycisk, aby zwinąć grupy.<br />-Aby rozwinąć wszystkie grupy, naciśnij klawisz **CTRL** + **A** aby zaznaczyć wszystkie węzły. Otwórz menu skrótów dla mapy i wybierz polecenie **grupy**, **rozwiń**. **Uwaga:**      To polecenie nie jest dostępna, jeśli rozwinięcie wszystkich grup generuje mapą bezużyteczne lub problemy z pamięcią. Zalecane jest, rozwiń węzeł mapy tylko do poziomu szczegółowości, które Cię interesują.<br />-Aby Zwiń wszystkie grupy, otwórz menu skrótów dla węzła lub mapy. Wybierz **grupy**, **Zwiń wszystko**.|
|Zobacz definicję kodu dla przestrzeni nazw, typu lub składowej.|Otwórz menu skrótów dla węzła, a następnie wybierz **przejdź do definicji**.<br /><br /> —lub—<br /><br /> Kliknij dwukrotnie węzeł. Rozwinięte grupy kliknij dwukrotnie nagłówek w grupie.<br /><br /> —lub—<br /><br /> Wybierz węzeł i naciśnij klawisz **F12**.<br /><br /> Na przykład:<br /><br /> – W przypadku przestrzeni nazw, zawierające jedną klasę plik kodu dla klasy otwiera Pokaż definicji klasy. W innych przypadkach **wyniki wyszukiwania symboli** okno zawiera listę plików kodu. **Uwaga:**      Po wykonaniu tego zadania w przestrzeni nazw języka Visual Basic nie można otworzyć pliku kodu za przestrzeni nazw. Ten problem występuje także podczas wykonywania tego zadania w grupie wybranych węzłów, które zawierają przestrzeni nazw języka Visual Basic. Aby obejść ten problem, ręcznie wskaż plik kodu za przestrzeń nazw, lub pominąć węzeł przestrzeni nazw z zaznaczenia.<br />— W przypadku klasy lub klasy częściowej plik kodu dla tej klasy otwiera Pokaż definicji klasy.<br />— Dla metody plik kodu dla klasy nadrzędnej otwiera Pokaż definicję metody.|
|Sprawdź zależności z elementami, które uczestniczą w łącze zagregowane.|Wybierz linki interesuje i otwórz menu skrótów dla zaznaczenia. Wybierz **Pokaż linki** lub **Pokaż linki na nowej mapie kodu**.<br /><br /> Program Visual Studio rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które w nim uczestniczą. **Uwaga:**  Zależności między elementami w grupach częściowe mogą znajdować tego zachowania: <ul><li>Łącza do elementów, które nie uczestniczą w swoje badania są usuwane z mapy, mimo że nadal istnieją tych łączy.</li><li>Załóżmy, że Sprawdź link do elementu w częściowej grupy, a następnie bada się innego łącza do tego samego elementu. Podczas badania usługi drugi docelowa grupa częściowe pokazuje tylko elementy z Twojego pierwszego badania. Łączy i elementów docelowych, które nie uczestniczyć w Twojego pierwszego badania, ale uczestniczyć w swojej drugiej badania nie są wyświetlane.</li></ul> Aby wyświetlić brakujące elementy z grupy, wybierz **ponownie Pobierz elementy podrzędne**![ikonę ponownie Pobierz elementy podrzędne](../modeling/media/dependencygraph_deletednodesicon.png) (wskazuje, że nie wszyscy członkowie grupy są wyświetlane na mapie). Możesz też spróbować cofnięcie akcji (klawiatura: naciśnij **CTRL + Z**) i zbadaj zależności dla nowej mapy.|
|Zbadaj zależności między wieloma węzłami w różnych grupach.|Rozwiń grupy, tak aby było widać wszystkie jego elementy podrzędne. Zaznacz wszystkie węzły, które są interesujące, łącznie z ich elementów podrzędnych. Mapa zawiera łącza grupy współzależności między wybranych węzłów.<br /><br /> Aby zaznaczyć wszystkie węzły w grupie, naciśnij i przytrzymaj **SHIFT** i lewego przycisku myszy podczas narysuj prostokąt wokół tej grupy. Aby zaznaczyć wszystkie węzły na mapie, naciśnij **CTRL**+**A**. **Porada:**  Aby wyświetlić łącza grup współzależności przez cały czas, wybierz opcję **układ** na pasku narzędzi mapy **zaawansowane**, **Pokaż wszystkie łącza grupy współzależności**.|
|Wyświetlić elementy, które odwołuje się do węzła lub łącza.|Otwórz menu skrótów dla węzła, a następnie wybierz **Znajdź wszystkie odwołania**. **Uwaga:**  Dotyczy to tylko wtedy, gdy `Reference` atrybut jest ustawiony dla węzła lub łącza w pliku .dgml mapy. Aby dodać odwołania do elementów z węzłów lub łączy, zobacz [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="HidingShowing"></a> Ukrywanie lub pokazywanie węzłów i łączy

Ukrywanie węzłów wyklucza je z udziału w układzie algorytmów. Domyślnie łącza między grupami są ukryte. Łącza grupy współzależności są poszczególnymi łączami połączenia między grupami węzłów. Jeśli grupy są zwinięte, mapy agreguje wszystkie łącza grupy współzależności do pojedynczego łącza między grupami. Gdyby rozwinąć grupę i wybrać węzły wewnątrz grupy, łącza grupy współzależności pojawiają się i pokażą zależności w tej grupie.

> [!CAUTION]
> Przed udostępnieniem map, który został utworzony w programie Visual Studio Enterprise z tymi, którzy korzystają z programu Visual Studio Professional, upewnij się odkryć wszystkie węzły lub łącza grupy współzależności, które powinni widzieć inni użytkownicy. W przeciwnym razie użytkownicy nie mogą odkryć tych elementów.

### <a name="to-hide-or-show-nodes"></a>Aby ukryć lub pokazać węzły

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Aby ukryć zaznaczone węzły.|1.  Wybierz węzły, które chcesz ukryć.<br />2.  Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **wybierz**, **Ukryj zaznaczone**.|
|Aby ukryć węzły niezaznaczone.|1.  Wybierz węzły, które mają być widoczne.<br />2.  Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **wybierz**, **Ukryj niezaznaczone**.|
|Pokaż ukryte węzły.|-Aby pokazać wszystkie ukryte węzły wewnątrz grupy, najpierw upewnij się, że grupa jest rozwinięta. Otwórz menu skrótów i wybierz polecenie **wybierz**, **Odkryj elementy podrzędne**.<br />     - lub -<br />     Kliknij przycisk **Odkryj elementy podrzędne**![Odkryj elementy podrzędne ikonę](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) ikony w lewym górnym rogu grupy (jest to widoczne tylko wtedy, gdy występują podrzędnego ukrytych węzłów).<br />-Aby pokazać wszystkie ukryte węzły, otwórz menu skrótów dla mapy lub węzła, a następnie wybierz **wybierz**, **odkryć wszystkie**.|

### <a name="to-hide-or-show-links"></a>Aby ukryć lub pokazać łącza

|**To**|**Na pasku narzędzi mapy wybierz układ, zaawansowane, a następnie wybierz**|
|-|-|
|Pokaż łącza grup współzależności przez cały czas.|**Pokaż wszystkie łącza grupy współzależności**. Powoduje to ukrycie agregowanych łącz między grupami.|
|Ukryj łącza grup współzależności przez cały czas.|**Ukryj wszystkie linki Międzygrupowe**|
|Pokaż tylko łącza grup współzależności dla zaznaczonych węzłów.|**Pokaż łącza grup współzależności na zaznaczonych węzłach**|
|Ukryj wszystkie łącza.|**Ukryj wszystkie łącza**. Aby ponownie wyświetlić linki, wybierz jedną z opcji wymienionych powyżej.|

## <a name="OrganizeGroups"></a> Grupowanie węzłów

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Pokazać kontener węzłów jako węzły grup lub węzły liści.|Aby pokazać kontener węzłów jako węzły liści: zaznacz węzły, otwórz menu skrótów dla zaznaczenia, a następnie wybierz **grupy**, **konwersji typu liść**.<br /><br /> Aby pokazać kontener węzłów jako węzły grup: zaznacz węzły, otwórz menu skrótów dla zaznaczenia, a następnie wybierz **grupy**, **konwersji do grupy**.|
|Zmień układ wewnątrz grupy.|Wybierz grupę, otwórz menu skrótów wybierz **układ**i wybierz żądany styl układu.<br /><br /> - lub -<br /><br /> 1.  Wybierz grupę, a następnie upewnij się, że jest rozwinięte.<br />2.  Ponownie kliknij nagłówek grupy i zostanie wyświetlony pasek narzędzi grupy.<br />     ![Wykres zależności &#45; narzędzi grupy](../modeling/media/dependencygraph_group.png)<br />3.  Otwórz **Zmień styl układu grupy** listy ![wykres zależności &#45; narzędzi grupy &#45; układ](../modeling/media/dependencygraph_grouptoolbar.gif) i wybierz żądany styl układu.<br /><br /> **Widok listy** Reorganizuje Członkowie tej grupy na liście. **Domyślne dla wykresu** powoduje przywrócenie grupy domyślny układ mapy. Innych opcjach, zobacz temat [zmienić układ mapy](#Selecting).|
|Dodaj węzeł do grupy.|Przeciągnij węzeł na grupę.<br /><br /> Podczas przeciągania węzła programu Visual Studio wyświetla wskaźnik do wyświetlenia, czy przenosisz węzła.<br /><br /> Można również przeciągać węzły na zewnątrz grupy.|
|Dodaj węzeł do niezgrupowanego węzła.|Przeciągnij węzeł na węzeł docelowy. Przez dodawanie węzłów do niego, można przekonwertować dowolny węzeł docelowy do grupy.|
|Aby grupować zaznaczone węzły.|1.  Zaznacz węzły, które chcesz grupować. Narzędzi wyskakujące pojawia się powyżej ostatniego węzła, którą wybierzesz.<br />     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)<br />2.  Na pasku narzędzi wybierz ikonę czwarty **grupować zaznaczone węzły** (jeśli jest rozwinięty węzeł będzie miał pięciu zamiast cztery ikony). Wpisz nazwę dla nowej grupy i naciśnij klawisz **zwracają**.<br />     - lub -<br />     Zaznacz węzły, które chcesz zgrupować i otwórz menu skrótów dla zaznaczenia. Wybierz **grupy**, **Dodaj grupę nadrzędną**, wpisz nazwę dla nowej grupy, a następnie naciśnij klawisz **zwracają**.<br /><br /> Można zmienić nazwę grupy. Otwórz menu skrótów dla grupy, a następnie wybierz **Edytuj**, **właściwości** aby otworzyć okno właściwości z usługą Visual Studio. W **etykiety** właściwości, zmiana nazwy grupy, zgodnie z potrzebami.|
|Usuń grupy.|Zaznacz jedną grupę lub kilka, które chcesz usunąć. Otwórz menu skrótów dla zaznaczenia, a następnie wybierz **grupy**, **Usuń grupę**.|
|Usuń węzły z ich grupy nadrzędnej.|Zaznacz węzły, które chcesz przenieść. Otwórz menu skrótów dla zaznaczenia, a następnie wybierz **grupy**, **Usuń z nadrzędnego**. Spowoduje to usunięcie węzłów się do ich nadrzędnych lub do spoza grupy, jeśli mają one nie grupy ponadnadrzędnej.<br /><br /> - lub -<br /><br /> Zaznacz węzły, a następnie przeciągnij je z niej.|

## <a name="AddRemoveNodesLinks"></a> Dodawanie, usuwanie lub zmiana nazwy węzłów, komentarze i łącza

Można wyświetlić więcej lub mniej elementów na mapie, aby przejść do szczegółów lub do uproszczenia mapy. Można również zmienić nazwy elementów i dodawanie komentarzy do elementów.

> [!CAUTION]
> Przed udostępnieniem mapy, który został utworzony przy użyciu programu Visual Studio Enterprise użytkownikom korzystającym z programu Visual Professional, upewnij się, że wszystkie elementy kodu, które powinni widzieć inni użytkownicy są widoczne na mapie. W przeciwnym razie użytkownicy ci nie będzie można pobrać elementów usuniętych kodu.

### <a name="add-a-node-for-a-code-element"></a>Dodaj węzeł dla elementu kodu

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Dodaj nowy węzeł ogólny w bieżącej lokalizacji wskaźnika myszy.|1.  Przesuń wskaźnik myszy do miejsca na mapie, gdzie chcesz umieścić nowy element kodu i naciśnij klawisz **Wstaw**.<br />     - lub -<br />     Otwórz menu skrótów dla mapy i wybierz polecenie **Edytuj**, **Dodaj**, **węzeł ogólny**.<br />2.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracają**.|
|Dodaj określonego typu węzła elementu kodu w bieżącej lokalizacji wskaźnika myszy.|1.  Przesuń wskaźnik myszy do miejsca na mapie, gdzie chcesz umieścić nowy element kodu, a następnie otwórz menu skrótów dla mapy.<br />2.  Wybierz **Edytuj**, **Dodaj**, a następnie wybierz typ węzła, które chcesz.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracają**.|
|Ogólny lub konkretnego typu węzła elementu kodu należy dodać do grupy.|1.  Wybierz węzeł grupy, a następnie otwórz menu skrótów.<br />2.  Wybierz **Edytuj**, **Dodaj**, a następnie wybierz typ węzła, które chcesz.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracają**.|
|Dodaj nowy węzeł tego samego typu i połączone z istniejącego węzła.|1.  Wybierz element kodu. Podręcznym pasku narzędzi pojawi się nad nim.<br />     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)<br />2.  Na pasku narzędzi, wybiera drugiej ikony **Utwórz węzeł z tej samej kategorii co ten węzeł i Dodaj nowe łącze do niej**.<br />3.  Wybierz miejsce na mapie, aby umieścić nowy element kodu, a następnie kliknij lewy przycisk myszy.<br />4.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracają**.|
|Dodaj nowego węzła ogólny, który jest połączony z istniejącego elementu kodu, który ma fokus.|1.  Za pomocą klawiatury, naciśnij klawisz **kartę** aż element kodu, aby połączyć ze ma fokus (kropkowane prostokąt).<br />2.  Naciśnij klawisz **Alt**+**Wstaw**.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracają**.|
|Dodaj nowy węzeł ogólny, który stanowi łącze do elementu kodu, który ma fokus.|1.  Za pomocą klawiatury, naciśnij klawisz **kartę** aż element kodu, aby połączyć ma fokus (kropkowane prostokąt).<br />2.  Naciśnij klawisz **Alt**+**Shift**+**Wstaw**.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracają**.|

|**Aby dodać elementy kodu dla**|**Wykonaj następujące kroki**|
|-|-|
|Elementy kodu w rozwiązaniu.|1.  Znajdź element kodu w **Eksploratora rozwiązań**. Użyj **Eksploratora rozwiązań** polu wyszukiwania lub Przeglądaj rozwiązanie. **Porada:**      Aby znaleźć elementy kodu, które są zależne od typu lub elementu członkowskiego, otwórz menu skrótów dla typu lub elementu członkowskiego w **Eksploratora rozwiązań**. Wybierz odpowiednią relację. **Eksplorator rozwiązań** pokazuje tylko tych elementów kodu z określonymi zależnościami.<br />2.  Przeciągnij elementy kodu, które Cię interesują do powierzchni mapy. Można również przeciągać elementy kodu, widoku klas lub przeglądarki obiektów.<br />     - lub -<br />     W **Eksploratora rozwiązań**, wybierz elementy kodu, które ma być mapowany. Następnie na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Pokaż na mapie kodu**.<br /><br /> Domyślnie hierarchię kontenera nadrzędnego dla nowych elementów kodu jest wyświetlany na mapie. Użyj **obejmują elementy nadrzędne** przycisk na pasku narzędzi mapy kodu, aby zmienić to zachowanie. Gdy wyłączone, element kodu, sama zostanie dodany do mapy. Aby wycofać to zachowanie dla tylko jednego przeciągnij i upuść działanie, naciśnij i przytrzymaj klawisz **CTRL** klucza podczas przeciągania elementów kodu na mapie.<br /><br /> Visual Studio dodaje elementy kodu dla elementów kodu najwyższego poziomu w zaznaczonym obszarze. Aby sprawdzić, czy element kodu zawiera inne elementy kodu, przesuń wskaźnik myszy na górze elementu kodu, aby pojawił się cudzysłów ostrokątny (strzałkę). Wybierz strzałkę, aby rozwinąć element kodu. Aby rozwinąć wszystkie elementy kodu, naciśnij klawisz **CTRL**+**A** aby zaznaczyć wszystkie elementy, otwórz menu skrótów dla mapy, a następnie wybierz **grupy**, **rozwijania** . To polecenie nie jest dostępna, jeśli rozwinięcie wszystkich grup może wygenerować mapy nienadające się do użytku lub brakiem problemy z pamięcią.|
|Elementy kodu powiązane elementy kodu na mapie.|Kliknij przycisk **Pokaż powiązane** znajdujący się na pasku narzędzi Mapa kodu i wybierz typ powiązane elementy, które Cię interesuje.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla elementu kodu. Wybierz jedną z **Pokaż...**  elementy menu, w zależności od rodzaju relację, która Cię interesuje. Na przykład możesz zobaczyć elementy, które odwołuje się do bieżącego elementu, elementy, które odwołują się bieżącego elementu, podstawowe i pochodne typy dla klas, obiektów wywołujących metodę i zawierający klasy, przestrzeni nazw i zestawów.<br /><br /> Aby uzyskać więcej informacji, zobacz [w tym temacie](../modeling/map-dependencies-across-your-solutions.md).|
|Skompilowanych zestawów .NET (.dll lub .exe) lub pliki binarne.|Przeciągnij zestawy lub pliki binarne z poza programem Visual Studio do mapy.<br /><br /> Można przeciągnąć z Eksploratora Windows lub Eksploratora plików, tylko wtedy, gdy są uruchomione go i programu Visual Studio, które znajdują się na tym samym poziomie uprawnień kontroli dostępu użytkownika (UAC). Na przykład jeśli jest włączona funkcja Kontrola konta użytkownika i korzystasz z programu Visual Studio jako Administrator, Eksplorator Windows lub Eksploratora plików zablokuje operację przeciągania.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Dodać łącze między istniejącymi elementami kodu

1. Wybierz element kodu źródłowego. Pasek narzędzi pojawi się nad elementem kodu.

    ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)

2. Na pasku narzędzi wybierz pierwszą ikonę **Utwórz nowe łącze z węzła do węzła, który klikniesz w następnej kolejności**.

3. Wybierz element docelowy kodu. Zostanie wyświetlone łącze między elementami dwóch kodu.

**OR**

1. Wybierz element kodu źródłowego na mapie.

2. Jeśli używasz myszy, zainstalowane, przesuń wskaźnik myszy poza granicami mapy.

3. Otwórz menu skrótów elementu kodu, a następnie wybierz **Edytuj** > **Dodaj** > **łącze generyczne**.

4. Kartę, a następnie wybierz element docelowy kodu dla tego połączenia.

5. Naciśnij klawisz **wprowadź**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Dodaj komentarz do istniejący węzeł na mapie

1. Wybierz element kodu. Pasek narzędzi pojawi się nad nim.

     ![Pasek narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png)

2. Na pasku narzędzi, wybierz ikonę trzeci **Utwórz nowy węzeł komentarza z nowym linkiem do wybranego węzła**.

     \- lub —

     Otwórz menu skrótów dla elementu kodu, a następnie wybierz **Edytuj** > **nowy komentarz**.

3. Wpisz swoje komentarze. Aby pisać w nowym wierszu, naciśnij klawisz **Shift** + **Enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Dodaj komentarz do mapy

1. Otwórz menu skrótów dla mapy i wybierz polecenie **Edytuj** > **nowy komentarz**.

2. Wpisz swoje komentarze. Aby pisać w nowym wierszu, naciśnij klawisz **Shift** + **Enter**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Zmień nazwę elementu kodu lub łącze

1. Wybierz element kodu lub łącze, które chcesz zmienić.

2. Naciśnij klawisz **F2**, lub Otwórz menu skrótów i wybierz pozycję **Edytuj** > **Zmień nazwę**.

3. Gdy pole edycji pojawi się na mapie, Zmień nazwę elementu kodu lub łącza.

**OR**

1. Otwórz menu skrótów i wybierz polecenie **Edytuj** > **właściwości**.

2. Edytuj **etykiety** właściwości w oknie właściwości usługi Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Usuń element kodu lub łącze z mapy

1. Wybierz element kodu lub łącze i naciśnij klawisz **Usuń** klucza.

     \- lub —

     Otwórz menu skrótów dla elementu kodu lub łącza, a następnie wybierz **Edytuj** > **Usuń**.

2. Jeśli element lub łącze jest częścią grupy **ponownie Pobierz elementy podrzędne** przycisk ![ikonę ponownie Pobierz elementy podrzędne](../modeling/media/dependencygraph_deletednodesicon.png) pojawia się wewnątrz grupy. Kliknij tutaj, aby pobrać brakujące elementy i łącza.

- Możesz usunąć elementy kodu i linki z mapy, bez wywierania wpływu na odpowiedni kod. Jeśli je usuniesz, ich definicje są usuwane z pliku DGML (.dgml).

- Mapy utworzone za pomocą edytowania DGML, dodając elementy Niezdefiniowany kod lub przy użyciu niektóre starsze wersje programu Visual Studio nie obsługują tej funkcji.

#### <a name="flag-a-code-element-for-follow-up"></a>Flaga element kodu do monitowania

1. Wybierz element kodu lub łącze, które chcesz Flaga monitowania.

2. Otwórz menu skrótów i wybierz polecenie **Edytuj** > **Flaga monitująca**.

- Domyślnie element kodu uzyskuje czerwone tło. Należy wziąć pod uwagę [Dodawanie komentarza](#AddComments) do niej odpowiednich informacji uzupełniających.

- Zmiana koloru tła elementu, lub wyczyść Flaga monitująca, wybierając **Edytuj** > **inne kolory Flag**.

## <a name="ChangeStyleCodeOrLink"></a> Zmienianie stylu elementu kodu lub łącza

Możesz zmienić ikony na elementy kodu i kolory elementów kodu i linki korzystające z wstępnie zdefiniowanych ikony i kolory. Na przykład można wybrać kolor, aby wyróżnić elementy kodu i linki, które mają określoną kategorią lub właściwością. Dzięki temu można zidentyfikować i skupić się na określonych obszarach mapy. Można określić niestandardowe ikony i kolory, edytując plik .dgml mapy; zobacz [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Aby zastosować wstępnie zdefiniowany kolor lub ikonę elementów kodu lub powiązania z określoną kategorią lub właściwością

1. Na pasku narzędzi mapy wybierz **legendy**.

2. W **legendy** pola, sprawdź, jeśli kod elementu kategoria lub właściwość już pojawia się na liście.

3. Jeżeli lista nie zawiera kategorii lub właściwości, wybierz **+** w **legendy** polu, a następnie wybierz **właściwość węzła**, **kategoria węzła** , **Właściwość łącza**, lub **Link kategorii**. Wybierz właściwość lub kategorię. Kategoria lub właściwość pojawi się w **legendy** pole.

    > [!NOTE]
    > Aby utworzyć i przypisać kategorię lub właściwość do elementu kodu, należy edytować plik .dgml mapy; zobacz [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. W **legendy** pole, kliknij ikonę obok kategorii lub właściwości, które dodano lub chcesz zmienić.

5. Skorzystaj z poniższej tabeli, aby wybrać styl, który ma zostać zmieniony:

    |**Aby zmienić**|**Choose**|
    |-|-|
    |Kolor tła|**Tło**|
    |Kolor konturu|**Pociągnięcia**|
    |Kolor tekstu (litera "f" jest wyświetlany w celu wyświetlenia wyniku)|**Pierwszy plan**|
    |Ikona|**Ikony**|

     **Selektor zestawu kolorów** lub **selektor zestawu ikon** pojawi się okno dialogowe umożliwiające wybranie koloru lub ikonę.

6. W **selektor zestawu kolorów** lub **selektor zestawu ikon** okno dialogowe, wykonaj jedną z następujących czynności:

    |**Aby zastosować**|**Wykonaj następujące kroki**|
    |-|-|
    |Zestaw kolorów i ikon|Otwórz **wybierz kolor** (lub **ikonę**) **ustaw** listy. Wybierz zestaw kolorów i ikon.|
    |Określony kolor lub ikonę|Otwórz listę wartości kategorii lub właściwości. Wybierz kolor lub ikonę.|

    > [!NOTE]
    > Można ponownie rozmieścić, usunąć lub tymczasowo dezaktywować style w **legendy** pole. Zobacz [Edytuj pole legendy](#ModifyLegend).

## <a name="ModifyLegend"></a> Edytuj pole legendy

Można ponownie rozmieścić, usunąć lub tymczasowo dezaktywować style w **legendy** pola:

1. Otwórz menu skrótów dla stylu w **legendy** pole.

2. Wykonaj jedno z następujących zadań:

    |**To**|**Choose**|
    |-|-|
    |Dezaktywuj element kodu|**Wyłącz**|
    |Usuń code element|**Delete**|
    |Przenieś styl w górę|**Przenieś w górę**|
    |Przenieś element kodu w dół|**Przenieś w dół**|

## <a name="CopyLegend"></a> Kopiowanie stylów z jednego mapy do innego

1. Upewnij się, że **legendy** pojawi się okno na mapę źródłową. Jeśli nie jest widoczny, na pasku narzędzi mapy, kliknij przycisk **legendy**.

2. Otwórz menu skrótów dla **legendy** pole. Wybierz **Kopiuj legendę**.

3. Wklej legendę na mapie docelowego.

## <a name="MergeMaps"></a> Scal map kodu

Mapy można scalić przez kopiowanie i wklejanie elementów kodu między mapy. Jeśli identyfikatory elementu kodu są zgodne, wklejanie kodu elementy funkcje takie jak operacji scalania. Aby ułatwić to zadanie, należy umieścić wszystkie zestawy lub pliki binarne, które mają być wyświetlane w tym samym folderze, tak aby pełna ścieżka każdego zestawu lub plik binarny jest taka sama dla każdego mapowania, które chcesz scalić.

Alternatywnie można przeciągnąć te zestawy lub pliki binarne do tego samego mapy z tego folderu.

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
