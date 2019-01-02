---
title: Animacje
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b32addb7dcd767e8848640d79933f9868bdd959
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918659"
---
# <a name="animations-for-visual-studio"></a>Animacje dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Podstawy animacji

### <a name="animation-best-practices-in-visual-studio"></a>Najlepsze rozwiązania animacji w programie Visual Studio
 Wykonaj te zasady, aby zapewnić style animacji spójne i przyjazny dla użytkownika w środowisku IDE programu Visual Studio.

-   **Należy zachować ostrożność.** Ogranicz animacji do tych, które służą do określonych celów.

-   **Czas i szybkość są ważne** aby zapewnić szybki i fizyczne możesz też przejść:

    -   Ukończ animowane przejścia w ciągu pół sekundy (500 ms).

    -   Animacje, które wystąpiłyby często konieczne Działaj wystarczająco szybko, że nie przerwań się przepływu pracy użytkownika.

    -   Animacje nie należy więc szybko lub jarring, jest trudny do zrozumienia, ale nie działa tak wolno fakt, że jeden cierpliwy przejścia zakończyć.

    -   Użyj zmiennej czasu, aby podkreślić wagę. Na przykład podczas przechodzenia przez sekwencję elementów na diagramie klasy, szybkości za pomocą przejścia między elementami, a następnie spowolnić skoncentrować się na istotnych elementów.

-   **Użyj stopniowego ułatwianie nieliniowych** z jednego stanu do innego, co daje poczucie cicha i fizyczne przenoszenie

-   Jeśli to możliwe, **Użyj subtelne animacji, po najechaniu wskaźnikiem** do wskazać elementy interaktywne, w obszarze myszy.

-   Jeśli użytkownik korzysta z silnie animacji w funkcji następnie **stanowić sposób, aby je wyłączyć** lokalnie (dla wszystkich funkcji) jako opcja w **Narzędzia > Opcje** okna dialogowego.

-   **Tylko jednej animacji powinny być wykonywane jednocześnie** i przekazać tylko jeden zestaw informacji.

-   **Ważne jest subtlety.** W większości przypadków animacji nie ma żądanie uwagi użytkownika, aby obsługiwać z przeznaczeniem. Drobne zmiany czasu, sekwencjonowania i zachowanie może znacząco wpłynąć na postrzeganie i wprowadzać różnica między skuteczne i nieskuteczne animacji.

-   W przypadku używania animacji do zwrócenia uwagi na coś, **upewnij się, że warto przerywania użytkownika**w pracy.

-   **Gdy są wyświetlane stan lub postęp** za pośrednictwem animacji:

    -   Zatrzymaj, przedstawiający toku ruchu, gdy nie jest przechodzenia do przodu bazowego procesu.

    -   Rozróżnia nieokreślony procesów z określania procesów.

    -   Sprawdź, czy animacja ma do zidentyfikowania stanów zakończenia i błędów.

    -   Należy zminimalizować użycie animacji efekt, które informacje o stanie i upewnij się, że mają one prawdziwych wartości, zapewniając dodatkowe informacje rzeczywistego użycia. Przykłady obejmują zmiany stanu przejściowego i zagrożeń

#### <a name="do-not"></a>Nie:

- Użyj ruchy (przenoszenia w niewielkich rozmiarach), preferowanie stopniowo i zmienia się za pośrednictwem przenoszenia obiektów.

- Użyj animacji, które odbywają się za pośrednictwem duży obszar powierzchnię ekranu. Bez względu na rozmiar to style, animacji rozprasza dla użytkownika.

- Użyj animacji, które nie odnoszą się do obiektu, który użytkownik aktualnie ma fokus w lub interakcji z.

