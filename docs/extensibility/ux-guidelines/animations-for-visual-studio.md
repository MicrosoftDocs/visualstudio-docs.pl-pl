---
title: Animacje dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698608"
---
# <a name="animations-for-visual-studio"></a>Animacje dla programu Visual Studio
## <a name="animation-fundamentals"></a>Podstawy animacji

### <a name="animation-best-practices-in-visual-studio"></a>Najważniejsze wskazówki dotyczące animacji w programie Visual Studio
Postępuj zgodnie z tymi regułami, aby zapewnić spójne i przyjazne dla użytkownika style animacji w programie Visual Studio IDE.

- **Bądź selektywny.** Ogranicz animacje do tych, które służą określonym celom.

- **Czas i szybkość są ważne,** aby zapewnić, że przejścia są szybkie i naturalne:

  - Ukończ animowane przejścia w ciągu pół sekundy (500 milisekund).

  - Animacje, które występują często muszą być na tyle szybkie, aby nie przerywać przepływu pracy użytkownika. Obejrzyj animację w pętli i dostosuj czas, aż poczuje się dobrze.

  - Animacje nie powinny być tak szybkie lub wstrząsające, że jest trudne do zrozumienia, ale nie tak powolne, że sprawia, że jeden niecierpliwy do przejścia do końca.

  - Użyj zmiennego czasu, aby podkreślić znaczenie. Na przykład podczas nawigowania po sekwencji elementów na diagramie klasy, szybkość przechodzenia między elementami, a następnie spowolnić, aby skupić się na ważnych elementów.

- **Używaj stopniowego nieliniowego luzowania** z jednego stanu do drugiego, dając poczucie spokoju i naturalnego ruchu.

- Jeśli to możliwe, **użyj subtelnej animacji na hover,** aby wskazać interaktywne elementy pod myszą.

- Jeśli w dużej mierze polegasz na animacjach w swoich funkcjach, **udostępnisz sposób na wyłączenie ich** lokalnie (dla wszystkich funkcji) jako opcję w oknie dialogowym Narzędzia > **Opcje.**

- **Tylko jedna animacja powinna wystąpić w czasie** i przekazać tylko jedną informację. Więcej niż jeden obiekt poruszający się lub próbujący przekazać wiele rzeczy może być mylący.

- **Subtelność jest ważna.** W większości przypadków animacja nie musi wymagać uwagi użytkownika, aby służyć jej celowi. Subtelne zmiany czasu, sekwencjonowania i zachowania mogą znacząco wpłynąć na percepcję i mogą mieć wpływ na skuteczną i nieskuteczną animację.

- Podczas korzystania z animacji, aby zwrócić uwagę na coś, **upewnij się, że warto przerwać użytkownika**pociągu myśli.

- **Podczas wyświetlania postępu lub stanu** za pomocą animacji:

  - Przestań pokazywać ruch postępu, gdy podstawowy proces nie jest postępowy.

  - Odróżnić nieokreślone procesy od procesów determinacji.

  - Upewnij się, że animacja ma identyfikowalne stany ukończenia i awarii.

  - Zminimalizuj użycie animacji efektów, które pokazują stan i upewnij się, że mają one rzeczywistą wartość, zapewniając dodatkowe informacje o rzeczywistym użyciu. Przykłady obejmują przejściowe zmiany stanu i sytuacje awaryjne

#### <a name="animation-donts"></a>Animacja nie:

- Nie używaj małych ruchów (ruch o małej powierzchni). Preferuj zanika i zmienia się nad poruszającymi się obiektami.

- Nie używaj animacji, które odbywają się na dużym obszarze ekranu nieruchomości. Niezależnie od rozmiaru, ten styl animacji rozprasza użytkownika.

- Nie używaj animacji niezwiązanych z obiektem, na który użytkownik aktualnie koncentruje się lub z którymi wchodzi w interakcję.

