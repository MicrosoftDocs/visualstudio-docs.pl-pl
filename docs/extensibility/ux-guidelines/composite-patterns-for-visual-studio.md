---
title: Wzorce złożone dla programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebc8f4f6c17af54f4dfdcfc0d0d05c5da9d2d88b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88114079"
---
# <a name="composite-patterns-for-visual-studio"></a>Wzorce złożone dla programu Visual Studio
Wzorce złożone łączą elementy interakcji i projektu w różnych konfiguracjach. Niektóre z najważniejszych wzorców złożonych w programie Visual Studio w odniesieniu do spójności obejmują:

- [Wizualizacja danych](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfejs użytkownika i wgląd w obiekt](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modele wyboru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Trwałość i zapisywanie ustawień](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Wizualizacja danych

### <a name="overview"></a>Omówienie
 Wykresy to Wizualizacja Metoda agregowania i wizualizacji danych w celu usprawnienia podejmowania decyzji. Mogą one pomóc użytkownikom z dużą ilością danych, ale niewiele znaczenia Zobacz, co jest zamierzenia uwagi i co może wymagać akcji.

 Użytkownik będzie korzystał z wykresu, jeśli spełniony jest dowolny z następujących warunków:

- Czy wykres ułatwi użytkownikom zidentyfikowanie zadań, na których mogą one działać?

- Czy wykres umożliwi użytkownikom prognozowanie konsekwencji potencjalnych zmian?

- Czy wykres będzie pomagać użytkownikom w wykrywaniu trendów i identyfikowaniu wzorców?

- Czy wykres umożliwi użytkownikom podejmowanie lepszych decyzji?

- Czy wykres pomoże odpowiedzieć konkretnym pytaniem, które użytkownicy mogą mieć w danym kontekście?

#### <a name="general-rules-for-charts"></a>Ogólne reguły dla wykresów

- Jasne etykietowanie danych. Ilustracje bez wyjaśnienia są tylko całkiem niewidocznymi obrazami.

- Rozpocznij od zera osi, aby uniknąć pochylenia proporcji. Długość wiersza i rozmiar paska są ważnymi wskaźnikami wizualnymi, aby zrozumieć relacje między punktami danych.

- Twórz wykresy, nie grafiki informacyjne. Grafiki informacyjne to artystyczne przedstawienia danych, a ich głównym celem jest wizualizacja wizualna. Wykresy mogą (i powinny) być atrakcyjne wizualnie, ale pozwalają wypowiadać dane dla siebie.

- Unikaj skeumorphism, grafów pasków, hashmarks kontrastu i innych Grafika informacyjna.

- Nie używaj efektów 3W jako elementów dekoracyjnych. Należy ich używać tylko wtedy, gdy rzeczywiście są one integralną częścią możliwości comprehend informacji.

- Unikaj używania wielu wierszy i wypełnień, ponieważ więcej niż dwa kolory mogą utrudniać odczytywanie i interpretowanie tego typu wykresu.

- Nie należy używać wykresu (ani żadnej ilustracji) jako jedynego sposobu poznania koncepcji lub operowania danymi. Powoduje to problemy dla użytkowników niedowidzących.

- Nie używaj wykresów jako elementów niedozwolonych lub dekoracyjnych na stronie. Innymi słowy, jeśli wykres nie dodaje żadnej wartości lub ułatwić użytkownikom rozwiązywanie problemu, nie należy go używać.

### <a name="chart-types"></a>Typy wykresów
 Typy wykresów używanych w programie Visual Studio obejmują wykresy słupkowe, wykresy liniowe, zmodyfikowany wykres kołowy znany jako wykres pierścieniowy lub "wykres pierścieniowy", "osie czasu", wykresy punktowe (zwane także "wykresami klastrów") oraz na wykresach Gantta. Każdy typ wykresu jest przydatny do komunikowania się z innym typem informacji.

### <a name="other-charting-considerations"></a>Inne zagadnienia dotyczące wykresów

#### <a name="color"></a>Kolor
 Istnieje określona paleta kolorów wykresów zdefiniowanych do użycia w programie Visual Studio. Paleta jest dostępna dla głównych typów kolorów, a kolory można rozróżnić nawet wtedy, gdy są używane jako bardzo wąskie fragmenty koloru. Możesz użyć tych kolorów w dowolnej kombinacji dla dowolnego typu wykresu lub grafu w interfejsie użytkownika. Nie musisz używać wszystkich siedmiu kolorów, jeśli nie potrzebujesz wielu różnych kolorów. Te kolory nie zostały zaprojektowane do użycia z żadnymi elementami pierwszego planu, dlatego nie umieszczaj tekstu ani glifów na podstawie tych kolorów. Te odcieni powinny być trwale kodowane i narażone na dostosowanie użytkowników w obszarze **narzędzia > opcje** (zobacz [udostępnianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Spowoduje|Hex|RGB|
|------------|---------|---------|
|![71B252 próbki](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![BF3F00 próbki](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![FCB714 próbki](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![903F8B próbki](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![117AD1 próbki](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17 122 209|
|![79D7F2 próbki](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121 215 242|
|![B5B5B5 próbki](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181 181 181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfejs użytkownika i wgląd w obiekt
 Ta sekcja zawiera kontekst do wglądu, znanego również jako widok wglądu w kod, typ interfejsu użytkownika obiektu, który jest unikatowy dla programu Visual Studio.

### <a name="overview"></a>Omówienie

- Interfejs użytkownika w obiekcie powinien dać użytkownikowi więcej informacji lub interaktywnie bez powiększania od ich głównego zadania.

- Główny wzorzec dla interfejsu użytkownika w programie Visual Studio jest znany jako "informacje w punkcie uwagi".

- Interfejs użytkownika w programie Visual Studio jest wbudowany lub zmiennoprzecinkowy oraz trwały lub przejściowy.

  - Widok wglądu w kod, typ interfejsu użytkownika w programie Visual Studio, jest wbudowany i trwały.

  - CodeLens, typ interfejsu użytkownika w programie Visual Studio, jest zmienny i przejściowy

  Zrozumienie, jak działa fragment kodu lub znalezienie szczegółowych informacji o tym kodzie, często wymaga dewelopera przełączenia kontekstu i przechodzenie do innej zawartości lub innego okna. Te zmiany kontekstu mogą być zakłócone, ponieważ użytkownicy mogą utracić fokus na oryginalnym zadaniu, jeśli opuszczają swoje okno główne. Ponadto uzyskanie oryginalnego kontekstu z powrotem może być trudne, szczególnie jeśli przełączenie systemu Windows spowodowało zaciemnienie oryginalnego kodu przez inny interfejs użytkownika.

  Interfejs użytkownika w obiekcie jest zgodny ze wzorcem o nazwie "informacje w punkcie uwagi". Te komunikaty, okna podręczne i okna dialogowe zapewniają użytkownikom dodatkowe, odpowiednie informacje, które zwiększają wyjaśnienie lub interaktywność bez utraty fokusu na głównym zadaniu. Przykłady interfejsu użytkownika na obiekcie obejmują wyskakujące okienka, które są wyświetlane, gdy użytkownik umieści wskaźnik myszy nad ikoną w obszarze powiadomień, czerwoną literą w nieprawidłowym wyrazie i widok wglądu wprowadzony w Visual Studio 2013.

### <a name="decision-points"></a>Punkty decyzyjne
 W programie Visual Studio istnieje kilka sposobów korzystania z tego wzorca informacji w punkcie uwagi. Wybór właściwego mechanizmu i wdrożenie go w spójny, przewidywalny sposób jest istotny dla ogólnego środowiska. W przeciwnym razie użytkownicy mogą mieć zamylące lub niespójne środowisko, które ogranicza fokus od samej zawartości.

#### <a name="relationships-between-master-and-detail-content"></a>Relacje między zawartością główną i szczegółową
 Informacje w punkcie uwagi są używane do wyświetlania relacji między zawartością, w której użytkownik jest skoncentrowany (zawartość "Master") i dodatkową powiązaną zawartością (zawartość "Szczegóły"). W tym wzorcu zawartość Szczegółowa jest jasno związana z zawartością, z którą użytkownik pracuje, i może być wyświetlana blisko zawartości głównej. Informacje uzupełniające lub informacje, których nie można podsumowywać bez przeciążania zawartości głównej, powinny być zgodne z kolejnymi wzorcami, takimi jak okno narzędzi.

- **Zawsze** Wyświetlaj szczegółową zawartość w pobliżu zawartości głównej.

- **Zawsze** upewnij się, że szczegółowa zawartość nadal umożliwia użytkownikowi pozostawanie skoncentrowanego na zawartości głównej. Często najlepszym sposobem osiągnięcia tego celu jest renderowanie zawartości szczegółowej w sposób zbliżony do zawartości głównej, jak to możliwe. Można to zrobić przez renderowanie szczegółowej zawartości w oknie podręcznym obok zawartości głównej lub przez renderowanie zawartości szczegółowej w tekście poniżej zawartości głównej.

- **Nigdy nie** Używaj informacji w punkcie uwagi, który odbierze użytkownika z głównej zawartości. Jeśli użytkownicy muszą oddzielnie wyświetlić zawartość szczegółową, należy uwidocznić jawną akcję, która umożliwi użytkownikowi wykonanie tej czynności.

#### <a name="design-details"></a>Szczegóły projektu
 Po ustaleniu, że interfejs użytkownika w obiekcie jest właściwym wyborem, istnieją cztery główne zagadnienia dotyczące projektowania:

1. **Trwałość:** czy zawartość powinna być trwała lub przejściowa?
   Czy użytkownicy będą mogli zachować widoczność informacji lub korzystać z niej? Użytkownicy będą mogli szybko skrócić się do informacji, a następnie kontynuować ich główne zadanie?

2. **Typ zawartości:** czy zawartość będzie informacyjna, poddana akcji czy nawigacja?
   Czy użytkownik potrzebuje dodatkowych informacji na temat zawartości głównej? Czy użytkownik musi wykonać zadanie, które ma wpływ na zawartość główną? Czy użytkownik musi być kierowany do innego zasobu?

3. **Typ wskaźnika:** czy wskaźnik otoczenia ma sens?
   Czy informacje są podsumowywane w przydatny sposób i wyświetlane bez przeciążania głównej zawartości?

4. **Gesty:** jakie gesty będą używane do wywoływania i odrzucania interfejsu użytkownika?
   Jak zostanie wystawiona zawartość szczegółowa i wysłana przez użytkownika? Czy jest dostępna wartość przy dodawaniu gestu, takiego jak przypinanie do przełączania między stanami przejściowymi i trwałymi?

   Każdy z tych czterech punktów decyzyjnych będzie miał wpływ na główne składniki interfejsu użytkownika w obiekcie.

### <a name="on-object-ui-components"></a>Składniki interfejsu użytkownika dla obiektów

1. Typ kontenera (prezenter zawartości)

    - Pływa

    - Śródwierszowo

2. Typ zawartości

    - Informacje: dane, które mogą być statyczne lub dynamiczne

    - Akcja: polecenia, które zmieniają zawartość główną

    - Nawigacja: linki, które przeprowadzą użytkownika do innego okna lub aplikacji, na przykład MSDN

3. Gestów

    - Invocation

    - Odrzucenia

    - Przypinanie

    - Inne interakcje

4. Trwałość i model zatwierdzania

    - Administracyjnej

    - Trwałość

    - Automatyczny

    - Na żądanie

5. Wskaźniki otoczenia (opcjonalnie)

    - Kreślenie podkreślenia

    - Ikona tagu inteligentnego

    - Inne wskaźniki otoczenia

#### <a name="container-content-presenter-type"></a>Typ kontenera (prezenter zawartości)
 Dostępne są dwie główne opcje do prezentowania zawartości w punkcie uwagi:

1. **Wbudowane:** prezenter wbudowany, taki jak widok wglądu, który został wprowadzony w edytorze kodu Visual Studio 2013, miejsce na nową zawartość przez przesunięcie istniejącej zawartości.

    - **Preferuj** wbudowane przedpłaty, jeśli oczekujesz, że użytkownicy będą chcieli poświęcać znaczną ilość czasu na odzyskanie lub posługiwanie się zawartością.

    - Jeśli użytkownicy będą mogli skrócić się do aktualnych informacji, należy **unikać** korzystania z nich, a następnie kontynuować ich główne zadania z minimalnym zakłóceniem.

2. **Przestawne:** ruchome prezenter jest umieszczony w pobliżu wybranej zawartości, ale nie zmienia układu istniejącej zawartości. Można zastosować różne strategie, takie jak wyświetlanie ruchomego panelu zawartości na najbliższym dostępnym białym miejscu do wybranego symbolu.

    - **Preferuj** przepływających użytkowników, jeśli oczekujesz, że użytkownicy będą chcieć skrócić się do informacji, które są obecne, a następnie kontynuuj zadania główne z minimalnym zakłóceniem.

    - Jeśli oczekujesz, że użytkownicy będą chcieli poświęcać znaczną ilość czasu na odzyskanie lub posługiwanie się zawartością, należy **unikać** przepływających użytkowników.

#### <a name="content-type"></a>Typ zawartości
 Istnieją trzy główne typy zawartości, które mogą być wyświetlane wewnątrz dowolnego kontenera interfejsu użytkownika w obiekcie. Można wyświetlić dowolną kombinację tych typów informacji. Trzy typy to:

1. **Informacje:** większość kontenerów interfejsu użytkownika dla obiektów będzie wyświetlać pewien rodzaj zawartości informacyjnej. Zawartość może reprezentować informacje o stanie obecnym środowiska lub może reprezentować informacje o potencjalnym stanie środowiska. Na przykład może służyć do wyświetlania efektu określonego polecenia, takiego jak Refaktoryzacja, na istniejącym kodzie.

    - **Zawsze** używaj kanonicznej reprezentacji wyświetlanych informacji. Na przykład kod powinien wyglądać jak kod, być gotowy z wyróżnioną składnią i powinien być uwzględniany dla każdej czcionki i innych ustawień środowiska ustawionych przez użytkownika.

    - Należy **zawsze** rozważyć obsługę wszelkich akcji w stosunku do zawartości informacyjnej, która byłaby możliwa, jeśli te same informacje są prezentowane jako zawartość główna. Na przykład, jeśli przedstawiasz istniejący kod wewnątrz kontenera interfejsu użytkownika w obiekcie, zdecydowanie Rozważ obsługę możliwości przeglądania i modyfikowania tego kodu.

    - **Zawsze** należy rozważyć użycie innego koloru tła w przypadku prezentowania zawartości informacyjnej, która reprezentuje potencjalne przyszły stan.

2. Możliwe do wykonania: niektóre kontenery interfejsu użytkownika w obiekcie zapewniają możliwość wykonywania pewnych akcji w stosunku do zawartości głównej, takich jak wykonywanie operacji refaktoryzacji.

    - **Zawsze** umieszczaj polecenia z możliwością podejmowania akcji niezależnie od zawartości informacyjnej.

    - **Zawsze** włączaj i wyłączaj akcje, jeśli są odpowiednie.

    - **Zawsze** odnoszą się do standardowych wytycznych dotyczących reprezentowania poleceń wewnątrz okien dialogowych.

    - **Zawsze** należy zachować liczbę akcji, które są widoczne w kontenerze interfejsu użytkownika w obiekcie, do bezwzględnego minimum. Praca z interfejsem użytkownika w obiekcie powinna być lekkim i szybkim doświadczeniem. Użytkownik nie musi wystawić energii na zarządzanie kontenerem interfejsu użytkownika w obiekcie.

    - **Zawsze** należy rozważyć, jak i kiedy kontener interfejsu użytkownika w obiekcie zostanie zamknięty lub odrzucony. Najlepszym rozwiązaniem jest to, że każda akcja, która zawiera okno dialogowe między treścią główną i szczegółową, powinna również zamykać kontener interfejsu użytkownika na obiekcie po wywołaniu tej akcji.

3. **Nawigacja:** niektóre kontenery interfejsu użytkownika w obiekcie obejmują linki, które przeprowadzą użytkownika do innego okna lub aplikacji, na przykład otwierając artykuł MSDN w przeglądarce sieci Web użytkownika.

    - **Zawsze** dołączaj wszystkie linki nawigacyjne "Open", aby użytkownicy nie mogli przechodzenia do innej zawartości.

    - **Zawsze** oddzielaj linki nawigacyjne od linków do działania.

#### <a name="ambient-indicators-optional"></a>Wskaźniki otoczenia (opcjonalnie)
 Wskaźniki otoczenia mogą być subtelne, w tym tekst przedstawiony w kolorze kontrastu od pozostałej części kodu lub oczywisty, w tym symbole Tickler, takie jak zygzaki i ikony tagów inteligentnych. Wskaźniki otoczenia komunikują się z dostępnością dodatkowych, istotnych informacji. W idealnym przypadku zapewniają przydatne informacje nawet bez konieczności korzystania z nich przez użytkownika.

- **Zawsze** umieszczaj wskaźnik otoczenia, aby nie rozpraszać ani nie przeciążyć użytkownika. Jeśli nie można ustawić wskaźnika otoczenia w taki sposób, weź pod uwagę inne rozwiązanie.

- **Zawsze** Umieść wskaźnik otoczenia jak najbliżej zawartości, z którą jest ona powiązana.

- **Zawsze** należy próbować utworzyć wskaźnik, który podsumowuje dostępne informacje. Rozważ podanie liczby dostępnych elementów danych (na przykład "3 odwołania" zamiast po prostu "odwołania") lub zapoznaj się z innym sposobem podsumowywania danych.

  - W przypadkach, gdy dane dla wskaźnika nie mogą być zawsze obliczane i wyświetlane, należy natychmiast rozważyć dostarczenie opinii progresywnej, ponieważ wartości są obliczane. Rozważmy na przykład animowanie zmian, które odzwierciedlają aktualizacje dostępnych danych, podobnie jak w przypadku Windows Phone odświeżane w wiadomościach e-mail na żywo w miarę zwiększania liczby nieprzeczytanych wiadomości e-mail.

- **Nigdy nie** dodawaj więcej wskaźników niż użytkownik może zależeć od danego elementu zawartości. Wskaźniki otoczenia powinny być przydatne bez konieczności interakcji z użytkownikiem. Wskaźniki tracą Ambience, jeśli wymagają przepełnienia i innych kontroli zarządzania w celu przełączenia ich do widoku.

#### <a name="gestures"></a>Gestów
 Kluczowym aspektem pozwalającym użytkownikowi na utrzymywanie fokusu w zawartości głównej jest poprzez obsługę odpowiednich gestów, aby otworzyć i odrzucić dodatkową zawartość szczegółową.

- **Zawsze** należy wymagać od użytkownika, aby otworzył dodatkową zawartość. Wspólne gesty otwarte obejmują:

  - **Aktywowanie:** etykietki narzędzi lub nieinteraktywna zawartość informacyjna

  - **Jawne polecenie:** inline Presenter

  - Kliknij **dwukrotnie wskaźnik otoczenia:** Okno podręczne CodeLens

- **Zawsze** Odrzuć zawartość szczegółową za każdym razem, gdy użytkownik naciśnie klawisz ESC.

- **Zawsze** należy wziąć pod uwagę kontekst interfejsu użytkownika w obiekcie. W przypadku prezenterów zawartości, które umożliwiają interakcję w kontenerze, należy uważnie rozważyć, czy mają być wyświetlane dodatkowe informacje o aktywowaniu, co może powodować zakłócenie przepływu pracy użytkownika.

- **Nigdy nie** Wyświetlaj zawartości na aktywowaniu, która wygląda na możliwość edytowania lub zapraszania interakcji z użytkownikiem. Takie zachowanie może frustrować użytkowników, jeśli próbują przenieść kursor nad zawartością szczegółową, ponieważ standardowe zachowanie etykietki narzędzia jest natychmiast odrzucane, gdy kursor nie znajduje się już nad zawartością główną, która go wygenerowała.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modele wyboru

### <a name="overview"></a>Omówienie
 Model wyboru jest mechanizmem używanym do wskazywania i potwierdzania operacji na co najmniej jednym obiekcie interesującym w interfejsie użytkownika. W tym temacie omówiono wzorce interakcji zaznaczenia w edytorach dokumentów programu Visual Studio: edytory tekstu, powierzchnie projektowe i powierzchnie modelowania.

 Użytkownicy muszą mieć możliwość wskazywania programu Visual Studio, w którym pracują, a program Visual Studio musi reagować na opinie użytkowników o tym, na czym polega. Różnice lub nieprawidłowa komunikacja między użytkownikiem a interfejsem użytkownika mogą spowodować, że użytkownik nie obserwowanie akcji, która może mieć niezamierzone konsekwencje. Często ten błąd jest niezauważalny, dopóki użytkownik nie zobaczy, że coś nie ma lub zostało zmienione. Modele wyboru są w związku z tym jednym z najważniejszych elementów projektowania interfejsu użytkownika. Chociaż modele wyboru w programie Visual Studio są spójne z systemem Windows, istnieją niewielkie wahania.

 W programie Visual Studio, jak w systemie Windows, modele wyboru różnią się w zależności od kontekstu, w którym występuje interakcja. Wybory mogą wystąpić w czterech typach obiektów:

- Tekst

- Obiekty graficzne

- Listy i drzewa

- Siatki

  W ramach tych obiektów istnieją trzy typy wyborów:

- Sąsiadując

- Rozłączny

- Region

#### <a name="scope"></a>Zakres
 Najważniejszym składnikiem wyboru jest upewnienie się, że użytkownik wie, w jakim oknie pracują (aktywacja) i gdzie fokus się znajduje (wybór). Program Visual Studio rozszerza funkcje zarządzania oknami w systemie Windows, ale schemat aktywacji jest taki sam: korzystanie z okna przenosi fokus do okna. Program Visual Studio ma dwa wskaźniki do aktywacji: jeden dla okien dokumentu i jeden dla okien narzędzi.

 W przypadku okien dokumentów okno aktywne jest wskazywane przez kartę okna dokumentu przechodzącą do przodu i zmieniającą jej kolor tła:

 ![Aktywny wybór karty w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 — 01_ActiveTab")

 **Aktywna karta wybór**

 W przypadku okien narzędzi, aktywne okno jest wskazywane przez zmianę koloru obszaru paska tytułu w oknie narzędzia:

 ![Wybór aktywnego okna narzędzi w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 — 02_ActiveToolWindow")

 **Okno aktywnego narzędzia z widocznym głównym wyborem węzła**

 ![Wybór okna narzędzia nieaktywnego w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 — 03_InactiveToolWindow")

 **Nieaktywne okno narzędzi, pokazujące ukryty wybór węzła**

 Gdy okno jest aktywne, jego fokus jest wskazywany zgodnie z modelami wyboru opisanymi w tej sekcji wytycznych.

#### <a name="context"></a>Kontekst
 Program Visual Studio został zaprojektowany tak, aby zachować silną koncepcję kontekstu, śledząc lokalizację pracy użytkownika. Aktywne jest tylko jedno okno, niezależnie od tego, czy jest ono oknem narzędzia czy dokumentu. Jednak okno dokumentu najwyższego poziomu zawsze zachowuje ukryty wybór. Chociaż fokus może znajdować się w oknie narzędzi, okno dokumentu, które było ostatnio aktywne, wyświetla zaznaczenie, nawet w nieaktywnym stanie. Dzieje się tak, aby zachować kontekst użytkownika w dokumencie, który był edytowany, z informacją o tym, że program Visual Studio zachował swój stan, dzięki czemu mogą oni bezproblemowo zwracać i przełączać się między oknami narzędzi i oknami dokumentów.

### <a name="text-selection"></a>Zaznaczanie tekstu
 Edytory programu Visual Studio, które są ściśle jednotekstowe, takie jak wbudowany edytor tekstu, używają tego samego modelu wyboru tekstu i wyglądu opisanego na stronie [myszy i wskaźników](/windows/desktop/uxguide/inter-mouse) w wytycznych dotyczących interakcji użytkownika systemu Windows w witrynie MSDN. Fokus wprowadzania w edytorze tekstu jest wskazywany przez pionowy pasek o nazwie punkt wstawiania. Punkt wstawiania jest pojedynczym pikselem i kolorem, gdy zostanie wyświetlona odcienie dowolnego elementu. Miga w zależności od stawki ustawionej przez ustawienie **współczynnika migania kursora** na karcie **szybkość** w aplecie **Klawiatura** w panelu sterowania.

#### <a name="contiguous-and-disjoint-selection"></a>Ciągły i rozłączony wybór
 Wybór w edytorze tekstu jest tylko ciągły. Rozłączane wybory tekstu nie są dozwolone, ale powinny być rozkierowane w Edytorze obiektów graficznych. Gdy wskaźnik myszy użytkownika znajduje się nad obszarem tekstu, kursor zmieni się w obramowanie I. Pojedyncze kliknięcie powoduje umieszczenie punktu wstawiania w edytorze tekstu w lokalizacji kliknięcia. Trzymanie przycisku myszy w dół powoduje wyróżnienie zaznaczenia i zwolnienie przycisku myszy spowoduje zakończenie zaznaczania.

#### <a name="region-selection-box-selection"></a>Wybór regionu (Wybieranie pola)
 Program Visual Studio obsługuje wybór regionów w edytorze tekstów, a ta opcja jest wywoływana. Zaznaczenie pola umożliwia użytkownikowi wybranie regionu tekstu, który nie jest zgodny ze zwykłym strumieniem tekstu. Podobnie jak w przypadku tekstu standardowego zaznaczenie musi być ciągłe. Zaznaczenie pola jest inicjowane przez przytrzymanie klawisza Alt podczas przeciągania z myszą. Zaznaczenie pola może być również inicjowane przez wciśnięcie klawisza Alt i Shift przy użyciu klawiszy strzałek, aby wskazać region zaznaczenia. Wybór pola używa wyróżnienia normalnego zaznaczenia i pokazuje kursor punktu wstawiania migający na końcu obszaru zaznaczenia.

 ![Pole &#40;regionalne&#41; wybór w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 — 04_BoxSelection")

 **Wybór regionu (pola) w programie Visual Studio**

#### <a name="text-selection-appearance"></a>Wygląd zaznaczonego tekstu
 Kolory używane do aktywnego i nieaktywnego wyboru w edytorze można dostosować. Aby dostosować wygląd edytora, użytkownik może przejść do pozycji **narzędzia > opcje**, a następnie w obszarze **środowisko > czcionki i kolory > edytorze tekstów**.

### <a name="graphical-selection"></a>Wybór graficzny

#### <a name="interaction"></a>Interakcja
 Wybór obiektu graficznego może być skomplikowany i zależy od wielu czynników:

- **Główny model wyboru edytora.** Aby edytować tekst lub siatki, można także użyć edytorów zawierających obiekty graficzne. Na przykład edytor może być edytorem tekstowym, który również obsługuje umieszczanie obiektów graficznych, takich jak Projektant Visual Studio XAML. Obsługa wielu typów obiektów może mieć wpływ na sposób wybierania przez użytkownika grup składających się z różnych typów obiektów.

- **Obsługa podstawowych i pomocniczych Stanów wyboru.** Edytor może zapewnić podstawowe i pomocnicze Stany wyboru, aby obiekty mogły być edytowane w artykułem, wyrównane ze sobą, zmieniać rozmiar razem i tak dalej.

- **Obsługa edycji w miejscu.** Edytory mogą również zezwalać na edycję zawartości ich obiektów graficznych. Na przykład kształt prostokąta może również zawierać tekst w obrębie elementu, który może zostać zmieniony przez użytkownika. Ponadto ten tekst może być wyśrodkowany lub wyrównany. Edytowanie w miejscu obejmuje bardziej szczegółowy poziom interakcji z użytkownikiem i w związku z tym wymaga odpowiedniego zestawu wskazówek wizualnych do prezentowania użytkownikowi informacji o stanie.

#### <a name="mouse-interaction"></a>Interakcja myszy

|Dane wejściowe|Wynik|
|-----------|------------|
|Kliknij niezaznaczony obiekt|Wybiera obiekt i wyświetla uchwyty linii przerywanej i wyboru, jeśli rozmiar obiektu jest zmienny.|
|Kliknij wybrany obiekt|Uaktywnia edycję w miejscu, jeśli obiekt ją obsługuje. Kliknięcie poza obiektem dezaktywuje tryb edycji w miejscu.|
|Kliknij dwukrotnie obiekt|Otwiera kod za obiekt do edycji i może wstawić domyślną procedurę obsługi zdarzeń, jeśli jest to konieczne.|
|Wskaż obiekt|Zmienia wskaźnik do kursora przenoszenia. Wygląd obiektu, taki jak jaskrawość lub kolor, może ulec zmianie.|
|Wskaż uchwyt zaznaczenia|Zmienia wskaźnik do kursora zmiany rozmiaru. W przypadku obiektów, które obsługują obrót, niektóre uchwyty zaznaczenia mogą zmienić wskaźnik na kursor obracania, gdy wskaźnik jest pozycjonowany inaczej (na przykład przeniesiono dalej) w odniesieniu do uchwytu zaznaczenia.|
|Przeciągnąć|Nawet jeśli obiekt nie jest wcześniej zaznaczony, zmienia wskaźnik myszy na przesuwający kursor i przenosi obiekt.|
|Edytor utraci fokus|Dezaktywuje tryb edycji w miejscu, chociaż obiekt zachowuje zawartość i wygląd podczas ostatniego stanu operacji/zaznaczania.|
|Wybór obiektu|Wskazywane przez obramowanie, linię kropkowaną lub inne wizualnie odrębne traktowanie w celu wyróżnienia granicy obiektu.|
|Zmień rozmiar zaznaczonego obiektu|Wskazywane przez uchwyty zaznaczania.<br /><br /> Obiekt o zmiennym rozmiarze ma osiem dojść, reprezentujących każdy kierunek, w którym można zmienić jego rozmiar. Aby można było zmienić rozmiar obiektu w niektórych kierunkach, można użyć mniej dojść. Gdy użytkownik zmienia rozmiar obiektu w dół, gdzie osiem dojść nie będzie interaktywne, można użyć czterech uchwytów. Rozmiary uchwytów powinny być powiązane z obramowaniem okna i metrykami krawędzi z funkcją interfejsu API **GetSystemMetrics** , aby rozmiar był proporcjonalny do rozdzielczości ekranu.<br /><br /> ![Uchwyty zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 — 05_ResizeHandles")|
|Obróć wybrany obiekt|![Obróć uchwyty](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 — 06_Rotate")|

#### <a name="keyboard-interaction"></a>Interakcja z klawiaturą

|Dane wejściowe|Wynik|
|-----------|------------|
|Tab|Przenosi wskaźnik ostrości między logiczną kolejnością obiektów w edytorze. Może to być od lewej do prawej lub od góry do dołu w zależności od wartości właściwości **TabIndex** (lub równoważnej), kolejności tworzenia obiektów i ogólnego przeznaczenia edytora. Shift + Tab odwraca kierunek wskaźnika koncentracji uwagi.|
|Spacja|Uaktywnia tryb przesuwania, gdy jest zachowywane naciśnięcie klawisza. Do przesuwania położenia okienka ekranu jest wymagane dodatkowe wejście myszy.|
|Ctrl+Spacja|Uaktywnia tryb powiększenia, gdy jest zachowywane naciśnięcie klawisza. Dodatkowe dane wejściowe myszy są wymagane do zwiększenia i zmniejszenia współczynnika powiększenia.|
|Ctrl + Alt + znak minus|Zmniejsza współczynnik powiększenia o jeden poziom.|
|Ctrl + Alt + znak plus|Zwiększa współczynnik powiększenia o jeden poziom.|
|Shift lub CTRL|Dodaje obiekt do grupy wyboru. Klawisz Ctrl umożliwia także usuwanie obiektów indywidualnie z grupy wyboru.|
|Enter|Wykonuje domyślne polecenie dla obiektu (zazwyczaj otwiera lub Edytuj).|
|F2|Aktywuje edytowanie w miejscu dla obiektu.|
|Klawisze strzałek|Przenosi zaznaczone obiekty w kierunku naciśniętego klawisza Strzałka, w małych przyrostach (na przykład 1 piksel w danym momencie)|
|CTRL + klawisze strzałek|Przenosi zaznaczone obiekty w kierunku naciśniętego klawisza Strzałka, w większych przyrostach (na przykład 10 pikseli w danym momencie)|
|Shift + klawisze strzałek|Zmienia rozmiar wybranych obiektów w odpowiednim kierunku, w małych przyrostach (na przykład 1 piksel w danym momencie)|
|Ctrl + Shift + klawisze strzałek|Zmienia rozmiar wybranych obiektów w odpowiednim kierunku, w większych przyrostach (na przykład 10 pikseli jednocześnie)|

 Gdy użytkownicy edytują kontrolki na miejscu, może być zrozumiałe dla obiektów, aby automatycznie zmieniać rozmiar przy użyciu danych wejściowych użytkownika. Na przykład, jeśli użytkownik edytuje kontrolkę etykieta, wówczas etykieta powinna się rozwijać, aby wyświetlić tekst wpisany przez użytkownika. Jeśli to nie zrobisz, użytkownik musi ręcznie zmienić rozmiar kontrolki po przeprowadzeniu edycji tekstu. Jeśli użytkownik ma wiele kontrolek, zostanie to Rote i nieproduktywne zadanie.

#### <a name="graphical-containers"></a>Kontenery graficzne
 W niektórych przypadkach edytory graficzne udostępniają kontenery dla innych obiektów graficznych, takich jak kontrolka panelu Windows Forms lub kontrolka układu siatki w projektancie HTML. Jeśli Edytor udostępnia kontenery dla innych obiektów graficznych, należy użyć następującego modelu wyboru dla kontenera (obiekty w kontenerze są zgodne ze standardowym modelem, jak opisano powyżej):

|Dane wejściowe|Wynik|
|-----------|------------|
|Pojedyncze kliknięcie kontenera|Wybiera obiekt kontenera bez bezpośredniego zaznaczania żadnego z zawartych w nim obiektów. Kontener może być przenoszony i/lub zmieniany przy użyciu standardowego wskaźnika myszy i klawiatury (zgodnie z powyższym opisem). Zawarte obiekty są przenoszone w odniesieniu do kontenera, ale nie można zmieniać rozmiaru zawartych obiektów, chyba że są również bezpośrednio zaznaczone.|
|Umieść kursor nad regionem granicy kontenera|Włącza myszą do kursora przenoszenia, wskazując, że kontener można przenieść.|
|Przeciągnij region graniczny kontenera|Zmienia mysz na przesuwający kursor i przenosi kontener (oraz zawarte w nim obiekty). Nie można przenieść kontenera bez uprzedniego wybrania jednego kliknięcia.|
|Pojedyncze kliknięcie obiektu w kontenerze|Anuluje wybór kontenera (w przypadku wybrania) i wybranie tylko klikniętego obiektu.|
|Shift + kliknięcie lub Ctrl + kliknięcie zawartego obiektu i/lub kontenera|Dodaje kliknięty obiekt do istniejącej grupy wyboru lub zaznaczenia. Jeśli kliknięty obiekt jest już elementem członkowskim grupy wyboru, zostanie usunięty z grupy wyboru.|

 Zawarte obiekty powinny być zgodne z modelem wyboru podstawowego, zgodnie z opisem w poprzedniej sekcji. Od testowania użyteczności projektanta Windows Forms użytkownicy oczekują bezproblemowego dostępu do zawartych obiektów bez popełnienia czynności (nałożonej przez obiekt zawierający).

#### <a name="disjoint-and-region-selections"></a>Rozłączenie i wybór regionów
 Edytory obiektów graficznych powinny obsługiwać wybrane rozłączenia. Należy pamiętać, że ta ilustracja nie pokazuje wyglądu kontrolki dla programu Visual Studio. Aby uzyskać szczegółowe specyfikacje wizualizacji, zobacz [wygląd obiektu graficznego](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) .

 ![Rozłączenia i selektory regionów](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 — 07_DisjointRegionSelectors")

 **Rozłączanie zaznaczenia**

 Edytory graficzne powinny również udostępniać wybrane regiony wskaźnikiem wyboru typu Neon. Jeśli edytor graficzny obsługuje inne typy obiektów (na przykład tekst), wybór regionów może nie być możliwy w zależności od ograniczeń tych innych typów obiektów.

 ![Markiza — zaznaczenie](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 — 08_MarqueeSelection")

 **Markiza — zaznaczenie**

#### <a name="primary-and-secondary-selections"></a>Wybór podstawowy i pomocniczy
 Niektóre graficzne edytory obiektów umożliwiają użytkownikowi edytowanie lub wyrównywanie obiektów w grupach. W takim przypadku należy wprowadzić koncepcję opcji podstawowe i pomocnicze. Wybór podstawowy to obiekt, do którego wszystkie inne obiekty odpowiadają na operacje grupy. Obiekt, który użytkownik wybiera jako pierwszy staje się formantem podstawowym, a kolejne wybrane stają się ustawieniami pomocniczymi. Wybór podstawowy ma odrębne podejście wizualne od dodatkowych opcji, aby wskazać, który obiekt jest podstawowym:

 ![Wybór podstawowy i pomocniczy](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 — 09_PrimarySecondary")

 **Wybór podstawowy z dwoma dodatkowymi opcjami**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Wygląd obiektu graficznego
 Uchwyty zaznaczania są kwadratami rysowanymi w prostokątnym wzorcu wokół obwiedni obiektu. Na poniższym wykresie przedstawiono przykłady różnych stanów, które mogą mieć obiekt graficzny z uchwytem, rozmiarem i wyglądem w miejscu. Rozmiary uchwytów powinny być powiązane z obramowaniem okna i metrykami krawędzi za pomocą interfejsu API **GetSystemMetrics** .

| Stan | Wygląd | Szczegóły wizualizacji |
|-------------------------|---------------| - |
| **Niezaznaczone** | Domyślne | ![Domyślny stan przycisku](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 — 10_DefaultState") |
| **Wybór podstawowy** | O zmiennych rozmiarach | ![Wybór podstawowy z uchwytami zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 — 11_PrimaryResize") |
| **Wybór podstawowy** | Bez możliwości zmiany rozmiaru | ![Wybór podstawowy bez zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 — 13_PrimaryNoResize") |
| **Wybór podstawowy** | Zablokowano | ![Zablokowany wybór podstawowy](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 — 15_PrimaryLocked") |
| **Wybór pomocniczy** | O zmiennych rozmiarach | ![Wybór pomocniczy z uchwytami zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 — 17_SecondaryResize") |
| **Wybór pomocniczy** | Bez możliwości zmiany rozmiaru | ![Wybór pomocniczy bez zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 — 19_SecondaryNoResize") |
| **Wybór pomocniczy** | Zablokowano | ![Zablokowany wybór pomocniczy](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 — 21_SecondaryLocked") |
| **Aktywny interfejs użytkownika** | Domyślne | ![Stan aktywności interfejsu użytkownika](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 — 23_UIActive") |

### <a name="view-selection-models"></a>Wyświetlanie modeli wyboru

#### <a name="tree-view"></a>Widok drzewa
 Zaznaczenie w widoku drzewa jest wyświetlane z prostym wyróżnieniem. Jeśli użytkownik kliknie nazwę węzła lub ikonę węzła, węzeł zostanie wybrany. Trójkątne glify po lewej stronie węzła rozszerzają lub zwijają kontrolkę drzewa, ale nie wpływają na wybór użytkownika, z wyjątkiem jednego wyjątku: przy zwijaniu węzła nadrzędnego, gdy zaznaczenie znajduje się w elemencie podrzędnym tego węzła, zaznaczenie przenosi do elementu nadrzędnego.

 ![Typowy widok drzewa w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 — 25_TreeView")

 **Typowy widok drzewa w programie Visual Studio**

 Widoki drzewa mogą obsługiwać elementy ciągłe i rozłączane, nawet na wielu poziomach w drzewie. W widocznych węzłach drzewa muszą zostać utworzone ciągłe lub rozłączone wiele zaznaczeń. Jeśli węzeł jest zwinięty, rozłączany wybór zostanie utracony, a zwinięty węzeł uzyska zaznaczenie. W ten sposób użytkownik może zobaczyć węzły, na które wpłynie operacja. Gdy węzły są zwinięte, staną się niejasne, których węzłów mogą dotyczyć.

 Po wybraniu węzła nadrzędnego operacja powinna zostać zastosowana do elementu nadrzędnego, chociaż mogą wystąpić sytuacje, w których jest to zrozumiałe dla operacji, która ma być stosowana do elementu nadrzędnego i wszystkich jego elementów podrzędnych. W takim przypadku należy zapewnić dodatkowy interfejs użytkownika podczas operacji, na przykład pole wyboru lub okno dialogowe potwierdzenia, aby opcja "Zastosuj do wszystkich elementów podrzędnych" była jawna dla użytkownika.

##### <a name="renaming"></a>Zmiana nazwy
 Jeśli węzły w drzewie obsługują zmianę nazwy, należy wprowadzić zmianę nazwy. Operacja w miejscu powinna być standardem dla wszystkich kontrolek drzewa w programie Visual Studio. Podaj polecenie zmiany nazwy, które natychmiast aktywuje tryb edycji w miejscu, z zaznaczonym tekstem obejmującym całą nazwę węzła, gotowy do akceptowania danych wejściowych użytkownika. Jeśli węzeł reprezentuje plik, nazwa pliku powinna zawierać rozszerzenie. Wyróżnienie zaznaczenia powinno zawierać tylko treść nazwy pliku, a nie rozszerzenie.

|Dane wejściowe|Wynik|
|-----------|------------|
|klawisz ENTER|Zatwierdza operację zmiany nazwy|
|Klawisz ESC|Anuluje operację zmiany nazwy|
|Kliknięcie poza regionem edycji w miejscu|Zatwierdza operację zmiany nazwy|
|Cofnij|Zapewnianie łatwego cofania operacji zmiany nazwy|

#### <a name="selection-within-lists-and-grid-controls"></a>Zaznaczenie w kontrolkach list i siatki
 Kluczową koncepcją w wyborze listy jest to, że jest oparta na wierszach, co oznacza, że po wykonaniu wyboru cały wiersz jest wybierany jako jednostka. Z kolei siatki mogą zezwalać na wybranie określonych komórek bez wpływu na inne aspekty wiersza. Siatki mogą również zawierać hierarchię zagnieżdżonych wierszy (na przykład w TreeGrid), która umożliwia zaznaczanie i dewybieranie całych gałęzi hierarchii przez współdziałanie z wierszami nadrzędnymi. Wybór na listach jest pokazywany przez prosty kolor wyróżniony dla całego wiersza danych. Fokus jest pokazywany kropkowanym obramowaniem o pojedynczej pikseli wokół bieżącego, edytowalnego wiersza lub komórki (wiersz, jeśli wszystkie komórki są tylko do odczytu).

> [!NOTE]
> **Fokus** i **wybór** to różne koncepcje. *Fokus* jest wskazaniem, który element interfejsu użytkownika jest przeznaczony do odbierania danych wejściowych, które nie są jawnie kierowane na inny obiekt, podczas gdy *zaznaczenie* odnosi się do stanu dołączenia obiektu w zestawie obiektów, na którym mogą być wykonywane kolejne operacje.

 Wybory na listach mogą być ciągłe, rozłączone lub region. Gdy jest dozwolonych wiele opcji, ciągły i rozłączony wybór powinny być zawsze obsługiwane, podczas gdy obsługa opcji region (Box) jest opcjonalna. Wybory regionów są inicjowane przez przeciąganie w białej przestrzeni treści listy.

| Obiekt | Wybór |
|--------|------------|
| Lista | Sąsiadując |
| Lista | Rozłączny |
| Lista | Region |

 Kliknięcie raz na liście wybiera wiersz, w którym nastąpiło kliknięcie. Jeśli użytkownik kliknie w komórce listy, która obsługuje edycję w miejscu, komórka jest również natychmiast aktywowana do edycji w miejscu. W przeciwnym razie cały wiersz jest wybierany natychmiast i zostanie wyświetlona.

 Przeciąganie w treści listy wykonuje jedną z trzech czynności:

- Powoduje zainicjowanie wyboru regionu, jeśli jest ona obsługiwana przez listę, a mysz w dół znajduje się w białym miejscu

- Inicjuje operację przeciągania/upuszczania, jeśli komórka lub wiersz listy obsługuje Źródło przeciągania

- Wybiera bieżący wiersz

##### <a name="in-place-editing"></a>Edytowanie w miejscu
 Jeśli dozwolone jest edytowanie w miejscu, istnieją dwa podstawowe modele: prosta kontrolka edycji i selektor właściwości. Przy użyciu prostej kontrolki edycji zawartość jest wyróżniona i gotowa do wprowadzenia przez użytkownika, gdy tylko edycja w miejscu zostanie aktywowana. W przypadku zaimplementowania selektora właściwości przycisk, który wywołuje selektor właściwości, jest wyświetlany, gdy zostanie aktywowany tryb edycji w miejscu i bieżące zaznaczenie nie zostanie wyróżnione. Przycisk selektora powinien być wyrównany do prawej strony w komórce. Aby zapoznać się z przykładami edycji w miejscu, zobacz **okno właściwości** i **Lista zadań** w programie Visual Studio.

##### <a name="keyboard-support"></a>Obsługa klawiatury
 Obsługa klawiatury dla wyboru w listach i siatkach jest zgodna ze standardowymi konwencjami systemu Windows:

- Klawisze strzałek przechodźą na listę, zaznaczając każdy wiersz/komórkę w miarę przenoszenia fokusu.

- Shift + strzałka wykonuje ciągły wybór w kierunku klawiszy strzałek.

- Ctrl + strzałka, po której następuje przełączanie między dodawaniem i usuwaniem elementów listy z zaznaczenia, tworzenie rozłączania.

- W przypadku siatek zawierających zagnieżdżone hierarchie klawisz Strzałka w prawo rozszerza wiersz nadrzędny, a klawisz Strzałka w lewo zwija jeden.

- Klawisz Tab przenosi fokus między komórkami w bieżącym wierszu, jeśli komórki są edytowalne.

- Klawisz ENTER wykonuje domyślne polecenie dla elementu na liście (często **otwarte**).

- Klawisz F2 aktywuje edytowanie w miejscu dla aktualnie zaznaczonej komórki.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Trwałość i zapisywanie ustawień

### <a name="overview"></a>Omówienie
 Chociaż każdy składnik oprogramowania w programie Visual Studio jest zazwyczaj odpowiedzialny za własny stan i trwałość, program Visual Studio automatycznie zapisuje w niektórych przypadkach ustawienia, takie jak rozmiary okna i położenia. Poniższa tabela to kombinacja ustawień zapisywanych automatycznie i ustawień, które wymagają wykonania jawnego użytkownika lub zaprogramowanego działania.

|Obiekt|Co należy zapisać|Kiedy należy zapisywać|Miejsce zapisu|
|------------|------------------|------------------|-------------------|
|Obiekt z wybieraniem (na przykład wiersz kodu)|Punkt przerwania w wierszu kodu<br /><br /> Skrót użytkownika skojarzony z wierszem kodu|Gdy projekt jest zapisywany|Plik **opcji użytkownika (. suo)** dla projektu|
|Oknie dialogowym|Lokalizacja okna dialogowego, jeśli została przeniesiona<br /><br /> Widok, który ostatnio używał użytkownika w oknie dialogowym|Gdy okno dialogowe zostanie zamknięte<br /><br /> Po zakończeniu sesji programu Visual Studio|W pamięci<br /><br /> Rejestr w **HKEY_CURRENT_USER**|
|Okno|Rozmiar i lokalizacja okna|Gdy okno zostanie zamknięte<br /><br /> Po zmianie trybu programu Visual Studio<br /><br /> Po zakończeniu sesji programu Visual Studio|Plik **opcji użytkownika (. suo)** dla projektu<br /><br /> Plik opcji niestandardowych dla ustawień okna|
|Dokument|Bieżące zaznaczenie w dokumencie<br /><br /> Widok dokumentu<br /><br /> Ostatnie miejsce odwiedzone przez użytkownika|Gdy dokument zostanie zapisany|Plik **opcji użytkownika (. suo)** dla projektu|
|Projekt|Odwołania do plików<br /><br /> Odwołania do katalogów na dysku<br /><br /> Odwołania do innego oprogramowania<br /><br /> Składniki<br /><br /> Informacje o stanie dotyczące samego projektu|Gdy projekt jest zapisywany|Plik projektu|
|Rozwiązanie|Odwołania do projektów<br /><br /> Odwołania do plików|Gdy projekt lub rozwiązanie zostanie zapisane|Plik **rozwiązania (. sln)**|
|Ustawienia w **narzędziach > opcje**|Dostosowanie klawiatury<br /><br /> Dostosowania paska narzędzi<br /><br /> Schematy kolorów|Gdy okno dialogowe **opcje > narzędzia** zostanie zamknięte<br /><br /> Po zakończeniu sesji programu Visual Studio|Rejestr w **HKEY_CURRENT_USER**|

 Co robi użytkownik, a kiedy to robi, określa, czy ustawienie jest zapisywane w pamięci (w trakcie sesji), zapisane na dysku (między sesjami jako ustawienie rejestru), jako część samego projektu lub pliku rozwiązania, jako część pliku **opcji rozwiązania (. suo)** lub jako plik ustawień niestandardowych, który zna tylko ten składnik oprogramowania. Powyższa tabela zawiera kilka zdarzeń, w których można zapisać ustawienia. Mogą jednak wystąpić sytuacje, w których można zapisać stan:

- Gdy użytkownik zmienia lokalizację w oknie dialogowym lub oknie

- Gdy użytkownik przenosi fokus do innego okna

- Gdy użytkownik przełącza się z projektu do trybu debugowania

- Gdy użytkownik wylogowuje się z konta

- Gdy komputer przechodzi w stan hibernacji lub zostanie zamknięty

- Gdy komputer/dysk twardy zostanie przeformatowany i ponownie skonfigurowany

### <a name="window-configurations"></a>Konfiguracje okna
 Konfiguracja okna jest podstawową prezentacją środowiska programistycznego — jest to schemat składający się z listy okien narzędzi dostępnych i sposobu ich rozmieszczenia. W przypadku systemu Windows zarządzanego przez środowisko IDE (IDE Windows) informacje o układzie są utrwalane dla użytkownika, więc gdy użytkownik uruchamia IDE, układ okna pojawia się tak samo jak podczas ostatniego zamykania programu Visual Studio. Stan i położenie okien środowiska IDE są utrwalane w pliku opcji niestandardowych w formacie XML. Okna narzędzi, które są tworzone przez pakiety ładowane do środowiska IDE, utrzymują swoje informacje o stanie w rejestrze i mogą nie być na użytkownika.

#### <a name="profile-specific-layouts"></a>Układy specyficzne dla profilu
 Każdy profil zawiera układy okna narzędzi, zorganizowane w sposób zaznajomiony z konkretną osóbem deweloperów (Visual C++ deweloperzy mogą widzieć **Eksplorator rozwiązań** po lewej stronie IDE, podczas gdy deweloperzy języka C# oczekują na wyświetlenie **Eksplorator rozwiązań** z prawej strony). Układy okien charakterystyczne dla profilu są ładowane, gdy użytkownik wybierze profil podczas uruchamiania. Autor pakietu powinien określić układ okna najbardziej odpowiedni dla środowiska klienta, wiedząc, że zmiany wprowadzane przez użytkownika w konfiguracji okna zostaną utrwalone.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Wprowadzanie dotykowe
 Użytkownicy coraz częściej korzystają z produktów programistycznych firmy Microsoft na urządzeniach dotykowych. Istnieją jednak pewne bariery utrudniające korzystanie z narzędzi programistycznych na urządzeniach dotykowych. Użytkownicy będą oczekiwać naszych produktów, aby zapewnić niezawodne i precyzyjne środowisko dotykowe. Celem tych wytycznych jest informowanie decyzji o tym, które funkcje dotyku należy uwzględnić, i aby zachęcić do spójnego środowiska dotykowego w programie Visual Studio i związanych z nim produktów.

### <a name="levels-of-experience"></a>Poziomy środowiska
 Następujące poziomy środowiska mają służyć jako przewodnik ułatwiający zespołom decydowanie, które funkcje dotykowe mają być oferowane w oparciu o żądany poziom zainteresowania inwestycji.

- **Podstawowe środowisko** to dla zespołów, które chcą zapewnić funkcje dotykowe, aby nie było żadnych martwych punktów końcowych w całej pracy.

- **Zoptymalizowane środowisko** jest przeznaczone dla zespołów, które chcą zapewnić najbardziej typowe funkcje dotyku (na przykład te, które są zazwyczaj dostępne w aplikacjach przeglądarki internetowej).

- **Środowisko podwyższonego poziomu** jest przeznaczone dla zespołów, które chcą dodawać funkcje, takie jak gesty lub inne opcjonalne funkcje, które mogą sprawiać, że aplikacja działa w pierwszej kolejności.

||Podstawowe środowisko|Zoptymalizowane środowisko|Obsługa podwyższonego poziomu|
|-|----------------------|--------------------------|-------------------------|
|**Umożliwia użytkownikom...**|Popraw kod i rozwiązanie/odczytywanie na poziomie projektu bez martwych punktów końcowych|Wykonywanie czynności konserwacyjnych, refaktoryzacji i nawigacji|Działaj w spójnym, intuicyjnym i płynnym środowisku z pewnością|
|**Edytor**|Panoramowanie i wybór dotyku<br /><br /> Pasek przewijania Touch do skoku i naciśnij klawisze + przeciągnij|Powiększenie szczypania<br /><br /> Szybkie przewijanie<br /><br /> Wybór<br /><br /> Łatwe korzystanie z menu kontekstowego||
|**Najważniejsze okna narzędzi**|Przesuwanie listy<br /><br /> Wybór elementu<br /><br /> Pasek przewijania Touch do skoku i naciśnij klawisze + przeciągnij|Łatwe przewijanie i zaznaczanie elementów||
|**Obsługi okien**||Zmień rozmiar okna<br /><br /> Szybki dostęp||
|**Źródło dokumentu**||Łatwa nawigacja między otwartymi plikami||
|**Gestów**||Upewnij się, że typowe gesty działają w środowisku IDE|Akcje na podstawie gestu<br /><br /> Obsługa przeciągania i upuszczania oraz projektantów|
|**Inne zagadnienia**|||Klawiatura niestandardowa Onscreen|

#### <a name="gestures"></a>Gestów
 Gesty zapewniają użytkownikom skrót do poleceń, które w przeciwnym razie mogą wymagać bardziej skomplikowanej interakcji. Zapoznaj się z wytycznymi dla systemu Windows dotyczącymi [typowych gestów dotykowych dla aplikacji klasycznych](/windows/desktop/wintouch/windows-touch-gestures-overview)i postępuj zgodnie z tymi wskazówkami dotyczącymi większości gestów, w tym prostych gestów, takich jak panoramowanie i
