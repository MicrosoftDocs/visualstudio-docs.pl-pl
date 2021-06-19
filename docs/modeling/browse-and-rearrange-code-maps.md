---
title: Przeglądanie i rozmieszczanie map kodu
description: Dowiedz się, jak zmienić rozmieszczenie elementów na mapach kodu, aby ułatwić ich odczytywanie i poprawianie ich wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83132cfccd0af7244cf31f502669144eb3388bd8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385555"
---
# <a name="browse-and-rearrange-code-maps"></a>Przeglądanie i rozmieszczanie map kodu

Rozmieszczaj elementy na mapach kodu, aby ułatwić ich odczytywanie i poprawianie ich wydajności.

Mapy kodu można dostosować bez wpływu na kod źródłowy w rozwiązaniu. Jest to przydatne, gdy chcesz skupić się na kluczowych elementach kodu lub przekazać pomysły dotyczące kodu. Aby na przykład wyróżnić interesujące obszary, można wybierać elementy kodu na mapie i filtrować je, zmieniać styl elementów kodu i linków, ukrywać lub usuwać elementy kodu oraz organizować elementy kodu przy użyciu właściwości, kategorii lub grup.

 **Wymagania**

- Aby tworzyć mapy kodu, musisz mieć Visual Studio Enterprise.

- Mapy kodu można wyświetlać i edytować w ograniczonych mapach kodu w Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Rozpoczynanie pracy z mapami kodu

Utwórz mapę kodu (aby uzyskać więcej informacji, zobacz [Mapowanie](../modeling/map-dependencies-across-your-solutions.md) zależności między rozwiązaniami). Jeśli nie chcesz czekać na zakończenie generowania mapy, kliknij link **Anuluj** w dowolnym momencie, aby zatrzymać proces generowania. Jeśli to zrobisz, nie będą jednak widzieć szczegółów wszystkich zależności i linków.

Po wygenerowaniu mapy zapoznaj się z tymi poradami dotyczącymi przeglądania kodu:

