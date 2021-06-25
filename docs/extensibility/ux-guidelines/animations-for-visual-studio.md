---
title: Animacje dla Visual Studio | Microsoft Docs
description: Dowiedz się więcej o zasadach, które pomagają zapewnić spójne i przyjazne dla użytkownika style animacji w Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1e8e61e5decea326fcb7f670ed2ab58f0137530
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902790"
---
# <a name="animations-for-visual-studio"></a>Animacje dla programu Visual Studio
## <a name="animation-fundamentals"></a>Podstawy animacji

### <a name="animation-best-practices-in-visual-studio"></a>Animacja najlepsze rozwiązania w zakresie Visual Studio
Postępuj zgodnie z tymi regułami, aby zapewnić spójne i przyjazne dla użytkownika style animacji w całym Visual Studio IDE.

- **Należy selektywnie.** Ogranicz animacje do tych, które służą określonym celom.

- **Chronometraż i szybkość są ważne,** aby upewnić się, że przejścia są szybkie i naturalne:

  - Wykonaj animowane przejścia w ciągu pół sekundy (500 milisekund).

  - Animacje, które często występują, muszą być wystarczająco szybkie, aby nie przerywały przepływu pracy użytkownika. Obejrzyj animację w pętli i dostosuj chronometraż, aż będzie on odpowiedni.

  - Animacje nie powinny być tak szybkie ani jarringowe, że trudne do zrozumienia, ale nie tak wolno, że sprawia, że przejście do końca jest niecierpliwe.

  - Użyj zmiennych chronometrażu, aby podkreślić ważność. Na przykład podczas nawigowania po sekwencji elementów na diagramie klas należy przyspieszyć przechodzenie między elementami, a następnie spowalniać, aby skoncentrować się na ważnych elementach.

- **Używaj stopniowego, nieliniowego easingu** z jednego stanu do innego, dając poczucie uspokojenia i naturalnego ruchu.

- Jeśli to możliwe, **użyj subtelnej animacji po zatrzymaniu wskaźnika myszy,** aby wskazać elementy interaktywne pod myszą.

- Jeśli w dużym stopniu korzystasz z  animacji w funkcjach, możesz je wyłączyć lokalnie (dla wszystkich funkcji) jako opcję w oknie dialogowym Narzędzia **> opcje.**

- **Jednocześnie powinna wystąpić tylko jedna animacja,** która przekaże tylko jeden element informacji. Przeniesienie więcej niż jednego obiektu lub próba przekazania wielu rzeczy może być myląca.

- **Subtelność jest ważna.** W większości przypadków animacja nie musi wymagać uwagi użytkownika, aby pełnić swoją funkcję. Subtelne zmiany w chronometrażu, sekwencjonowania i zachowaniu mogą mieć znaczący wpływ na postrzeganie i mogą stanowić różnicę między efektywną i nieskuteczną animacją.

- Korzystając z animacji w celu zwrócenia uwagi **na** coś, upewnij się, że warto przerwać trenowanie myślenia użytkownika.

- **Podczas wyświetlania postępu lub stanu za pomocą** animacji:

  - Zatrzymaj wyświetlanie ruchu postępu, gdy podstawowy proces nie jest rozwijany.

  - Rozróżniaj nieokreślone procesy od procesów deterministyczny.

  - Upewnij się, że animacja ma rozpoznawalne stany ukończenia i niepowodzenia.

  - Zminimalizuj użycie animacji efektów, które pokazują stan, i upewnij się, że mają rzeczywistą wartość, udostępniając dodatkowe informacje dotyczące rzeczywistego użycia. Przykłady obejmują przejściowe zmiany stanu i sytuacje awaryjne

#### <a name="animation-donts"></a>Animacja nie jest:

- Nie używaj małych przepływów (ruch w niewielkim rozmiarze). Preferuj zanikanie i zmiany zamiast przenoszenia obiektów.

- Nie używaj animacji, które odbywają się na dużym obszarze powierzchni ekranu. Niezależnie od rozmiaru ten styl animacji rozprasza użytkownika.

