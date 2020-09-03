---
title: Animacje
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825358"
---
# <a name="animations-for-visual-studio"></a>Animacje dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Podstawy animacji

### <a name="animation-best-practices-in-visual-studio"></a>Najlepsze rozwiązania w zakresie animacji w programie Visual Studio
 Postępuj zgodnie z tymi regułami, aby zapewnić spójne i przyjazne dla użytkownika style animacji w środowisku IDE programu Visual Studio.

- **Być selektywne.** Ogranicz animacje do tych, które obsługują określone cele.

- **Czas i szybkość są ważne** , aby upewnić się, że przejścia są szybkie i naturalne:

  - Ukończ przejścia animowane w jednej połowie sekundy (500 milisekund).

  - Animacje, które mogą wystąpić często, muszą być szybko wystarczające, aby nie przerywać przepływu pracy użytkownika.

  - Animacje nie powinny być tak szybkie ani jarring, że trudno jest zrozumieć, ale nie tak długo, że cierpliwy do zakończenia przejścia.

  - Użyj chronometrażu zmiennej, aby wyróżnić znaczenie. Na przykład podczas przechodzenia przez sekwencję elementów na diagramie klasy szybkość przejść między elementami, a następnie spowalniają koncentrację na ważnych elementach.

- **Używaj stopniowego, nieliniowej krzywej napięcia** z jednego stanu do innego, co daje sens Calm i naturalny ruch

- Jeśli to możliwe, należy **użyć delikatnej animacji przy aktywowaniu** , aby wskazać elementy interaktywne pod myszą.

- Jeśli często używasz animacji w funkcjach, **Zapewnij użytkownikom możliwość ich wyłączenia** lokalnie (dla wszystkich funkcji) jako opcję w oknie dialogowym **Narzędzia > opcje** .

- **Tylko jedną animację należy wykonać jednocześnie** i przekazać tylko jedną część informacji.

- **Subtlety jest ważna.** W większości przypadków animacje nie muszą wymagać od użytkownika uwagi do ich przeznaczenia. Delikatne zmiany czasu, sekwencjonowania i zachowania mogą znacząco wpływać na percepcję i mogą zwiększyć różnicę między skuteczną i nieskuteczną animacją.

- W przypadku używania animacji do narysowania uwagi na coś należy **się upewnić, że nie przerywa**pouczenia się użytkownika.

- **Podczas wyświetlania postępu lub stanu** przez animację:

  - Zatrzymaj wyświetlanie ruchu postępu, gdy podstawowy proces nie zostanie przetworzony.

  - Odróżnienie nieokreślonych procesów od procesów odkończenia.

  - Upewnij się, że animacja ma zidentyfikowane Stany ukończenia i niepowodzenia.

  - Zminimalizuj użycie animacji efektów, które pokazują stan i upewnij się, że mają rzeczywiste wartości, dostarczając dodatkowe informacje o rzeczywistym użyciu. Przykłady obejmują przejściowe zmiany stanu i sytuacje awaryjne

#### <a name="do-not"></a>Nie:

- Używaj małych przesunięć (przenoszenia w niewielkim rozmiarze), wywołując zanikanie i zmiany w przypadku przenoszenia obiektów.

- Używaj animacji, które odbywają się na dużym obszarze ekranu. Bez względu na rozmiar ten styl animacji ma rozpraszać użytkownika.

- Używaj animacji, które nie odnoszą się do obiektu, w którym użytkownik jest obecnie ukierunkowany, lub z którymi się komunikują.

