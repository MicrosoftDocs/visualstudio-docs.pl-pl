---
title: Typowe wzorce kontrolki dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52ced7e134efd0de9d2f61b039e5c851ba1387a6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931599"
---
# <a name="common-control-patterns-for-visual-studio"></a>Typowe wzorce kontrolki dla programu Visual Studio
##  <a name="BKMK_CommonControls"></a> Formanty standardowe  
  
### <a name="overview"></a>Omówienie  
Formanty standardowe tworzą większość interfejsu użytkownika w programie Visual Studio. Większość wspólnych kontrolek używanych w interfejsie programu Visual Studio należy stosować [wytycznych interakcji pulpitu Windows](/windows/desktop/uxguide/controls). Ten temat dotyczy programu Visual Studio i obejmuje szczególnych sytuacjach lub szczegółowe informacje, które polepszają tych wytycznych Windows.  
  
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
Przede wszystkim należy wziąć pod uwagę podczas style kontrolki jest, czy formanty będą używane w motywem interfejsu użytkownika. Formanty w standardowego interfejsu użytkownika są-motywem interfejsu użytkownika i należy wykonać [stylu normalnym pulpitu Windows](/windows/desktop/uxguide/controls), czyli nie są ponownie szablonem i powinno pojawić się w ich domyślny wygląd kontrolki.  
  
-   **Standard (Narzędzia) w oknach dialogowych:** nie motywów. Nie należy ponownie szablon. Użyj domyślnych stylu kontrolki podstawowe.  
  
-   **Okna narzędzi, edytory dokumentu, powierzchni projektowania i motywów okna dialogowe:** Użyj wyspecjalizowane wygląd kompozycji przy użyciu usługi kolorów.  
  
###  <a name="BKMK_Scrollbars"></a> Paski przewijania  
 Paski przewijania powinien być zgodny [paski przewijania typowe wzorce interakcji dla Windows](/windows/desktop/Controls/about-scroll-bars) , chyba że są one rozszerzone przy użyciu informacji o zawartości, jak pokazano w edytorze kodu.  
  
###  <a name="BKMK_InputFields"></a> Pól danych wejściowych  
 Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wytyczne dotyczące pól tekstowych](/windows/desktop/uxguide/ctrl-text-boxes).  
  
#### <a name="visual-style"></a>Styl wizualny  
  
-   Pola wejściowe nie powinny wstawiony w oknach dialogowych narzędzia. Użyć podstawowa stylu wewnętrznej do formantu.  
  
-   Motywem pól wejściowych stosuje się tylko w motywem okien dialogowych i okna narzędzi.  
  
#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje  
  
-   Pola tylko do odczytu mają tła szary (wyłączony), ale pierwszy plan domyślny (aktywny).  
  
-   Wymagane pola powinny mieć  **\<wymagane >** jako znaki wodne w nich. Nie należy zmieniać kolor tła, z wyjątkiem sytuacji, w rzadkich sytuacjach.  
  
