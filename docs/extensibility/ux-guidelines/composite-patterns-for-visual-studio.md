---
title: Wzorce kompozytowe dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698616"
---
# <a name="composite-patterns-for-visual-studio"></a>Wzorce złożone dla programu Visual Studio
Wzorce kompozytowe łączą elementy interakcji i projektowania w różnych konfiguracjach. Niektóre z najważniejszych wzorów kompozytowych w programie Visual Studio w odniesieniu do spójności obejmują:

- [Wizualizacja danych](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfejs użytkownika obiektu i podglądanie](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modele wyboru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Ustawienia trwałości i zapisywania](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Wizualizacja danych

### <a name="overview"></a>Omówienie
 Wykresy to wizualny sposób agregowania i wizualizowania danych w celu usprawnienia procesu decyzyjnego. Mogą one pomóc użytkownikom w obliczu wielu danych, ale niewiele znaczenia zobaczyć, co zasługuje na uwagę i co może wymagać działania.

 Użytkownik skorzysta z wykresu, jeśli którykolwiek z następujących warunków jest spełniony:

- Czy wykres pomoże użytkownikom zidentyfikować zadania, na których mogą działać?

- Czy wykres umożliwi użytkownikom prognozowanie konsekwencji potencjalnych zmian?

- Czy wykres pomoże użytkownikom odkrywać trendy i identyfikować wzorce?

- Czy wykres pozwoli użytkownikom na podejmowanie lepszych decyzji?

- Czy wykres pomoże odpowiedzieć na konkretne pytanie, które użytkownicy mogą mieć w danym kontekście?

#### <a name="general-rules-for-charts"></a>Ogólne reguły wykresów

- Wyraźnie oznacz dane etykiet. Ilustracje bez wyjaśnienia są po prostu ładne zdjęcia.

- Rozpocznij osie od zera, aby uniknąć przekrzywienia proporcji. Długość linii i rozmiar paska są ważnymi wskazówkami wizualnymi do zrozumienia relacji między punktami danych.

- Tworzenie wykresów, a nie infografik. Infografiki są artystycznymi reprezentacjami danych, a ich głównym celem jest wizualne opowiadanie historii. Wykresy mogą (i powinny) być atrakcyjne wizualnie, ale niech dane mówią same za siebie.

- Unikaj skeumorfizmu, obrazowych wykresów słupkowych, znaków skrótu kontrastu i innych dotknięć infografiki.

- Nie używaj efektów 3D jako elementu dekoracyjnego. Używaj ich tylko wtedy, gdy naprawdę integralną częścią zdolności użytkownika do zrozumienia informacji.

- Unikaj używania wielu linii i wypełnień, ponieważ więcej niż dwa kolory mogą utrudnić poprawne odczytanie i interpretację tego typu wykresu.

- Nie używaj wykresu (ani żadnej ilustracji) jako jedynego sposobu zrozumienia pojęcia lub interakcji z danymi. Stwarza to trudności dla użytkowników z wadami wzroku.

- Nie używaj wykresów jako elementów nieodpłatnych lub dekoracyjnych na stronie. Innymi słowy, jeśli wykres nie dodaje żadnej wartości ani nie pomaga użytkownikom rozwiązać problemu, nie używaj go.

### <a name="chart-types"></a>Typy wykresów
 Typy wykresów używanych w programie Visual Studio obejmują wykresy słupkowe, wykresy liniowe, zmodyfikowany wykres kołowy znany jako wykres pierścieniowy lub "wykres pierścieniowy", osie czasu, wykresy punktowe (nazywane również "wykresami klastrowymi") i wykresy Gantta. Każdy typ wykresu jest przydatny do przekazywania innego typu informacji.

### <a name="other-charting-considerations"></a>Inne zagadnienia dotyczące wykresów

#### <a name="color"></a>Kolor
 Istnieje określona paleta kolorów wykresów zdefiniowanych do użycia w programie Visual Studio. Paleta jest dostępna dla głównych typów ślepoty kolorów, a kolory można różnicować nawet wtedy, gdy są używane jako bardzo wąskie plasterki koloru. Te kolory można używać w dowolnej kombinacji dla dowolnego typu wykresu lub wykresu w interfejsie użytkownika. Nie musisz używać wszystkich siedmiu kolorów, jeśli nie potrzebujesz tak wielu różnych kolorów. Kolory te nie zostały zaprojektowane do użycia z żadnymi elementami pierwszego planu, więc nie należy umieszczać tekstu ani glifów na tych kolorach. Te odcienie powinny być zakodowane na twardo i narażone na dostosowanie użytkownika w obszarze **Narzędzia > Opcje** (patrz Udostępnianie kolorów dla użytkowników [końcowych).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Próbkę|Hex|RGB|
|------------|---------|---------|
|![Próbka 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Próbka BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Próbka FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Próbka 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Próbka 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Próbka 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Próbka B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>Interfejs użytkownika obiektu i podglądanie
 Ta sekcja zawiera kontekst wgląd, znany również jako widok wglądu w kod, typ interfejsu użytkownika w obiekcie unikatowy dla programu Visual Studio.

### <a name="overview"></a>Omówienie

- Interfejs użytkownika on-object powinien dać użytkownikowi więcej informacji lub interaktywności bez umniejszania ich głównego zadania.

- Główny wzorzec interfejsu użytkownika w obiekcie w programie Visual Studio jest znany jako "informacje w punkcie uwagi."

- Interfejs użytkownika w obiekcie w programie Visual Studio jest wbudowany lub zmienny i trwałe lub przejściowe.

  - Widok wglądu do kodu, typ interfejsu użytkownika na obiekt w programie Visual Studio, jest wbudowany i trwały.

  - CodeLens, typ interfejsu użytkownika w obiekcie w programie Visual Studio, jest zmienny i przejściowy

  Zrozumienie, jak działa fragment kodu lub znajdowanie szczegółów dotyczących tego kodu, często wymaga od dewelopera przełączania kontekstu i przechodzenia do innej zawartości lub innego okna. Te zmiany kontekstu mogą być destrukcyjne, ponieważ użytkownicy mogą utracić koncentrację na swoim oryginalnym zadaniu, jeśli opuszczą główne okno. Ponadto uzyskanie tego oryginalnego kontekstu z powrotem może być trudne, zwłaszcza jeśli przełączanie okien spowodowało ich oryginalny kod być zasłonięte przez inny interfejs użytkownika.

  Interfejs użytkownika obiektu następuje wzorzec o nazwie "informacje w punkcie uwagi." Te komunikaty, wyskakujące okna i okna dialogowe zapewniają użytkownikom dodatkowe, istotne informacje, które dodają wyjaśnienia lub interaktywność bez utraty koncentracji na ich głównym zadaniu. Przykłady interfejsu użytkownika na obiekcie obejmują wyskakujące okna, które pojawiają się, gdy użytkownik najedzie wskaźnik na ikonę w obszarze powiadomień, czerwony squiggle pod błędnie napisany wyraz i widok wglądu wprowadzony w programie Visual Studio 2013.

### <a name="decision-points"></a>Punkty decyzyjne
 W programie Visual Studio istnieje kilka sposobów, aby użyć tego wzorca informacji w punkcie uwagi. Wybór odpowiedniego mechanizmu i wdrożenie go w spójny, przewidywalny sposób ma zasadnicze znaczenie dla ogólnego doświadczenia. W przeciwnym razie użytkownicy mogą być przedstawiane z mylące lub niespójne środowisko, które umniejsza fokus z samej zawartości.

#### <a name="relationships-between-master-and-detail-content"></a>Relacje między zawartością wzorcą i szczegółami
 Informacje w punkcie uwagi są używane do wyświetlania relacji między zawartością, na którą koncentruje się użytkownik (zawartość "główna") a dodatkową zawartością pokrewną (zawartość "szczegóły"). W tym wzorcu zawartość szczegółów jest wyraźnie związana z zawartością, z którymi użytkownik pracuje i może być wyświetlana w pobliżu zawartości wzorcowej. Dodatkowe informacje lub informacje, których nie można podsumować bez przytłaczającej zawartości wzorca, powinny być zgodne z innym wzorcem, takim jak okno narzędzia.

- **Zawsze** wyświetlaj zawartość szczegółów w bliskiej odległości od zawartości wzorcowej.

- **Zawsze** upewnij się, że zawartość szczegółów nadal umożliwia użytkownikowi pozostanie skoncentrowany na zawartości wzorcowej. Często najlepszym sposobem osiągnięcia tego celu jest renderowanie zawartości szczegółów tak blisko zawartości głównej, jak to możliwe. Można to zrobić, renderując zawartość szczegółów w wyskakującym oknie obok zawartości wzorcowej lub renderując zawartość szczegółów w linii pod zawartością wzorcową.

- **Nigdy nie** używaj informacji w punkcie uwagi, który zabiera użytkownika z dala od zawartości wzorcowej. Jeśli użytkownicy muszą wyświetlać zawartość szczegółów oddzielnie, uwidaczniać jawne działania, które umożliwia użytkownikowi to zrobić.

#### <a name="design-details"></a>Szczegóły projektu
 Po ustaleniu, że interfejs użytkownika na obiekcie jest właściwym wyborem, istnieją cztery główne zagadnienia projektowe:

1. **Trwałość:** czy zawartość ma być trwała lub przejściowa?
   Czy użytkownicy chcą zachować informacje widoczne w odniesieniu do lub interakcji z? Czy użytkownicy będą chcieli szybko spojrzeć na informacje, a następnie kontynuować swoje główne zadanie?

2. **Typ zawartości:** czy zawartość będzie informacyjna, konfigurowalna lub nawigacyjna?
   Czy użytkownik potrzebuje dodatkowych szczegółów dotyczących zawartości wzorcowej? Czy użytkownik musi wykonać zadanie, które ma wpływ na zawartość wzorcową? A może użytkownik musi zostać przekierowany do innego zasobu?

3. **Typ wskaźnika:** czy wskaźnik otoczenia ma sens?
   Czy informacje można podsumować w użyteczny sposób i wyświetlić bez przytłaczającej zawartości głównej?

4. **Gesty:** jakie gesty będą używane do wywoływania i odrzucania interfejsu użytkownika?
   W jaki sposób użytkownik przywoła zawartość szczegółów i wyśle ją? Czy dodanie gestu, takiego jak przypinanie, ma być przydatne w celu przełączania się między stanami przejściowymi i trwałymi?

   Każdy z tych czterech punktów decyzyjnych będzie miał wpływ na główne składniki interfejsu użytkownika obiektu.

### <a name="on-object-ui-components"></a>Składniki interfejsu użytkownika na obiekcie

1. Typ kontenera (prezenter zawartości)

    - Pływające

    - Śródwierszowo

2. Typ zawartości

    - Informacje: dane, które mogą być statyczne lub dynamiczne

    - Zasysanych: polecenia, które zmieniają zawartość główną

    - Nawigacja: łącza, które przekierują użytkownika do innego okna lub aplikacji, takiej jak MSDN

3. Gestów

    - Wywołania

    - Zwolnienia

    - Przypinanie

    - Inne interakcje

4. Model trwałości i zatwierdzania

    - Przejściowe

    - Trwałość

    - Automatyczny

    - Na żądanie

5. Wskaźniki otoczenia (opcjonalnie)

    - Podkreślenie squiggle

    - Ikona tagu inteligentnego

    - Inne wskaźniki otoczenia

#### <a name="container-content-presenter-type"></a>Typ kontenera (prezenter zawartości)
 Istnieją dwie główne opcje dostępne do prezentowania treści w punkcie uwagi:

1. **Wbudowany:** prezenter wbudowany, taki jak widok wglądu, który został wprowadzony w Edytorze kodu programu Visual Studio 2013, sprawia, że miejsce na nową zawartość przez przeniesienie istniejącej zawartości.

    - **Preferuj** prezenterów wbudowanych, jeśli oczekujesz, że użytkownicy będą chcieli poświęcić znaczną ilość czasu na odwoływanie się do prezentującej zawartości lub interakcję z nią.

    - **Unikaj** prezenterów wbudowanych, jeśli oczekujesz, że użytkownicy będą chcieli spojrzeć na informacje, które prezentujesz, a następnie kontynuować ich główne zadanie przy minimalnych zakłóceniach.

2. **Przestawne:** przestawny prezenter jest umieszczony jak najbliżej wybranej zawartości, ale nie zmienia układu istniejącej zawartości. Można zastosować różne strategie, takie jak wyświetlanie pływającego panelu zawartości nad najbliższym dostępnym białymi znakami do wybranego symbolu.

    - **Preferuj** pływających prezenterów, jeśli oczekujesz, że użytkownicy będą chcieli spojrzeć na informacje, które prezentujesz, a następnie kontynuować ich główne zadanie z minimalnym zakłóceniem.

    - **Unikaj** pływających prezenterów, jeśli oczekujesz, że użytkownicy będą chcieli poświęcić znaczną ilość czasu na odwoływanie się do prezentującej zawartości lub interakcję z nią.

#### <a name="content-type"></a>Typ zawartości
 Istnieją trzy główne typy zawartości, które mogą być wyświetlane wewnątrz dowolnego kontenera interfejsu użytkownika obiektu. Można pokazać dowolną kombinację tego typu informacji. Trzy typy to:

1. **Informacje:** większość kontenerów interfejsu użytkownika w obiekcie wyświetli pewnego rodzaju treści informacyjne. Zawartość może reprezentować informacje o obecnym stanie środowiska lub może reprezentować informacje o potencjalnym przyszłym stanie środowiska. Na przykład może służyć do pokazywania wpływu określonego polecenia, takich jak refaktoryzacji, na istniejący kod.

    - **Zawsze** używaj kanonicznego przedstawienia wyświetlanych informacji. Na przykład kod powinien wyglądać jak kod, wraz z podświetlaniem składni i powinien być zgodny z czcionką i innymi ustawieniami środowiska ustawionymi przez użytkownika.

    - **Zawsze** należy rozważyć wspieranie wszelkich działań dotyczących zawartości informacyjnej, które byłyby możliwe, jeśli te same informacje są prezentowane jako zawartość główna. Na przykład jeśli przedstawiając istniejący kod wewnątrz kontenera interfejsu użytkownika na obiekcie, zdecydowanie rozważyć wspieranie możliwości przeglądania i modyfikowania tego kodu.

    - **Zawsze** należy rozważyć użycie innego koloru tła, jeśli przedstawienie zawartości informacyjnej, która reprezentuje potencjalny stan przyszłości.

2. Możliwość działania: niektóre kontenery interfejsu użytkownika w obiekcie zapewni możliwość wykonywania niektórych akcji za pomocą zawartości wzorcowej, takich jak wykonywanie operacji refaktoryzacji.

    - **Zawsze** umieszczaj polecenia zasysane oddzielnie od zawartości informacyjnej.

    - **W** razie potrzeby należy zawsze włączać i wyłączać akcje.

    - **Zawsze** zapoznaj się ze standardowymi wytycznymi dotyczącymi reprezentowania poleceń wewnątrz okien dialogowych.

    - **Zawsze** należy zachować liczbę akcji, które są widoczne w kontenerze interfejsu użytkownika na obiekcie do absolutnego minimum. Interakcja z interfejsem użytkownika na obiekcie powinna być lekkim i szybkim działaniem. Użytkownik nie powinien być musiał wydawać energii na zarządzanie kontenerem interfejsu użytkownika na obiekcie.

    - **Zawsze** należy rozważyć, jak i kiedy kontener interfejsu użytkownika na obiekcie zostanie zamknięty lub odrzucony. Najlepszym rozwiązaniem jest każda akcja, która kończy okno dialogowe między zawartością wzorca i szczegółów należy również zamknąć kontener interfejsu użytkownika w obiekcie, gdy ta akcja jest wywoływana.

3. **Nawigacja:** niektóre kontenery interfejsu użytkownika na obiekcie zawierają łącza, które zadają użytkownikowi do innego okna lub aplikacji, takie jak otwieranie artykułu MSDN w przeglądarce sieci Web użytkownika.

    - **Zawsze** dołączaj dowolne łącze nawigacyjne z "Otwórz", aby użytkownicy nie byli zaskoczeni przejściem do innej zawartości.

    - **Zawsze** oddzielaj łącza nawigacyjne od zasysanych łączy.

#### <a name="ambient-indicators-optional"></a>Wskaźniki otoczenia (opcjonalnie)
 Wskaźniki otoczenia mogą być subtelne, w tym tekst przedstawiony w kontrastowym kolorze z pozostałej części kodu lub oczywisty, w tym symbole tickler, takie jak podkreślenia faliste i ikony tagów inteligentnych. Wskaźniki otoczenia informują o dostępności dodatkowych, istotnych informacji. Idealnie, dostarczają przydatnych informacji, nawet bez konieczności użytkownika do interakcji z nimi.

- **Zawsze** umieszczaj wskaźnik otoczenia tak, aby nie rozpraszał ani nie przytłaczał użytkownika. Jeśli nie można ustawić wskaźnika otoczenia w taki sposób, rozważ inne rozwiązanie.

- **Wskaźnik** otoczenia należy zawsze umieszczać jak najbliżej zawartości, z którą jest powiązana.

- **Zawsze** staraj się utworzyć wskaźnik, który podsumowuje informacje, które udostępnia. Należy rozważyć podanie liczby dostępnych elementów danych (na przykład "3 odwołania" zamiast po prostu "Odwołania") lub pomyśl o innym sposobie podsumowania danych.

  - W przypadkach, gdy dane dla wskaźnika nie zawsze mogą być obliczane i wyświetlane, należy natychmiast rozważyć dostarczenie stopniowego sprzężenia zwrotnego podczas obliczania wartości. Rozważmy na przykład animowanie zmian odzwierciedlających aktualizacje dostępnych danych, podobnie jak kafelek na żywo wiadomości e-mail w systemie Windows Phone w miarę zwiększania liczby nieprzeczytanych wiadomości e-mail.

- **Nigdy nie** dodawaj więcej wskaźników niż użytkownik może rozsądnie przyjąć dla danego elementu zawartości. Wskaźniki otoczenia powinny być przydatne bez konieczności interakcji z użytkownikiem. Wskaźniki tracą swoją atmosferę, jeśli wymagają przepełnienia i innych kontroli zarządzania, aby je zobaczyć.

#### <a name="gestures"></a>Gestów
 Kluczowym aspektem pozwalając użytkownikowi zachować fokus na zawartości wzorcowej jest wspieranie odpowiednich gestów, aby otworzyć i odrzucić dodatkową zawartość szczegółów.

- **Zawsze** wymagaj od użytkownika wykonania jakiegoś jawnego gestu, aby otworzyć dodatkową zawartość. Typowe otwarte gesty obejmują:

  - **Hover:** etykietki narzędzi lub nieinteraktywna treść informacyjna

  - **Jawne polecenie:** prezenter wbudowany

  - **Kliknij dwukrotnie wskaźnik otoczenia:** Wyskakujące okno codelens

- **Zawsze** odrzucaj zawartość szczegółów za każdym razem, gdy użytkownik naciśnie klawisz Esc.

- **Zawsze** należy wziąć pod uwagę kontekst interfejsu użytkownika obiektu. W przypadku prezenterów zawartości, które umożliwiają interakcję w kontenerze, należy dokładnie rozważyć, czy wyświetlić dodatkowe informacje na temat aktywowania, co może być destrukcyjne dla przepływu pracy użytkownika.

- **Nigdy nie wyświetlaj** zawartości po najechaniu kursorem, która wydaje się być edytowalna lub zachęca do interakcji z użytkownikiem. To zachowanie może udaremnić użytkowników, jeśli próbują przenieść kursor nad zawartością szczegółów, jak standardowe zachowanie dla etykietki narzędzia jest natychmiast odrzucić, gdy kursor nie jest już nad zawartością główną, która go wyprodukowała.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Modele wyboru

### <a name="overview"></a>Omówienie
 Model wyboru to mechanizm używany do wskazywania i potwierdzania operacji na jednym lub kilku interesujących obiektach w interfejsie użytkownika. W tym temacie omówiono wzorce interakcji wyboru w edytorach dokumentów programu Visual Studio: edytory tekstu, powierzchnie projektowe i powierzchnie modelowania.

 Użytkownicy muszą mieć sposób wskazywania visual studio, co pracują, a visual studio musi odpowiadać przewidywalnie z opinii użytkowników o tym, co działa na. Różnice lub nieporozumienie między użytkownikiem a interfejsem użytkownika może spowodować, że użytkownik nie zauważy akcji, która może mieć niezamierzone konsekwencje. Często błąd pozostaje niezauważony, dopóki użytkownik nie zobaczy, że czegoś brakuje lub uległ zmianie. Modele wyboru są zatem jednym z najważniejszych elementów projektu interfejsu użytkownika. Chociaż modele wyboru w programie Visual Studio są zgodne z systemem Windows, istnieją niewielkie różnice.

 W programie Visual Studio, podobnie jak w systemie Windows, modele wyboru różnią się w zależności od kontekstu, w którym występuje interakcja. Selekcje mogą występować w czterech typach obiektów:

- Tekst

- Obiekty graficzne

- Listy i drzewa

- Siatki

  W obrębie tych obiektów istnieją trzy typy zaznaczeń:

- Ciągłe

- Rozłącznych

- Region

#### <a name="scope"></a>Zakres
 Najważniejszym elementem wyboru jest zapewnienie, że użytkownik wie, w którym oknie pracują (aktywacja) i gdzie znajduje się fokus (wybór). Visual Studio rozszerza funkcje zarządzania oknami w systemie Windows, ale schemat aktywacji jest taki sam: interakcja z oknem przynosi fokus do okna. Visual Studio ma dwa wskaźniki aktywacji: jeden dla okien dokumentów i jeden dla okien narzędzi.

 W przypadku okien dokumentów aktywne okno jest wskazywane przez kartę okna dokumentu przechodzącą do przodu i zmieniającą kolor tła:

 ![Wybór karty Aktywne w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Wybór aktywnej karty**

 W przypadku okien narzędzi aktywne okno jest wskazywane przez zmianę koloru obszaru paska tytułu okna narzędzia:

 ![Wybór aktywnego okna narzędzia w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Aktywne okno narzędzia z podstawowym wyborem węzła**

 ![Wybór nieaktywnego okna narzędzia w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Nieaktywne okno narzędzia z utajonym wyborem węzła**

 Gdy okno jest aktywne, jego fokus jest wskazywany zgodnie z modelami wyboru opisanymi w tej sekcji wytycznych.

#### <a name="context"></a>Kontekst
 Visual Studio został zaprojektowany, aby zachować silną koncepcję kontekstu, śledząc, gdzie użytkownik pracuje. Aktywne jest tylko jedno okno, niezależnie od tego, czy jest to okno narzędzia, czy dokumentu. Jednak okno dokumentu najwyższego rzędu zawsze zachowuje utajony wybór. Chociaż fokus może znajdować się w oknie narzędzia, okno dokumentu, które było ostatnio aktywne, wyświetla zaznaczenie, nawet w stanie nieaktywnym. Odbywa się to w celu zachowania kontekstu użytkownika w dokumencie, który edytowali, pokazując im, że program Visual Studio zachował ich stan, dzięki czemu mogą zwracać i przesuwać płynnie między oknami narzędzi i oknami dokumentów.

### <a name="text-selection"></a>Zaznaczanie tekstu
 Edytory programu Visual Studio, które są ściśle tekstowe, takie jak wbudowany edytor tekstu, używają tego samego modelu wyboru tekstu i wyglądu opisanego na stronie [Myszy i wskaźniki](/windows/desktop/uxguide/inter-mouse) w wskazówki dotyczące interakcji użytkownika systemu Windows w usłudze MSDN. Fokus wejściowy w edytorze tekstu jest wskazywany przez pionowy pasek zwany punktem wstawiania. Punkt wstawiania jest pojedynczy piksel grubości i kolorowe jako odwrotność tego, co pojawia się za nim. Miga zgodnie z szybkością ustawioną przez ustawienie **szybkości migania kursora** na karcie **Szybkość** apletu **Klawiatura** w Panelu sterowania.

#### <a name="contiguous-and-disjoint-selection"></a>Wybór ciągły i rozłączny
 Zaznaczenie w edytorze tekstu jest tylko ciągłe. Rozłączne zaznaczenia tekstu nie są dozwolone, ale powinny być kierowane w edytorach obiektów graficznych. Gdy wskaźnik myszy użytkownika znajduje się nad obszarem tekstowym, kursor zmieni się w wiązkę I. Pojedyncze kliknięcie umieszcza punkt wstawiania w edytorze tekstu w lokalizacji kliknięcia. Przytrzymanie przycisku myszy w dół rozpoczyna podświetlenie zaznaczenia, a zwolnienie przycisku myszy kończy zaznaczenie.

#### <a name="region-selection-box-selection"></a>Wybór regionu (wybór pola)
 Visual Studio obsługuje wybór regionu w edytorze tekstu i to się nazywa zaznaczenie pola. Zaznaczenie pola umożliwia użytkownikowi wybranie regionu tekstu, który nie jest zgodny ze zwykłym strumieniem tekstu. Podobnie jak w przypadku standardowego zaznaczenia tekstu, zaznaczenie musi być ciągłe. Zaznaczenie pola jest inicjowane przez przytrzymanie klawisza Alt podczas przeciągania myszą. Zaznaczenie pola można również zainicjować, przytrzymując klawisze Alt i Shift podczas używania klawiszy strzałek w celu wskazania regionu zaznaczenia. Zaznaczenie pola używa zwykłego podświetlenia zaznaczenia i pokazuje kursor punktu wstawiania migający na końcu obszaru zaznaczenia.

 ![Wybór pola&#41; &#40;regionalnej w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Wybór regionu (pola) w programie Visual Studio**

#### <a name="text-selection-appearance"></a>Wygląd zaznaczenia tekstu
 Kolory używane do aktywnego i nieaktywnego wyboru w edytorze można dostosować. Aby dostosować wygląd edytora, użytkownik może przejść do **narzędzia > opcje**, a następnie poszukaj w obszarze Środowisko > **Czcionki i kolory > Edytor tekstu**.

### <a name="graphical-selection"></a>Wybór graficzny

#### <a name="interaction"></a>Interakcja
 Wybór obiektów graficznych może być złożony i zależy od wielu czynników:

- **Podstawowy model wyboru edytora.** Edytory zawierające obiekty graficzne mogą być również używane do edycji tekstu lub siatek. Na przykład edytor może być edytor oparty na tekście, który obsługuje również rozmieszczenie obiektów graficznych, takich jak visual studio XAML projektanta. Obsługa wielu typów obiektów może mieć wpływ na sposób wybierania przez użytkownika grup składających się z różnych typów obiektów.

- **Obsługa stanów wyboru podstawowego i pomocniczego.** Edytor może zapewnić podstawowe i pomocnicze stany zaznaczenia, dzięki czemu obiekty mogą być edytowane w zgodzie, wyrównane ze sobą, zmienić ich zgrupowanie i tak dalej.

- **Obsługa edycji w miejscu.** Edytorzy mogą również zezwalać na edycję zawartości ich obiektów graficznych. Na przykład kształt prostokąta może również zawierać tekst wewnątrz, który może być zmieniony przez użytkownika. Ponadto tekst ten może być wyśrodkowany lub uzasadniony. Edycja w miejscu obejmuje bardziej szczegółowy poziom interakcji z użytkownikiem i dlatego wymaga odpowiedniego zestawu wskazówek wizualnych do prezentowania informacji o stanie użytkownikowi.

#### <a name="mouse-interaction"></a>Interakcja z myszą

|Dane wejściowe|Wynik|
|-----------|------------|
|Kliknij niezaznaczony obiekt|Zaznacza obiekt i wyświetla linię przerywaną i uchwyty zaznaczenia, jeśli obiekt jest zmienny.|
|Kliknij zaznaczony obiekt|Aktywuje edycję w miejscu, jeśli obiekt go obsługuje. Kliknięcie poza obiektem dezaktywuje tryb edycji w miejscu.|
|Kliknij dwukrotnie obiekt|Otwiera kod za obiektem do edycji i może wstawić domyślny program obsługi zdarzeń, jeśli to konieczne.|
|Wskaż obiekt|Zmienia wskaźnik na kursor przenoszenia. Wygląd obiektu, taki jak jego jasność lub kolor, może ulec zmianie.|
|Wskaż uchwyt zaznaczenia|Zmienia wskaźnik na kursor zmiany rozmiaru. W przypadku obiektów obsługujących obrót niektóre uchwyty zaznaczenia mogą zmieniać wskaźnik na kursor obracania, ponieważ wskaźnik jest inaczej ustawiony (na przykład przeniesiony dalej) względem uchwytu zaznaczenia.|
|Przeciągnij|Nawet jeśli obiekt nie jest wcześniej zaznaczony, zmienia wskaźnik na kursor przenoszenia i przesuwa obiekt.|
|Edytor traci ostrość|Dezaktywuje tryb edycji w miejscu, chociaż obiekt zachowuje zawartość i wygląd, który miał podczas ostatniego stanu operacji/zaznaczenia.|
|Wybór obiektu|Wskażene obramowaniem, linią kropkową lub innym wizualnie odrębnym traktowaniem w celu podświetlenia granicy obiektu.|
|Ponowne rozmiary zaznaczonego obiektu|Wskazywane za pomocą uchwytów wyboru.<br /><br /> Obiekt o zmiennym rozmiarze ma osiem uchwytów, reprezentujących każdy kierunek, w którym można zniego zmieścić. Mniej uchwytów może być używany, jeśli obiekt może być ponownie wysuwalone tylko w niektórych kierunkach. Gdy użytkownik rozmiary obiektu w dół, gdzie osiem uchwytów nie będzie interaktywne, a następnie cztery uchwyty mogą być używane. Rozmiary dojścia powinny być powiązane z metrykami obramowania okna i krawędzi za pomocą funkcji Interfejsu API **GetSystemMetrics** do rozmiaru proporcjonalnie do rozdzielczości ekranu.<br /><br /> ![Uchwyty zmienić rozmiar](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Obracanie zaznaczonego obiektu|![Obracanie uchwytów](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interakcja z klawiaturą

|Dane wejściowe|Wynik|
|-----------|------------|
|Tab|Przenosi wskaźnik fokusu między logiczną kolejność obiektów w edytorze. Może to być od lewej do prawej lub od góry do dołu w zależności od wartości właściwości **TabIndex** (lub równoważne), kolejność tworzenia obiektu i ogólny cel edytora. Shift+Tab odwraca kierunek wskaźnika ostrości.|
|Spacja|Aktywuje tryb przesuwania, gdy naciśnięcie klawisza jest utrzymywane. Do przesuwania położenia rzutni wymagane jest dodatkowe wejście myszy.|
|Ctrl+Spacja|Aktywuje tryb powiększenia, gdy naciśnięcie klawisza jest utrzymywane. Aby zwiększyć i zmniejszyć współczynnik powiększenia, wymagane jest dodatkowe wprowadzanie myszy.|
|Ctrl+Alt+Znak minus|Zmniejsza współczynnik powiększenia o jeden poziom.|
|Ctrl+Alt+Plus Znak|Zwiększa współczynnik powiększenia o jeden poziom.|
|Przesunięcie lub ctrl|Dodaje obiekt do grupy wyboru. Ctrl umożliwia również pojedyncze usuwanie obiektów z grupy wyboru.|
|Enter|Wykonuje domyślne polecenie dla obiektu (zwykle Otwórz lub Edytuj).|
|F2|Aktywuje edycję w miejscu obiektu.|
|Klawisze strzałek|Przesuwa zaznaczone obiekt(-y) w kierunku naciśnięcia klawisza strzałki, małymi krokami (na przykład 1 piksel naraz)|
|Ctrl+klawisze strzałek|Przesuwa zaznaczone obiekt(-y) w kierunku naciśnięcia klawisza strzałki w większych odstępach (na przykład 10 pikseli naraz)|
|Klawisze Shift i strzałki|Zmiana rozmiaru zaznaczonych obiektów w odpowiednim kierunku w małych odstępach (na przykład 1 piksel naraz)|
|Ctrl+Shift+klawisze strzałek|Zmiana rozmiaru zaznaczonych obiektów w odpowiednim kierunku w większych odstępach (na przykład 10 pikseli naraz)|

 Gdy użytkownicy edytują formanty w miejscu, może to mieć sens dla obiektów, aby automatycznie zmienić rozmiar z danych wejściowych użytkownika. Na przykład jeśli użytkownik edytuje formant etykiety, etykieta powinna rosnąć, aby wyświetlić tekst, który użytkownik właśnie wpisał. Jeśli nie zostanie to zrobione, użytkownik musi zmienić rozmiar formantu ręcznie po edycji tekstu. Jeśli użytkownik ma wiele formantów, staje się to zgniłe i bezproduktywne zadanie.

#### <a name="graphical-containers"></a>Pojemniki graficzne
 W niektórych przypadkach edytory graficzne udostępniają kontenery dla innych obiektów graficznych, takich jak formant Panelu formularzy systemu Windows lub formant Układ siatki w projektancie HTML. Jeśli edytor udostępnia kontenery dla innych obiektów graficznych, należy użyć następującego modelu wyboru tylko dla kontenera (obiekty w kontenerze są zgodne ze standardowym modelem, jak opisano powyżej):

|Dane wejściowe|Wynik|
|-----------|------------|
|Pojedyncze kliknięcie na pojemniku|Wybiera obiekt kontenera bez bezpośredniego zaznaczania któregokolwiek z zawartych obiektów. Kontener może zostać przeniesiony i/lub zmieniona za pomocą standardowego wprowadzania danych za pomocą myszy i klawiatury (jak opisano powyżej). Zawarte obiekty są przenoszone w odniesieniu do kontenera, ale zawarte obiekty nie są ponownie rozmiar, chyba że są one również bezpośrednio zaznaczone.|
|Umieść wskaźnik myszy na regionie granicy kontenera|Zamienia mysz w kursor ruchu, wskazując, że kontener można przenieść.|
|Przeciągnij obszar obwiedni kontenera|Zmienia mysz na kursor przenoszenia i przesuwa kontener (i zawarte obiekty wewnątrz). Kontenera nie można przenieść bez uprzedniego wybrania za pomocą jednego kliknięcia.|
|Pojedyncze kliknięcie obiektu w kontenerze|Odznacza kontener (jeśli jest zaznaczony) i wybiera tylko kliknięty obiekt.|
|Shift+click OR Ctrl+click on a contained object and/or container Shift+click OR Ctrl+click on a contained object and/or container|Dodaje kliknięty obiekt do istniejącej grupy zaznaczenia lub zaznaczenia. Jeśli kliknięty obiekt jest już członkiem grupy wyboru, zostanie usunięty z grupy wyboru.|

 Zawarte obiekty powinny być zgodne z podstawowym modelem wyboru, jak opisano w poprzedniej sekcji. Od testowania użyteczności projektanta formularzy systemu Windows użytkownicy oczekiwali bezproblemowego dostępu do zawartych obiektów bez interwencji (narzuconych przez obiekt hermetyzacji).

#### <a name="disjoint-and-region-selections"></a>Rozłączne i wybór regionu
 Edytory obiektów graficznych powinny obsługiwać rozłączne selekcje. Należy pamiętać, że ta grafika nie pokazuje wyglądu formantu dla programu Visual Studio. Szczegółowe specyfikacje wizualne można znaleźć w sekcji [Wygląd wyboru obiektów graficznych.](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance)

 ![Selektory rozłączne i regionu](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Wybór rozłączny**

 Edytory graficzne powinny również udostępniać selekcje regionów ze wskaźnikiem wyboru typu ramki zaznaczenia. Jeśli edytor graficzny obsługuje inne typy obiektów (takie jak tekst), wybór regionu może nie być możliwy w zależności od ograniczeń tych innych typów obiektów.

 ![Zaznaczenie ramki zaznaczenia](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Zaznaczenie ramki zaznaczenia**

#### <a name="primary-and-secondary-selections"></a>Wybór podstawowy i pomocniczy
 Niektóre edytory obiektów graficznych umożliwiają użytkownikowi edytowanie lub wyrównywanie obiektów w grupach. W takim przypadku należy wprowadzić koncepcję selekcji podstawowych i wtórnych. Wybór podstawowy jest obiektem, na który wszystkie inne obiekty odpowiadają na operacje grupy. Obiekt, który użytkownik wybiera jako pierwszy, staje się formantem podstawowym, a kolejne selekcje stają się wyborami pomocniczymi. Wybór podstawowy ma odrębną obróbkę wizualną od wyboru(-ów), aby wskazać, który obiekt jest pierwotny:

 ![Wybór podstawowy i pomocniczy](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Wybór podstawowy z dwoma zaznaczeniami pomocniczymi**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Graficzny wygląd zaznaczenia obiektu
 Uchwyty zaznaczenia są kwadratami narysowanymi w prostokątnym szyku wokół obwiedni obiektu. Poniższy wykres przedstawia przykłady różnych stanów, które obiekt graficzny może mieć z uchwytem, rozmiarem i wyglądem edycji w miejscu. Rozmiar dojścia powinny być powiązane z metryki obramowania okna i krawędzi przy użyciu interfejsu API **GetSystemMetrics.**

| Stan | Wygląd | Szczegóły wizualne |
|-------------------------|---------------| - |
| **Niezaznaczone** | Domyślne | ![Domyślny stan przycisku](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Wybór podstawowy** | Resizable | ![Wybór podstawowy z uchwytami o rozmiarze](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Wybór podstawowy** | Nie zmienny rozmiar | ![Wybór podstawowy bez uchwytów o rozmiarze](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Wybór podstawowy** | Zablokowano | ![Wybór podstawowy zablokowany](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Wybór pomocniczy** | Resizable | ![Wybór pomocniczy z uchwytami o rozmiarze](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Wybór pomocniczy** | Nie zmienny rozmiar | ![Wybór pomocniczy bez uchwytów o rozmiarze](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Wybór pomocniczy** | Zablokowano | ![Wybór pomocniczy zablokowany](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Aktywny interfejs użytkownika** | Domyślne | ![Stan aktywny interfejsu użytkownika](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Wyświetlanie modeli wyboru

#### <a name="tree-view"></a>Widok drzewa
 Zaznaczenie w widoku drzewa jest wyświetlane z prostym podświetleniem. Jeśli użytkownik kliknie nazwę węzła lub ikonę węzła, węzeł zostanie wybrany. Trójkątne glify po lewej stronie węzła rozwinąć lub umowy kontroli drzewa, ale nie wpływają na wybór użytkownika, z jednym wyjątkiem: po zwinięciu węzła nadrzędnego, gdy zaznaczenie znajduje się na podrzędnym tego węzła, zaznaczenie przenosi się do elementu nadrzędnego.

 ![Typowy widok drzewa w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Typowy widok drzewa w programie Visual Studio**

 Widoki drzewa mogą obsługiwać ciągłe i rozłączne zaznaczenia, nawet na wielu poziomach w drzewie. Ciągłe lub rozłączne wiele zaznaczeń musi być dokonane na widocznych węzłów drzewa. Jeśli węzeł jest zwinięty, wybór rozłączny zostanie utracony, a węzeł, który został zwinięty, uzyskuje zaznaczenie. W ten sposób użytkownik może zobaczyć węzły, których dotyczy operacja. Gdy węzły są zwinięte, staje się niejasne, które węzły mogą mieć wpływ.

 Gdy węzeł nadrzędny jest zaznaczony, operacja powinna mieć zastosowanie do elementu nadrzędnego, chociaż mogą wystąpić przypadki, w których ma sens dla operacji, aby zastosować do elementu nadrzędnego i wszystkich jego wiązek łajda. W takim przypadku podaj dodatkowy interfejs użytkownika podczas operacji, takie jak pole wyboru lub okno dialogowe potwierdzenia, aby opcja "zastosuj do wszystkich śr" była jawna dla użytkownika.

##### <a name="renaming"></a>Zmienianie nazw
 Jeśli węzły w drzewie obsługują zmianę nazwy, zmiana nazwy powinna być wykonana w miejscu. Operacja w miejscu powinna być standardem we wszystkich formantów drzewa w programie Visual Studio. Podaj polecenie zmień nazwę, które natychmiast aktywuje tryb edycji w miejscu, z zaznaczeniem tekstu obejmującym całą nazwę węzła, gotowym do zaakceptowania danych wejściowych użytkownika. Jeśli węzeł reprezentuje plik, nazwa pliku powinna zawierać rozszerzenie. Podświetlenie zaznaczenia powinno zawierać tylko treść nazwy pliku, a nie rozszerzenie.

|Dane wejściowe|Wynik|
|-----------|------------|
|klawisz ENTER|Zatwierdza operację zmiany nazwy|
|Esc|Anuluje operację zmiany nazwy|
|Kliknięcie poza regionem edycji w miejscu|Zatwierdza operację zmiany nazwy|
|Cofanie|Łatwe cofanie, aby anulować operację zmiany nazwy|

#### <a name="selection-within-lists-and-grid-controls"></a>Zaznaczanie na listach i formanty siatki
 Kluczową koncepcją w wyborze listy jest to, że jest oparta na wierszach, co oznacza, że po dokonaniu zaznaczenia cały wiersz jest wybierany jako jednostka. Natomiast siatki mogą zezwalać na wybór określonych komórek bez wpływu na inny aspekt wiersza. Siatki mogą również zawierać hierarchię zagnieżdżonych wierszy (na przykład w TreeGrid), które umożliwiają zaznaczanie całych gałęzi hierarchii i odznaczanie ich przez interakcję z wierszami nadrzędnymi. Zaznaczenie na listach jest wyświetlane przez prosty kolor podświetlenia w całym wierszu danych. Fokus jest wyświetlany przez jednopikselowe kropkowane obramowanie wokół bieżącego edytowanego wiersza lub komórki (wiersz, jeśli wszystkie komórki są tylko do odczytu).

> [!NOTE]
> **Skupienie** i **wybór** to różne pojęcia. *Fokus* jest wskazanie, który element interfejsu użytkownika jest przeznaczony do odbierania danych wejściowych nie jawnie skierowane do innego obiektu, podczas gdy *wybór* odnosi się do stanu włączenia obiektu w zestawie obiektów, na których mogą mieć miejsce kolejne operacje.

 Selekcje na listach mogą być ciągłe, rozłączne lub regionowe. Gdy dozwolone jest wiele wyborów, wybór ciągły i rozłączny powinien być zawsze obsługiwany, podczas gdy obsługa wyborów regionu (pola) jest opcjonalna. Zaznaczenia regionu są inicjowane przez przeciąganie w białym odstępie treści listy.

| Obiekt | Wybór |
|--------|------------|
| List | Ciągłe |
| List | Rozłącznych |
| List | Region |

 Kliknięcie raz na liście powoduje zaznaczenie wiersza, w którym nastąpiło kliknięcie. Jeśli użytkownik kliknie komórkę listy obsługującą edycję w miejscu, komórka zostanie natychmiast aktywowana w celu edycji w miejscu. W przeciwnym razie cały wiersz jest natychmiast zaznaczony i pokazuje podświetlenie.

 Przeciąganie w treści listy powoduje jedną z trzech rzeczy:

- Inicjuje wybór regionu, jeśli lista go obsługuje, a wskaźnik myszy znajduje się w odstępie

- Inicjuje operację przeciągania/upuszczania, jeśli komórka listy lub wiersz obsługuje źródło przeciągania

- Wybiera bieżący wiersz

##### <a name="in-place-editing"></a>Edycja w miejscu
 Gdy edycja w miejscu jest dozwolona, istnieją dwa podstawowe modele: prosty formant edycji i selektor właściwości. Dzięki prostemu formancie edycji zawartość jest podświetlona i gotowa do wprowadzania danych przez użytkownika, gdy tylko zostanie aktywowana edycja w miejscu. W przypadku zaimplementowania selektora właściwości przycisk, który wywołuje selektor właściwości jest wyświetlany po włączeniu trybu edycji w miejscu, a bieżące zaznaczenie nie jest wyróżnione. Przycisk selektora powinien być prawonaprawny w komórce. Przykłady edycji w miejscu można znaleźć w **oknie właściwości** i na **liście zadań** w programie Visual Studio.

##### <a name="keyboard-support"></a>Obsługa klawiatury
 Obsługa klawiatury do wyboru na listach i w siatkach jest zgodna ze standardowymi konwencjami systemu Windows:

- Klawisze strzałek nawigują po liście, zaznaczając każdy wiersz/komórkę podczas przenoszenia fokusu.

- Shift + strzałka wykonuje ciągły wybór w kierunku klawiszy strzałek.

- Ctrl + strzałka, po której następuje spacja przełącza między dodawaniem i usuwaniem elementów listy z zaznaczenia, tworząc rozłączne zaznaczenie.

- W przypadku siatek zawierających hierarchie zagnieżdżone klawisze Strzałka w prawo rozwija wiersz nadrzędny, a klawisz Strzałka w lewo zwija jeden.

- Klawisz Tab przenosi fokus między komórkami w bieżącym wierszu, jeśli komórki są edytowalne.

- Klawisz Enter wykonuje polecenie domyślne na elemencie na liście (często **Otwórz).**

- Klawisz F2 aktywuje edycję w miejscu dla aktualnie wybranej komórki.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Ustawienia trwałości i zapisywania

### <a name="overview"></a>Omówienie
 Chociaż każdy składnik oprogramowania w programie Visual Studio jest zwykle odpowiedzialny za swój własny stan i trwałość, Visual Studio automatycznie zapisuje ustawienia w niektórych przypadkach, na przykład w przypadku rozmiarów okien i pozycji. Poniższa tabela to kombinacja ustawień zapisanych automatycznie i ustawień, które wymagają wyraźnego użytkownika lub zaprogramowanej akcji.

|Obiekt|Co zapisać|Kiedy zapisać|Gdzie zapisać|
|------------|------------------|------------------|-------------------|
|Wybieralny obiekt (na przykład wiersz kodu)|Punkt przerwania w wierszu kodu<br /><br /> Skrót użytkownika skojarzony z wierszem kodu|Po zapisaniu projektu|Plik **opcji użytkownika (.suo)** dla projektu|
|Okno dialogowe|Lokalizacja okna dialogowego, jeśli zostało przeniesione<br /><br /> Widok, który użytkownik ostatnio używał w oknie dialogowym|Po zamknięciu okna dialogowego<br /><br /> Po zakończeniu sesji programu Visual Studio|W pamięci<br /><br /> Rejestr w **HKEY_Current_User**|
|Okno|Wielkość i lokalizacja okna|Po zamknięciu okna<br /><br /> Gdy zmienia się tryb programu Visual Studio<br /><br /> Po zakończeniu sesji programu Visual Studio|Plik **opcji użytkownika (.suo)** dla projektu<br /><br /> Plik opcji niestandardowych dla ustawień okna|
|Dokument|Bieżące zaznaczenie w dokumencie<br /><br /> Widok dokumentu<br /><br /> Ostatnie kilka miejsc, które użytkownik odwiedził|Po zapisaniu dokumentu|Plik **opcji użytkownika (.suo)** dla projektu|
|Projekt|Odwołania do plików<br /><br /> Odwołania do katalogów na dysku<br /><br /> Odniesienia do innego oprogramowania<br /><br /> Składniki<br /><br /> Informacje o stanie samego projektu|Po zapisaniu projektu|Plik projektu|
|Rozwiązanie|Odniesienia do projektów<br /><br /> Odwołania do plików|Po zapisaniu projektu lub rozwiązania|Plik **rozwiązania (.sln)**|
|Ustawienia w **narzędziach > opcje**|Dostosowania klawiatury<br /><br /> Dostosowania paska narzędzi<br /><br /> Schematy kolorów|Po zamknięciu okna dialogowego **Opcje > narzędzia**<br /><br /> Po zakończeniu sesji programu Visual Studio|Rejestr w **HKEY_Current_User**|

 To, co robi użytkownik i kiedy to robi, decyduje o tym, czy ustawienie jest zapisywane w pamięci (podczas sesji), zapisywane na dysku (w sesjach jako ustawienie rejestru), jako część samego pliku projektu lub rozwiązania, jako część pliku **opcji rozwiązania (.suo),** czy jako plik ustawień niestandardowych, o którym wie tylko ten składnik oprogramowania. Powyższa tabela przedstawia kilka zdarzeń, w których można zapisać ustawienia. Istnieją jednak inne czasy, w których można zapisać stan:

- Gdy użytkownik zmieni lokalizację w oknie dialogowym lub oknie

- Gdy użytkownik przenosi fokus do innego okna

- Gdy użytkownik przełącza się z projektu do trybu debugowania

- Gdy użytkownik wyloguje się ze swojego konta

- Gdy komputer przejdzie w stan hibernacji lub wyłączy się

- Gdy komputer/dysk twardy ma zostać sformatowany i ponownie skonfigurowany

### <a name="window-configurations"></a>Konfiguracje okien
 Konfiguracja okna jest podstawową prezentacją środowiska programistycznego - jest to schemat składający się z listy okien narzędziowych obecnych i sposobu, w jaki są one rozmieszczone. W przypadku okien zarządzanych przez ide (IDE windows), informacje o układzie są zachowywane na użytkownika, więc gdy użytkownik uruchamia IDE, układ okna jest taki sam, jak podczas ostatniego zamykania programu Visual Studio. Stan i położenie okien IDE jest zachowywany w pliku opcji niestandardowych w formacie XML. Okna narzędzi, które są tworzone przez pakiety ładowane do IDE utrwalić ich informacje o stanie w rejestrze i może lub nie może być na użytkownika.

#### <a name="profile-specific-layouts"></a>Układy specyficzne dla profilu
 Każdy profil zawiera układy okien narzędzi, zorganizowane w sposób znany określonym personas dewelopera (Visual C++ deweloperzy oczekują, aby zobaczyć **Eksploratora rozwiązań** po lewej stronie IDE, podczas gdy deweloperzy języka C# oczekują, aby zobaczyć **Eksploratora rozwiązań** po prawej stronie). Układy okien specyficzne dla profilu są ładowane po wybraniu przez użytkownika profilu podczas uruchamiania. Autor pakietu należy określić układ okna najbardziej odpowiednie dla ich doświadczenia klienta, wiedząc, że zmiany, które użytkownik wprowadza do konfiguracji okna zostaną następnie utrwalone.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Wprowadzanie dotykowe
 Użytkownicy coraz częściej korzystają z produktów deweloperskich firmy Microsoft na urządzeniach dotykowych. Istnieją jednak bariery, które utrudniają korzystanie z narzędzi programistycznych na urządzeniach dotykowych. Użytkownicy oczekują, że nasze produkty zapewnią niezawodne i precyzyjne wrażenia dotykowe. Celem tych wskazówek jest informowanie decyzji o tym, które funkcje dotykowe do włączenia i zachęcić spójne środowisko dotykowe w programie Visual Studio i powiązanych produktach.

### <a name="levels-of-experience"></a>Poziom doświadczenia
 Poniższe poziomy doświadczenia mają służyć jako przewodnik, aby pomóc zespołom w podjęciu decyzji, które możliwości dotykowe oferują na podstawie pożądanego poziomu zainteresowania inwestycjami w dotyku.

- **Podstawowe doświadczenie** jest dla zespołów, które chcą zapewnić możliwości dotykowe, więc nie ma ślepych zaułków w całej swojej pracy.

- **Zoptymalizowane środowisko** jest dla zespołów, które chcą zapewnić najbardziej typowe funkcje dotykowe (na przykład te zazwyczaj dostępne w aplikacjach przeglądarki internetowej).

- Podwyższone **środowisko** jest dla zespołów, które chcą dodać możliwości, takie jak gesty lub inne opcjonalne funkcje, które mogą sprawić, że ich aplikacja jest przyjazna dla dotyku.

||Podstawowe doświadczenie|Zoptymalizowane środowisko|Podwyższone doświadczenie|
|-|----------------------|--------------------------|-------------------------|
|Umożliwia użytkownikom ...|Napraw kod i rozwiązanie/odczyt na poziomie projektu bez ślepych zaułków|Wykonywanie zadań konserwacji, refaktoryzatorów i nawigacji|Działaj z ufnością, niezmiennie intuicyjną i płynną|
|Edytor|Przesuwanie i zaznaczanie dotykowe<br /><br /> Dotknięcie paska przewijania, aby przejść i nacisnąć +przeciągnąć|Powiększanie szczypania<br /><br /> Szybkie przewijanie<br /><br /> Wybór<br /><br /> Łatwe korzystanie z menu kontekstowego||
|Okna narzędzi wierzchniej|Przesuwanie listy<br /><br /> Wybór towaru<br /><br /> Dotknięcie paska przewijania, aby przejść i nacisnąć +przeciągnąć|Łatwe przewijanie i wybór elementów||
|Windowing||Okno Zmienić rozmiar<br /><br /> Szybki dostęp||
|Dobrze dokumentuj||Łatwa nawigacja między otwartymi plikami||
|Gestów||Upewnij się, że typowe gesty działają w całym środowisko IDE|Akcje oparte na gestach<br /><br /> Obsługa przeciągania i upuszczania i projektantów|
|Inne zagadnienia|||Niestandardowa klawiatura ekranowa|

#### <a name="gestures"></a>Gestów
 Gesty zapewniają użytkownikom skrót do poleceń, które w przeciwnym razie mogą wymagać bardziej skomplikowanej interakcji. Zapoznaj się z wytycznymi systemu Windows dotyczącymi [typowych gestów dotykowych dla aplikacji klasycznych](/windows/desktop/wintouch/windows-touch-gestures-overview)i postępuj zgodnie z tymi wskazówkami dotyczącymi większości gestów, w tym prostych gestów, takich jak przesuwanie i powiększanie.
