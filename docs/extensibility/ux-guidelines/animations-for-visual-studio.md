---
title: Animacje dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953347c79470b4a77fcd590a1107416f5fcce872
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694286"
---
# <a name="animations-for-visual-studio"></a>Animacje dla programu Visual Studio
## <a name="animation-fundamentals"></a>Podstawy animacji

### <a name="animation-best-practices-in-visual-studio"></a>Najlepsze rozwiązania animacji w programie Visual Studio
Wykonaj te zasady, aby zapewnić style animacji spójne i przyjazny dla użytkownika w środowisku IDE programu Visual Studio.

-   **Należy zachować ostrożność.** Ogranicz animacji do tych, które służą do określonych celów.

-   **Czas i szybkość są ważne** aby zapewnić szybki i fizyczne możesz też przejść:

    -   Ukończ animowane przejścia w ciągu pół sekundy (500 ms).

    -   Animacje, które wystąpiłyby często konieczne Działaj wystarczająco szybko, że nie przerwań się przepływu pracy użytkownika. Obejrzyj animacje w pętli i dostosować czas, dopóki pozornie prawo.

    -   Nie powinien być animacji, więc szybko lub jarring, jest trudny do zrozumienia, ale nie działa tak wolno fakt, że jeden cierpliwy przejścia zakończyć.

    -   Użyj zmiennej czasu, aby podkreślić wagę. Na przykład podczas przechodzenia przez sekwencję elementów na diagramie klasy, szybkości za pomocą przejścia między elementami, a następnie spowolnić skoncentrować się na istotnych elementów.

-   **Użyj stopniowego ułatwianie nieliniowych** z jednego stanu do innego, co daje poczucie cicha i fizyczne przenoszenie.

-   Jeśli to możliwe, **Użyj subtelne animacji, po najechaniu wskaźnikiem** do wskazać elementy interaktywne, w obszarze myszy.

-   Jeśli użytkownik dużym stopniu polegają na animacji w funkcji, następnie **stanowić sposób, aby je wyłączyć** lokalnie (dla wszystkich funkcji) jako opcja w **Narzędzia > Opcje** okna dialogowego.

-   **Tylko jednej animacji powinny być wykonywane jednocześnie** i przekazać tylko jeden zestaw informacji. Więcej niż jeden obiekt przenoszenia lub próba przekazania kilkoma rzeczami może być mylące.

-   **Ważne jest subtlety.** W większości przypadków animacji nie ma żądanie uwagi użytkownika, aby obsługiwać z przeznaczeniem. Drobne zmiany czasu, sekwencjonowania i zachowanie może znacząco wpłynąć na postrzeganie i wprowadzać różnica między skuteczne i nieskuteczne animacji.

-   W przypadku używania animacji do zwrócenia uwagi na coś, **upewnij się, że warto przerywania użytkownika**w pracy.

-   **Gdy są wyświetlane stan lub postęp** za pośrednictwem animacji:

    -   Zatrzymaj Wyświetlanie postępu przenoszenia podczas przesuwania nie bazowego procesu.

    -   Rozróżnia nieokreślony procesów z określania procesów.

    -   Sprawdź, czy animacja ma do zidentyfikowania stanów zakończenia i błędów.

    -   Należy zminimalizować użycie animacji efekt, które informacje o stanie i upewnij się, że mają one prawdziwych wartości, zapewniając dodatkowe informacje rzeczywistego użycia. Przykłady obejmują zmiany stanu przejściowego i zagrożeń

#### <a name="animation-donts"></a>Animacja — ostrzeżenia:

-   Nie używaj ruchy (przenoszenia w niewielkich rozmiarach). Preferuj zanikanie i zmienia się w przenoszenia obiektów.

-   Nie używaj animacji, które odbywają się za pośrednictwem duży obszar powierzchnię ekranu. Bez względu na rozmiar to style, animacji rozprasza dla użytkownika.

-   Nie używaj animacji niezwiązanych ze sobą na obiekt, który użytkownik aktualnie ma fokus w lub interakcji z.

-   Nie używaj animacji, które wymagają interakcji użytkownika, aby zresetować stan, takich jak zmuszania użytkownika odpowiedzieć migające powiadomienie, aby udostępnić ją zatrzymać migające. Powinna być wystarczające, aby je odrzucić interakcji z nimi w jakikolwiek sposób.