-   Błąd sprawdzania poprawności: Zobacz [powiadomienia i postęp dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Pól danych wejściowych z tego względu celu dopasowania do zawartości, nie Dopasuj szerokość okna, w którym są wyświetlane, ani też arbitralnie jest zgodna z długością pola długie, takich jak ścieżki. Długość może to oznaczać użytkownikowi ograniczenia dotyczące liczby znaków są dozwolone w tym polu.  
  
     ![Nieprawidłowe pole wejściowe, długość: jest mało prawdopodobne, że nazwa będzie długich. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Nieprawidłowe pole wejściowe, długość: jest mało prawdopodobne, że nazwa będzie długich.
  
     ![Popraw długość pola wejściowego: pola wejściowego jest uzasadnione szerokość oczekiwanej zawartości. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Popraw długość pola wejściowego: pola wejściowego jest uzasadnione szerokość oczekiwanej zawartości.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Pola kombi i list rozwijanych  
Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wskazówki dotyczące list rozwijanych i pól kombi](/windows/desktop/uxguide/ctrl-drop).  
  
#### <a name="visual-style"></a>Styl wizualny  
  
-   W oknach dialogowych narzędzia nie re szablonu kontrolki. Użyć podstawowa stylu wewnętrznej do formantu.  
  
-   Wykonaj standardowe motywy dla formantów w motywem interfejsu użytkownika, pola kombi i list rozwijanych.  
  
#### <a name="layout"></a>Układ  
Pola kombi i listy rozwijane z tego względu celu dopasowania do zawartości, nie Dopasuj szerokość okna, w którym są wyświetlane, ani też arbitralnie jest zgodna z długością pola długie, takich jak ścieżki.  
  
![Niepoprawne: szerokość listy rozwijanej jest za długa dla zawartości, która będzie wyświetlana. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Niepoprawne: szerokość listy rozwijanej jest za długa dla zawartości, która będzie wyświetlana.
  
![Poprawne: z listy rozwijanej jest o rozmiarze do Zezwalaj na wzrost tłumaczenia, ale nie niepotrzebnie długie. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Poprawne: z listy rozwijanej jest o rozmiarze do Zezwalaj na wzrost tłumaczenia, ale nie niepotrzebnie długie. 
  
###  <a name="BKMK_CheckBoxes"></a> Pola wyboru  
Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wskazówki dotyczące wyboru](/windows/desktop/uxguide/ctrl-check-boxes).  
  
#### <a name="visual-style"></a>Styl wizualny  
  
-   W oknach dialogowych narzędzia nie re szablonu kontrolki. Użyć podstawowa stylu wewnętrznej do formantu.  
  
-   W interfejsie użytkownika motywów pola wyboru wykonaj standardowe motywy dla formantów.  
  
#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje  
  
-   Interakcja z polem wyboru nigdy nie należy pop okna dialogowego lub przejść do innego obszaru.  
  
-   Dostosowanie pól wyboru z linią bazową elementu pierwszego wiersza tekstu.  
  
     ![Niepoprawne: pole wyboru skupia się na tekst. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Niepoprawne: pole wyboru skupia się na tekst.
  
     ![Poprawne: pole wyboru jest powiązana z pierwszego wiersza tekstu. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Poprawne: pole wyboru jest powiązana z pierwszego wiersza tekstu.
  
###  <a name="BKMK_RadioButtons"></a> Przyciski radiowe  
Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wytyczne dotyczące przycisków radiowych](/windows/desktop/uxguide/ctrl-radio-buttons).  
  
#### <a name="visual-style"></a>Styl wizualny  
W oknach dialogowych narzędzia czy nie style przycisków radiowych. Użyć podstawowa stylu wewnętrznej do formantu.  
  
#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje  
Nie jest konieczne użycie ramki grupy wybór opcji, należy ująć, o ile nie trzeba zachować rozróżnienia grupy w układzie ścisłej.  
  
###  <a name="BKMK_GroupFrames"></a> Grupa ramek  
Dla zachowania typowe interakcji, postępuj zgodnie z [pulpitu Windows wytyczne dotyczące grupy ramek](/windows/desktop/uxguide/ctrl-group-boxes).  
  
#### <a name="visual-style"></a>Styl wizualny  
W oknach dialogowych narzędzia nie stylu ramki grupy. Użyć podstawowa stylu wewnętrznej do formantu.  
  
#### <a name="layout"></a>Układ  
  
-   Nie jest konieczne użycie ramki grupy wybór opcji, należy ująć, o ile nie trzeba zachować rozróżnienia grupy w układzie ścisłej.  
  
-   Nigdy nie używaj ramki grupy dla pojedynczego formantu.  
  
-   Czasami jest można użyć linii poziomej zamiast kontener ramki grupy.  
  
##  <a name="BKMK_TextControls"></a> Kontrolek tekstu

### <a name="static-text-fields"></a>Statyczne pola tekstowe

Statyczne pole tekstowe przedstawia informacje tylko do odczytu i nie może zostać wybrane przez użytkownika. Unikaj korzystania z niego na dowolny tekst, który użytkownik może chcieć, aby skopiować do Schowka. Jednak zmienić w celu odzwierciedlenia zmiany w stanie tylko do odczytu tekst statyczny. W przykładzie poniżej tekst statyczny Nazwa wyjściowego, w obszarze zmiany informacji w grupie, aby odzwierciedlić zmiany wprowadzone w polu tekstowym Namespace głównego nad nim.

Istnieją dwa sposoby, aby wyświetlić informacje tekst statyczny.

Statyczny tekst nie może być na swój własny w oknie dialogowym bez żadnych relacji zawierania gdy występuje konflikt nie grupowania. Zdecyduj, czy to naprawdę konieczne dodatkowe wiersze pola. Przykładem jest wyświetlanie ścieżkę katalogu, w sekcji, utworzonych przez linię grupy, jak pokazano poniżej:  

![Statyczny tekst informacji w kontrolek tekstu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statyczny tekst informacji w kontrolek tekstu

W oknie dialogowym, gdy istnieje inne obszary pogrupowanych i zawierania informacji może pomóc zwiększyć czytelność i po sekcji można ukryte lub pokazane (podobnie jak w **okno właściwości** okienko opisu) lub chcesz były zgodne z podobnym interfejsem użytkownika, Umieść statyczny tekst wewnątrz pola. To pole grupy powinny być pojedynczą regułę i kolorowe z `ButtonShadow`:

![Tekst statyczny w oknie dialogowym właściwości](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Tekst statyczny w oknie dialogowym właściwości

### <a name="read-only-text-box"></a>Pole tekstowe tylko do odczytu

Dzięki temu użytkownikowi zaznacz tekst wewnątrz pola, ale nie można go edytować. Te pola tekstowe są otoczony zwykle Dłuto 3D przy użyciu `ButtonShadow` wypełnienia.

Pole tekstowe mogą stać się aktywny (edytowalne), gdy użytkownik zmienia skojarzone kontrolki, takiej jak sprawdzanie lub usunięcie zaznaczenia pola polem wyboru lub wybierając/zaznaczenia przycisku radiowego. Na przykład w **narzędzia &gt; opcje** strony przedstawione poniżej **strony głównej** pole tekstowe jest uaktywniany podczas **Użyj domyślnej** pole wyboru jest zaznaczone.

![Pole tekstowe tylko do odczytu, wyświetlanie stanów nieaktywne i aktywne](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Pole tekstowe tylko do odczytu, wyświetlanie stanów nieaktywne i aktywne

### <a name="using-text-in-dialogs"></a>Przy użyciu tekstu w oknach dialogowych

Kluczowe wytyczne dla tekstu w oknach dialogowych:

-   Etykiety pola tekstowe, pola listy i ramki w oknach dialogowych unthemed rozpoczynać zlecenie, ma początkową wielką tylko pierwszy wyraz i kończyć dwukropkiem.

    > Postępuj zgodnie z kontrolek tekstu w oknach dialogowych motywem [wskazówki dotyczące interfejsu użytkownika pulpitu Windows](/windows/desktop/uxguide/top-violations) ale nie końcowych znaków interpunkcyjnych z wyjątkiem znaków zapytania w łącza pomocy.

-   Etykiety pola wyboru i przyciski opcji rozpoczynać czasownikiem początkową wielką tylko pierwszy wyraz i mieć bez końcowych znaków interpunkcyjnych.

-   Etykiety przyciski, menu, elementy menu i karty mają początkowych wielkich liter na poszczególnych wyrazów (tytuł wielkości liter).

-   Terminologia etykiety powinny być zgodne z podobnych etykiet w innych oknach dialogowych.

-   Jeśli to możliwe ma składnik zapisywania i edytorem, zapisu lub zatwierdzić tekstu, zanim przejdzie do deweloperów dla implementacji.

-   Wszystkie kontrolki powinny mieć etykiety z wyjątkiem w szczególnych okolicznościach, w których klawiszem TAB jest wystarczająca.
Użyj tekstu pomocy, gdy jest to konieczne.

### <a name="helper-text"></a>Tekst pomocy

Uwzględnione w oknach dialogowych, aby pomóc użytkownikowi zrozumieć celu w oknie dialogowym lub wskaż, jakie działania należy podjąć. Pomocnika, tekstu powinna służyć tylko w razie potrzeby Aby uniknąć zaśmiecania proste okien dialogowych. Dwie odmiany pomocnika, tekstu to okno dialogowe i znak wodny.

Postępuj zgodnie z typowych lokalizacji pomocnika, tekstu i zachować ostrożność przy wprowadzaniu nowe obszary. Typowe scenariusze dotyczące tekstu pomocy są:

-   Tekst pomocy w oknach dialogowych, aby zapewnić dodatkowe kierunek o tym, jak wchodzić w interakcje z złożonych okna dialogowego.

-   Tekst znaku wodnego okien narzędzi puste lub okien dialogowych, aby wyjaśnić, dlaczego jest widoczna żadna zawartość.

-   Okienko opisu, takich jak u dołu **okno właściwości**.

-   Znak wodny tekstu w edytorze puste, aby wyjaśnić, jaką akcję, użytkownik powinien wykonać, aby rozpocząć pracę.
  
### <a name="dialog-helper-text"></a>Tekst pomocy w oknie dialogowym

Projektant środowisko użytkownika może pomóc określić, kiedy pomocnika, tekstu jest odpowiednie. Projektant można określić, gdzie pojawia się tekst pomocnika oraz jego ogólną zawartość. Pomoc dla użytkownika mogą zapisu/edytować tekst.

### <a name="watermarks"></a>Znaki wodne

Okna dialogowe korzystać z wytycznych nieco znaku wodnego. Ponieważ okno dialogowe może znajdować się zagęszczoną w przypadku wielu elementów interfejsu użytkownika (etykiety, tekst wskazówki, przyciski i inne kontrolki kontenera, z tekstem), szczególnie gdy one wyświetlone na czarno znaki wodne wyróżniały się lepiej w ciemnoszary (VSColor: `ButtonShadow`). Zwykle pojawia się znak wodny wewnątrz kontrolki, takie jak pola listy na białym tle (VSColor: `Window`).

-   Tekst jest wyświetlany w ciemnoszary (VSColor: `ButtonShadow`). Jednakże jeśli znak wodny, który jest wyświetlany w kolorze szarym lub inne kolorowe (VSColor: `ButtonFace`) w tle i ma dotyczyć o jego czytelność, zawsze pod ręką czarny tekst (VSColor: `WindowText`).

-   Znaki wodne można wyśrodkowany lub wyrównany do lewej. Podczas podejmowania decyzji wyrównania jest stosowanie reguł standardowego projektu. Nie można wybrać znak wodny w tle.

![Przykład tekstu znaku wodnego](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Przykład tekstu znaku wodnego

### <a name="context-specific-dynamic-text"></a>(Zależne od kontekstu dynamiczny) tekst

Dynamiczny tekst może być używany jeden z dwóch sposobów, w oknie dialogowym lub niemodalne interfejsu użytkownika: albo jako dynamiczny etykiety lub zawartości dynamicznej.

-   Dynamiczne etykiety: typowym zastosowaniem dynamiczny tekst jest opisowy paneli, które oferują więcej informacji dla wybranego elementu, takie jak w oknie dialogowym, która zawiera listę elementów i właściwości dla tych elementów w siatce po prawej stronie. Etykiety siatki właściwości może być dynamiczny, tak aby wybranie elementu po lewej stronie siatki, po prawej stronie zawiera informacje dotyczące określonego elementu.

-   Dynamiczny tekst: może być przydatne w przypadkach, gdy konieczne jest wyświetlenie szczegółowych informacji i nie ogólnych informacji w ten sposób, ale należy zwrócić uwagę, aby nie nadużywać.

Jeśli chcesz, aby użytkownicy mieli możliwość kopiowania informacji, dynamiczne tekst powinien być w pole tekstowe tylko do odczytu.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Przyciski i hiperłączy  
  
### <a name="overview"></a>Omówienie  
Formanty przycisków i łącze (hiperłącza) należy stosować [podstawowe wskazówki pulpitu Windows o hiperlinkach](/windows/desktop/uxguide/ctrl-links) do użycia, znaną terminologię, rozmiaru i odstępy.  
  
### <a name="choosing-between-buttons-and-links"></a>Wybieranie między programami przycisków i łączy  
Tradycyjnie przyciski były używane dla akcji i hiperłączy zostały zarezerwowane dla nawigacji. Przyciski mogą być używane we wszystkich przypadkach, ale rolę łącza została rozszerzona w programie Visual Studio, aby przyciski i łącza są bardziej wymienne, w niektórych sytuacjach.  
  
Kiedy należy używać przycisków poleceń:  
  
-   Podstawowe polecenia  
  
-   Wyświetlanie systemu windows używane do zbierania danych wejściowych i zapewnianiu, nawet jeśli leżą one dodatkowych poleceń  
  
-   Akcje destrukcyjne lub nieodwracalne  
  
-   Przyciski zobowiązania w kreatorach i oknach przepływów stron  
  
Należy unikać przycisków poleceń w oknach narzędzi lub jeśli potrzebujesz więcej niż dwa wyrazy dla etykiety. Linki mogą mieć dłuższy etykiety.  
  
 Kiedy należy używać linków:  
  
-   Nawigacja do innego okna dokumentu lub strony sieci web  
  
-   Sytuacjach wymagających dłuższego etykiety lub krótkie zdanie opisujący przeznaczenie działania  
  
-   Ścisła miejsca do magazynowania, którym przycisk będzie przeciąży interfejsu użytkownika, pod warunkiem, że akcja nie jest destrukcyjne lub nieodwracalne  
  
-   Cofnięcia myślą dodatkowych poleceń w sytuacjach, w których istnieje wiele poleceń  
  
#### <a name="examples"></a>Przykłady  
![Polecenie łącza używane na pasku informacyjnym następującego komunikatu o stanie](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Polecenie łącza używane na pasku informacyjnym następującego komunikatu o stanie
  
![Łączy używane w menu podręcznym CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Łączy używane w menu podręcznym CodeLens
  
![Łączy używane dla dodatkowych poleceń, gdzie przyciski będą przyciągnięcia zbyt dużo uwagi](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Łączy używane dla dodatkowych poleceń, gdzie przyciski będą przyciągnięcia zbyt dużo uwagi
  
### <a name="common-buttons"></a>Typowe przycisków  
  
#### <a name="text"></a>Tekst  
Postępuj zgodnie z wytycznymi pisania w [interfejsu użytkownika tekstu i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Styl wizualny  
  
##### <a name="standard-unthemed"></a>Standard (unthemed)  
Większość przycisków w programie Visual Studio pojawi się w oknach dialogowych narzędzia i nie powinny być różne. Powinny one odzwierciedlać standardowy wygląd przycisków, zgodnie z ustawieniami systemu operacyjnego.  
  
##### <a name="themed"></a>Motywów  
W niektórych przypadkach przyciski mogą być używane w interfejsie użytkownika ze stylem, i należy odpowiednio ich tych przycisków styl. Zobacz [okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) uzyskać informacji na temat formantów z motywów.  
  
### <a name="special-buttons"></a>Specjalne przyciski  
  
#### <a name="browse-buttons"></a>Przeglądaj przycisków  
**[Przeglądaj …]**  przyciski są używane w siatkach, okien dialogowych i okien narzędzi i innych niemodalne elementów interfejsu użytkownika. Selektor, który pomaga użytkownika wypełniania wartości do kontrolki są wyświetlane. Istnieją dwie odmiany długich i krótkich tego przycisku.  
  
![Długie przycisk [Przeglądaj...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />Długie przycisk [Przeglądaj...]
  
![Przycisk krótki tylko do wielokropka [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />Przycisk krótki tylko do wielokropka [...]
  
Kiedy należy używać tylko do wielokropka krótki przycisk:  
  
-   Jeśli istnieje więcej niż jednego długiego **[Przeglądaj …]**  przycisku w oknie dialogowym, takie jak kiedy kilka pól umożliwiają przeglądanie. Użyj krótkiej **[...]**  przycisku dla każdego uniknąć pomylenia klucze dostępu, utworzone przez tę sytuację (**& Przeglądaj** i **prz & eglądaj** w tym samym oknie dialogowym).  
  
-   W oknie dialogowym ścisłej lub po nie uzasadnione miejsce do umieszczenia długie przycisku.  
  
-   Jeśli przycisk pojawi się w formancie siatki.  
  
Wytyczne dotyczące przy użyciu przycisku:  
  
-   Nie należy używać klucza dostępu. Dostępu do niego za pomocą klawiatury, użytkownik musi kartę z sąsiadujących kontroli. Upewnij się, że kolejność tabulacji jest taka, że dowolnego przycisku Przeglądaj znajduje się natychmiast po wypełni pola. Nigdy nie używaj znaku podkreślenia poniżej pierwszego okresu.  
  
-   Ustaw Microsoft Active Accessibility (MSAA) **nazwa** właściwość **Przeglądaj...**  (z uwzględnieniem wielokropek), który ekran czytelnicy odczyta go jako "Przeglądaj" i "kropka kropka kropka" albo "okres czasu okres." Zarządzane formanty, oznacza to ustawienie **AccessibleName** właściwości.  
  
-   Nigdy nie używaj wielokropek **[...]**  przycisk końcówką akcji przeglądania. Na przykład, jeśli potrzebujesz **[nowa...]**  przycisk, ale nie ma wystarczająco dużo miejsca dla tekstu, a następnie w oknie dialogowym musi być zaprojektowane od nowa.  
  
##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy  
![Zmiany rozmiaru [Przeglądaj...] przyciski: standardowa wersja 75 x 23 pikseli, skróconej pikseli 26 x 23](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Ustalanie rozmiaru przycisków [przeglądania...]
  
![Przyciski odstępy [Przeglądaj...]: odstępy między pokrewnych kontroli i standardowych pikseli 7 przycisk przeglądania, odstępy między pokrewnych kontroli i krótki przegląd przycisk 5 pikseli](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Odstępy przycisków [przeglądania...]
  
#### <a name="graphical-buttons"></a>Przyciski graficzne  
Niektóre przyciski należy zawsze używać graficzny i nigdy nie dołączaj tekstu, aby zaoszczędzić miejsce i uniknąć problemów z lokalizacji. Są one często używane w innych sortowanie list i formanty pola wyboru.  
  
> **Uwaga:** Użytkownicy muszą kartę w tych przycisków (nie ma żadnych kluczy dostępu), więc umieść je w kolejności rozsądne. Mapa `name` właściwości przycisku akcję, która zajmuje się tak, aby czytniki zawartości ekranu poprawnie interpretować Akcja przycisku.  
  
| Funkcja | Przycisk |  
| --- | --- |  
| Dodaj | ![Przycisk "Dodaj" graficzny](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Usuń | ![Przycisk "Usuń" graficzny](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Dodaj wszystko | ![Przycisk "Dodaj wszystkie" graficzny](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Usuń wszystko | ![Przycisk "Usuń wszystkie" graficzny](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Przenieś w górę | ![Graficzne "przycisk Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Przenieś w dół | ![Graficzne "przycisk Przenieś w dół"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Usuwanie | ![Przycisk "Usuń" graficzny](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy  
Zmiany rozmiaru graficzny przycisków jest taka sama, jak w przypadku krótkiej **[Przeglądaj …]**  przycisku (26 x 23 w pikselach):  
  
![Wygląd graficzny obrazu na przycisku z lub bez przezroczysty kolor przedstawiający](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Wygląd graficzny obrazu na przycisku z lub bez przezroczysty kolor przedstawiający
  
### <a name="hyperlinks"></a>Hiperłącza  
Hiperlinki dobrze nadają się do akcji na podstawie nawigacji, takich jak otwieranie tematu pomocy, modalne okno dialogowe lub kreatora. Jeśli hiperlink jest używany dla polecenia, zawsze powinna zostać wyświetlona widoczne i zauważalne zmiany w interfejsie użytkownika. Ogólnie rzecz biorąc w akcji, które są zaangażowani w zapewnienie akcję (np. Zapisz i Anuluj i Usuń) za pomocą przycisku lepiej są przekazywane.  
  
#### <a name="writing-style"></a>Styl pisania  
Postępuj zgodnie z [pulpitu Windows wskazówki dotyczące tekst interfejsu użytkownika](/windows/desktop/uxguide/text-ui). Nie używaj "Dowiedz się więcej o," "Powiedz mi więcej o" lub "Get uzyskać pomoc w tym" właściwej. Zamiast tego frazę tekst łącza pomocy pod względem podstawowego zapytania, odpowiedzi z zawartości pomocy. Na przykład "**jak dodać serwer do Eksploratora serwera?**"  
  
#### <a name="visual-style"></a>Styl wizualny  
  
-   Zawsze należy używać hiperlinków [usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Jeśli hiperlink nie ma zdefiniowanych poprawnie, pojawi się czerwony, gdy jest ona aktywna lub pokazuje inny kolor po odwiedzana.  
  
-   Nie dołączaj podkreślenia w kontroli przechowywany stan, chyba że łącze jest fragmentu zdanie w ramach pełnej zdania, podobnie jak w znaku wodnego.  
  
-   Podkreślenia nie są wyświetlane po najechaniu wskaźnikiem. Zamiast tego opinii do użytkownika, że łącze jest aktywne jest zmiana koloru niewielkie i kursor odpowiednie łącze.  
  
##  <a name="BKMK_TreeViews"></a> Widok drzewa  
  
Widok drzewa udostępniają sposób organizowania złożony, który wyświetla listę w grupy nadrzędny podrzędny. Użytkownika można rozwinąć lub zwinąć grupy nadrzędne, aby pokazać lub ukryć podstawowych elementów podrzędnych. Każdy element w widoku drzewa można wybrać w celu udostępniania dodatkowych akcji.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Styl wizualny widok drzewa  
  
#### <a name="expanders"></a>Ekspanderów znajdujących  
Kontrolki widoku drzewa powinna być zgodna projektowania ekspander używane przez Windows i programu Visual Studio. Każdy węzeł będzie używał kontrolki expander Wyświetl lub Ukryj podstawowe elementy. Za pomocą kontrolki expander zapewnia spójność dla użytkowników, którzy mogą występować w widokach innego drzewa w ramach Windows i programu Visual Studio.  
  
![Poprawne: właściwego stylu węzła widoku drzewa za pomocą kontrolki expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Poprawne: właściwego stylu węzła widoku drzewa za pomocą kontrolki expander
  
![Wprowadzony tekst jest niepoprawny: niewłaściwy stylu węzła widoku drzewa](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Wprowadzony tekst jest niepoprawny: niewłaściwy stylu węzła widoku drzewa
  
#### <a name="selection"></a>Wybór  
Po wybraniu węzła w widoku drzewa podświetlenie powinni rozwinąć pozycję do pełnej szerokości kontrolki widoku drzewa. Pomoże to użytkownikom jednoznacznie zidentyfikować element, który został wybrany. Wybór kolorów powinny odzwierciedlać bieżący motyw programu Visual Studio.  
  
![Poprawny: wyróżnianie wybranego węzła pasuje całą szerokość kontrolki widoku drzewa. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Poprawny: wyróżnianie wybranego węzła pasuje całą szerokość kontrolki widoku drzewa.
  
![Wprowadzony tekst jest niepoprawny: wyróżnianie wybranego węzła nie mieści się całą szerokość kontrolki widoku drzewa. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Wprowadzony tekst jest niepoprawny: wyróżnianie wybranego węzła nie mieści się całą szerokość kontrolki widoku drzewa.
  
#### <a name="icons"></a>Ikony  
Ikony powinny można używać tylko w kontrolki widoku drzewa, jeśli asystują w wizualnie identyfikowania różnic między elementami. Ogólnie rzecz biorąc ikony, należy używać tylko w heterogenicznych listy, w których ikony przenoszą informacje do rozróżniania typów elementów. Na liście jednorodnych korzystali z ikon często może być traktowany jak hałas i należy ich unikać. W takim przypadku ikona grupy (nadrzędnego) można uzyskać na typ elementów w nim. Wyjątkiem od tej reguły będzie, jeśli ikony są dynamiczne i jest używany do wskazania stanu.  
  
#### <a name="scroll-bars"></a>Paski przewijania  
Paski przewijania zawsze powinna być ukryta, jeśli zawartość mieści się w kontrolce widoku drzewa. Dopuszczalne jest używania pasków przewijania w oknie przewijany być ukryty lub półprzezroczystym i są wyświetlane, gdy okno zawierające widok drzewa jest ustawiony fokus lub po aktywowaniu drzewa wyświetlić sam.  
  
![Zarówno i poziome paski przewijania są wyświetlane, ponieważ zawartość przekroczenia limitów kontrolki widoku drzewa. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Zarówno i poziome paski przewijania są wyświetlane, ponieważ zawartość przekroczenia limitów kontrolki widoku drzewa.
  
###  <a name="BKMK_TreeViewInteractions"></a> Interakcje widok drzewa  
  
#### <a name="context-menus"></a>Menu kontekstowe  
Węzeł drzewa widoku może ujawnić podmenu Opcje w menu kontekstowym. Zwykle dzieje się po użytkownik kliknął prawym przyciskiem myszy element lub naciśnięty klawisz Menu na klawiaturze Windows za pomocą wybranego elementu. Jest ważne, że węzeł uzyska fokus i jest zaznaczone. Dzięki temu użytkownikowi określić podmenu należy do elementu.  
  
![Element, który ma Generowanie fokus zyski menu kontekst do powiadamiania użytkownika, który element został wybrany. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />Element, który ma Generowanie fokus zyski menu kontekst do powiadamiania użytkownika, który element został wybrany.
  
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
  
-   **Strzałka w prawo:** Rozwiń węzeł. Po rozwinięciu węzła powinno być kontynuowane, przechodząc do najbliższej kolumnę po prawej stronie. Nawigacja ma zostać zatrzymana, na końcu wiersza.  
  
-   **Karta:** Powoduje przejście do najbliższej komórce po prawej stronie.  Na końcu wiersza nawigacji w dalszym ciągu następnego wiersza.  
  
-   **Shift + Tab:** Powoduje przejście do najbliższej komórki po lewej stronie.  Na początku wiersza, nawigacji w dalszym ciągu po prawej stronie komórki w poprzednim wierszu.  
  
![Formant trid w programie Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Formant trid w programie Visual Studio