- Użyj animacji, które wymagają interakcji użytkownika, aby zresetować stan, takich jak zmuszania użytkownika odpowiedzieć migające powiadomienie, aby udostępnić ją zatrzymać migające. Powinna być wystarczające, aby je odrzucić interakcji z nimi w jakikolwiek sposób.

  Aby uzyskać więcej informacji na temat aplikacji dla tych najlepszych rozwiązań, zobacz [wzorców animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metryki animacji

-   System powinien widoczny reagowanie na gesty użytkownika w mniej niż 10 milisekund.

-   Animowane przejścia nie powinno zająć dłużej niż 500 MS, aby wykonać.

-   Jednym ze sposobów w celu kompensacji przejścia, które wymagają wydłużenie czasu jest podzielić ją na dwie części; na przykład w pierwszej części animację można pustego kontenera zawartości (maks. 500 milisekund), następuje zanikanie zawartości do kontenera (maks. 500 ms).

-   Czasy ładowania, które mogą być obliczane preferowany jest wskaźnik postępu decydującym (wskaźnik postępu gotowe procent).

-   Czas ładowania, których nie można obliczyć wskaźnik zajętości, takich jak kursor lub osadzonego rotowania animacji (ładowanie lub wskaźnik pracy) jest.

### <a name="animation-as-communicator"></a>Animacja jako communicator
 W interfejsie użytkownika programu Visual Studio animacji działa tylko jako narzędzie do komunikacji.  Jest używany do komunikowania się różne informacje, takie jak zmian strukturalnych w Interfejsie użytkownika; na przykład, kiedy menu zostanie otwarty lub zamyka. Animacja ułatwiają wizualizowanie zachowań zależnych od czasu, złożonych systemów, takich jak wizualizacja postępu instalacji lub służyć do przyciągania uwagi, alertów i powiadomień.

 Animacje interfejsu użytkownika zwykle działają na cztery sposoby: wizualizowanie, zwróć uwagę, symulowanie i wskazać odpowiedzi razy/postępu.

#### <a name="visualize"></a>Wizualizuj
 Animacji można wyróżnić trójwymiarowej charakter obiektów i ułatwić użytkownikom wizualizowanie ich struktury przestrzennych. Aby to osiągnąć, animacji może potrzebne do obracania obiektu w pełny okrąg, powoli do i z powrotem, Włącz lub Przenieś obiekt bliżej i nieco zwiększyć jego rozmiar, aby podkreślić przerzucania lub fokus.

 Mimo że obiektów trójwymiarowych można przenieść za pomocą kontrolki użytkownika projektanta należy określić wcześniej (programowo lub ręcznie) jak do najlepszych animować przepływu, który zapewnia optymalną opis obiektu. To zaprogramowane może animacji, a następnie aktywowany przez użytkownika, umieszczając kursor nad obiektem, natomiast przeniesień kontrolowanej przez użytkownika wymaga od użytkownika zrozumieć sposób modyfikowania obiektu. Ograniczanie ruchu na pojedynczej osi lub orientacji jednocześnie. albo skalowanie, obrócić, albo tłumaczenie, ale nie więcej niż jedną jednocześnie.

 Kategoria wizualizacja zawiera aspektów danych, relacje, stan, struktury, kolejność i czas.

##### <a name="data"></a>Dane
 Przedstawiają informacje o złożone i zmiennych:

-   Nawigacja po wizualizacje informacje, takie jak wykresy i diagramy

-   Krokowe wykonywanie sekwencji, samouczek i stronicowania

-   Wywoływanie bardziej szczegółowe informacje, wskazując i wyróżnianie określonych informacji

-   Nałożenie szczegóły i dodatkowe informacje na podstawie zaznaczonego elementu

-   Morfingu prvku z jedną reprezentację strukturalnym lub organizacji do innego

-   Reprezentuje zmiany wraz z upływem czasu przy użyciu czasu suwaki, biegu shuttle koła i kontrolki transportu (Odtwórz, Zatrzymaj i wstrzymania).

##### <a name="relationships"></a>Relacje

-   Pokazują, jak elementy powiązane ze sobą lub elementy, które odnoszą się do danego elementu.

-   Wyświetlanie hierarchii i nadrzędny podrzędny lub element równorzędny relacji

-   Jeden element spowoduje utworzenie innego

-   Jeden element minimalizuje do innego elementu

-   Jeden element pomocą zastosowaniu tetheringu do innego

##### <a name="state"></a>Stan

-   Aktualizacje zawartości.

-   Wybieranie i fokus

-   Postęp

-   błędy

##### <a name="structure"></a>Struktura

-   Przestawianie struktury w jednym węźle

-   Zmiana orientacji

-   Minimalizowanie i zmaksymalizować, lub zwijać i rozwijać

##### <a name="sequence"></a>Sekwencja

-   Sekwencja pokaz slajdów

-   Przerzucanie obrazów

##### <a name="time"></a>Godzina

-   Pokaż zmian na przestrzeni czasu, czas wygaśnięcia i zrzut ekranu

-   Przenieś do Kosz, Cofnij i wykonaj ponownie

-   Przywróć historycznego stanu

#### <a name="attract-attention"></a>Zwróć uwagę
 Jeśli celem jest zwrócenie uwagi użytkownika pojedynczy element z kilku lub ostrzegać użytkowników o zaktualizowane informacje, animacji może być odpowiednie. Na przykład swoją stronę początkową aplikacji może stosować wprowadzenie przycisku, który slajdy na miejsce po załadowaniu strony.

 Zgodnie z zasadą przenoszenie ostatniego elementu na ekranie przyciąga uwagi użytkownika.  W serii animowanych elementów ostatni obiekt przenoszenie będą zgodne z uwagi użytkownika.

##### <a name="alert"></a>Zgłoś alert

-   Ostrzegać użytkowników, Uzyskaj uwagi, Pokaż postęp

-   Pokazują, że coś, co jest wykonywana prawidłowo lub nieprawidłowo lub wyświetlić postęp lub zmiany w toku

-   Monituj użytkowników podczas zadania, takie jak wyszukiwanie więcej informacji w trybie online lub poznawania bieżące zadanie

##### <a name="notifications"></a>Powiadomienia

-   Ostrzegać użytkowników o warunek błędu

-   Przerwie pracę użytkownika, aby zobaczyć, czy chce zająć się czymś innym

-   Delikatnie informuje użytkownika, który proces zostało ukończone lub zmienione, takie jak kiedy pobranie zostanie ukończone.

#### <a name="simulate"></a>Symulowanie
 Ta kategoria obejmuje physicality i wymiary.

-   Ilustrują pochodzenie obiektów lub gdzie przejdź do

-   Rozwijanie i zwijanie lub otwierania i zamykania

-   Włącza przesuwanie przewijanie i strony

-   Łączenie urządzeń i kolejności z

-   Karuzela i właściwości accordion

-   Przerzucanie i obracanie interfejsu użytkownika

#### <a name="response-and-progress-indicators"></a>Wskaźniki odpowiedzi i postępu
 Wskaźniki postępu dostępnych jest kilka istotnych zalet:

-   Oba wskaźniki postępu określania i nieokreślony przywróceniu zaufania użytkownika, że system nie wystąpiła awaria i pracuje nad problem.

-   Określania wskaźników przyznać użytkownikowi, który zorientować się, jak daleko wzdłuż akcji postępuje oraz uczucia uzyskania bliższych do zakończenia.

##  <a name="BKMK_AnimationPatterns"></a> Wzorce animacji

### <a name="overview"></a>Omówienie
 Animacje w programie Visual Studio są przeznaczone do obsługi określonych funkcji i utrudnia wydajność pracy użytkowników. Cechy animacji ogólne stosować się do uwzględnienia:

- Małe i dyskretny kod

- Fizyczne i realistyczne

- Subtelnym, przytłumionym

- Szybkie i wydajne

- Swobodna, nie hurried

  Poniższa ilustracja przedstawia style animacji, zaleca się używania w programie Visual Studio. Nie animacji i subtelne animacje takich jak zanikanie / fade się najczęściej są używane. Istnieje ograniczona aplikacji przepływu animacji, takich jak rozwinąć lub zwinąć, X i Y pozycji zmian które obrotu.

  ![Zalecane animacji, stylów dla programu Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")

  **Style animacji zalecany dla programu Visual Studio**

#### <a name="appear-and-disappear"></a>Pojawiają się i znikają
 W ramach tego wzorca elementu przechodzi z widoczne poza widoku i ponownie bez animacji przejścia:

 ![Pojawiają się&#47;zniknąć animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")

##### <a name="correct-usage"></a>Poprawne użycie
 Świeży elementy interfejsu użytkownika, które muszą natychmiast lub pojawiania się tak, aby użytkownik nie jest efektów ani zablokowane. Ponadto powolne animacji przenoszenia mogą być uważane za przeciągnięcia wydajności nie zostanie wykonana ze stylem pojawiają się i zniknąć.

##### <a name="incorrect-usage"></a>Nieprawidłowe użycie
 Przypadki, w których interfejsu użytkownika pojawi się więc nagle użytkownik ma nie wiadomo, co się stało i Dodawanie animacji pomógłby kontekstowych opisu.

##### <a name="animation-properties"></a>Właściwości animacji
 Czas opóźnienia jest zazwyczaj zero sekund.

##### <a name="examples"></a>Przykłady

-   Automatyczne ukrywanie okien narzędzi

-   Aktywowany klawiatury Edytor interfejsu użytkownika, takie jak IntelliSense i pomocy parametru

-   Regiony rozwijanie i zwijanie kodu

#### <a name="fade-in-and-fade-out"></a>Wsunąć i fade-out
 W ramach tego wzorca elementu interfejsu użytkownika przechodzi z nie są widoczne (0% nieprzezroczystość) widoczne (krycie 100%) lub na odwrót:

 ![Zanikanie&#45;w&#47;zanikanie&#45;się animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")

##### <a name="correct-usage"></a>Poprawne użycie
 Najczęściej jest to zalecane animacji interfejsu użytkownika. Jest Delikatny efekt, który dodaje zainteresowania bez przerywania przepływu. W niektórych przypadkach użytkownik może nawet nie zauważysz, że nie jest animacji i po prostu uświadamia sobie bezproblemowe płynące system interfejsu użytkownika.

##### <a name="animation-properties"></a>Właściwości animacji

-   Nieprzezroczystość początkowy: 0% na wsunąć, 100% w przypadku fade-out

-   Kończenie nieprzezroczystość: 100% w przypadku wsunąć, 0% fade-out

-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używana jako część sekwencji animacji. kombinacja

-   Styl sterowania tempem zmian: InOut sinus

##### <a name="examples"></a>Przykłady

-   Automatyczne ukrywanie okien narzędzi

-   Menu otwierających i zamykających

-   Tła i pierwszego planu przejścia kartę

#### <a name="color-blend-from-a-to-b"></a>Odcienie koloru od A do B
 W ramach tego wzorca elementu interfejsu użytkownika zmieni się z kolor na kolor B:

 ![Kolor blend animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")

##### <a name="correct-usage"></a>Poprawne użycie
 Jak animowany przejście, kiedy element interfejsu użytkownika kolorów w jednym kontekście lub stanie do innego.

##### <a name="animation-properties"></a>Właściwości animacji

-   Kolor początkowy: Specyficzne dla interfejsu użytkownika

-   Kolor końcowy: Specyficzne dla interfejsu użytkownika

-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używana jako część sekwencji animacji. kombinacja

-   Styl sterowania tempem zmian: InOut sinus

##### <a name="examples"></a>Przykłady

-   Przejścia stanów polecenie okna dokumentu (aktywny, ostatnie aktywnych i nieaktywnych)

-   Narzędzie okna stanami (ukierunkowane i po przeniesieniu fokusu)

#### <a name="expand-and-contract"></a>Rozwinąć lub zwinąć
 Element interfejsu użytkownika w ramach tego wzorca rozszerza się w X, Y lub w obu kierunkach:

 ![Rozwiń&#47;kontraktu animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")

##### <a name="correct-usage"></a>Poprawne użycie
 Jak animowany przejście, kiedy element interfejsu użytkownika rozmiar w jednym kontekście do innego.

##### <a name="animation-properties"></a>Właściwości animacji

-   X skali: % lub określonego wymiaru (w pikselach)

-   Skala Y: % lub określonego wymiaru (w pikselach)

-   Pozycji zakotwiczenia: Ogólnie lewa górna (dla języków, od lewej do prawej) lub prawym górnym rogu (dla języków od prawej do lewej)

-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używana jako część sekwencji animacji. kombinacja

##### <a name="examples"></a>Przykłady

-   Panel Eksploratora architektury, rozwijanie i zwijanie

-   Element strony Start rozwijać i zwijać

#### <a name="x-y-position-change"></a>X i Y pozycji zmiany
 W ramach tego wzorca elementu interfejsu użytkownika zmiany położenia X lub Y i / lub:

 ![X&#47;położenie Y Zmienianie animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")

##### <a name="correct-usage"></a>Poprawne użycie
 Jak animowany przejście, kiedy element interfejsu użytkownika pozycji w jednym kontekście do innego.

##### <a name="animation-properties"></a>Właściwości animacji

-   Pozycja początkowa X i Y: Specyficzne dla interfejsu użytkownika

-   Kończenie X i Y pozycji: Specyficzne dla interfejsu użytkownika

-   Ścieżki ruchu: Brak

-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używana jako część sekwencji animacji. kombinacja

-   Styl sterowania tempem zmian: InOut sinus

##### <a name="example"></a>Przykład
 Zmiana kolejności kartę

#### <a name="rotate"></a>Obrót
 W ramach tego wzorca obraca element interfejsu użytkownika:

 ![Obróć animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")

##### <a name="correct-usage"></a>Poprawne użycie
 Tylko w przypadku nieokreślonej rotowania wskaźnik postępu.

##### <a name="animation-properties"></a>Właściwości animacji

-   Kąt obrotu: 360

-   Obrót Centrum: Drugie obiektu

-   Czas trwania: Ciągłe

##### <a name="example"></a>Przykład
 Wskaźnik postępu nieokreślony (rotowania)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Typowe akcje interfejsu użytkownika powłoki i zalecane animacji

#### <a name="tab-open"></a>Karta Otwórz

- Styl: Są wyświetlane

- Czas trwania: Zero sekund

  ![Karcie Animacja Otwórz w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")

#### <a name="tab-close"></a>Zamknij kartę

- Styl: Zmienianie pozycji X

- Czas trwania: 200 MS

  ![Karta Zamknij animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")

#### <a name="tab-reorder"></a>Której kolejność chcesz zmienić kartę

- Styl: Zmienianie pozycji X

- Czas trwania: 200 MS

  ![Karta zmiany kolejności animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")

#### <a name="close-floating-document"></a>Zamknij dokument zmiennoprzecinkowy

- Styl: Są wyświetlane

- Czas trwania: 200 MS

  ![Zamknij liczb zmiennoprzecinkowych animacji dokumentu w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Zmiana stanu okna

- Styl: Aby zachować spójność z innymi oknami, umożliwiają definiowanie animacji Zamknij dokument bieżącego systemu operacyjnego.

- Czas trwania: 200 MS

  ![Okno stanu przejścia animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")

#### <a name="menu-open"></a>Menu Otwórz

- Styl: Wsunąć

- Czas trwania: 200 MS

  ![Menu Otwórz animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")

#### <a name="menu-close"></a>Zamknij menu

- Styl: Fade-out

- Czas trwania: 200 MS

  ![Zamknij animację menu w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Odsłoń okna narzędzia autoukrywanie

- Styl: Są wyświetlane

- Czas trwania: Zero sekund

  ![Automatyczne&#45;Ukryj Animacja okna narzędzi w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")
