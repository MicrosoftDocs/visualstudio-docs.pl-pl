---
title: Animacje dla programu Visual Studio | Microsoft Docs
description: Dowiedz się więcej o regułach, które pomagają zapewnić spójne i przyjazne dla użytkownika style animacji w środowisku IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85ebfd4f396a5ae0e04ff5e7cc0f52bba1825ec5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060266"
---
# <a name="animations-for-visual-studio"></a>Animacje dla programu Visual Studio
## <a name="animation-fundamentals"></a>Podstawy animacji

### <a name="animation-best-practices-in-visual-studio"></a>Najlepsze rozwiązania w zakresie animacji w programie Visual Studio
Postępuj zgodnie z tymi regułami, aby zapewnić spójne i przyjazne dla użytkownika style animacji w środowisku IDE programu Visual Studio.

- **Być selektywne.** Ogranicz animacje do tych, które obsługują określone cele.

- **Czas i szybkość są ważne** , aby upewnić się, że przejścia są szybkie i naturalne:

  - Ukończ przejścia animowane w jednej połowie sekundy (500 milisekund).

  - Animacje, które mogą wystąpić często, muszą być szybko wystarczające, aby nie przerywać przepływu pracy użytkownika. Obejrzyj animację w pętli i Dostosuj czas do momentu, gdy będzie to możliwe.

  - Animacje nie powinny być tak szybkie ani jarring, że trudno jest zrozumieć, ale nie tak długo, że cierpliwy do zakończenia przejścia.

  - Użyj chronometrażu zmiennej, aby wyróżnić znaczenie. Na przykład podczas przechodzenia przez sekwencję elementów na diagramie klasy szybkość przejść między elementami, a następnie spowalniają koncentrację na ważnych elementach.

- **Używaj stopniowego napięcia nieliniowego** z jednego stanu do innego, co daje sens Calm i naturalny ruch.

- Jeśli to możliwe, należy **użyć delikatnej animacji przy aktywowaniu** , aby wskazać elementy interaktywne pod myszą.

- Jeśli korzystasz z wieloznacznej animacji w funkcjach, **Określ sposób, aby wyłączać je** lokalnie (dla wszystkich funkcji) jako opcję w oknie dialogowym **Narzędzia > opcje** .

- **Tylko jedną animację należy wykonać jednocześnie** i przekazać tylko jedną część informacji. Więcej niż jeden obiekt przenoszony lub próba przekazania wielu elementów może być mylący.

- **Subtlety jest ważna.** W większości przypadków animacja nie musi zażądać uwagi użytkownika w celu jej przeprowadzenia. Subtelne zmiany w czasie, sekwencjonowaniu i zachowaniu mogą znacząco wpływać na percepcję i mogą powodować różnice między skuteczną i nieskuteczną animacją.

- W przypadku używania animacji do narysowania uwagi do czegoś należy **się upewnić, że nastąpi przerwanie** uczenia się użytkownika.

- **Podczas wyświetlania postępu lub stanu** przez animację:

  - Zatrzymaj wyświetlanie ruchu postępu, gdy podstawowy proces nie zostanie przetworzony.

  - Odróżnienie nieokreślonych procesów od procesów odkończenia.

  - Upewnij się, że animacja ma zidentyfikowane Stany ukończenia i niepowodzenia.

  - Zminimalizuj użycie animacji efektów, które pokazują stan i upewnij się, że mają rzeczywiste wartości, dostarczając dodatkowe informacje o rzeczywistym użyciu. Przykłady obejmują przejściowe zmiany stanu i sytuacje awaryjne

#### <a name="animation-donts"></a>Animacja:

- Nie używaj małych przesunięć (przenoszenia w niewielkim zakresie). Preferuj zanikanie i zmiany nad przesuwaniem obiektów.

- Nie używaj animacji, które są wykonywane na dużym obszarze ekranu. Bez względu na rozmiar ten styl animacji ma rozpraszać użytkownika.

- Nie używaj animacji, które nie są powiązane z obiektem, na którym użytkownik jest obecnie ukierunkowany lub z którym się nie współdziała.

