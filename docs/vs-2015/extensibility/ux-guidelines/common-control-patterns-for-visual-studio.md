---
title: Typowe wzorce kontrolki
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efde723cfb72c8f91b0ba88c0a24bb2d9a3d245d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757015"
---
# <a name="common-control-patterns-for-visual-studio"></a>Typowe wzorce kontrolki dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Formanty standardowe

### <a name="overview"></a>Omówienie
 Formanty standardowe tworzą większość interfejsu użytkownika w programie Visual Studio. Większość wspólnych kontrolek używanych w interfejsie programu Visual Studio należy stosować [wytycznych interakcji pulpitu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Ten dokument jest przeznaczony dla programu Visual Studio i obejmuje szczególnych sytuacjach lub szczegółowe informacje, które polepszają tych wytycznych Windows.

#### <a name="common-controls-in-this-topic"></a>Typowe kontrolki, w tym temacie

-   [Paski przewijania](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

-   [Pól danych wejściowych](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

-   [Pola kombi i list rozwijanych](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

-   [Pola wyboru](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

-   [Przyciski radiowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

-   [Grupa ramek](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

-   [Kontrolek tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

-   [Przyciski i hiperłączy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

-   [Widok drzewa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Styl wizualny
 Przede wszystkim należy wziąć pod uwagę podczas style kontrolki jest, czy formanty będą używane w motywem interfejsu użytkownika. Formanty w standardowego interfejsu użytkownika są-motywem interfejsu użytkownika i należy wykonać [stylu normalnym pulpitu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), czyli nie są ponownie szablonem i powinno pojawić się w ich domyślny wygląd kontrolki.

-   **Standard (Narzędzia) w oknach dialogowych:** nie motywów. Czy nie re szablonu. Użyj domyślnych stylu kontrolki podstawowe.

-   **Okna narzędzi, edytory dokumentu, powierzchni projektowania i motywów okna dialogowe:** Użyj wyspecjalizowane wygląd kompozycji przy użyciu usługi kolorów.

###  <a name="BKMK_Scrollbars"></a> Paski przewijania
 Paski przewijania powinien być zgodny [typowe wzorce interakcji dla Windows paski przewijania](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) chyba, że ich zostały rozszerzone o informacje o zawartości, takie jak w edytorze kodu.

###  <a name="BKMK_InputFields"></a> Pól danych wejściowych
 Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wytyczne dotyczące pól tekstowych](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualny

-   Pola wejściowe nie powinny być różne w oknach dialogowych narzędzia. Użyć podstawowa stylu wewnętrznej do formantu.

-   Motywem pól wejściowych stosuje się tylko w motywem okien dialogowych i okna narzędzi.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

-   Pola tylko do odczytu mają tła szary (wyłączony), ale pierwszy plan domyślny (aktywny).

-   Wymagane pola powinny mieć  **\<wymagane >** jako znaki wodne w nich. Nie należy zmieniać kolor tła, z wyjątkiem sytuacji, w rzadkich sytuacjach.

-   Błąd sprawdzania poprawności: Zobacz [powiadomienia i postęp dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

-   Pól danych wejściowych z tego względu celu dopasowania do zawartości, nie Dopasuj szerokość okna, w którym są wyświetlane, ani też arbitralnie jest zgodna z długością długie pola, na przykład ścieżki. Długość może to oznaczać użytkownikowi ograniczenia dotyczące liczby znaków są dozwolone w tym polu.

     ![Szerokość formantu nieprawidłowe pole wejściowe](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl") **długość nieprawidłowe pole wejściowe: Jest mało prawdopodobne, że nazwa będzie długich.**

     ![Popraw szerokość formantu pola wejściowego](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl") **Popraw dane wejściowe długość pola: Pola wejściowego jest uzasadnione szerokość oczekiwanej zawartości.**

###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Pola kombi i list rozwijanych
 Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wskazówki dotyczące list rozwijanych i pól kombi](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualny

-   W oknach dialogowych narzędzia czy nie re szablonu kontrolki. Użyć podstawowa stylu wewnętrznej do formantu.

-   Wykonaj standardowe motywy dla formantów w motywem interfejsu użytkownika, pola kombi i list rozwijanych.

#### <a name="layout"></a>Układ
 Pola kombi i listy rozwijane z tego względu celu dopasowania do zawartości, nie Dopasuj szerokość okna, w którym są wyświetlane, ani też arbitralnie jest zgodna z długością długie pola, na przykład ścieżki.

 ![Niepoprawne listy&#45;dół układ](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")

 **Nieprawidłowe pole długości kontrolki listy rozwijanej**

 ![Poprawne listy&#45;dół układ](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")

 **Długość poprawne pole dla formantu listy rozwijanej**

###  <a name="BKMK_CheckBoxes"></a> Pola wyboru
 Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wskazówki dotyczące wyboru](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualny

-   W oknach dialogowych narzędzia czy nie re szablonu kontrolki. Użyć podstawowa stylu wewnętrznej do formantu.

-   W interfejsie użytkownika motywów pola wyboru wykonaj standardowe motywy dla formantów.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

-   Interakcja z polem wyboru nigdy nie należy pop okna dialogowego lub przejść do innego obszaru.

-   Dostosowanie pól wyboru z linią bazową elementu pierwszego wiersza tekstu.

     ![Nieprawidłowe pole wyboru wyrównanie](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign") **wyrównanie nieprawidłowe pole wyboru: Pole wyboru skupia się na tekst.**

     ![Popraw wyrównanie pole wyboru](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign") **Popraw wyrównanie pola wyboru: Pole wyboru jest powiązana z linią bazową elementu pierwszego wiersza tekstu.**

###  <a name="BKMK_RadioButtons"></a> Przyciski radiowe
 Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wytyczne dotyczące przycisków radiowych](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualny
 W oknach dialogowych narzędzia czy nie style przycisków radiowych. Użyć podstawowa stylu wewnętrznej do formantu.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje
 Nie jest konieczne użycie ramki grupy wybór opcji, należy ująć.

###  <a name="BKMK_GroupFrames"></a> Grupa ramek
 Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wytyczne dotyczące grupy ramek](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualny
 W oknach dialogowych narzędzia czy nie styl grupy ramek. Użyć podstawowa stylu wewnętrznej do formantu.

#### <a name="layout"></a>Układ

-   Nie jest konieczne użycie ramki grupy wybór opcji, należy ująć, o ile nie trzeba zachować rozróżnienia grupy w układzie ścisłej.

-   Nigdy nie używaj ramki grupy dla pojedynczego formantu.

-   Czasami jest można użyć linii poziomej zamiast kontener ramki grupy.

##  <a name="BKMK_TextControls"></a> Kontrolek tekstu

### <a name="labels"></a>Etykiety

#### <a name="active-label-state"></a>Stan aktywny etykiety

##### <a name="utility-standard-dialogs"></a>Narzędzie okien dialogowych (standardowa))

-   Ogólnie rzecz biorąc postępuj zgodnie z wytycznymi pulpitu Windows dla etykiety kontroli.

-   W oknach dialogowych narzędzia etykiety powinna zostać wyświetlona pogrubiona, kolor czcionki i tekstu standardowego środowiska. Zobacz [czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

-   Wielokropek zawsze należy stosować etykiety.

##### <a name="signature-themed-dialogs"></a>Okna dialogowe (motywem) podpisu)
 Formanty etykiet, może być pogrubić lub światła szary.

#### <a name="disabled-label-state"></a>Stan etykieta wyłączone
 Etykiety powinny odzwierciedlać wyglądu kontrolki, które są skojarzone. Na przykład jeśli skojarzone kontrolka jest wyłączona, następnie etykieta powinna zostać wyświetlona szare, jak i wyłączonych. Zwykle odbywa się przez system operacyjny i wymaga nie specjalnego traktowania.

#### <a name="dynamic-labels"></a>Dynamiczne etykiety
 Zmiana etykiety dynamicznych na podstawie bieżącego zaznaczenia. Zawsze, gdy jest to możliwe, umożliwia dynamiczne etykiet w układy wzorzec/szczegół pomóc użytkownikowi zrozumieć, że wyświetlane informacje dotyczy określonego zaznaczenia, a nie ogólne informacje.

 ![Etykieta dynamicznych z zawartością dynamiczną](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")

 **Przykład etykiety dynamiczne, używane z zawartością dynamiczną**

#### <a name="instructional-text"></a>Tekst
 Niektóre elementy interfejsu korzystają z instruktażowy tekst w celu ułatwienia zrozumienia tego celu interfejsu użytkownika lub wskaż, jakie działania należy podjąć.

-   Tekst jest najbardziej typowe w górnej części okna dialogowe, ale może znajdować się w innych obszarach, aby zapewnić instrukcje grupowania złożonego formantu.

-   Tekst nie jest interakcyjny, ale może zawierać hiperłącza do tematów Pomocy.

-   Użyj tekst oszczędnie i tylko wtedy, gdy potrzebne.

##### <a name="formatting"></a>Formatowanie
 Tekst powinien być środowiska czcionkę tekstu formantu standardowego (innych niż motywem). Zobacz [czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Aby uzyskać więcej informacji na temat pisania tekst, zobacz [interfejsu użytkownika tekstu i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Formatowanie tekstu instruktażowy](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")

 **Tekst w oknie dialogowym programu Visual Studio**

#### <a name="informational-text"></a>Tekst informacyjny
 Tekst informacyjny to tekst, który zapewnia dodatkowe informacje o użytkowniku. Może być statyczne lub dynamiczne lub używane jako powiadomienie. Zawsze jest tylko do odczytu, ale jeśli jest to przydatne w przypadku użytkownik musi mieć możliwość kopiowania informacji dynamiczny tekst będzie umieszczona w kontenerze kontrolek, takich jak pole tekstowe tylko do odczytu.

##### <a name="dynamic-context-specific-text"></a>Dynamiczny tekst (specyficzne dla kontekstu)
 Tekst informacji dynamicznych zmienia się w zależności od kontekstu, np. gdy użytkownik Przełącza fokus. Często, ale nie zawsze zawartość dynamiczna jest powiązany z dynamicznych etykiety.

 ![Tekst informacji dynamicznych](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")

 **Dynamiczny tekst informacyjny zmienia się w zależności od kontekstu.**

##### <a name="formatting"></a>Formatowanie
 Istnieją dwa sposoby, aby wyświetlić pola tekstowego tylko do odczytu: bezpośrednio w Interfejsie użytkownika powierzchni (zobacz powyżej) albo zawartych w innej kontrolki, takie jak grupy ramki lub pola tekstowego. Albo jest poprawny w zależności od sytuacji. Jest projektanta funkcji do określenia sposobu prezentowania informacji tylko do odczytu.

 Tekst może być wewnątrz pola tekstowego tylko do odczytu. Zwykle oznacza to, zawartość można wybrać i skopiować, mimo że nie można edytować.

 ![Tekst informacyjny formatowania dla odczytu&#45;tylko pola](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")

 **Tekst informacyjny formatowanie pola tylko do odczytu**

#### <a name="watermarks"></a>Znaki wodne
 Treść może być taka sama, różnią się ze znaków wodnych i tekst to, czy znaki wodne są zastępowane zawartości kontrolki/okno nie jest pusty, gdy tekst pozostaje widoczne przez cały czas.

 Znaki wodne należy używać, gdy okno lub kontroli jest pusta. One wskazują na to, co trzeba zrobić, aby wypełnić obszaru i może zawierać linki akcji, aby otworzyć odpowiednie okien, takie jak źródła przeciągania.

##### <a name="visual-style"></a>Styl wizualny

- W oknie, znaki wodne powinien wyśrodkowane w poziomie.

- Znaki wodne powinna być być wyrównane, nie wyrównane do lewej.

- Znaki wodne, może być w pionie wyśrodkowany lub umieszczony w pobliżu górnej części obszaru. Jeśli znajduje się w górnej części obszaru, musi istnieć wystarczającej ilości miejsca powyżej, aby znak wodny detaliczny wyróżnia się.

- Użyj `Environment.GrayText` czcionka środowiska tokenu i standard kolorów. Hiperlinki należy używać tokenów hiperłącze standardowy udostępniony: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, i `Environment.PanelHyperlinkDisabled`.

- Nie można wybrać ze znaków wodnych w tle

- Jeśli to możliwe zawierać linki w znaku wodnego, aby pomóc użytkownikowi wprowadzenie.

  ![Znak wodny tekstu w oknie projektanta](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")

  ![Znak wodny tekstu w oknie narzędzia](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")

  **Przykłady tekstu znaku wodnego w programie Visual Studio**

##  <a name="BKMK_ButtonsAndHyperlinks"></a> Przyciski i hiperłączy

### <a name="overview"></a>Omówienie
 Formanty przycisków i łącze (hiperłącza) należy stosować [podstawowe wskazówki pulpitu Windows o hiperlinkach](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) do użycia, znaną terminologię, rozmiaru i odstępy.

### <a name="choosing-between-buttons-and-links"></a>Wybieranie między programami przycisków i łączy
 Tradycyjnie przyciski były używane dla akcji i hiperłączy zostały zarezerwowane dla nawigacji. Przyciski mogą być używane we wszystkich przypadkach, ale rolę łącza została rozszerzona w programie Visual Studio, aby przyciski i łącza są bardziej wymienne, w niektórych sytuacjach.

 Kiedy należy używać przycisków poleceń:

- Podstawowe polecenia

- Wyświetlanie systemu windows używane do zbierania danych wejściowych i zapewnianiu, nawet jeśli leżą one dodatkowych poleceń

- Akcje destrukcyjne lub nieodwracalne

- Przyciski zobowiązania w kreatorach i oknach przepływów stron

  Należy unikać przycisków poleceń w oknach narzędzi lub jeśli potrzebujesz więcej niż dwa wyrazy dla etykiety. Linki mogą mieć dłuższy etykiety.

  Kiedy należy używać linków:

- Nawigacja do innego okna dokumentu lub strony sieci web

- Sytuacjach wymagających dłuższego etykiety lub krótkie zdanie opisujący przeznaczenie działania

- Ścisła miejsca do magazynowania, którym przycisk będzie przeciąży interfejsu użytkownika, pod warunkiem, że akcja nie jest destrukcyjne lub nieodwracalne

- Cofnięcia myślą dodatkowych poleceń w sytuacjach, w których istnieje wiele poleceń

#### <a name="examples"></a>Przykłady
 ![Pasek informacyjny polecenia łącza następującego komunikatu o stanie](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")

 **Polecenie łącza używane na pasku informacyjnym następującego komunikatu o stanie**

 ![Łączy używane w menu podręcznym CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")

 **Łączy używane w menu podręcznym CodeLens**

 ![Łącza służące jako dodatkowej polecenia](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")

 **Łączy używane dla dodatkowych poleceń, gdzie przyciski będą przyciągnięcia zbyt dużo uwagi**

### <a name="common-buttons"></a>Typowe przycisków

#### <a name="text"></a>Tekst
 Postępuj zgodnie z wytycznymi pisania w [interfejsu użytkownika tekstu i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Styl wizualny

##### <a name="standard-dialogs"></a>Standardowych oknach dialogowych
 Większość przyciski w programie Visual Studio pojawi się w standardowych oknach dialogowych i nie powinny być różne. Powinny one odzwierciedlać standardowy wygląd przycisków, zgodnie z ustawieniami systemu operacyjnego.

##### <a name="themed"></a>Motywów
 W niektórych przypadkach przyciski mogą być używane w interfejsie użytkownika ze stylem, i należy odpowiednio ich tych przycisków styl. Zobacz [okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) uzyskać informacji na temat formantów z motywów.

### <a name="special-buttons"></a>Specjalne przyciski

#### <a name="browse-buttons"></a>Przeglądaj... przyciski
 **[Przeglądaj …]**  przyciski są używane w siatkach, okien dialogowych i okien narzędzi i innych niemodalne elementów interfejsu użytkownika. Selektor, który pomaga użytkownika wypełniania wartości do kontrolki są wyświetlane. Istnieją dwie odmiany długich i krótkich tego przycisku.

 ![Długi &#91;Przeglądaj... &#93; przycisk](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")

 **Długie przycisk [Przeglądaj...]**

 ![Krótki wielokropka&#45;tylko &#91;Przeglądaj... &#93; przycisk](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")

 **Przycisk krótki tylko do wielokropka [...]**

 Kiedy należy używać tylko do wielokropka krótki przycisk:

- Jeśli istnieje więcej niż jednego długiego **[Przeglądaj …]**  przycisku w oknie dialogowym, takie jak kiedy kilka pól umożliwiają przeglądanie. Użyj krótkiej **[...]**  przycisku dla każdego uniknąć pomylenia klucze dostępu, utworzone przez tę sytuację (**& Przeglądaj** i **prz & eglądaj** w tym samym oknie dialogowym).

- W oknie dialogowym ścisłej lub po nie uzasadnione miejsce do umieszczenia długie przycisku.

- Jeśli przycisk pojawi się w formancie siatki.

  Wytyczne dotyczące przy użyciu przycisku:

- Nie należy używać klucza dostępu. Dostępu do niego za pomocą klawiatury, użytkownik musi kartę z sąsiadujących kontroli. Upewnij się, że kolejność tabulacji jest taka, że dowolnego przycisku Przeglądaj znajduje się natychmiast po wypełni pola. Nigdy nie używaj znaku podkreślenia poniżej pierwszego okresu.

- Ustaw Microsoft Active Accessibility (MSAA) **nazwa** właściwość **Przeglądaj...**  (z uwzględnieniem wielokropek), który ekran czytelnicy odczyta go jako "Przeglądaj" i "kropka kropka kropka" albo "okres czasu okres." Zarządzane formanty, oznacza to ustawienie **AccessibleName** właściwości.

- Nigdy nie używaj wielokropek **[...]**  przycisk końcówką akcji przeglądania. Na przykład, jeśli potrzebujesz **[nowa...]**  przycisk, ale nie ma wystarczająco dużo miejsca dla tekstu, a następnie w oknie dialogowym musi być zaprojektowane od nowa.

##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy
 ![Ustalanie rozmiaru &#91;Przeglądaj... &#93; przyciski](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")

 **Ustalanie rozmiaru przycisków [przeglądania...]**

 ![Odstępy &#91;Przeglądaj... &#93; przyciski](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")

 **Odstępy przycisków [przeglądania...]**

#### <a name="graphical-buttons"></a>Przyciski graficzne
 Niektóre przyciski należy zawsze używać graficzny i nigdy nie dołączaj tekstu, aby zaoszczędzić miejsce i uniknąć problemów z lokalizacji. Są one często używane w innych sortowanie list i formanty pola wyboru.

> [!NOTE]
>  Użytkownicy muszą kartę w tych przycisków (nie ma żadnych kluczy dostępu), więc umieść je w kolejności rozsądne. Właściwość name przycisku są mapowane na akcję, która zajmuje się tak, aby czytniki zawartości ekranu poprawnie interpretować Akcja przycisku.

|||
|-|-|
|Dodaj|![Przycisk "Dodaj" graficzny](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|
|Usuń|![Przycisk "Usuń" graficzny](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|
|Dodaj wszystko|![Przycisk "Dodaj wszystkie" graficzny](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|
|Usuń wszystko|![Przycisk "Usuń wszystkie" graficzny](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|
|Przenieś w górę|![Graficzne "przycisk Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|
|Przenieś w dół|![Graficzne "przycisk Przenieś w dół"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|
|Usuwanie|![Przycisk "Usuń" graficzny](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy
 Zmiany rozmiaru graficzny przycisków jest taka sama, jak w przypadku krótkiej **[Przeglądaj …]**  przycisku (26 x 23 w pikselach):

 ![Przycisk z lub bez przezroczysty kolor przedstawiający](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")

 **Wygląd graficzny obrazu na przycisku z lub bez przezroczysty kolor przedstawiający**

### <a name="hyperlinks"></a>Hiperłącza
 Hiperlinki dobrze nadają się do akcji na podstawie nawigacji, takie jak otwieranie tematu pomocy, modalne okno dialogowe lub kreatora. Jeśli hiperlink jest używany dla polecenia, zawsze powinna zostać wyświetlona widoczne i zauważalne zmiany w interfejsie użytkownika. Ogólnie rzecz biorąc w akcji, które są zaangażowani w zapewnienie akcję (np. Zapisz i Anuluj i Usuń) za pomocą przycisku lepiej są przekazywane.

#### <a name="writing-style"></a>Styl pisania
 Postępuj zgodnie z [pulpitu Windows wskazówki dotyczące tekst interfejsu użytkownika](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Nie używaj "Dowiedz się więcej o," "Powiedz mi więcej o" lub "Get uzyskać pomoc w tym" właściwej. Zamiast tego frazę tekst łącza pomocy pod względem podstawowego zapytania, odpowiedzi z zawartości pomocy. Na przykład "**jak dodać serwer do Eksploratora serwera?**"

#### <a name="visual-style"></a>Styl wizualny

-   Zawsze należy używać hiperlinków [usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Jeśli hiperlink nie ma zdefiniowanych poprawnie, pojawi się czerwony, gdy jest ona aktywna lub pokazuje inny kolor po odwiedzana.

-   Nie dołączaj podkreślenia w kontroli przechowywany stan, chyba że łącze jest fragmentu zdanie w zdaniu pełną, takie jak w znaku wodnego.

-   Podkreślenia nie powinny być wyświetlane po najechaniu wskaźnikiem. Zamiast tego opinii do użytkownika, że łącze jest aktywne jest zmiana koloru niewielkie i kursor odpowiednie łącze.

##  <a name="BKMK_TreeViews"></a> Widok drzewa

### <a name="overview"></a>Omówienie
 Widok drzewa udostępniają sposób organizowania złożony, który wyświetla listę w grupy nadrzędny podrzędny. Użytkownika można rozwinąć lub zwinąć grupy nadrzędne, aby pokazać lub ukryć podstawowych elementów podrzędnych. Każdy element w widoku drzewa można wybrać w celu udostępniania dodatkowych akcji.

 W tym temacie omówiono dopuszczalnych, odpowiedniego projektu i funkcje widoków drzewa.

#### <a name="in-this-topic"></a>W tym temacie:

-   [Styl wizualny](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

-   [Interakcje](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

###  <a name="BKMK_TreeViewVisualStyle"></a> Styl wizualny

#### <a name="expanders"></a>Ekspanderów znajdujących
 Kontrolki widoku drzewa powinna być zgodna projektowania ekspander używane przez Windows i programu Visual Studio. Każdy węzeł będzie używał kontrolki expander Wyświetl lub Ukryj podstawowe elementy. Za pomocą kontrolki expander zapewnia spójność dla użytkowników, którzy mogą występować w widokach innego drzewa w ramach Windows i programu Visual Studio.

 ![Popraw kontrolki widoku drzewa](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Poprawne: właściwego stylu węzła widoku drzewa za pomocą kontrolki expander**

 ![Węzły widok drzewa nieprawidłowa](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")

 **Wprowadzony tekst jest niepoprawny: niewłaściwy stylu węzła widoku drzewa**

#### <a name="selection"></a>Wybór
 Po wybraniu węzła w widoku drzewa podświetlenie powinni rozwinąć pozycję do pełnej szerokości kontrolki widoku drzewa. Pomoże to użytkownikom jednoznacznie zidentyfikować element, który został wybrany. Wybór kolorów powinny odzwierciedlać bieżący motyw programu Visual Studio.

 ![Popraw kontrolki widoku drzewa](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Poprawny: wyróżnianie wybranego węzła pasuje całą szerokość kontrolki widoku drzewa.**

 ![Wyróżnianie widok drzewa nieprawidłowa](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")

 **Wprowadzony tekst jest niepoprawny: wyróżnianie wybranego węzła nie mieści się całą szerokość kontrolki widoku drzewa.**

#### <a name="icons"></a>Ikony
 Ikony powinny można używać tylko w kontrolki widoku drzewa, jeśli asystują w wizualnie identyfikowania różnic między elementami. Ogólnie rzecz biorąc ikony, należy używać tylko w heterogenicznych listy, w których ikony przenoszą informacje do rozróżniania typów elementów. Na liście jednorodnych korzystali z ikon często może być traktowany jak hałas i należy ich unikać. W takim przypadku ikona grupy (nadrzędnego) można uzyskać na typ elementów w nim. Wyjątkiem od tej reguły będzie, jeśli ikony są dynamiczne i jest używany do wskazania stanu.

#### <a name="scroll-bars"></a>Paski przewijania
 Paski przewijania zawsze powinna być ukryta, jeśli zawartość mieści się w kontrolce widoku drzewa. Dopuszczalne jest używania pasków przewijania w oknie przewijany być ukryty lub półprzezroczystym i są wyświetlane, gdy okno zawierające widok drzewa jest ustawiony fokus lub po aktywowaniu drzewa wyświetlić sam.

 ![Widok z pasków przewijania drzewa](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")

 **Zarówno i poziome paski przewijania są wyświetlane, ponieważ zawartość przekroczenia limitów kontrolki widoku drzewa.**

###  <a name="BKMK_TreeViewInteractions"></a> Interakcje

#### <a name="context-menus"></a>Menu kontekstowe
 Węzeł drzewa widoku może ujawnić podmenu Opcje w menu kontekstowym. Zwykle dzieje się po użytkownik kliknął prawym przyciskiem myszy element lub naciśnięty klawisz Menu na klawiaturze Windows za pomocą wybranego elementu. Jest ważne, że węzeł uzyska fokus i jest zaznaczone. Dzięki temu użytkownikowi określić podmenu należy do elementu.

 ![Menu węzła i kontekst wybranego drzewa](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")

 **Element, który ma Generowanie fokus zyski menu kontekst do powiadamiania użytkownika, który element został wybrany.**

#### <a name="keyboard"></a>Klawiatury
 W widoku drzewa powinna zapewniają możliwość wybierz elementy i rozwijanie/zwijanie węzłów za pomocą klawiatury. Daje to gwarancję, że nawigacja spełnia naszych wymagań w zakresie ułatwień dostępu.

##### <a name="tree-view-control"></a>Kontrolka widoku drzewa
 Kontrolki drzewa w usłudze Visual Studio, należy wykonać typowej nawigacji klawiatury:

-   **Strzałka: w górę** Wybierz elementy przez przeniesienie w górę drzewa

-   **Strzałka: w dół** Wybierz elementy, przenosząc niżej na drzewie

-   **Strzałka w prawo:** Rozwiń węzeł w drzewie

-   **Strzałka w lewo:** Zwiń węzeł w drzewie

-   **Wprowadź klucz:** Zainicjuj, obciążenia, należy wykonać wybranego elementu

##### <a name="trid-tree-view-and-grid-view"></a>Trid (widok drzewa i siatki)
 Formant trid jest formant złożony, który zawiera widok drzewa w obrębie siatki. Rozwijanie, zwijanie i przechodząc drzewa należy przestrzegać tych samych poleceń klawiatury w widoku drzewa, z następującymi dodatkami:

- **Strzałka w prawo:** Rozwiń węzeł. Po rozwinięciu węzła powinno być kontynuowane, przechodząc do najbliższej kolumnę po prawej stronie. Nawigacja ma zostać zatrzymana, na końcu wiersza.

- **Karta:** Powoduje przejście do najbliższej komórce po prawej stronie.  Na końcu wiersza nawigacji w dalszym ciągu następnego wiersza.

- **Shift + Tab:** Powoduje przejście do najbliższej komórki po lewej stronie.  Na początku wiersza, nawigacji w dalszym ciągu po prawej stronie komórki w poprzednim wierszu.

  ![Trid sterowania w programie Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")

  **Formant trid w programie Visual Studio**