- Przyjrzyj się klastrom zależności naturalnych w kodzie. Na pasku narzędzi mapy wybierz przycisk **Układ,** **Szybkie klastry** Szybkie ![ klastry na pasku narzędzi ](../modeling/media/quickclustersicon.gif) grafu. Zobacz [Zmienianie układu mapy](#Selecting).

     ![Wykres zależności &#45; układu szybkich klastrów](../modeling/media/dependencygraph_quickclusters.png)

- Zorganizuj mapę w mniejsze obszary, grupując powiązane węzły. Zwiń te grupy, aby zobaczyć tylko zależności międzygrupowe, które są wyświetlane automatycznie. Zobacz [Grupy węzłów](#OrganizeGroups).

- Użyj filtrów, aby uprościć mapę i skoncentrować się na typach węzłów lub linkach, które Cię interesują. Zobacz [Filtrowanie węzłów i linków](#FilterNodes).

- Maksymalizuj wydajność dużych map. Aby uzyskać więcej informacji, zobacz [Mapowanie zależności między rozwiązaniami.](../modeling/map-dependencies-across-your-solutions.md) Na przykład włącz **pomiń** kompilację na pasku narzędzi mapy, aby Visual Studio nie odbuduje rozwiązania podczas aktualizowania elementów na mapie.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Zmienianie układu mapy

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Rozmieść przepływ zależności dla całej mapy w określonym kierunku. Może to ułatwić wyświetlanie warstw architektury w kodzie.|Na pasku narzędzi mapy wybierz pozycję **Układ,** a następnie:<br /><br /> -   **Od góry do dołu** ![ Przycisk Wykres od góry do dołu](../modeling/media/topbottomgraphbutton.gif)<br />-   **Od dołu do góry** ![ Przycisk Od dołu do góry wykresu](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Od lewej do prawej** ![ Przycisk Układ od lewej do prawej](../modeling/media/leftrightgraphbutton.gif)<br />-   **Od prawej do lewej** ![ Przycisk Wykres od prawej do lewej](../modeling/media/rightleftgraphbutton.gif)|
|Zobacz klastry zależności naturalnych w kodzie z najbardziej zależnymi węzłami na środku klastrów i najmniej zależnymi węzłami na zewnątrz tych klastrów.|Na pasku narzędzi mapy wybierz pozycję **Układ,** a następnie przycisk Szybkie **klastry** Szybkie ![ klastry na pasku narzędzi grafu. ](../modeling/media/quickclustersicon.gif)|
|Wybierz co najmniej jeden węzły na mapie.|Kliknij węzeł, aby go wybrać. Aby zaznaczyć lub usunąć zaznaczenie więcej niż jednego węzła, przytrzymaj **naciśnięty klawisz CTRL** podczas klikania.<br /><br /> Klawiatura: naciśnij klawisz **TAB** lub użyj klawiszy strzałek, aby przenieść prostokąt z kropkowanym fokusem do węzła i naciśnij klawisz **SPACJA,** aby go zaznaczyć. Naciśnij **klawisz CTRL**  +  **SPACJA,** aby wybrać wiele węzłów lub usunąć ich zaznaczenie.|
|Przenieś określone węzły na mapie.|Przeciągnij węzły, aby je przenieść. Aby przenieść inne węzły i linki poza drogę podczas przeciągania węzłów, naciśnij i przytrzymaj klawisz **SHIFT.**<br /><br /> Klawiatura: przytrzymaj **klawisz CTRL** i naciśnij klawisze strzałek.|
|Zmień układ wewnątrz grupy niezależnie od innych węzłów i grup na mapie.|Wybierz węzeł i otwórz menu skrótów. Wybierz **pozycję Układ** i wybierz styl układu.<br /><br /> — lub —<br /><br /> Wybierz węzeł i rozwiń go, aby wyświetlić węzły podrzędne. Kliknij tytuł węzła, aby wyświetlić pasek narzędzi grupowania w oknie podręcznym, a następnie otwórz listę narzędzi Zmień styl układu grafu zależności grupy &#45; grupy &#45; ![ ](../modeling/media/dependencygraph_grouptoolbar.gif) układu. Wybierz jeden z układów drzewa, Szybkie **klastry** lub Widok listy **(który** rozmieszcza zawartość grupy na liście).<br /><br /> Aby [uzyskać więcej informacji,](#OrganizeGroups) zobacz Węzły grupy.|
|Cofanie akcji na mapie.|Naciśnij **klawisze CTRL**  +  **Z** lub użyj Visual Studio **Cofnij.**|

## <a name="browse-the-map"></a><a name="Explore"></a> Przeglądanie mapy

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Skanuj mapę.|Przeciągnij mapę w dowolnym kierunku za pomocą myszy.<br /><br /> — lub —<br /><br /> Przytrzymaj **klawisz SHIFT** i obróć kółka myszy, aby przewijać w poziomie. Przytrzymaj **klawisz SHIFT**  +  **CTRL** i obróć kółka myszy, aby przewijać w poziomie.|
|Powiększanie lub pomniejszanie mapy.|Obracaj kółka myszy.<br /><br /> — lub —<br /><br /> Użyj listy **rozwijanej Zoom** na pasku narzędzi mapy kodu.<br /><br /> — lub —<br /><br /> Użyj skrótów klawiaturowych. Aby powiększyć widok, naciśnij **klawisze CTRL + SHIFT + .** (okres). Aby pomniejszyć widok, naciśnij **klawisze CTRL + SHIFT + ,** (przecinek).|
|Powiększanie określonego obszaru za pomocą myszy.|Przytrzymaj prawy przycisk myszy podczas rysowania prostokąta wokół tego obszaru, który Cię interesuje.|
|Zmień rozmiar mapy i dopasuj do jej okna.|Wybierz **pozycję Powiększ, aby dopasować** **z listy Zoom** na pasku narzędzi mapy kodu.<br /><br /> — lub —<br /><br /> Kliknij **ikonę Powiększenie, aby dopasować** ![ ikona powiększenia na pasku narzędzi mapy na pasku narzędzi mapy ](../modeling/media/almcodemapzoomicon.png) kodu. Klawiatura: naciśnij **klawisze CTRL + 0** (zero).|
|Znajdź węzeł na mapie według jego nazwy. **Porada:**  Działa to tylko w przypadku elementów na mapie. Aby znaleźć elementy w rozwiązaniu, ale nie na mapie, znajdź je w Eksplorator rozwiązań **,** a następnie przeciągnij je na mapę. (Przeciągnij zaznaczenie lub na  pasku narzędzi Eksplorator rozwiązań kliknij pozycję **Pokaż na mapie kodu).**|1. Wybierz  ikonę Znajdź ikona Znajdź na pasku narzędzi mapy na pasku narzędzi mapy kodu (Klawiatura: naciśnij klawisze ![ ](../modeling/media/almcodemapfindicon.png) **CTRL + F),** aby wyświetlić pole wyszukiwania w prawym górnym rogu mapy.<br />2. Wpisz nazwę elementu i naciśnij klawisz **Return** lub kliknij ikonę "lupa". Pierwszy element, który pasuje do wyszukiwania, zostanie wyświetlony wybrany na mapie.<br />3. Aby dostosować wyszukiwanie, otwórz listę rozwijaną i wybierz opcję wyszukiwania. Dostępne opcje to **Find Next (Znajdź dalej),** **Find Previous (Znajdź poprzedni)** **i Select All (Zaznacz wszystko).** Następnie kliknij odpowiedni przycisk obok pola tekstowego wyszukiwania.<br />     ![Lista rozwijana opcji&#45;wyszukiwania](../modeling/media/almcodemapssearchdropdown.png)<br />     Możesz też użyć klawiatury: naciśnij **klawisz F3,** aby wybrać następny pasujący węzeł, lub **klawisze SHIFT + F3,** aby wybrać poprzedni pasujący węzeł.<br />4. Wybierz dowolną z opcji, które określają sposób obsługi terminów wyszukiwania, klikając ikony poniżej pola tekstowego wyszukiwania.<br />     ![Opcje dopasowania wyszukiwania](../modeling/media/almcodemapssearchmatchicons.png)<br />     Opcje to, od lewej do prawej, dopasowywanie z rozróżnianą wielkością liter, dopasowywanie tylko całych wyrazów, używanie składni wyrażeń regularnych .NET, automatyczne rozwijanie grup w celu pokazywania dopasowań do elementów ujętych w nawiasy. **Ważne:**  Możesz użyć pola wyszukiwania, aby znaleźć dopasowania w zwiniętych grupach tylko wtedy, gdy te grupy zostały wcześniej rozwinięte. Aby znaleźć te dopasowania i automatycznie rozwinąć ich grupy nadrzędne, wybierz tę opcję w polu wyszukiwania.|
|Zaznacz wszystkie niezazna wybrane węzły.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **pozycję Wybierz**, **Odwróć zaznaczenie.**|
|Wybierz dodatkowe węzły, które są linkami do wybranych węzłów.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **pozycję Wybierz** i jedną z nich:<br /><br /> - Aby wybrać dodatkowe węzły, które połączą się bezpośrednio z wybranym węzłem, wybierz **pozycję Zależności przychodzące.**<br />— Aby wybrać dodatkowe węzły, które połączą się bezpośrednio z wybranego węzła, wybierz pozycję **Zależności wychodzące.**<br />- Aby wybrać dodatkowe węzły, które łączy się bezpośrednio z wybranym węzłem i z wybranego węzła, wybierz **pozycję Oba.**<br />— Aby wybrać wszystkie węzły połączone z wybranym węzłem i z wybranego węzła, wybierz **pozycję Connected Subgraph (Podgraf połączony).**<br />- Aby wybrać wszystkie elementy children wybranego węzła, wybierz pozycję **Elementy children**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Filtrowanie węzłów i linków

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Pokazywanie lub ukrywanie okienka Filtry.|Wybierz przycisk **Filtry na** pasku narzędzi mapy kodu. Okienko **Filtry** jest domyślnie wyświetlane jako strona z Eksplorator rozwiązań **kartami.**|
|Filtruj typy węzłów, które są wyświetlane na mapie.|Ustaw lub wyczyść pola wyboru na liście **Elementy kodu** w okienku Filtry.|
|Filtruj typy linków, które są wyświetlane na mapie.|Ustaw lub wyczyść pola wyboru na liście **Relacje** w okienku Filtry.|
|Pokazywanie lub ukrywanie węzłów projektu testowego na mapie.|Ustaw lub wyczyść pole **wyboru Zasoby** testowe na liście **Różne** w okienku Filtry.|

Ikony wyświetlane na panelu Legenda mapy odzwierciedlają ustawienia na liście. Aby wyświetlić lub ukryć panel Legenda, kliknij przycisk **Legenda** na pasku narzędzi mapy kodu.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Badanie węzłów i linków

Mapy kodu pokazują następujące rodzaje linków:

- Pojedyncze łącze reprezentuje jedną relację między dwoma węzłami.

- Link między grupami reprezentuje relację między dwoma węzłami w różnych grupach.

- Link agregowania reprezentuje wszystkie relacje, które wskazują w tym samym kierunku między dwiema grupami.

> [!TIP]
> Domyślnie mapa pokazuje linki międzygrupowe tylko dla wybranych węzłów. Aby zmienić to zachowanie w celu pokazywania  lub ukrywania zagregowanych linków między  grupami, kliknij przycisk Układ na pasku narzędzi mapy kodu i wybierz pozycję **Zaawansowane,** a następnie pozycję Pokaż wszystkie linki między grupami lub Ukryj wszystkie linki między **grupami.** Aby uzyskać więcej informacji, zobacz [Ukrywanie lub pokazywanie węzłów](#HidingShowing) i linków.

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Zobacz więcej informacji o węźle lub linku.|Przesuń wskaźnik myszy na górę węzła lub linku, aż pojawi się etykietka narzędzia.<br /><br /> Etykietka narzędzia dla zagregowanego linku zawiera listę poszczególnych zależności, które reprezentuje.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla węzła lub linku. Wybierz **pozycję Edytuj**, **Właściwości**.|
|Pokazywanie lub ukrywanie zawartości grupy.|- Aby rozwinąć grupę, otwórz menu skrótów dla węzła i wybierz pozycję **Grupuj,** **rozwiń .**<br />     — lub —<br />     Przesuń wskaźnik myszy na górę węzła, aż pojawi się przycisk strzałkę w dół. Kliknij ten przycisk, aby rozwinąć grupę. Klawiatura: aby rozwinąć lub zwinąć wybraną grupę, naciśnij klawisz **PLUS** ( **+** ) lub klawisz **MINUS** ( **-** ).<br />- Aby zwinąć grupę, otwórz menu skrótów dla węzła i wybierz pozycję **Grupuj,** **Zwiń**.<br />     — lub —<br />     Przesuń wskaźnik myszy na górę grupy, aż pojawi się przycisk strzałki w górę. Kliknij ten przycisk, aby zwinąć grupę.<br />- Aby rozwinąć wszystkie grupy, naciśnij **klawisze CTRL**  +  **A,** aby zaznaczyć wszystkie węzły. Otwórz menu skrótów mapy i wybierz pozycję **Grupuj,** **rozwiń**. **Uwaga:**      To polecenie nie jest dostępne, jeśli rozwinięcie wszystkich grup generuje problemy z bezużyteczną mapą lub pamięcią. Zaleca się, aby mapa była rozwijana tylko do poziomu szczegółowości, który Cię zależy.<br />— Aby zwinąć wszystkie grupy, otwórz menu skrótów dla węzła lub mapy. Wybierz **pozycję Grupuj,** **zwiń wszystko.**|
|Zobacz definicję kodu dla przestrzeni nazw, typu lub elementu członkowskiego.|Otwórz menu skrótów dla węzła i wybierz **pozycję Przejdź do definicji**.<br /><br /> -lub-<br /><br /> Kliknij dwukrotnie węzeł. W przypadku rozwiniętych grup kliknij dwukrotnie nagłówek grupy.<br /><br /> -lub-<br /><br /> Wybierz węzeł i naciśnij **klawisz F12.**<br /><br /> Na przykład:<br /><br /> - W przypadku przestrzeni nazw zawierającej jedną klasę zostanie otwarty plik kodu dla klasy w celu pokazania definicji tej klasy. W innych przypadkach w **oknie Znajdź wyniki symboli** jest wyświetlona lista plików kodu. **Uwaga:**      W przypadku wykonania tego zadania w Visual Basic nazw plik kodu za przestrzenią nazw nie zostanie otwarty. Ten problem występuje również podczas wykonywania tego zadania w grupie wybranych węzłów, które zawierają Visual Basic nazw. Aby pominąć ten problem, przejdź ręcznie do pliku kodu za przestrzenią nazw lub pomiń węzeł dla przestrzeni nazw z wybranej przestrzeni nazw.<br />- W przypadku klasy lub klasy częściowej zostanie otwarty plik kodu dla tej klasy w celu pokazania definicji klasy.<br />- W przypadku metody zostanie otwarty plik kodu dla klasy nadrzędnej, aby wyświetlić definicję metody.|
|Sprawdź zależności i elementy, które uczestniczą w zagregowanym linku.|Wybierz linki, które Cię interesują, a następnie otwórz menu skrótów do wyboru. Wybierz **pozycję Show Contributing Links (Pokaż** linki współtworujące) lub **Show Contributing Links (Pokaż linki współtworujące) na nowej mapie kodu.**<br /><br /> Program Visual Studio rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które w nim uczestniczą. **Uwaga:**  Podczas badania zależności między elementami w grupach częściowych może wystąpić takie zachowanie: <ul><li>Linki do elementów, które nie uczestniczą w badaniu, znikną z mapy, mimo że te linki nadal istnieją.</li><li>Załóżmy, że analizujesz link do elementu w grupie częściowej, a następnie analizujesz inny link do tego samego elementu. Podczas drugiego egzaminu docelowa grupa częściowa pokazuje tylko elementy z pierwszego egzaminu. Linki i elementy docelowe, które nie uczestniczą w pierwszym egzaminie, ale uczestniczą w drugim egzaminie, nie są wyświetlane.</li></ul> Aby wyświetlić brakujące elementy z grupy, wybierz pozycję **Pobieranie** ponownie dzieci Ikona pobierania dzieci (co oznacza, że nie wszyscy członkowie grupy są wyświetlani ![ na ](../modeling/media/dependencygraph_deletednodesicon.png) mapie). Możesz również spróbować cofnąć akcje (klawiatura: naciśnij **klawisze CTRL+Z)** i zbadać zależności na nowej mapie.|
|Badanie zależności między wieloma węzłami w różnych grupach.|Rozwiń grupy, aby zobaczyć wszystkie ich dzieci. Wybierz wszystkie interesujące Cię węzły, w tym ich dzieci. Mapa przedstawia łącza międzygrupowe między wybranymi węzłami.<br /><br /> Aby wybrać wszystkie węzły w grupie, naciśnij i przytrzymaj klawisze **SHIFT** oraz lewy przycisk myszy podczas rysowania prostokąta wokół tej grupy. Aby wybrać wszystkie węzły na mapie, naciśnij **klawisze CTRL** + **A**. **Porada:**  Aby przez cały czas wyświetlać  linki międzygrupowe, wybierz pozycję Układ na pasku narzędzi **mapy,** Zaawansowane, Pokaż wszystkie **linki międzygrupowe.**|
|Zobacz elementy, do których odwołuje się węzeł lub link.|Otwórz menu skrótów węzła i wybierz pozycję **Znajdź wszystkie odwołania.** **Uwaga:**  Ma to zastosowanie tylko wtedy, gdy atrybut jest ustawiony dla węzła lub linku w pliku `Reference` .dgml mapy. Aby dodać odwołania do elementów z węzłów lub linków, zobacz [Dostosowywanie map kodu przez edytowanie plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Ukrywanie lub pokazywanie węzłów i linków

Ukrywanie węzłów wyklucza je z udziału w układzie algorytmów. Domyślnie łącza między grupami są ukryte. Łącza grupy współzależności są poszczególnymi łączami połączenia między grupami węzłów. Gdy grupy są zwinięte, mapa agreguje wszystkie linki między grupami w pojedyncze łącza między grupami. Gdyby rozwinąć grupę i wybrać węzły wewnątrz grupy, łącza grupy współzależności pojawiają się i pokażą zależności w tej grupie.

> [!CAUTION]
> Przed udostępnieniem mapy utworzonej w programie Visual Studio Enterprise osobom, które używają usługi Visual Studio Professional, pamiętaj, aby odkryć wszystkie węzły lub linki międzygrupowe, które mają widzieć inne osoby. W przeciwnym razie użytkownicy nie mogą odkryć tych elementów.

### <a name="to-hide-or-show-nodes"></a>Aby ukryć lub pokazać węzły

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Ukryj wybrane węzły.|1. Wybierz węzły, które chcesz ukryć.<br />2. Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **pozycję Wybierz,** **Ukryj wybrane.**|
|Ukryj niezaznajdywane węzły.|1. Wybierz węzły, które mają pozostać widoczne.<br />2. Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **pozycję Wybierz,** **Ukryj niezaznakło.**|
|Pokaż ukryte węzły.|— Aby wyświetlić wszystkie ukryte węzły w grupie, najpierw upewnij się, że grupa jest rozwinięta. Otwórz menu skrótów i wybierz **pozycję Wybierz**, Odkryj **elementy children.**<br />     — lub —<br />     Kliknij **ikonę Odkryj dzieci Ikona** Odkryj dzieci w lewym górnym rogu grupy (jest ona widoczna tylko wtedy, gdy istnieją ![ ukryte ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) węzły podrzędne).<br />— Aby wyświetlić wszystkie ukryte węzły, otwórz menu skrótów mapy lub węzła, a następnie wybierz pozycję **Wybierz**, **Odkryj wszystko.**|

### <a name="to-hide-or-show-links"></a>Aby ukryć lub pokazać linki

|**Do**|**Na pasku narzędzi mapy wybierz pozycję Układ, Zaawansowane, a następnie wybierz pozycję**|
|-|-|
|Pokaż linki między grupami przez cały czas.|**Pokaż wszystkie linki międzygrupowe**. Powoduje to ukrycie agregowanych łącz między grupami.|
|Ukryj linki między grupami przez cały czas.|**Ukryj wszystkie linki między grupami**|
|Pokaż tylko linki międzygrupowe dla wybranych węzłów.|**Pokazywanie linków międzygrupowych w wybranych węzłach**|
|Ukryj wszystkie linki.|**Ukryj wszystkie linki**. Aby ponownie wyświetlić linki, wybierz jedną z opcji wymienionych powyżej.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Grupy węzłów

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Pokaż węzły kontenera jako węzły grupy lub węzły liści.|Aby wyświetlić węzły kontenera jako węzły liścia: wybierz węzły, otwórz menu skrótów dla wybranego elementu, a następnie wybierz pozycję Grupuj, Konwertuj na **liścia**.<br /><br /> Aby wyświetlić węzły kontenera jako węzły grupy: wybierz węzły, otwórz menu skrótów dla wybranego elementu, a następnie wybierz pozycję Grupuj, **Konwertuj na grupę.**|
|Zmień układ wewnątrz grupy.|Wybierz grupę, otwórz menu skrótów, wybierz **pozycję Układ** i wybierz odpowiedni styl układu.<br /><br /> — lub —<br /><br /> 1. Wybierz grupę i upewnij się, że jest rozwinięta.<br />2. Ponownie kliknij nagłówek grupy i pojawi się pasek narzędzi grupy.<br />     ![Pasek narzędzi grupy &#45; graf zależności](../modeling/media/dependencygraph_group.png)<br />3. Otwórz **pozycję** Zmień styl układu listy grup Wykres zależności &#45; paska narzędzi grupy &#45; układu i wybierz odpowiedni ![ styl ](../modeling/media/dependencygraph_grouptoolbar.gif) układu.<br /><br /> **Widok listy** zmienia rozmieszczenie członków grupy na liście. **Wartość domyślna** wykresu powoduje zresetowanie układu grupy do domyślnego układu mapy. Aby uzyskać informacje o innych opcjach, [zobacz Zmienianie układu mapy.](#Selecting)|
|Dodaj węzeł do grupy.|Przeciągnij węzeł na grupę.<br /><br /> Podczas przeciągania węzła Visual Studio wskaźnik, aby pokazać, że węzeł jest przenoszyny.<br /><br /> Można również przeciągać węzły na zewnątrz grupy.|
|Dodaj węzeł do węzła niegrupowego.|Przeciągnij węzeł na węzeł docelowy. Możesz przekonwertować dowolny węzeł docelowy na grupę, dodając do niego węzły.|
|Grupowanie wybranych węzłów.|1. Wybierz węzły, które chcesz zgrupować. Nad ostatnim węzłem, który wybierzesz, zostanie wyświetlony podręczny pasek narzędzi.<br />     ![Pasek narzędzi grafu zależności](../modeling/media/depedencygraph_toolbar.png)<br />2. Na pasku narzędzi wybierz czwartą ikonę Grupuj wybrane węzły **(jeśli** węzeł jest rozwinięty, będzie mieć pięć zamiast czterech ikon). Wpisz nazwę nowej grupy i naciśnij klawisz **Return**.<br />     — lub —<br />     Wybierz węzły, które chcesz pogrupować, i otwórz menu skrótów dla wybranego elementu. Wybierz **pozycję** Grupa, **Dodaj grupę** nadrzędną, wpisz nazwę nowej grupy i naciśnij klawisz **Return**.<br /><br /> Nazwę grupy można zmienić. Otwórz menu skrótów dla grupy i wybierz pozycję **Edytuj,** **właściwości,** aby otworzyć Visual Studio okno Właściwości. We właściwości **Etykieta** zmień nazwę grupy zgodnie z potrzebami.|
|Usuń grupy.|Zaznacz jedną grupę lub kilka, które chcesz usunąć. Otwórz menu skrótów dla wybranego elementu i wybierz pozycję **Grupuj,** **usuń grupę**.|
|Usuń węzły z grupy nadrzędnej.|Zaznacz węzły, które chcesz przenieść. Otwórz menu skrótów dla wybranego elementu i wybierz pozycję **Grupuj,** **Usuń z elementu nadrzędnego.** Spowoduje to usunięcie węzłów do ich rodziców podrzędnych lub do spoza grupy, jeśli nie mają żadnej grupy rodziców podrzędnych.<br /><br /> — lub —<br /><br /> Wybierz węzły i przeciągnij je z grupy.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Dodawanie, usuwanie lub zmienianie nazw węzłów, linków i komentarzy

Możesz wyświetlić więcej lub mniej elementów na mapie, aby przejść do szczegółów lub uprościć mapę. Można również zmieniać nazwy elementów i dodawać komentarze do elementów.

> [!CAUTION]
> Przed udostępnieniem mapy utworzonej przy użyciu narzędzia Visual Studio Enterprise tym użytkownikom programu Visual Professional upewnij się, że wszystkie elementy kodu, które mają być widoczne dla innych użytkowników, są widoczne na mapie. W przeciwnym razie ci użytkownicy nie będą mogli pobrać usuniętych elementów kodu.

### <a name="add-a-node-for-a-code-element"></a>Dodawanie węzła dla elementu kodu

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Dodaj nowy węzeł ogólny w bieżącej lokalizacji wskaźnika myszy.|1. Przenieś wskaźnik myszy w miejsce na mapie, w którym chcesz umieścić nowy element kodu, a następnie naciśnij klawisz **Insert**.<br />     — lub —<br />     Otwórz menu skrótów mapy i wybierz polecenie **Edytuj,** **Dodaj,** **Węzeł ogólny**.<br />2. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|
|Dodaj określony typ węzła elementu kodu w bieżącej lokalizacji wskaźnika myszy.|1. Przenieś wskaźnik myszy w miejsce na mapie, w którym chcesz umieścić nowy element kodu, i otwórz menu skrótów mapy.<br />2. Wybierz **pozycję Edytuj,** **Dodaj** i wybierz odpowiedni typ węzła.<br />3. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|
|Dodaj do grupy ogólny lub określony typ węzła elementu kodu.|1. Wybierz węzeł grupy i otwórz menu skrótów.<br />2. Wybierz **pozycję Edytuj,** **Dodaj** i wybierz odpowiedni typ węzła.<br />3. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|
|Dodaj nowy węzeł tego samego typu i połączony z istniejącego węzła.|1. Wybierz element kodu. Nad nim zostanie wyświetlony podręczny pasek narzędzi.<br />     ![Pasek narzędzi grafu zależności](../modeling/media/depedencygraph_toolbar.png)<br />2. Na pasku narzędzi wybierz drugą ikonę Utwórz węzeł z tą samą kategorią co ten węzeł i dodaj do niego **nowy link**.<br />3. Wybierz miejsce na mapie, aby umieścić nowy element kodu, a następnie kliknij lewy przycisk myszy.<br />4. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|
|Dodaj nowy węzeł ogólny połączony z istniejącym elementem kodu, który ma fokus.|1. Używając klawiatury, naciskaj klawisz **Tab,** aż element kodu, z który ma być link, ma fokus (prostokąt kropkowany).<br />2. Naciśnij klawisze **Alt** + **Insert**.<br />3. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|
|Dodaj nowy węzeł ogólny, który łączy się z istniejącym elementem kodu, który ma fokus.|1. Używając klawiatury, naciskaj klawisz **Tab,** aż element kodu, do który ma być link, ma fokus (prostokąt kropkowany).<br />2. Naciśnij klawisze **Alt** + **Shift** + **Insert**.<br />3. Wpisz nazwę nowego węzła i naciśnij klawisz **Return**.|

|**Aby dodać elementy kodu dla**|**Wykonaj następujące kroki**|
|-|-|
|Elementy kodu w rozwiązaniu.|1. Znajdź element kodu w **Eksplorator rozwiązań**. Użyj pola **Eksplorator rozwiązań** wyszukiwania lub przejrzyj rozwiązanie. **Porada:**      Aby znaleźć elementy kodu, które mają zależności od typu lub elementu członkowskiego, otwórz menu skrótów dla typu lub elementu członkowskiego w **Eksplorator rozwiązań**. Wybierz odpowiednią relację. **Eksplorator rozwiązań** tylko te elementy kodu z określonymi zależnościami.<br />2. Przeciągnij interesujące Cię elementy kodu na powierzchnię mapy. Możesz również przeciągać elementy kodu z Widok klasy przeglądarki obiektów.<br />     — lub —<br />     W **Eksplorator rozwiązań** wybierz elementy kodu, które chcesz mapować. Następnie na pasku narzędzi **Eksplorator rozwiązań** pozycję **Pokaż na mapie kodu.**<br /><br /> Domyślnie hierarchia kontenerów nadrzędnych dla nowych elementów kodu jest wyświetlana na mapie. Użyj **przycisku Uwzględnij rodziców** na pasku narzędzi mapy kodu, aby zmienić to zachowanie. Gdy ta wartość jest wyłączona, do mapy jest dodawany tylko sam element kodu. Aby odwrócić to zachowanie tylko dla jednej akcji przeciągania i upuszczania, naciśnij i przytrzymaj klawisz **CTRL** podczas przeciągania elementów kodu do mapy.<br /><br /> Visual Studio dodaje elementy kodu dla elementów kodu najwyższego poziomu w wybranej opcji. Aby sprawdzić, czy element kodu zawiera inne elementy kodu, przesuń wskaźnik myszy na górę elementu kodu w taki sposób, aby pojawił się strzałkę w dół. Wybierz szewron, aby rozwinąć element kodu. Aby rozwinąć wszystkie elementy kodu, naciśnij **klawisze CTRL** A, aby zaznaczyć wszystkie elementy, otwórz menu skrótów mapy i wybierz pozycje +  **Grupuj,** **Rozwiń**. To polecenie nie jest dostępne, jeśli rozwinięcie wszystkich grup spowoduje, że mapa będzie bezużytetyczna lub nie będzie brakować pamięci.|
|Elementy kodu powiązane z elementami kodu na mapie.|Kliknij przycisk **Pokaż powiązane** na pasku narzędzi mapy kodu i wybierz typ powiązanych elementów, które Cię interesują.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla elementu kodu. Wybierz jeden z **elementów Pokaż ...** w menu w zależności od rodzaju relacji, która Cię interesuje. Można na przykład zobaczyć elementy, do których odwołuje się bieżący element, elementy odwołujące się do bieżącego elementu, typy podstawowe i pochodne dla klas, wywołujące metody oraz zawierające klasy, przestrzenie nazw i zestawy.<br /><br /> Aby uzyskać więcej informacji, zobacz [ten temat.](../modeling/map-dependencies-across-your-solutions.md)|
|Skompilowane zestawy .NET (.dll lub .exe) lub pliki binarne.|Przeciągnij zestawy lub pliki binarne z zewnątrz Visual Studio na mapę.<br /><br /> Możesz przeciągać z Eksplorator Windows lub Eksplorator plików tylko wtedy, gdy jest on uruchomiony i Visual Studio na tym samym poziomie uprawnień Access Control (UAC). Jeśli na przykład program UAC jest włączony i używasz konta Visual Studio jako administrator, Eksplorator Windows lub Eksplorator plików spowoduje zablokowanie operacji przeciągania.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Dodawanie połączenia między istniejącymi elementami kodu

1. Wybierz element kodu źródłowego. Nad elementem kodu zostanie wyświetlony pasek narzędzi.

    ![Pasek narzędzi grafu zależności](../modeling/media/depedencygraph_toolbar.png)

2. Na pasku narzędzi wybierz pierwszą ikonę Utwórz nowy link w tym węźle, z którym kiedykolwiek klikniesz **następny węzeł.**

3. Wybierz docelowy element kodu. Zostanie wyświetlony link między dwoma elementami kodu.

**OR**

1. Wybierz element kodu źródłowego na mapie.

2. Jeśli masz zainstalowaną mysz, przesuń wskaźnik myszy poza granice mapy.

3. Otwórz menu skrótów elementu kodu i wybierz polecenie **Edytuj**  >  **dodaj**  >  **link ogólny.**

4. Wybierz element kodu docelowego linku, na który należy wybrać klawisz Tab.

5.  Naciśnij klawisz **Enter**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Dodawanie komentarza do istniejącego węzła na mapie

1. Wybierz element kodu. Nad nim pojawi się pasek narzędzi.

     ![Pasek narzędzi grafu zależności](../modeling/media/depedencygraph_toolbar.png)

2. Na pasku narzędzi wybierz trzecią ikonę Utwórz nowy węzeł komentarza z **nowym linkiem do wybranego węzła**.

     \- lub —

     Otwórz menu skrótów dla elementu kodu i wybierz polecenie **Edytuj**  >  **nowy komentarz**.

3. Wpisz swoje komentarze. Aby wpisać w nowym wierszu, naciśnij **klawisz Shift**  +  **Enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Dodawanie komentarza do samej mapy

1. Otwórz menu skrótów mapy i wybierz polecenie **Edytuj**  >  **nowy komentarz.**

2. Wpisz swoje komentarze. Aby wpisać w nowym wierszu, naciśnij **klawisz Shift**  +  **Enter**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Zmienianie nazwy elementu kodu lub linku

1. Wybierz element kodu lub link, którego nazwę chcesz zmienić.

2. Naciśnij **klawisz F2** lub otwórz menu skrótów, a następnie wybierz polecenie **Edytuj zmień**  >  **nazwę**.

3. Gdy pole edycji pojawi się na mapie, zmień nazwę elementu kodu lub linku.

**OR**

1. Otwórz menu skrótów i wybierz **polecenie Edytuj**  >  **właściwości.**

2. Edytuj właściwość **Label** w Visual Studio okno Właściwości.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Usuwanie elementu kodu lub linku z mapy

1. Wybierz element kodu lub link i naciśnij **klawisz** Delete.

     \- lub —

     Otwórz menu skrótów dla elementu kodu lub linku i wybierz polecenie **Edytuj**  >  **usuń**.

2. Jeśli element lub link jest częścią grupy, przycisk **Pobierz** ponownie elementy children przycisk Pobierz ponownie ikona elementów children pojawia ![ się wewnątrz ](../modeling/media/dependencygraph_deletednodesicon.png) grupy. Kliknij tę pozycję, aby pobrać brakujące elementy i linki.

- Możesz usunąć elementy kodu i linki z mapy bez wpływu na kod źródłowy. Po ich usunięciu ich definicje są usuwane z pliku DGML (.dgml).

- Mapy utworzone przez edycję DGML, dodanie niezdefiniowanych elementów kodu lub użycie niektórych wcześniejszych wersji Visual Studio nie obsługują tej możliwości.

#### <a name="flag-a-code-element-for-follow-up"></a>Flagowanie elementu kodu w celu obserwowania

1. Wybierz element kodu lub link, który chcesz flagować w celu obserwowania.

2. Otwórz menu skrótów i wybierz **polecenie Edytuj**  >  **flagę dla opcji Obserwuj.**

- Domyślnie element kodu uzyskuje czerwone tło. Rozważ [dodanie do niego komentarza](#AddComments) z odpowiednimi informacjami.

- Zmień kolor tła elementu lub wyczyść flagę obserwowania, wybierając pozycję   >  **Edytuj inne kolory flagi**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Zmienianie stylu elementu kodu lub linku

Ikony elementów kodu oraz kolory elementów kodu i linków można zmieniać przy użyciu wstępnie zdefiniowanych ikon i kolorów. Można na przykład wybrać kolor wyróżniania elementów kodu i linków, które mają określoną kategorię lub właściwość. Dzięki temu można zidentyfikować konkretne obszary mapy i skoncentrować się na nich. Możesz określić niestandardowe ikony i kolory, edytując plik .dgml mapy; Zobacz [Dostosowywanie map kodu, edytując pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Aby zastosować wstępnie zdefiniowany kolor lub ikonę do elementów kodu lub linków z określoną kategorią lub właściwością

1. Na pasku narzędzi mapy wybierz pozycję **Legenda.**

2. W polu **Legenda** sprawdź, czy kategoria lub właściwość elementu kodu jest już widoczna na liście.

3. Jeśli lista nie zawiera kategorii ani właściwości, wybierz pozycję w polu Legenda, a następnie wybierz pozycję Właściwość węzła, Kategoria węzła, Właściwość linku **+** lub Kategoria **linku.**     Następnie wybierz właściwość lub kategorię. Kategoria lub właściwość jest teraz wyświetlana w **polu Legenda.**

    > [!NOTE]
    > Aby utworzyć kategorię lub właściwość i przypisać ją do elementu kodu, możesz edytować plik .dgml mapy; Zobacz [Dostosowywanie map kodu przez edycję plików DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

4. W polu **Legenda** kliknij ikonę obok dodanej kategorii lub właściwości lub chcesz zmienić.

5. Skorzystaj z poniższej tabeli, aby wybrać styl, który ma zostać zmieniony:

    |**Aby zmienić**|**Wybierz**|
    |-|-|
    |Kolor tła|**Tło**|
    |Kolor konturu|**Obrysu**|
    |Kolor tekstu (w celu pokazania wyniku jest wyświetlana litera "f")|**Pierwszy plan**|
    |Ikona|**Ikony**|

     Zostanie wyświetlone okno  dialogowe **Selektor** zestawu kolorów lub Selektor ustawień ikon, w których można wybrać kolor lub ikonę.

6. W **oknie dialogowym S** wyboru zestawu kolorów lub **ikony** Ustaw s wyboru wykonaj jedną z następujących czynności:

    |**Aby zastosować**|**Wykonaj następujące kroki**|
    |-|-|
    |Zestaw kolorów lub ikon|Otwórz listę **zestawu Wybierz** **kolor** **(lub ikonę).** Wybierz zestaw kolorów lub ikon.|
    |Określony kolor lub ikona|Otwórz listę wartości kategorii lub właściwości. Wybierz kolor lub ikonę.|

    > [!NOTE]
    > Style można zmieniać, usuwać lub tymczasowo dezaktywować w **polu Legenda.** Zobacz [Edytowanie pola Legenda.](#ModifyLegend)

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Edytowanie pola Legenda

Możesz zmienić rozmieszczenie, usunąć lub tymczasowo dezaktywować style w **polu Legenda:**

1. Otwórz menu skrótów stylu w polu **Legenda.**

2. Wykonaj jedno z następujących zadań:

    |**Do**|**Wybierz**|
    |-|-|
    |Dezaktywacja elementu kodu|**Wyłącz**|
    |Usuwanie elementu kodu|**Usuwanie**|
    |Przenieś styl w górę|**Przenieś w górę**|
    |Przenoszenie elementu kodu w dół|**Przenieś w dół**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Kopiowanie stylów z jednej mapy do innej

1. Upewnij się, **że pole Legenda** jest wyświetlane na mapie źródłowej. Jeśli nie jest widoczny, na pasku narzędzi mapy kliknij pozycję **Legenda.**

2. Otwórz menu skrótów dla **pola Legenda.** Wybierz **pozycję Kopiuj legendę.**

3. Wklej legendę na mapie docelowej.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Scalanie map kodu

Mapy można scalać, kopiując i wklejając elementy kodu między mapami. Jeśli identyfikatory elementów kodu są zgodne, wklejanie elementów kodu działa jak operacja scalania. Aby ułatwić to zadanie, umieść wszystkie zestawy lub pliki binarne, które chcesz zwizualizować, w tym samym folderze, tak aby pełna ścieżka każdego zestawu lub pliku binarnego była taka sama dla każdej mapy, którą chcesz scalić.

Alternatywnie można przeciągać te zestawy lub pliki binarne do tej samej mapy z tego folderu.

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