- Nie używaj animacji, które wymagają interakcji z użytkownikiem, aby zresetować stan, takich jak wymuszanie reakcji użytkownika na migające powiadomienie w celu zatrzymania jego migania. Korzystanie z nich w dowolny sposób powinno być wystarczające, aby je odrzucić.

Aby uzyskać więcej informacji na temat aplikacji dla tych najlepszych rozwiązań, zobacz [wzorce animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metryki animacji

- System powinien w sposób widoczny reagować na gesty użytkownika w mniej niż 10 milisekund.

- Animowane przejścia nie powinny trwać dłużej niż 500 milisekund.

- Jednym ze sposobów, aby skompensować przejścia, które wymagają dłuższego czasu, jest oddzielenie go na dwie części. Na przykład pierwsza część animacji może być pustym kontenerem zawartości (do 500 milisekund), po którym następuje zanikanie zawartości do kontenera (do 500 ms).

- W przypadku czasów ładowania, które można obliczyć, preferowany jest wskaźnik postępu wyznaczników (procentowy wskaźnik postępu).

- W przypadku czasów ładowania, których nie można obliczyć, jest odpowiedni wskaźnik zajętości, taki jak kursor lub osadzony symbol obracającej animacji (wskaźnik ładowania lub pracy).

### <a name="animation-as-communicator"></a>Animacja jako program Communicator
W interfejsie użytkownika programu Visual Studio funkcja animacji działa tylko jako narzędzie komunikacyjne.  Jest on używany do komunikowania się z różnymi informacjami, takimi jak strukturalne zmiany w interfejsie użytkownika (na przykład po otwarciu lub zamknięciu menu). Animacja może pomóc w wizualizowaniu zależnych od czasu zachowań systemów złożonych, takich jak wizualizacja postępu instalacji. Animacje mogą również służyć do przyciągania uwagi do alertów i powiadomień.

 Animacje interfejsu użytkownika zwykle działają na cztery sposoby: Wizualizuj, Przyciągaj uwagę, Symuluj i czasy reakcji/wskaźniki postępu.

#### <a name="visualize"></a>Wizualizacja
Animacja może wyróżnić trójwymiarowy charakter obiektów i ułatwić użytkownikom wizualizację swojej struktury przestrzennej. Aby osiągnąć ten efekt, animacja może być konieczna, aby obrócić obiekt w pełnym okręgu, wolno przełączać go do tyłu i do przodu, lub znacznie zwiększyć jego rozmiar, aby podkreślić lub skupić.

Chociaż obiekty trójwymiarowe mogą być przenoszone przy użyciu kontrolki użytkownika, Projektant powinien określić z góry (programowo lub ręcznie) sposób, w jaki najlepiej animować ruch, który zapewnia optymalne zrozumienie obiektu. Tę animację programową można następnie aktywować przez użytkownika, umieszczając kursor nad obiektem, a ruchy sterowane przez użytkownika wymagają od użytkownika zrozumienia sposobu manipulowania obiektem. Ograniczyć przenoszenie do pojedynczej osi lub orientacji w danym momencie. skalowanie, obracanie lub tłumaczenie, ale nie rób więcej niż jeden jednocześnie.

Kategoria Wizualizacja zawiera aspekty danych, relacji, stanu, struktury, sekwencji i czasu.

##### <a name="data"></a>Dane
Ilustruj informacje złożone i zmienne:

- Poruszanie się za poorednictwem wizualizacji informacji, takich jak wykresy i wykresy

- Krokowe przechodzenie przez sekwencję, przewodnik i stronicowanie

- Wywoływanie szczegółów, wskazywanie i wyróżnianie konkretnych informacji

- Szczegóły nakładania i dodatkowe informacje na temat elementu z fokusem

- Przepłynnowanie między strukturalną lub reprezentacją organizacyjną a inną

- Przedstawianie zmian w czasie przy użyciu suwaków czasu, kół biegu i-wahadłowych oraz urządzeń do sterowania transportem (Play, stop i PAUSE)

##### <a name="relationships"></a>Relacje

- Ilustruje, jak elementy są powiązane ze sobą lub które elementy odnoszą się do danego elementu

- Pokaż hierarchie i relacje nadrzędny-podrzędny lub równorzędny

- Jeden element jest duplikowany innym

- Jeden element minimalizuje do innego elementu

- Jeden element jest powiązany z innym

##### <a name="state"></a>Stan

- Aktualizacje zawartości

- Fokus i wybór użytkownika

- Postęp

- błędy

##### <a name="structure"></a>Struktura

- Przestawianie struktury na jednym węźle

- Zmiana orientacji

- Minimalizuj i Maksymalizuj lub Rozwijaj i zwijaj

##### <a name="sequence"></a>Sequence

- Sekwencja slajdów

- Przerzucanie obrazów

##### <a name="time"></a>Godzina

- Pokaż zmiany w czasie, przekroczeniu czasu i zrzut ekranu przedstawiający

- Przenieś do kosza, Cofnij i wykonaj ponownie

- Przywróć stan historyczny

#### <a name="attract-attention"></a>Zwróć uwagę
Jeśli celem jest narysowanie uwagi użytkownika do pojedynczego elementu z kilku lub aby ostrzec użytkownika o zaktualizowanych informacjach, może być konieczne przeprowadzenie animacji. Na przykład na stronie startowej aplikacji może być używany przycisk Wprowadzenie, który ma slajdy po załadowaniu strony.

Jako reguła, ostatni przenoszony element na ekranie przyciąga uwagę użytkownika.  W serii animowanych elementów Uwaga użytkownika będzie podążać za ostatnim przenoszonym obiektem.

##### <a name="alert"></a>Alerty

- Zgłoś alert, uzyskaj uwagę, Pokaż postęp

- Pokazuje, że coś jest wykonywane prawidłowo lub nieprawidłowo, lub pokazać postęp lub zmiany postępu

- Monituj użytkowników w trakcie wykonywania zadania, takich jak Znajdowanie dodatkowych informacji online lub uczenie się o bieżącym zadaniu

##### <a name="notifications"></a>Powiadomienia

- Zgłoś alert dotyczący błędu

- Przerwij użytkownikowi, aby zobaczyć, czy chcesz wziąć udział w coś innego

- Poinformuj użytkownika o tym, że proces został ukończony lub zmieniony, tak jak po zakończeniu pobierania.

#### <a name="simulate"></a>Symulowanie
Ta kategoria obejmuje fizyczną i zwymiarowaność.

- Ilustruje miejsce, z którego pochodzą obiekty lub do których się odnoszą

- Rozwiń i Zwiń lub Otwórz i Zamknij

- Przesuwanie, przewijanie i obracanie stron

- Układanie i porządkowanie z

- Karuzela i zgodnie z przepisami

- Przerzucanie i obracanie interfejsu użytkownika

#### <a name="response-and-progress-indicators"></a>Wskaźniki odpowiedzi i postępu
Wskaźniki postępu mają kilka istotnych zalet:

- Zarówno wskaźniki Nieprzerwania, jak i nieokreślony postęp zapewnią użytkownikowi, że system nie uległ awarii i pracuje nad problemem.

- Wskaźniki dekończące dają użytkownikowi informacje o tym, jak daleko jest postęp, a także o tym, jak to się robi.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Wzorce animacji

### <a name="overview"></a>Omówienie
Animacje w programie Visual Studio mają na celu zapełnienie określonej funkcji bez zakłócania produktywności użytkowników. Ogólnie rzecz biorąc, animacje w programie Visual Studio powinny być następujące:

- Małe i niezauważalne

- Naturalne i realistyczne

- Delikatne i Subdued

- Szybka i wydajna

- Swobodny, nie hurried

Na tej ilustracji przedstawiono style animacji, które zalecamy dla programu Visual Studio. W przypadku, gdy nie ma animacji ani subtelnych animacji, takich jak zanikanie/zanikanie w dół, są najczęściej używane. Istnieje ograniczone zastosowanie animacji przenoszenia, takich jak rozszerzanie i kontrakt, zmiana pozycji X i Y oraz obracanie.

![Zalecane style animacji dla programu Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 — a_VSAnimStyles")<br />Zalecane style animacji dla programu Visual Studio

#### <a name="appear-and-disappear"></a>Pojawia się i znika
Ten wzorzec powoduje, że element zmienia się z widoczne na out-of-View i z powrotem bez animacji przejścia.

![Animacja wyświetlana i znika](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 — b_AppearAndDisappear")<br />Animacja wyświetlana i znika

##### <a name="correct-usage"></a>Poprawne użycie
Nowe elementy interfejsu użytkownika, które muszą być natychmiast wyświetlane lub znikane, aby użytkownik nie był rozpraszany ani nie zachodzi. Ponadto animacje o powolnej przenoszeniu mogą być postrzegane jako przeciągnięcie do wydajności, co nie będzie miało stylu wyświetlania i znikania.

##### <a name="incorrect-usage"></a>Nieprawidłowe użycie
Przypadki, w których interfejs użytkownika jest wyświetlany, dlatego użytkownik nie ma pomysłu, co się stało, a dodanie animacji pomoże Ci zrozumieć kontekst.

##### <a name="animation-properties"></a>Właściwości animacji
Czas opóźnienia jest zwykle równy zero sekund.

##### <a name="examples"></a>Przykłady
- Autoukrywanie okien narzędzi

- Interfejs użytkownika edytora aktywowanego przez klawiaturę, na przykład IntelliSense i pomoc dotyczącą parametrów

- Rozwijanie i zwijanie regionów kodu

#### <a name="fade-in-and-fade-out"></a>Zanikanie i stopniowe Rozjaśnianie
Przy użyciu tego wzorca element interfejsu użytkownika przechodzi z niewidoczne (0% nieprzezroczystości) do widocznych (100% krycia) lub odwrotnie.

![Animacja zanikania i zanikania](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 — c_FadeInFadeOut")<br />Animacja zanikania i zanikania

##### <a name="correct-usage"></a>Poprawne użycie
Jest to najczęściej zalecaną animację interfejsu użytkownika. Jest to delikatny efekt, który dodaje zainteresowania bez zakłócania przepływu. W niektórych przypadkach użytkownik może nie pamiętać, że istnieje animacja, postrzegający płynny i przepływny system interfejsu użytkownika.

##### <a name="animation-properties"></a>Właściwości animacji

- Nieprzezroczystość początkowa: 0% dla zanikania, 100% dla stopniowego zanikania

- Końcowa nieprzezroczystość: 100% dla zanikania, 0% do zanikania w poziomie

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl napięcia: sinus InOut

##### <a name="examples"></a>Przykłady

- Autoukrywanie okien narzędzi

- Menu Otwórz i Zamknij

- Przejścia do kart tła i pierwszego planu

#### <a name="color-blend-from-a-to-b"></a>Kolor Blend od A do B
Przy użyciu tego wzorca element UI zmienia się z Color A na Color B.

![Animacja mieszania koloru](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 — d_ColorBlend")<br />Animacja mieszania koloru

##### <a name="correct-usage"></a>Poprawne użycie
Jako animowane przejście, gdy element interfejsu użytkownika zmienia kolor z jednego kontekstu lub stanu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Kolor początkowy: specyficzny dla interfejsu użytkownika

- Kolor końcowy: specyficzny dla interfejsu użytkownika

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl napięcia: sinus InOut

##### <a name="examples"></a>Przykłady

- Przejścia stanu okna dokumentu (aktywne, ostatnie aktywne i nieaktywne)

- Przejścia stanu okna narzędzi (skoncentrowany i nieskoncentrowany)

#### <a name="expand-and-contract"></a>Rozwiń i Zwiń kontrakt
W tym wzorcu element interfejsu użytkownika rozwija się w obu kierunkach X, Y lub obu.

![Animacja rozwijania i kontraktu](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 — e_ExpandContract")<br />Animacja rozwijania i kontraktu

##### <a name="correct-usage"></a>Poprawne użycie
Jako animowane przejście, gdy element interfejsu użytkownika zmienia rozmiar z jednego kontekstu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Skalowanie X:% lub określony wymiar (w pikselach)

- Skalowanie Y:% lub określony wymiar (w pikselach)

- Położenie zakotwiczenia: zwykle w lewym górnym rogu (w przypadku języków od lewej do prawej) lub prawego górnego (w przypadku języków pisanych od prawej do lewej)

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

##### <a name="examples"></a>Przykłady

- Panel Eksplorator architektury rozwiń i Zwiń

- Rozwijanie i zwijanie elementu strony początkowej programu Visual Studio 2017

#### <a name="x-y-position-change"></a>Zmiana pozycji X-Y
Przy użyciu tego wzorca element interfejsu użytkownika zmienia jego położenie X lub Y lub oba te elementy.

![Animacja zmiany położenia X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 — f_XYPositionChange")<br />Animacja zmiany położenia X-Y

##### <a name="correct-usage"></a>Poprawne użycie
Jako animowane przejście, gdy element interfejsu użytkownika zmienia położenie z jednego kontekstu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Początkowe położenie X i Y: specyficzne dla interfejsu użytkownika

- Końcowe położenie osi X i Y: specyficzne dla interfejsu użytkownika

- Ścieżka ruchu: brak

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

- Styl napięcia: sinus InOut

##### <a name="example"></a>Przykład
Zmiana kolejności tabulacji

#### <a name="rotate"></a>Obrót
Przy użyciu tego wzorca element interfejsu użytkownika obraca się.

![Animacja obrotu elementu interfejsu użytkownika](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 — g_Rotate")<br />Animacja obrotu elementu interfejsu użytkownika

##### <a name="correct-usage"></a>Poprawne użycie
Tylko dla wskaźnika nieokreślonych wirujących postępów.

##### <a name="animation-properties"></a>Właściwości animacji

- Stopień obrotu: 360

- Centrum rotacji: środek obiektu

- Czas trwania: ciągły

##### <a name="example"></a>Przykład
Wskaźnik nieokreślonego postępu (wirowanie)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Typowe akcje interfejsu użytkownika powłoki i zalecane animacje

#### <a name="tab-open"></a>Otwarta karta
![Animacja otwierająca kartę](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 — h_TabOpen")<br />Animacja otwierająca kartę

- Styl: pojawia się

- Czas trwania: zero sekund

#### <a name="tab-close"></a>Zamknij kartę
![Animacja zamknięcia karty](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 — i_TabClose")<br />Animacja zamknięcia karty

- Styl: zmiana położenia X

- Czas trwania: 200 MS

#### <a name="tab-reorder"></a>Zmiana kolejności tabulacji
![Animacja zmiany kolejności tabulacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 — j_TabReorder")<br />Animacja zmiany kolejności tabulacji

- Styl: zmiana położenia X

- Czas trwania: 200 MS

#### <a name="close-floating-document"></a>Zamknij swobodny dokument
![Zamknij animację dokumentu zmiennoprzecinkowego](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 — k_CloseFloatingDocument")<br />Zamknij animację dokumentu zmiennoprzecinkowego

- Styl: pojawia się

- Czas trwania: 200 MS

#### <a name="window-state-transition"></a>Przejście stanu okna
![Animacja przejścia stanu okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 — l_WindowStateTransition")<br />Animacja przejścia stanu okna

- Styl: aby zapewnić spójność z innymi oknami, zezwól bieżącemu systemowi operacyjnemu na definiowanie animacji zamykania dokumentu.

- Czas trwania: 200 MS

#### <a name="menu-open"></a>Menu Otwórz
![Menu Otwórz animację](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 — m_MenuOpen")<br />Menu Otwórz animację

- Styl: zanikanie

- Czas trwania: 200 MS

#### <a name="menu-close"></a>Zamknij menu
![Animacja zamykania menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 — n_MenuClose")<br />Animacja zamykania menu

- Styl: zanikanie w dół

- Czas trwania: 200 MS

#### <a name="auto-hide-tool-window-reveal"></a>Pokaż Autoukrywanie okna narzędzi
![Autoukrywanie okna narzędzi, Odsłoń animację](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 — o_AutoHideToolWindowReveal")<br />Autoukrywanie okna narzędzi, Odsłoń animację

- Styl: pojawia się

- Czas trwania: zero sekund