- Nie używaj animacji, które wymagają interakcji użytkownika, aby zresetować stan, na przykład zmuszając użytkownika do odpowiedzi na migające powiadomienie, aby zatrzymać miganie. Interakcja z nimi w jakikolwiek sposób powinna być wystarczająca, aby je odrzucić.

Aby uzyskać więcej informacji na temat aplikacji dla tych najlepszych rozwiązań, zobacz [Wzorce animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metryki animacji

- System powinien w sposób widoczny reagować na gesty użytkownika w czasie krótszym niż 10 milisekund.

- Animowane przejścia nie powinny trwać dłużej niż 500 milisekund.

- Jednym ze sposobów kompensacji przejść, które wymagają dłuższych czasów, jest rozdzielenie go na dwie części. Na przykład pierwszą częścią animacji może być pusty kontener zawartości (do 500 milisekund), a następnie zawartość zanika do kontenera (do 500 milisekund).

- W przypadku czasów ładowania, które można obliczyć, preferowany jest wskaźnik postępu determinant (wskaźnik postępu procentowego wykonania).

- W przypadku czasów ładowania, których nie można obliczyć, odpowiedni jest wskaźnik zajętości, taki jak kursor lub osadzona animacja wirowania (wskaźnik ładowania lub pracy).

### <a name="animation-as-communicator"></a>Animacja jako komunikator
W programie Visual Studio UI animacja działa tylko jako narzędzie komunikacji.  Służy do przekazywania różnych informacji, takich jak zmiany strukturalne w interfejsie użytkownika (na przykład, gdy menu zostanie otwarte lub zamknięte). Animacja może pomóc w wizualizacji zależnego od czasu zachowania złożonych systemów, takiego jak wizualizacja postępu instalacji. Animacje mogą być również używane do przyciągania uwagi z alertów i powiadomień.

 Animacje interfejsu użytkownika zazwyczaj działają na cztery sposoby: wizualizować, przyciągać uwagę, symulować i wskaźników czasu reakcji/postępu.

#### <a name="visualize"></a>Wizualizacja
Animacja może podkreślić trójwymiarowy charakter obiektów i ułatwić użytkownikom wizualizację ich struktury przestrzennej. Aby to osiągnąć, animacja może wymagać obracania obiektu w pełnym kole, powolnego obracania go w tę i z powrotem lub przybliżania obiektu i nieznacznego zwiększenia jego rozmiaru, aby podkreślić najazd lub fokus.

Chociaż obiekty trójwymiarowe mogą być przenoszone za pomocą kontroli użytkownika, projektant powinien określić z wyprzedzeniem (programowo lub ręcznie), jak najlepiej animować ruch, który zapewnia optymalne zrozumienie obiektu. Ta zaprogramowana animacja może być następnie aktywowana przez użytkownika przez umieszczenie kursora nad obiektem, podczas gdy ruchy kontrolowane przez użytkownika wymagają od użytkownika zrozumienia, jak manipulować obiektem. Ograniczyć ruch do jednej osi lub orientacji naraz; skaluj, obracaj lub tłumacz, ale nie rób więcej niż jednego jednocześnie.

Kategoria Wizualizuj obejmuje aspekty danych, relacji, stanu, struktury, sekwencji i czasu.

##### <a name="data"></a>Dane
Zilustruj złożone i zmienne informacje:

- Przechodzenie przez wizualizacje informacji, takie jak wykresy i wykresy

- Przechodzenie przez sekwencję, zwiedzanie z przewodnikiem i stronicowanie

- Wywoływanie szczegółów, wskakiwanie i wyróżnianie określonych informacji

- Nakładanie szczegółów i dodatkowych informacji na element skoncentrowany

- Zmiana z jednej reprezentacji strukturalnej lub organizacyjnej na inną

- Przedstawianie zmian w czasie za pomocą suwaków czasu, kół jog-and-shuttle i kontroli transportu (odtwarzanie, zatrzymywanie i pauza)

##### <a name="relationships"></a>Relacje

- Ilustruje, w jaki sposób elementy odnoszą się do siebie nawzajem lub które elementy odnoszą się do danego elementu

- Pokazywale hierarchii i relacje nadrzędny-podrzędny lub równorzędny

- Jeden element rodzi inny

- Jeden element minimalizuje do innego elementu

- Jeden element uwięziony na drugim

##### <a name="state"></a>Stan

- Aktualizacje zawartości

- Koncentracja i wybór użytkownika

- Postęp

- Errors

##### <a name="structure"></a>Struktura

- Obracanie struktury w jednym węźle

- Reorientowanie

- Minimalizowanie i maksymalizacja lub rozwijanie i zwijanie

##### <a name="sequence"></a>Sequence

- Sekwencja pokazu slajdów

- Przeglądanie obrazów

##### <a name="time"></a>Time

- Pokaż zmiany w czasie, upływu czasu i screencast

- Przechodzenie do kosza, cofania i ponawiania

- Przywracanie stanu historycznego

#### <a name="attract-attention"></a>Przyciągnij uwagę
Jeśli celem jest zwrócenie uwagi użytkownika na pojedynczy element z kilku lub powiadomienie użytkownika o zaktualizowanych informacjach, animacja może być odpowiednia. Na przykład strona początkowa aplikacji może użyć przycisku Wprowadzenie, który przesuwa się na miejsce po załadowaniu strony.

Z reguły ostatni ruchomy element na ekranie przyciąga uwagę użytkownika.  W serii animowanych elementów uwaga użytkownika będzie podążać za ostatnim ruchomym obiektem.

##### <a name="alert"></a>Alerty

- Ostrzegaj użytkownika, zwracaj uwagę, pokazuj postęp

- Pokaż, że coś jest wykonywane poprawnie lub niepoprawnie lub pokaż zmiany postępu lub postępu

- Monitowanie użytkowników podczas zadania, takie jak znajdowanie większej ilości informacji w trybie online lub poznawanie bieżącego zadania

##### <a name="notifications"></a>Powiadomienia

- Ostrzeganie użytkownika o warunku błędu

- Przerwij użytkownika, aby sprawdzić, czy chciałby zająć się czymś innym

- Delikatnie poinformuj użytkownika, że proces został zakończony lub zmieniony, na przykład po zakończeniu pobierania.

#### <a name="simulate"></a>Symulować
Kategoria ta obejmuje fizyczność i wymiarowość.

- Zilustruj, skąd pochodzą obiekty lub dokąd się udają

- Rozwijanie i zwijanie lub otwieranie i zamykanie

- Przesuwanie, przewijanie i obracanie strony

- Układanie i zamawianie z

- Karuzela i akordeon

- Przerzucanie i obracanie interfejsu użytkownika

#### <a name="response-and-progress-indicators"></a>Wskaźniki reakcji i postępu
Wskaźniki postępu mają kilka znaczących zalet:

- Zarówno określone, jak i nieokreślone wskaźniki postępu uspokajają użytkownika, że system nie uległ awarii i pracuje nad problemem.

- Określone wskaźniki dają użytkownikowi poczucie, jak daleko postępuje akcja, a także poczucie zbliżania się do mety.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Wzorce animacji

### <a name="overview"></a>Omówienie
Animacje w programie Visual Studio mają służyć określonej funkcji bez utrudniania wydajności użytkownika. Ogólnie rzecz biorąc animacje w programie Visual Studio powinny być:

- Małe i dyskretne

- Naturalne i realistyczne

- Subtelne i stonowane

- Szybkość i wydajność

- Zrelaksowany, nie pospieszny

Na tej ilustracji przedstawiono style animacji zalecane dla programu Visual Studio. Najczęściej używane są animacje ani subtelne animacje, takie jak zanikanie/zanikanie. Istnieje ograniczone zastosowanie animacji ruchu, takich jak rozwiń i kontrakt, X i Y zmiany pozycji i rotacji.

![Zalecane style animacji dla programu Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Zalecane style animacji dla programu Visual Studio

#### <a name="appear-and-disappear"></a>Pojawiają się i znikają
Z tego wzorca element przełącza się z widocznych do out-of-view i z powrotem bez animacji przejścia.

![Pojawiają się i znikają animacje](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Pojawiają się i znikają animacje

##### <a name="correct-usage"></a>Prawidłowe użycie
Świeże elementy interfejsu użytkownika, które muszą natychmiast pojawić się lub zniknąć, aby użytkownik nie był rozpraszany ani blokowany. Ponadto animacje wolno poruszające mogą być postrzegane jako przeciąganie wydajności, które nie nastąpi w przypadku stylu pojawiania się i znikania.

##### <a name="incorrect-usage"></a>Nieprawidłowe użycie
Przypadki, w których interfejs użytkownika pojawia się tak gwałtownie użytkownik nie ma pojęcia, co się stało, a dodanie animacji pomoże w kontekstowym zrozumienia.

##### <a name="animation-properties"></a>Właściwości animacji
Opóźnienie jest zazwyczaj zero sekund.

##### <a name="examples"></a>Przykłady
- Automatyczne ukrywanie okien narzędzi

- Interfejs użytkownika edytora aktywowany za pomocą klawiatury, taki jak IntelliSense i Parameter Help

- Rozwijanie i zwijanie regionów kodu

#### <a name="fade-in-and-fade-out"></a>Zanikanie i zanikanie
Z tym wzorcem element interfejsu użytkownika przechodzi z niewidoczne (0% krycia) do widoczne (100% krycia) lub odwrotnie.

![Animacja zanikania i zanikania](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animacja zanikania i zanikania

##### <a name="correct-usage"></a>Prawidłowe użycie
Jest to najczęściej zalecana animacja interfejsu użytkownika. Jest to subtelny efekt, który zwiększa zainteresowanie bez przerywania przepływu. W niektórych przypadkach użytkownik może nawet nie zdawać sobie sprawy, że istnieje animacja, postrzeganie płynnego i płynnego systemu interfejsu użytkownika.

##### <a name="animation-properties"></a>Właściwości animacji

- Nieprzezroczystość rozruchowa: 0% dla zanikania, 100% dla zanikania

- Nieprzezroczystość końcowa: 100% dla zanikania, 0% dla zanikania

- Czas trwania: 200 milisekund samodzielny, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl luzowania: Sine InOut

##### <a name="examples"></a>Przykłady

- Automatyczne ukrywanie okien narzędzi

- Menu otwieranie i zamykanie

- Przejścia karty tło i pierwszy plan

#### <a name="color-blend-from-a-to-b"></a>Mieszanka kolorów od A do B
W tym wzorze element interfejsu użytkownika zmienia się z koloru A na kolor B.

![Animacja mieszania kolorów](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animacja mieszania kolorów

##### <a name="correct-usage"></a>Prawidłowe użycie
Jako animowane przejście, gdy element interfejsu użytkownika zmienia kolor z jednego kontekstu lub stanu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Kolor początkowy: specyficzny dla interfejsu użytkownika

- Kolor końcowy: specyficzny dla interfejsu użytkownika

- Czas trwania: 200 milisekund samodzielny, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl luzowania: Sine InOut

##### <a name="examples"></a>Przykłady

- Przejścia stanu okna dokumentu (aktywne, ostatnio aktywne i nieaktywne)

- Przejścia stanu okna narzędzia (skoncentrowane i nieskoncentrowane)

#### <a name="expand-and-contract"></a>Rozwiń i zamów
Za pomocą tego wzorca element interfejsu użytkownika rozwija się w X, Y lub w obu kierunkach.

![Rozwijanie i animacja kontraktów](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Rozwijanie i animacja kontraktów

##### <a name="correct-usage"></a>Prawidłowe użycie
Jako animowane przejście, gdy element interfejsu użytkownika zmienia rozmiar z jednego kontekstu do drugiego.

##### <a name="animation-properties"></a>Właściwości animacji

- Skala X: % lub określony wymiar (w pikselach)

- Skala Y: % lub określony wymiar (w pikselach)

- Pozycja zakotwiczenia: zazwyczaj lewa górna (w językach od lewej do prawej) lub prawa górna (w językach od prawej do lewej)

- Czas trwania: 200 milisekund samodzielny, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

##### <a name="examples"></a>Przykłady

- Rozwijanie i zwijanie panelu Eksplorator architektury

- Element strony początkowej programu Visual Studio 2017 rozwijanie i zwijanie

#### <a name="x-y-position-change"></a>Zmiana pozycji X-Y
Z tym wzorcem element interfejsu użytkownika zmienia jego pozycję X lub Y lub oba.

![Animacja zmiany pozycji X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animacja zmiany pozycji X-Y

##### <a name="correct-usage"></a>Prawidłowe użycie
Jako animowane przejście, gdy element interfejsu użytkownika zmienia położenie z jednego kontekstu do drugiego.

##### <a name="animation-properties"></a>Właściwości animacji

- Pozycja początkowa X i Y: specyficzne dla interfejsu użytkownika

- Koniec pozycji X i Y: specyficzne dla interfejsu użytkownika

- Ścieżka ruchu: brak

- Czas trwania: 200 milisekund samodzielny, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl luzowania: Sine InOut

##### <a name="example"></a>Przykład
Ponowne kolejność kart

#### <a name="rotate"></a>Obrót
Z tym wzorem element interfejsu użytkownika obraca się.

![Animacja obrotu elementu interfejsu użytkownika](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animacja obrotu elementu interfejsu użytkownika

##### <a name="correct-usage"></a>Prawidłowe użycie
Tylko dla nieokreślonego wskaźnika postępu wirowania.

##### <a name="animation-properties"></a>Właściwości animacji

- Stopień obrotu: 360

- Środek obrotu: środek obiektu

- Czas trwania: ciągły

##### <a name="example"></a>Przykład
Nieokreślony wskaźnik postępu (przędzenie)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Typowe akcje interfejsu użytkownika powłoki i zalecane animacje

#### <a name="tab-open"></a>Otwarto kartę
![Animacja otwierania karty](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animacja otwierania karty

- Styl: pojawiają się

- Czas trwania: zero sekund

#### <a name="tab-close"></a>Zamknij tabulatora
![Animacja zamykania tabulatora](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animacja zamykania tabulatora

- Styl: X zmiana pozycji

- Czas trwania: 200 milisekund

#### <a name="tab-reorder"></a>Ponowne kolejność kart
![Ponowne kolejność animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animacja ponownego kolejności kart

- Styl: X zmiana pozycji

- Czas trwania: 200 milisekund

#### <a name="close-floating-document"></a>Zamknij pływający dokument
![Zamykanie animacji dokumentu przestawnego](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Zamykanie animacji dokumentu przestawnego

- Styl: pojawiają się

- Czas trwania: 200 milisekund

#### <a name="window-state-transition"></a>Przejście stanu okna
![Animacja przejścia stanu okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animacja przejścia stanu okna

- Styl: aby być spójnym z innymi oknami, pozwól bieżącemu systemowi operacyjnemu zdefiniować animację zamknięcia dokumentu.

- Czas trwania: 200 milisekund

#### <a name="menu-open"></a>Otwarte menu
![Animacja otwierania menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animacja otwierania menu

- Styl: fade-in

- Czas trwania: 200 milisekund

#### <a name="menu-close"></a>Zamknięcie menu
![Animacja zamykania menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animacja zamykania menu

- Styl: zanikanie

- Czas trwania: 200 milisekund

#### <a name="auto-hide-tool-window-reveal"></a>Automatyczne ukrywanie okna narzędzia
![Automatyczne ukrywanie animacji okna narzędzia](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Automatyczne ukrywanie animacji okna narzędzia

- Styl: pojawiają się

- Czas trwania: zero sekund