- Nie używaj animacji niepowiązanych z obiektem, na który użytkownik aktualnie skupia się ani z nim korzysta.

- Nie używaj animacji, które wymagają interakcji z użytkownikiem w celu zresetowania stanu, na przykład wymuś od użytkownika odpowiadanie na pulsujące powiadomienie, aby zatrzymać jego flashowanie. Interakcja z nimi w jakikolwiek sposób powinna być wystarczająca, aby je odrzucić.

Aby uzyskać więcej informacji na temat aplikacji dla tych najlepszych rozwiązań, zobacz [Wzorce animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metryki animacji

- System powinien w widoczny sposób reagować na gesty użytkownika w mniej niż 10 milisekundach.

- Animowane przejścia nie powinny trwać dłużej niż 500 milisekund.

- Jednym ze sposobów kompensowania przejść, które wymagają dłuższego czasu, jest oddzielienie go na dwie części. Na przykład pierwszą częścią animacji może być pusty kontener zawartości (do 500 milisekund), a następnie zawartość zanika do kontenera (do 500 milisekund).

- W przypadku czasów ładowania, które można obliczyć, preferowany jest wskaźnik postępu deterministycznego (wskaźnik postępu wykonywanego w procentach).

- W przypadku czasów ładowania, których nie można obliczyć, odpowiedni jest wskaźnik zajętości, taki jak kursor lub osadzona animacja wirowania (ładowanie lub wskaźnik roboczy).

### <a name="animation-as-communicator"></a>Animacja jako komentator
W Visual Studio użytkownika animacja działa tylko jako narzędzie do komunikacji.  Służy do przekazywania różnych informacji, takich jak zmiany strukturalne w interfejsie użytkownika (na przykład po otworze lub zamknięciu menu). Animacja może pomóc w wizualizacji zależnej od czasu zachowania złożonych systemów, takich jak wizualizacja postępu instalacji. Animacje mogą również przyciągać uwagę alertami i powiadomieniami.

 Animacje interfejsu użytkownika zwykle działają na cztery sposoby: wizualizowanie, przyciąganie uwagi, symulowanie i wskaźniki czasu odpowiedzi/postępu.

#### <a name="visualize"></a>Wizualizacja
Animacja może podkreślać trójwymiarową naturę obiektów i ułatwić użytkownikom wizualizowanie ich struktury przestrzennej. Aby to osiągnąć, animacja może wymagać rozkręcania obiektu w pełnym kole, powolnego obracania go do przodu i do tyłu lub przybliżania i nieco zwiększania jego rozmiaru, aby podkreślić przewrót lub fokus.

Mimo że obiekty trójwymiarowe mogą być przenoszone za pomocą kontrolki użytkownika, projektant powinien z wyprzedzeniem (programowo lub ręcznie) określić, jak najlepiej animować ruch, który zapewnia optymalne zrozumienie obiektu. Ta zaprogramowana animacja może następnie zostać aktywowana przez użytkownika przez umieszczenie kursora na obiekcie, natomiast ruchy kontrolowane przez użytkownika wymagają od użytkownika zrozumienia sposobu manipulowania obiektem. Ogranicz ruch do pojedynczej osi lub orientacji na raz; skalowanie, obracanie lub tłumaczenie, ale nie robisz więcej niż jednego jednocześnie.

Kategoria Visualize obejmuje aspekty danych, relacji, stanu, struktury, sekwencji i czasu.

##### <a name="data"></a>Dane
Zilustruj informacje złożone i zmienne:

- Przechodzenie przez wizualizacje informacji, takie jak wykresy i grafy

- Przechodzenie przez sekwencję, przewodnik z przewodnikiem i stronicowanie

- Wywoływanie szczegółów, wskazujenie i wyróżnianie określonych informacji

- Nakładanie szczegółów i dodatkowych informacji na element ukierunkowany

- Zmiana reprezentacji strukturalnej lub organizacyjnej na inną

- Reprezentacja zmian w czasie przy użyciu suwaków czasu, kółka do koła z kołami do przewoportowania oraz kontrolek transportu (odtwarzanie, zatrzymywanie i wstrzymywanie)

##### <a name="relationships"></a>Relacje

- Ilustracja relacji elementów ze sobą lub elementów związanych z danym elementem

- Pokazywanie hierarchii i relacji nadrzędny-podrzędny lub równorzędny

- Jeden element duduje inny

- Jeden element minimalizuje do innego elementu

- Jeden element, który jest przypęty do innego

##### <a name="state"></a>Stan

- Aktualizacje zawartości

- Fokus i wybór użytkownika

- Postęp

- błędy

##### <a name="structure"></a>Struktura

- Przewłacanie struktury na jednym węźle

- Reorientacja

- Minimalizowanie i maksymalizowanie lub rozwijanie i zwijanie

##### <a name="sequence"></a>Sequence

- Sekwencja pokazu slajdów

- Przerzucanie obrazów

##### <a name="time"></a>Godzina

- Pokazywanie zmian w czasie, czasie i emisji ekranu

- Przenoszenie do kosza, cofanie i ponowne przenoszenie

- Przywracanie stanu historycznego

#### <a name="attract-attention"></a>Przyciąganie uwagi
Jeśli celem jest zwrócenie uwagi użytkownika na jeden element z kilku lub powiadomienie użytkownika o zaktualizowanych informacjach, animacja może być odpowiednia. Na przykład strona startowa aplikacji może zawierać przycisk Wprowadzenie, który wysuwa się na miejsce po ładowaniu strony.

Z reguły ostatni ruchomy element na ekranie przyciąga uwagę użytkownika.  W serii animowanych elementów uwagę użytkownika będzie obserwować ostatni przenoszący się obiekt.

##### <a name="alert"></a>Alerty

- Ostrzeganie użytkownika, zwracanie uwagi, pokazywanie postępu

- Pokaż, że coś jest wykonywane prawidłowo lub niepoprawnie albo pokaż postęp lub zmiany postępu

- Monituj użytkowników podczas zadania, na przykład znajdowanie dodatkowych informacji w trybie online lub uczenie się o bieżącym zadaniu

##### <a name="notifications"></a>Powiadomienia

- Alert użytkownika o warunku błędu

- Przerwij użytkownikom, aby sprawdzić, czy chce uczestniczyć w czymś innym

- Informuje użytkownika, że proces został zakończony lub zmieniony, na przykład po zakończeniu pobierania.

#### <a name="simulate"></a>Symulować
Ta kategoria obejmuje fizyczność i wymiarowość.

- Zilustruj, skąd pochodzą obiekty lub dokąd trafiają

- Rozwijanie i zwijanie lub otwieranie i zamykanie

- Przesuwanie, przewijanie i zmienianie strony

- Układanie na stosie i porządek na Z

- Karuzela i accordion

- Przerzucanie i obracanie interfejsu użytkownika

#### <a name="response-and-progress-indicators"></a>Wskaźniki odpowiedzi i postępu
Wskaźniki postępu mają kilka kluczowych zalet:

- Zarówno wskaźnik postępu determinowania, jak i nieokreślony, ponownie uacyjniają użytkownika, że system nie ulega awarii i pracuje nad problemem.

- Wskaźniki deterministyczne zapewniają użytkownikowi poczucie postępu akcji, a także wrażenie zbliżania się do końca.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Wzorce animacji

### <a name="overview"></a>Omówienie
Animacje w Visual Studio mają służyć określonej funkcji bez zakłócania produktywności użytkowników. Ogólnie rzecz biorąc, animacje Visual Studio powinny być:

- Małe i dyskretne

- Naturalna i realistyczna

- Subtelne i subduowane

- Szybkie i wydajne

- Bez przeszkód

Na tej ilustracji przedstawiono style animacji zalecane dla Visual Studio. Nie są najczęściej używane żadne animacje ani subtelne animacje, takie jak zanikanie/zanikanie. Istnieje ograniczone zastosowanie animacji ruchu, takich jak rozwijanie i kontrakt, zmiana położenia X i Y oraz obrót.

![Zalecane style animacji dla Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Zalecane style animacji dla Visual Studio

#### <a name="appear-and-disappear"></a>Pojawianie się i znikanie
Dzięki temu wzorcowi element jest zmieniany z widocznego na out-of-view i back bez animacji przejścia.

![Animacja pojawiania się i znikania](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animacja pojawiania się i znikania

##### <a name="correct-usage"></a>Poprawne użycie
Nowe elementy interfejsu użytkownika, które muszą natychmiast pojawiać się lub znikać, aby użytkownik nie był rozpraszany ani nie przeszkadzał. Ponadto wolno przesuwane animacje mogą być postrzegane jako przeciąganie wydajności, które nie wystąpią w stylu "pojawianie się i znikanie".

##### <a name="incorrect-usage"></a>Nieprawidłowe użycie
Przypadki, w których interfejs użytkownika pojawia się tak nagle, nie ma pojęcia, co się stało, a dodanie animacji pomoże w zrozumieniu kontekstowym.

##### <a name="animation-properties"></a>Właściwości animacji
Opóźnienie czasu zazwyczaj wynosi zero sekund.

##### <a name="examples"></a>Przykłady
- Automatyczne ukrywanie okien narzędzi

- Interfejs użytkownika edytora z aktywowaną klawiaturą, na przykład Funkcja IntelliSense i pomoc dla parametrów

- Rozwijanie i zwijanie regionów kodu

#### <a name="fade-in-and-fade-out"></a>Zanikanie i zanikanie
W przypadku tego wzorca element interfejsu użytkownika przechodzi z niewidocznej (0% przezrębności) do widocznej (100% przezłodzeń) lub odwrotnie.

![Animacja zanikanie i zanikanie](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202–c_FadeInFadeOut")<br />Animacja zanikanie i zanikanie

##### <a name="correct-usage"></a>Poprawne użycie
Jest to najczęściej zalecana animacja interfejsu użytkownika. Jest to subtelny efekt, który zwiększa zainteresowanie bez przerywania przepływu. W niektórych przypadkach użytkownik może nawet nie zdawać sobie sprawy, że istnieje animacja, która postrzega płynny i przepływjący system interfejsu użytkownika.

##### <a name="animation-properties"></a>Właściwości animacji

- Początkowy przejaście: 0% dla zanikanie, 100% dla zanikanie

- Końcowa przejalność: 100% dla zanikanie, 0% dla zanikanie

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl easingu: Sinus InOut

##### <a name="examples"></a>Przykłady

- Automatyczne ukrywanie okien narzędzi

- Otwieranie i zamykanie menu

- Przejścia kart tła i pierwszego planu

#### <a name="color-blend-from-a-to-b"></a>Połączenie kolorów od A do B
W przypadku tego wzorca element interfejsu użytkownika zmienia kolor A na B.

![Animacja mieszania kolorów](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animacja mieszania kolorów

##### <a name="correct-usage"></a>Poprawne użycie
Animowane przejście, gdy element interfejsu użytkownika zmienia kolor z jednego kontekstu lub stanu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Kolor początkowy: specyficzny dla interfejsu użytkownika

- Kolor końcowy: specyficzny dla interfejsu użytkownika

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl easingu: Sinus InOut

##### <a name="examples"></a>Przykłady

- Przejścia stanu okna dokumentu (aktywne, ostatnie aktywne i nieaktywne)

- Przejścia stanu okna narzędzi (skoncentrowane i nieekskoncentrowane)

#### <a name="expand-and-contract"></a>Rozwijanie i kontrakt
W tym wzorcu element interfejsu użytkownika rozwija się w kierunku X, Y lub w obu kierunkach.

![Animacja rozwijania i kontraktu](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Animacja rozwijania i kontraktu

##### <a name="correct-usage"></a>Poprawne użycie
Animowane przejście, gdy element interfejsu użytkownika zmienia rozmiar z jednego kontekstu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- X skala: % lub określony wymiar (w pikselach)

- Skala Y: % lub określony wymiar (w pikselach)

- Pozycja zakotwiczenia: zazwyczaj w lewym górnym rogu (w językach od lewej do prawej) lub w prawym górnym rogu (w językach od prawej do lewej)

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

##### <a name="examples"></a>Przykłady

- Rozwijanie i zwijanie panelu Eksploratora architektury

- Visual Studio 2017 r. Rozwijanie i zwijanie elementu strony startowej

#### <a name="x-y-position-change"></a>Zmiana położenia X-Y
W przypadku tego wzorca element interfejsu użytkownika zmienia swoją pozycję X lub Y albo obie te pozycje.

![Animacja zmiany położenia X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animacja zmiany położenia X-Y

##### <a name="correct-usage"></a>Poprawne użycie
Animowane przejście, gdy element interfejsu użytkownika zmienia położenie z jednego kontekstu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Pozycja początkowa X i Y: specyficzna dla interfejsu użytkownika

- Końcowe położenie X i Y: specyficzne dla interfejsu użytkownika

- Ścieżka ruchu: brak

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl easingu: Sinus InOut

##### <a name="example"></a>Przykład
Zmiana kolejności kart

#### <a name="rotate"></a>Obrót
W przypadku tego wzorca element interfejsu użytkownika jest obracany.

![Animacja rotacji elementu interfejsu użytkownika](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animacja rotacji elementu interfejsu użytkownika

##### <a name="correct-usage"></a>Poprawne użycie
Tylko dla nieokreślony wskaźnik postępu wirowania.

##### <a name="animation-properties"></a>Właściwości animacji

- Stopień rotacji: 360

- Środek obrotu: środek obiektu

- Czas trwania: continuous

##### <a name="example"></a>Przykład
Nieokreślony wskaźnik postępu (obracanie)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Typowe akcje interfejsu użytkownika powłoki i zalecane animacje

#### <a name="tab-open"></a>Otwieranie karty
![Animacja otwierania karty](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202–h_TabOpen")<br />Animacja otwierania karty

- Styl: wyświetlane

- Czas trwania: zero sekund

#### <a name="tab-close"></a>Zamknij kartę
![Animacja zamykania karty](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202–i_TabClose")<br />Animacja zamykania karty

- Styl: Zmiana położenia X

- Czas trwania: 200 milisekund

#### <a name="tab-reorder"></a>Zmiana kolejności kart
![Animacja zmiany kolejności tabuł w Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animacja zmiany kolejności kart

- Styl: Zmiana położenia X

- Czas trwania: 200 milisekund

#### <a name="close-floating-document"></a>Zamykanie dokumentu zmiennoprzecinkowego
![Animacja zamykania dokumentów zmiennoprzecinkowych](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202–k_CloseFloatingDocument")<br />Animacja zamykania dokumentów zmiennoprzecinkowych

- Styl: wyświetlane

- Czas trwania: 200 milisekund

#### <a name="window-state-transition"></a>Przejście stanu okna
![Animacja przejścia stanu okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animacja przejścia stanu okna

- Styl: aby zapewnić spójność z innymi oknami, niech bieżący system operacyjny zdefiniuje animację zamknięcia dokumentu.

- Czas trwania: 200 milisekund

#### <a name="menu-open"></a>Otwarte menu
![Animacja otwierania menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animacja otwierania menu

- Styl: zanikanie

- Czas trwania: 200 milisekund

#### <a name="menu-close"></a>Zamykanie menu
![Animacja zamykania menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animacja zamykania menu

- Styl: zanikanie

- Czas trwania: 200 milisekund

#### <a name="auto-hide-tool-window-reveal"></a>Automatyczne ukrywanie okna narzędzia — ujawnianie
![Okno narzędzi automatycznego ukrywania odsłania animację](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Okno narzędzi automatycznego ukrywania odsłania animację

- Styl: wyświetlane

- Czas trwania: zero sekund