Aby uzyskać więcej informacji na temat aplikacji dla tych najlepszych rozwiązań, zobacz [wzorców animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metryki animacji

-   System powinien widoczny reagowanie na gesty użytkownika w mniej niż 10 milisekund.

-   Animowane przejścia nie powinien trwać dłużej niż 500 milisekund, aby zakończyć.

-   Jednym ze sposobów, aby zrekompensować przejścia, które wymagają wydłużenie czasu jest dzielenie dwóch części. Na przykład w pierwszej części animację można pustego kontenera zawartości (maks. 500 milisekund), następuje zanikanie zawartości do kontenera (maks. 500 ms).

-   Czasy ładowania, które mogą być obliczane preferowany jest wskaźnik postępu decydującym (wskaźnik postępu gotowe procent).

-   Czas ładowania, których nie można obliczyć wskaźnik zajętości, takich jak kursor lub osadzonego rotowania animacji (ładowanie lub wskaźnik pracy) jest.

### <a name="animation-as-communicator"></a>Animacja jako communicator
W interfejsie użytkownika Visual Studio animacji działa tylko jako narzędzie do komunikacji.  Jest on używany do komunikowania się różne informacje, takie jak zmian strukturalnych w Interfejsie użytkownika (na przykład, gdy menu spowoduje otwarcie lub zamknięcie). Animacja może pomóc w wizualizacji zachowań zależnych od czasu, złożonych systemów, takich jak wizualizacja postępu instalacji. Animacje mogą również Zwróć uwagę, alertów i powiadomień.

 Animacje interfejsu użytkownika zwykle działają na cztery sposoby: wizualizowanie, zwróć uwagę, zasymulować, i czasy odpowiedzi/postępu wskaźników.

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

-   Reprezentuje zmiany wraz z upływem czasu przy użyciu czasu suwaki, biegu shuttle koła i kontrolki transportu (Odtwórz, Zatrzymaj i wstrzymania)

##### <a name="relationships"></a>Relacje

-   Pokazują, jak elementy powiązane ze sobą lub elementy, które odnoszą się do danego elementu

-   Wyświetlanie hierarchii i nadrzędny podrzędny lub element równorzędny relacji

-   Jeden element spowoduje utworzenie innego

-   Jeden element minimalizuje do innego elementu

-   Jeden element pomocą zastosowaniu tetheringu do innego

##### <a name="state"></a>Stan

-   Aktualizacje zawartości

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

##### <a name="alert"></a>Alerty

-   Ostrzegać użytkowników, Uzyskaj uwagi, Pokaż postęp

-   Pokazują, że coś, co jest wykonywana prawidłowo lub nieprawidłowo lub wyświetlić postęp lub zmiany w toku

-   Monituj użytkowników podczas zadania, takie jak wyszukiwanie więcej informacji w trybie online lub poznawania bieżące zadanie

##### <a name="notifications"></a>Powiadomienia

-   Ostrzegać użytkowników o warunek błędu

-   Przerwie pracę użytkownika, aby zobaczyć, czy chce zająć się czymś innym

-   Delikatnie poinformowania użytkownika o ukończeniu procesu lub zmienione, takie jak po zakończeniu pobierania.

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
Animacje w programie Visual Studio są przeznaczone do obsługi określonych funkcji bez zakłócały wydajność pracy użytkowników. Ogólnie rzecz biorąc animacji w programie Visual Studio powinny być następujące:

-   Małe i dyskretny kod

-   Fizyczne i realistyczne

-   Subtelnym, przytłumionym

-   Szybkie i wydajne

-   Swobodna, nie hurried

Ta ilustracja przedstawia style animacji, zalecamy dla programu Visual Studio. Nie animacji lub subtelne animacje, takie jak zanikanie / zanikanie najczęściej są używane. Istnieje ograniczona zastosowania animacji przenoszenia, takie jak rozwinąć lub zwinąć, X i Y pozycji zmian które obrotu.

![Zalecane animacji, stylów dla programu Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 a_VSAnimStyles")<br />Style animacji zalecany dla programu Visual Studio

#### <a name="appear-and-disappear"></a>Pojawiają się i znikają
W ramach tego wzorca elementu zmienia się z widoczne poza widoku i ponownie bez animacji przejścia.

![Pojawiają się i znikają animacji](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 b_AppearAndDisappear")<br />Pojawiają się i znikają animacji

##### <a name="correct-usage"></a>Poprawne użycie
Świeży elementy interfejsu użytkownika, które muszą natychmiast lub pojawiania się tak, aby użytkownik nie jest efektów ani zablokowane. Ponadto powoli przenoszonych animacje mogą być uważane za przeciągnięcia wydajności nie zostanie wykonana ze stylem pojawiają się i zniknąć.

##### <a name="incorrect-usage"></a>Nieprawidłowe użycie
Przypadki, w których interfejsu użytkownika pojawi się więc nagle użytkownik ma nie wiadomo, co się stało i Dodawanie animacji pomógłby kontekstowych opisu.

##### <a name="animation-properties"></a>Właściwości animacji
Czas opóźnienia jest zazwyczaj zero sekund.

##### <a name="examples"></a>Przykłady
-   Automatyczne ukrywanie okien narzędzi

-   Aktywowany klawiatury Edytor interfejsu użytkownika, takie jak IntelliSense i pomocy parametru

-   Regiony rozwijanie i zwijanie kodu

#### <a name="fade-in-and-fade-out"></a>Wsunąć i fade-out
W ramach tego wzorca elementu interfejsu użytkownika przechodzi z nie są widoczne (0% nieprzezroczystość) widoczne (100% nieprzezroczystości) lub odwrotnie.

![Animacja wsunąć i fade-out](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 c_FadeInFadeOut")<br />Wsunąć i fade-out animacji

##### <a name="correct-usage"></a>Poprawne użycie
Najczęściej jest to zalecane animacji interfejsu użytkownika. Jest Delikatny efekt, który dodaje zainteresowania bez przerywania przepływu. W niektórych przypadkach użytkownik może nawet nie zauważysz to animacji, odczuwaniu umożliwiającej płynne i przepływających interfejsu użytkownika systemu.

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
W ramach tego wzorca elementu interfejsu użytkownika zmieni się z kolor na kolor B.

![Kolor blend animacji](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 d_ColorBlend")<br />Animacja mieszania kolorów

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
Element interfejsu użytkownika w ramach tego wzorca rozszerza się w X, Y lub w obu kierunkach.

![Rozwinąć lub zwinąć animacji](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 e_ExpandContract")<br />Rozwinąć lub zwinąć animacji

##### <a name="correct-usage"></a>Poprawne użycie
Jak animowany przejście, kiedy element interfejsu użytkownika rozmiar w jednym kontekście do innego.

##### <a name="animation-properties"></a>Właściwości animacji

-   X skali: % lub określonego wymiaru (w pikselach)

-   Skala Y: % lub określonego wymiaru (w pikselach)

-   Zakotwicz pozycja: ogólnie lewa górna (dla języków, od lewej do prawej) lub prawym górnym rogu (dla języków od prawej do lewej)

-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używana jako część sekwencji animacji. kombinacja

##### <a name="examples"></a>Przykłady

-   Panel Eksploratora architektury, rozwijanie i zwijanie

-   Element strony Start rozwijać i zwijać

#### <a name="x-y-position-change"></a>X i Y pozycji zmiany
W ramach tego wzorca elementu interfejsu użytkownika zmiany położenia X lub Y i / lub.

![Pozycja X i Y Zmienianie animacji](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 f_XYPositionChange")<br />Animacja zmiany pozycji X i Y

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
W ramach tego wzorca obraca element interfejsu użytkownika.

![Animacja rotacji elementu interfejsu użytkownika](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 g_Rotate")<br />Animacja rotacji elementu interfejsu użytkownika

##### <a name="correct-usage"></a>Poprawne użycie
Tylko w przypadku nieokreślonej rotowania wskaźnik postępu.

##### <a name="animation-properties"></a>Właściwości animacji

-   Kąt obrotu: 360

-   Obrót Centrum: środkowej obiektu

-   Czas trwania: ciągłe

##### <a name="example"></a>Przykład
Wskaźnik postępu nieokreślony (rotowania)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Typowe akcje interfejsu użytkownika powłoki i zalecane animacji

#### <a name="tab-open"></a>Karta Otwórz
![Animacja Otwórz kartę](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 h_TabOpen")<br />Animacja Otwórz kartę

-   Styl: wyświetlane

-   Czas trwania: zero sekund.

#### <a name="tab-close"></a>Zamknij kartę
![Zamknij animację karcie](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 i_TabClose")<br />Animacja Zamknij kartę

-   Styl: Zmienianie pozycji X

-   Czas trwania: 200 MS

#### <a name="tab-reorder"></a>Której kolejność chcesz zmienić kartę
![Karta zmiany kolejności animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 j_TabReorder")<br />Karta zmiany kolejności animacji

-   Styl: Zmienianie pozycji X

-   Czas trwania: 200 MS

#### <a name="close-floating-document"></a>Zamknij dokument zmiennoprzecinkowy
![Zamknij liczb zmiennoprzecinkowych animacji dokumentu](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 k_CloseFloatingDocument")<br />Zamknij zmiennoprzecinkowy animacji dokumentu

-   Styl: wyświetlane

-   Czas trwania: 200 MS

#### <a name="window-state-transition"></a>Zmiana stanu okna
![Animacja przejścia stanu okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 l_WindowStateTransition")<br />Animacja przejścia stanu okna

-   Styl: Aby zachować spójność z innymi oknami, umożliwiają definiowanie animacji Zamknij dokument bieżącego systemu operacyjnego.

-   Czas trwania: 200 MS

#### <a name="menu-open"></a>Menu Otwórz
![Menu Otwórz animacji](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 m_MenuOpen")<br />Menu Otwórz animacji

-   Styl: wsunąć

-   Czas trwania: 200 MS

#### <a name="menu-close"></a>Zamknij menu
![Zamknij animację menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 n_MenuClose")<br />Zamknij animację menu

-   Styl: fade-out

-   Czas trwania: 200 MS

#### <a name="auto-hide-tool-window-reveal"></a>Odsłoń okna narzędzia autoukrywanie
![Autoukrywanie animacji Odsłoń okna narzędzia](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")<br />Autoukrywanie animacji Odsłoń okna narzędzi

-   Styl: wyświetlane

-   Czas trwania: zero sekund.