- Użyj animacji, które wymagają interakcji z użytkownikiem w celu zresetowania stanu, na przykład wymuszenia reakcji użytkownika na migające powiadomienie, aby zatrzymać jego miganie. Korzystanie z nich w dowolny sposób powinno być wystarczające, aby je odrzucić.

  Aby uzyskać więcej informacji na temat aplikacji dla tych najlepszych rozwiązań, zobacz [wzorce animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metryki animacji

- System powinien w sposób widoczny reagować na gesty użytkownika w mniej niż 10 milisekund.

- Animowane przejścia nie powinny trwać dłużej niż 500 milisekund.

- Jednym ze sposobów, aby skompensować przejścia, które wymagają dłuższego czasu, jest oddzielenie go na dwie części: na przykład pierwsza część animacji może być pustym kontenerem zawartości (do 500 milisekund), po którym następuje zanikanie zawartości do kontenera (do 500 ms).

- W przypadku czasów ładowania, które można obliczyć, preferowany jest wskaźnik postępu wyznaczników (procentowy wskaźnik postępu).

- W przypadku czasów ładowania, których nie można obliczyć, jest odpowiedni wskaźnik zajętości, taki jak kursor lub osadzona Poprzednia animacja (wskaźnik ładowania lub pracy).

### <a name="animation-as-communicator"></a>Animacja jako program Communicator
 W interfejsie użytkownika programu Visual Studio funkcja animacji działa tylko jako narzędzie komunikacyjne.  Służy do komunikowania się z różnymi informacjami, takimi jak zmiany strukturalne w interfejsie użytkownika; na przykład po otwarciu lub zamknięciu menu. Animacja może pomóc w wizualizowaniu zależnych od czasu zachowań systemów złożonych, takich jak wizualizacja postępu instalacji lub użycie do przyciągnięcia uwagi do alertów i powiadomień.

 Animacje interfejsu użytkownika zwykle działają na cztery sposoby: wizualizowanie, przyciąganie uwagi, symulowanie i wskazywanie czasów odpowiedzi/postępu.

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

- Reprezentuje zmiany w czasie, korzystając z suwaków czasu, kół biegu i-wahadłowych oraz urządzeń do sterowania transportem (Play, stop i PAUSE).

##### <a name="relationships"></a>Relacje

- Ilustruje, jak elementy są powiązane ze sobą lub które elementy odnoszą się do danego elementu.

- Pokaż hierarchie i relacje nadrzędny-podrzędny lub równorzędny

- Jeden element jest duplikowany innym

- Jeden element minimalizuje do innego elementu

- Jeden element jest powiązany z innym

##### <a name="state"></a>Stan

- Aktualizacje zawartości.

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
 Jeśli celem jest narysowanie uwagi użytkownika do pojedynczego elementu z kilku lub aby ostrzec użytkownika o zaktualizowanych informacjach, może być konieczne przeprowadzenie animacji. Na przykład na stronie startowej aplikacje może być używany przycisk Wprowadzenie, który ma slajdy po załadowaniu strony.

 Jako reguła, ostatni przenoszony element na ekranie przyciąga uwagę użytkownika.  W serii animowanych elementów Uwaga użytkownika będzie podążać za ostatnim przenoszonym obiektem.

##### <a name="alert"></a>Alerty

- Zgłoś alert, uzyskaj uwagę, Pokaż postęp

- Pokazuje, że coś jest wykonywane prawidłowo lub nieprawidłowo, lub pokazać postęp lub zmiany postępu

- Monituj użytkowników w trakcie wykonywania zadania, takich jak znajdowanie dalszych informacji online lub uczenie się o bieżącym zadaniu

##### <a name="notifications"></a>Powiadomienia

- Zgłoś alert dotyczący błędu

- Przerwij użytkownikowi, aby zobaczyć, czy chcesz wziąć udział w coś innego

- Poinformuj użytkownika o tym, że proces został ukończony lub zmieniony, na przykład po zakończeniu pobierania.

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
 Animacje w programie Visual Studio mają na celu zapełnienie określonej funkcji i nie utrudniają produktywności użytkowników. Ogólne cechy animacji zgodne z uwzględnieniem:

- Małe i niezauważalne

- Naturalne i realistyczne

- Delikatne i Subdued

- Szybka i wydajna

- Swobodny, nie hurried

  Na poniższej ilustracji przedstawiono style animacji zalecane do użycia w programie Visual Studio. W przypadku, gdy nie są używane żadne animacje i delikatnych animacji, takie jak zanikanie/zanikanie w dół. Istnieje ograniczone zastosowanie animacji przenoszenia, takich jak rozszerzanie i kontraktu, zmiana pozycji X i Y oraz obracanie.

  ![Zalecane style animacji dla programu Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 — a_VSAnimStyles")

  **Zalecane style animacji dla programu Visual Studio**

#### <a name="appear-and-disappear"></a>Pojawia się i znika
 Ten wzorzec powoduje, że element zmienia się z widocznego na out-of-View i z powrotem bez animacji przejścia:

 ![Pojawiają się&#47;znikają animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 — b_AppearAndDisappear")

##### <a name="correct-usage"></a>Poprawne użycie
 Nowe elementy interfejsu użytkownika, które muszą być natychmiast wyświetlane lub znikane, aby użytkownik nie był rozpraszany ani nie zachodzi. Ponadto wolne przenoszone animacje mogą być postrzegane jako wydajność przeciągania, która nie będzie miała stylu wyświetlanego i znika.

##### <a name="incorrect-usage"></a>Nieprawidłowe użycie
 Przypadki, w których interfejs użytkownika jest wyświetlany, dlatego użytkownik nie ma pomysłu, co się stało, a dodanie animacji pomoże Ci zrozumieć kontekst.

##### <a name="animation-properties"></a>Właściwości animacji
 Czas opóźnienia jest zwykle równy zero sekund.

##### <a name="examples"></a>Przykłady

- Autoukrywanie okien narzędzi

- Interfejs użytkownika edytora aktywowanego przez klawiaturę, taki jak IntelliSense i pomoc dotycząca parametrów

- Rozwijanie i zwijanie regionów kodu

#### <a name="fade-in-and-fade-out"></a>Zanikanie i stopniowe Rozjaśnianie
 Przy użyciu tego wzorca element interfejsu użytkownika przechodzi z niewidoczne (0% nieprzezroczystości) do widocznych (100% krycia) lub odwrotnie:

 ![Zanikanie&#45;w&#47;zanikanie&#45;animacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 — c_FadeInFadeOut")

##### <a name="correct-usage"></a>Poprawne użycie
 Jest to najczęściej zalecaną animację interfejsu użytkownika. Jest to delikatny efekt, który dodaje zainteresowania bez zakłócania przepływu. W niektórych przypadkach użytkownik może jeszcze nie pamiętać, że istnieje animacja i po prostu postrzega płynny, przepływny system interfejsu użytkownika.

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
 Z tym wzorcem element UI zmienia się z Color A na Color B:

 ![Animacja mieszania kolorów w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 — d_ColorBlend")

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
 Ten wzorzec polega na tym, że element interfejsu użytkownika rozszerza się w osi X, Y lub w obu kierunkach:

 ![Rozwiń animację kontraktu&#47;w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 — e_ExpandContract")

##### <a name="correct-usage"></a>Poprawne użycie
 Jako animowane przejście, gdy element interfejsu użytkownika zmienia rozmiar z jednego kontekstu na inny.

##### <a name="animation-properties"></a>Właściwości animacji

- Skalowanie X:% lub określony wymiar (w pikselach)

- Skalowanie Y:% lub określony wymiar (w pikselach)

- Położenie zakotwiczenia: zwykle w lewym górnym rogu (w przypadku języków od lewej do prawej) lub prawego górnego (w przypadku języków pisanych od prawej do lewej)

- Czas trwania: 200 milisekund autonomicznych, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacji

##### <a name="examples"></a>Przykłady

- Panel Eksplorator architektury rozwiń i Zwiń

- Rozwiń i Zwiń element strony początkowej

#### <a name="x-y-position-change"></a>Zmiana pozycji X-Y
 W tym wzorcu element interfejsu użytkownika zmienia jego pozycję X lub Y, lub obie:

 ![Animacja zmiany położenia X&#47;Y w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 — f_XYPositionChange")

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
 Przy użyciu tego wzorca element interfejsu użytkownika obraca się:

 ![Obróć animację w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 — g_Rotate")

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

- Styl: pojawia się

- Czas trwania: zero sekund

  ![Animacja otwierająca kartę w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 — h_TabOpen")

#### <a name="tab-close"></a>Zamknij kartę

- Styl: zmiana położenia X

- Czas trwania: 200 MS

  ![Animacja zamknięcia karty w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 — i_TabClose")

#### <a name="tab-reorder"></a>Zmiana kolejności tabulacji

- Styl: zmiana położenia X

- Czas trwania: 200 MS

  ![Animacja zmiany kolejności tabulacji w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 — j_TabReorder")

#### <a name="close-floating-document"></a>Zamknij swobodny dokument

- Styl: pojawia się

- Czas trwania: 200 MS

  ![Zamknij animację dokumentu zmiennoprzecinkowego w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 — k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Przejście stanu okna

- Styl: aby zapewnić spójność z innymi oknami, zezwól bieżącemu systemowi operacyjnemu na definiowanie animacji zamykania dokumentu.

- Czas trwania: 200 MS

  ![Animacja przejścia stanu okna w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 — l_WindowStateTransition")

#### <a name="menu-open"></a>Menu Otwórz

- Styl: zanikanie

- Czas trwania: 200 MS

  ![Menu Otwórz animację w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 — m_MenuOpen")

#### <a name="menu-close"></a>Zamknij menu

- Styl: zanikanie w dół

- Czas trwania: 200 MS

  ![Animacja zamykania menu w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 — n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Pokaż Autoukrywanie okna narzędzi

- Styl: pojawia się

- Czas trwania: zero sekund

  ![Auto&#45;Ukryj animację okna narzędzi w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 — o_AutoHideToolWindowReveal")
