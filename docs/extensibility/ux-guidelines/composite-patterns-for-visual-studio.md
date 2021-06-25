---
title: Wzorce złożone dla Visual Studio | Microsoft Docs
description: Dowiedz się więcej na temat ważnych wzorców złożonych dla spójności Visual Studio. Wzorce złożone łączą elementy interakcji i projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8b84baa7be7449b8edb6241e415fc90c9acd594
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901425"
---
# <a name="composite-patterns-for-visual-studio"></a>Wzorce złożone dla programu Visual Studio
Wzorce złożone łączą elementy interakcji i projektu w różnych konfiguracjach. Niektóre z najważniejszych wzorców złożonych w Visual Studio pod względem spójności to:

- [Wizualizacja danych](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfejs użytkownika obiektu i podgląd](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modele wyboru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Ustawienia trwałości i zapisywania](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Wizualizacja danych

### <a name="overview"></a>Omówienie
 Wykresy to wizualny sposób agregowania i wizualizowania danych w celu ulepszania procesu podejmowania decyzji. Mogą one pomóc użytkownikom w obliczu wielu danych, ale w niewielkim znaczeniu widzą, co przyciąga uwagę i co może wymagać akcji.

 Użytkownik będzie korzystać z wykresu, jeśli zostanie spełnione dowolne z następujących warunków:

- Czy wykres pomoże użytkownikom identyfikować zadania, w których mogą wykonywać działania?

- Czy wykres umożliwi użytkownikom prognozowanie konsekwencji potencjalnych zmian?

- Czy wykres pomoże użytkownikom odkrywać trendy i identyfikować wzorce?

- Czy wykres umożliwi użytkownikom podejmowanie lepszych decyzji?

- Czy wykres pomoże odpowiedzieć na konkretne pytanie, które użytkownicy mogą mieć w danym kontekście?

#### <a name="general-rules-for-charts"></a>Ogólne reguły dotyczące wykresów

- Wyraźnie oznacz etykietami dane. Ilustracje bez wyjaśnienia są po prostu całkiem proste.

- Osie startowe od zera, aby uniknąć pochyłych proporcji. Długość linii i rozmiar słupka są ważnymi wizualnymi wskaźnikami do zrozumienia relacji między punktami danych.

- Tworzenie wykresów, a nie infografiki. Infografiki to reprezentacje reprezentacji danych, a ich głównym celem jest wizualne opowiadanie historii. Wykresy mogą (i powinny) być atrakcyjne wizualnie, ale niech dane mówią same za siebie.

- Unikaj skeumorfizmów, obrazowych grafów słupkowych, znaczników kontrastu i innych dotyków infografiki.

- Nie używaj efektów 3D jako elementu dekoracyjnego. Używaj ich tylko wtedy, gdy są one naprawdę integralne dla możliwości zrozumienia informacji przez użytkownika.

- Unikaj używania wielu linii i wypełnień, ponieważ więcej niż dwa kolory mogą utrudnić prawidłowy odczyt i interpretację tego typu wykresu.

- Nie należy używać wykresu (ani żadnej ilustracji) jako jedynego środka zrozumienia koncepcji lub interakcji z danymi. Stanowi to trudności dla użytkowników z wadami wzroku.

- Nie używaj wykresów jako elementów dekoracyjnych ani dekoracyjnych na stronie. Innymi słowy, jeśli wykres nie dodaje żadnej wartości ani nie pomaga użytkownikom w rozwiązaniu problemu, nie używaj go.

### <a name="chart-types"></a>Typy wykresów
 Typy wykresów używanych w programie Visual Studio obejmują wykresy słupkowe, liniowe, zmodyfikowany wykres kołowy znany jako wykres pierścieniowy lub "wykres pierścieniowy", osie czasu, wykresy punktowe (zwane również "wykresami klastrowymi") i wykresy Gantta. Każdy typ wykresu jest przydatny do komunikowania informacji innego typu.

### <a name="other-charting-considerations"></a>Inne zagadnienia dotyczące wykresów

#### <a name="color"></a>Kolor
 Istnieje określona paleta kolorów wykresów zdefiniowanych do użycia w Visual Studio. Paleta jest dostępna dla głównych typów niewidomości kolorów, a kolory można rozróżnić nawet wtedy, gdy są używane jako bardzo wąskie wycinki kolorów. Tych kolorów można używać w dowolnej kombinacji dla dowolnego typu wykresu lub grafu w interfejsie użytkownika. Nie musisz używać wszystkich siedmiu kolorów, jeśli nie potrzebujesz tak wielu odrębnych kolorów. Te kolory nie były przeznaczone do zastosowania z żadnymi elementami pierwszego planu, dlatego nie umieszczaj tekstu ani glifów na tych kolorach. Te kolory powinny być zakodowane i widoczne dla użytkowników w obszarze Narzędzia **> opcje** (zobacz Udostępnianie kolorów dla [użytkowników końcowych).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Próbkę|Hex|RGB|
|------------|---------|---------|
|![Swatch 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Swatch BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Swatch FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Swatch 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Swatch 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Swatch 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Swatch B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfejs użytkownika obiektu i podgląd
 Ta sekcja zawiera kontekst do wglądu, znanego również jako widok podglądu kodu, typ interfejsu użytkownika obiektu unikatowy dla Visual Studio.

### <a name="overview"></a>Omówienie

- Interfejs użytkownika obiektu on-object powinien zapewnić użytkownikowi więcej informacji lub interakcyjność bez utraty jego głównego zadania.

- Główny wzorzec dla interfejsu użytkownika obiektu w Visual Studio jest znany jako "informacje w punkcie uwagi".

- Interfejs użytkownika obiektu on-object w Visual Studio jest w tekście lub zmiennoprzecinający i trwały albo przejściowy.

  - Widok podglądu kodu, typ interfejsu użytkownika obiektu w Visual Studio, jest w tekście i jest trwały.

  - CodeLens, typ interfejsu użytkownika obiektu w Visual Studio, jest zmiennoprzecinający i przejściowy

  Zrozumienie sposobu działania fragmentu kodu lub znalezienie szczegółów dotyczących tego kodu często wymaga od dewelopera przełączenia kontekstu i przejście do innej zawartości lub innego okna. Te zmiany kontekstowe mogą zakłócać działanie, ponieważ użytkownicy mogą utracić fokus na oryginalnym zadaniu, jeśli opuszczą okno główne. Ponadto uzyskanie oryginalnego kontekstu może być trudne, zwłaszcza jeśli przełączanie okien spowodowało ukrycie oryginalnego kodu przez inny interfejs użytkownika.

  Interfejs użytkownika obiektu jest zgodny ze wzorcem nazywanym "informacjami w punkcie uwagi". Te komunikaty, okna podręczne i okna dialogowe zapewniają użytkownikom dodatkowe, istotne informacje, które dodają wyjaśnienie lub interakcyjność bez koncentracji na ich głównym zadaniu. Przykłady interfejsu użytkownika obiektu to okna podręczne wyświetlane, gdy użytkownik zatrzyma wskaźnik myszy na ikonie w obszarze powiadomień, czerwony zygsk pod błędnie napisanym słowem oraz widok podglądu wprowadzony w Visual Studio 2013.

### <a name="decision-points"></a>Punkty decyzyjne
 W Visual Studio istnieje kilka sposobów wykorzystania tego wzorca informacji w punkcie uwagi. Wybór odpowiedniego mechanizmu i wdrożenie go w spójny, przewidywalny sposób ma kluczowe znaczenie dla ogólnego działania. W przeciwnym razie użytkownikom może zostać przedstawione mylące lub niespójne środowisko, które odwraca uwagę od samej zawartości.

#### <a name="relationships-between-master-and-detail-content"></a>Relacje między zawartością wzorzec i szczegół
 Informacje w punkcie uwagi są używane do wyświetlania relacji między zawartością, na których koncentruje się użytkownik (zawartość "główna") i dodatkową powiązaną zawartością (zawartością "szczegółową"). W tym wzorcu zawartość szczegółów jest wyraźnie powiązana z zawartością, z pomocą których użytkownik pracuje, i może być wyświetlana w pobliżu głównej zawartości. Informacje uzupełniające lub informacje, których nie można podsumować bez przeciążenia zawartości głównej, powinny być zgodne z innym wzorcem, takim jak okno narzędzi.

- **Zawsze** wyświetlaj zawartość szczegółów w pobliżu głównej zawartości.

- **Zawsze** upewnij się, że zawartość szczegółów nadal umożliwia użytkownikowi skoncentrowanie się na głównej zawartości. Często najlepszym sposobem osiągnięcia tego celu jest renderowanie zawartości szczegółów jak najbardziej zbliżonej do głównej zawartości. Można to zrobić przez renderowanie zawartości szczegółów w oknie podręcznym obok głównej zawartości lub przez renderowanie zawartości szczegółów w tekście poniżej zawartości głównej.

- **Nigdy** nie używaj informacji w punkcie uwagi, który odciąga użytkownika od głównej zawartości. Jeśli użytkownicy muszą oddzielnie wyświetlać szczegółową zawartość, udostępnij jawną akcję, która umożliwia użytkownikowi taką czynność.

#### <a name="design-details"></a>Szczegóły projektu
 Gdy ustalisz, że interfejs użytkownika obiektu jest właściwym wyborem, istnieją cztery główne zagadnienia dotyczące projektowania:

1. **Trwałość:** czy zawartość powinna być trwała, czy przejściowa?
   Czy użytkownicy będą chcieli zachować widoczność informacji, aby odwoływać się do informacji lub wchodzić z nimi w interakcje? A może użytkownicy będą chcieli szybko uzyskać dostęp do informacji, a następnie kontynuować swoje główne zadanie?

2. **Typ zawartości:** czy zawartość będzie informacyjna, z akcjami lub nawigacją?
   Czy użytkownik potrzebuje dodatkowych szczegółów dotyczących zawartości głównej? Czy użytkownik musi wykonać zadanie, które ma wpływ na zawartość master? Czy może użytkownik musi być skierowany do innego zasobu?

3. **Typ wskaźnika:** czy wskaźnik otoczenia ma sens?
   Czy informacje można podsumować w użyteczny sposób i wyświetlić bez przeciążania głównej zawartości?

4. **Gesty:** jakie gesty będą używane do wywoływania i odrzucania interfejsu użytkownika?
   W jaki sposób użytkownik będzie odbierać zawartość szczegółów i ją wysyłać? Czy dodanie gestu, takiego jak przypinanie, ma wartość, aby przełączać się między stanami przejściowymi i trwałymi?

   Każdy z tych czterech punktów decyzyjnych będzie miał wpływ na główne składniki interfejsu użytkownika obiektu.

### <a name="on-object-ui-components"></a>Składniki interfejsu użytkownika obiektu

1. Typ kontenera (prezenter zawartości)

    - Pływające

    - Śródwierszowo

2. Typ zawartości

    - Informacyjne: dane, które mogą być statyczne lub dynamiczne

    - Z akcjami: polecenia, które zmieniają zawartość wzorcową

    - Nawigacja: linki, które przejmą użytkownika do innego okna lub aplikacji, takiej jak MSDN

3. Gestów

    - Invocation

    - Zwolnienia

    - Przypinanie

    - Inne interakcje

4. Model trwałości i zatwierdzania

    - Przejściowe

    - Trwałość

    - Automatyczny

    - Na żądanie

5. Wskaźniki otoczenia (opcjonalnie)

    - Podkreślenia zygzyka

    - Ikona tagu inteligentnego

    - Inne wskaźniki otoczenia

#### <a name="container-content-presenter-type"></a>Typ kontenera (prezenter zawartości)
 Dostępne są dwie główne opcje prezentowania zawartości w punkcie uwagi:

1. **Wbudowane:** prezenter w tekście, taki jak widok podglądu wprowadzony w edytorze kodu Visual Studio 2013, tworzy miejsce dla nowej zawartości, przesuwając istniejącą zawartość.

    - **Preferuj** prezenterów w tekście, jeśli spodziewasz się, że użytkownicy będą chcieli poświęcić znaczną ilość czasu na odwoływanie się do prezentej zawartości lub interakcję z nimi.

    - **Unikaj** prezenterów w tekście, jeśli spodziewasz się, że użytkownicy będą chcieli uzyskać dostęp do prezentowych informacji, a następnie kontynuować swoje główne zadanie przy minimalnych zakłóceniach.

2.  Zmiennoprzecinkową: przestawny prezenter jest umieszczony jak najbardziej blisko wybranej zawartości, ale nie zmienia układu istniejącej zawartości. Można stosować różne strategie, takie jak wyświetlanie przestawnych paneli zawartości w najbliższym dostępnym białym miejscu dla wybranego symbolu.

    - **Preferuj** osoby prezenterów zmiennoprzecinków, jeśli spodziewasz się, że użytkownicy będą chcieli uzyskać dostęp do prezentowych informacji, a następnie kontynuować swoje główne zadanie przy minimalnych zakłóceniach.

    - **Unikaj** prezenterów zmiennoprzecinków, jeśli spodziewasz się, że użytkownicy będą chcieli poświęcić znaczną ilość czasu na odwoływanie się do prezentej zawartości lub interakcję z nimi.

#### <a name="content-type"></a>Typ zawartości
 Istnieją trzy główne typy zawartości, które mogą być wyświetlane wewnątrz dowolnego kontenera interfejsu użytkownika obiektu. Można wyświetlać dowolną kombinację tych typów informacji. Te trzy typy to:

1. **Informacyjne: większość** kontenerów interfejsu użytkownika obiektów będzie wyświetlać jakąś zawartość informacyjną. Zawartość może reprezentować informacje o obecnym stanie środowiska lub może reprezentować informacje o potencjalnym przyszłym stanie środowiska. Na przykład może służyć do pokazania wpływu określonego polecenia, takiego jak refaktoryzacja, na istniejący kod.

    - **Zawsze** używaj kanonicznej reprezentacji wyświetlanych informacji. Na przykład kod powinien wyglądać jak kod z wyróżnieniami składni i powinien przestrzegać wszystkich ustawień czcionki i innych ustawień środowiska ustawionych przez użytkownika.

    - **Zawsze** należy rozważyć obsługę wszelkich akcji dotyczących zawartości informacyjnej, które byłyby możliwe, gdyby te same informacje były prezentowane jako zawartość główna. Na przykład w przypadku prezentowania istniejącego kodu wewnątrz kontenera interfejsu użytkownika obiektu zdecydowanie rozważ obsługę możliwości przeglądania i modyfikowania tego kodu.

    - **Zawsze** należy rozważyć użycie innego koloru tła w przypadku prezentowania zawartości informacyjnej, która reprezentuje potencjalny przyszły stan.

2. Z możliwością działania: niektóre kontenery interfejsu użytkownika obiektu zapewniają możliwość wykonania pewnych działań na głównej zawartości, takich jak wykonanie operacji refaktoryzacji.

    - **Polecenia** z akcjami należy zawsze pozycjonować niezależnie od zawartości informacyjnej.

    - **Zawsze włączaj** i wyłączaj akcje, gdy jest to konieczne.

    - **Zawsze** należy zapoznać się ze standardowymi wytycznymi dotyczącymi reprezentowania poleceń wewnątrz okien dialogowych.

    - **Zawsze** minimaliuj bezwzględnie liczbę akcji, które są widoczne w kontenerze interfejsu użytkownika obiektu. Interakcja z interfejsem użytkownika obiektu powinna być lekkim, szybkim interfejsem użytkownika. Użytkownik nie powinien mieć więcej energii na zarządzanie kontenerem interfejsu użytkownika obiektu.

    - **Zawsze zastanów** się, jak i kiedy kontener interfejsu użytkownika obiektu będzie zamknięty lub odrzucony. Najlepszym rozwiązaniem jest zamknięcie kontenera interfejsu użytkownika obiektu po wywołaniu każdej akcji, która kończy okno dialogowe między zawartością wzorzec i szczegół.

3. **Nawigacja:** niektóre kontenery interfejsu użytkownika obiektu zawierają linki, które przekierowywają użytkownika do innego okna lub aplikacji, na przykład otwierania artykułu MSDN w przeglądarce internetowej użytkownika.

    - **Zawsze** dołączaj dowolny link nawigacyjny z właściwością "Otwórz", aby użytkownicy nie byli zaskoczeni przejściem do innej zawartości.

    - **Zawsze oddzielaj** linki nawigacyjne od linków z akcjami.

#### <a name="ambient-indicators-optional"></a>Wskaźniki otoczenia (opcjonalnie)
 Wskaźniki otoczenia mogą być subtelne, w tym tekst przedstawiony w kontrastującym kolorze z resztą kodu, lub oczywiste, w tym symbole znaczników, takie jak podkreślenia zygmki i ikony tagów inteligentnych. Wskaźniki otoczenia informują o dostępności dodatkowych, istotnych informacji. W idealnym przypadku zapewniają przydatne informacje nawet bez konieczności interakcji z nimi przez użytkownika.

- **Zawsze** umieść wskaźnik otoczenia, aby nie rozpraszał ani nie przeciążał użytkownika. Jeśli nie można ustawić wskaźnika otoczenia w taki sposób, rozważ inne rozwiązanie.

- **Zawsze** umieść wskaźnik otoczenia tak blisko zawartości, z która jest powiązany.

- **Zawsze** próbuj utworzyć wskaźnik, który podsumowuje udostępniane informacje. Rozważ podanie liczby dostępnych elementów danych (na przykład "3 odwołania" zamiast po prostu "Odwołania") lub rozważ inny sposób podsumowania danych.

  - W przypadkach, gdy dane dla wskaźnika nie zawsze mogą być obliczane i wyświetlane, natychmiast rozważ przekazywanie progresywnych informacji zwrotnych, ponieważ wartości są obliczane. Rozważ na przykład animowanie zmian, które odzwierciedlają aktualizacje dostępnych danych, podobnie jak kafelek wiadomości e-mail na żywo na stronie Windows Phone odświeża się wraz ze wzrostem liczby nieprzeczytanych wiadomości e-mail.

- **Nigdy** nie dodawaj większej liczby wskaźników, niż użytkownik może względnie wziąć pod uwagę dla danej zawartości. Wskaźniki otoczenia powinny być przydatne bez konieczności interakcji z użytkownikiem. Wskaźniki tracą swoją ambience, jeśli wymagają przepełnienia i innych kontrolek zarządzania w celu ich wyświetlenia.

#### <a name="gestures"></a>Gestów
 Kluczowym aspektem umożliwiającym użytkownikowi skoncentrowanie się na zawartości głównej jest obsługa odpowiednich gestów otwierania i odrzucania dodatkowej zawartości szczegółowej.

- **Zawsze** wymagaj od użytkownika wykonania pewnego jawnego gestu w celu otwarcia dodatkowej zawartości. Typowe otwarte gesty obejmują:

  - **Aktywowanie:** etykietki narzędzi lub nieinterakcyjna zawartość informacyjna

  - **Jawne polecenie:** prezenter w tekście

  - **Kliknij dwukrotnie wskaźnik otoczenia:** Okno podręczne codeLens

- **Zawsze** odrzucaj zawartość szczegółów za każdym razem, gdy użytkownik naciśnie klawisz Esc.

- **Zawsze** należy wziąć pod uwagę kontekst interfejsu użytkownika obiektu. W przypadku prezenterów zawartości, którzy umożliwiają interakcję w kontenerze, dokładnie zastanów się, czy po zatrzymaniu wskaźnika myszy mają być wyświetlane dodatkowe informacje, co może zakłócać przepływ pracy użytkownika.

- **Nigdy nie** wyświetlaj zawartości po najechaniu kursorem, który wydaje się być edytowalny lub zachęca do interakcji z użytkownikiem. To zachowanie może frustrować użytkowników, jeśli spróbują przenieść kursor na zawartość szczegółów, ponieważ standardowym zachowaniem etykietki narzędzia jest natychmiastowe odrzucanie, gdy kursor nie znajduje się już nad zawartością wzorcową, która ją wytłała.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modele wyboru

### <a name="overview"></a>Omówienie
 Model wyboru jest mechanizmem używanym do wskazywania i potwierdzania operacji na co najmniej jednym obiektu w interfejsie użytkownika. W tym temacie omówiono wzorce interakcji wyboru Visual Studio edytorach dokumentów: edytorach tekstu, powierzchniach projektowych i powierzchniach modelowania.

 Użytkownicy muszą mieć sposób wskazywania, Visual Studio nad czym pracują, a użytkownicy muszą Visual Studio w przewidywalny sposób odpowiedzieć na opinie użytkowników dotyczące tego, na czym ona działa. Różnice lub błędna relacja między użytkownikiem a interfejsem użytkownika może spowodować, że użytkownik nie zaznajomi się z akcją, co może mieć niezamierzone konsekwencje. Często błąd jest niezauwaowany, dopóki użytkownik nie zobaczy, że coś nie istnieje lub coś się zmieniło. W związku z tym modele wyboru są jednym z najważniejszych elementów projektu interfejsu użytkownika. Chociaż modele wyboru w Visual Studio są spójne z systemem Windows, istnieją niewielkie odchylenia.

 W Visual Studio, tak jak w systemie Windows, modele wyboru różnią się w zależności od kontekstu, w którym występuje interakcja. Wybory mogą wystąpić w czterech typach obiektów:

- Tekst

- Obiekty graficzne

- Listy i drzewa

- Siatki

  W ramach tych obiektów istnieją trzy typy wyborów:

- Ciągłe

- Rozłącznych

- Region (Region)

#### <a name="scope"></a>Zakres
 Najważniejszym składnikiem wyboru jest zapewnienie, że użytkownik wie, w którym oknie pracuje (aktywacja) i gdzie znajduje się fokus (wybór). Visual Studio rozszerza funkcjonalność zarządzania oknami w systemie Windows, ale schemat aktywacji jest taki sam: interakcja z oknem powoduje skoncentrowanie się na oknie. Visual Studio ma dwa wskaźniki aktywacji: jeden dla okien dokumentów i jeden dla okien narzędzi.

 W przypadku okien dokumentów aktywne okno jest wskazywane przez kartę okna dokumentu przychodzącą z przodu i zmieniającą jej kolor tła:

 ![Wybór karty Aktywne w Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Wybór karty Aktywne**

 W przypadku okien narzędzi aktywne okno jest wskazywane przez zmianę koloru obszaru paska tytułu okna narzędzi:

 ![Wybór aktywnego okna narzędzi w Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Okno narzędzi aktywne z podstawowym wyborem węzła**

 ![Wybór nieaktywnego okna narzędzi w Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Nieaktywne okno narzędzia z ukrytym wyborem węzła**

 Gdy okno jest aktywne, jego fokus jest wskazywany zgodnie z modelami wyboru opisanymi w tej sekcji wytycznych.

#### <a name="context"></a>Kontekst
 Visual Studio zaprojektowano tak, aby zachować silną koncepcję kontekstu, śledząc, gdzie użytkownik pracuje. Aktywne jest tylko jedno okno, niezależnie od tego, czy jest to okno narzędzia, czy dokumentu. Jednak pierwsze okno dokumentu zawsze zachowuje ukryte zaznaczenie. Mimo że fokus może być wyświetlany w oknie narzędzi, ostatnio aktywne okno dokumentu wyświetla zaznaczenie, nawet w stanie nieaktywnym. Odbywa się to w celu zachowania kontekstu użytkownika w edytowanym dokumencie, pokazując, że użytkownik Visual Studio zachowywał swój stan, dzięki czemu może bezproblemowo powracać i przenosić między oknami narzędzi i oknami dokumentów.

### <a name="text-selection"></a>Zaznaczanie tekstu
 Visual Studio, które są wyłącznie tekstowe, takie jak wbudowany edytor tekstu, używają tego samego modelu zaznaczania [](/windows/desktop/uxguide/inter-mouse) tekstu i wyglądu opisanego na stronie Myszy i wskaźniki w wytycznych dotyczących interakcji środowiska użytkownika systemu Windows w witrynie MSDN. Fokus danych wejściowych w edytorze tekstów jest wskazywany przez pionowy pasek nazywany punktem wstawiania. Punkt wstawiania ma grubość jednego piksela i kolor jest odwrotny do tego, co się za nim znajduje. Miga zgodnie z szybkością ustawioną przez ustawienie  szybkości **migania** kursora na karcie Szybkość apletu Klawiatura w Panel sterowania. 

#### <a name="contiguous-and-disjoint-selection"></a>Ciągły i rozłączny wybór
 Zaznaczenie w edytorze tekstów jest tylko ciągłe. Rozłączne wybory tekstu nie są dozwolone, ale należy je rozwiązać w edytorach obiektów graficznych. Gdy wskaźnik myszy użytkownika znajduje się nad obszarem tekstowym, kursor zmienia się na kępę I. Pojedyncze kliknięcie umieszcza punkt wstawiania w edytorze tekstów w lokalizacji kliknięcia. Przytrzymanie przycisku myszy w dół powoduje wyróżnienie zaznaczenia i zwolnienie przycisku myszy powoduje zakończenie wyróżniania zaznaczenia.

#### <a name="region-selection-box-selection"></a>Wybór regionu (wybór pola)
 Visual Studio obsługuje wybory regionów w edytorze tekstów, co jest nazywane zaznaczaniem pól. Wybranie pola umożliwia użytkownikowi wybranie regionu tekstu, który nie jest podążany za zwykłym strumieniem tekstu. Podobnie jak w przypadku zaznaczania tekstu standardowego, zaznaczenie musi być ciągłe. Wybór pola jest inicjowany przez przytrzymanie klawisza Alt podczas przeciągania za pomocą myszy. Zaznaczenie pola może być również inicjowane przez przytrzymanie klawiszy Alt i Shift podczas używania klawiszy strzałek do wskazywania regionu zaznaczenia. Zaznaczenie pola używa normalnego wyróżnienia zaznaczenia i pokazuje migający kursor punktu wstawiania na końcu obszaru zaznaczenia.

 ![Pole &#40;regionalne&#41; wyboru w Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Wybór regionu (pola) w Visual Studio**

#### <a name="text-selection-appearance"></a>Wygląd zaznaczenia tekstu
 Kolory używane do aktywnego i nieaktywnego wyboru w edytorze można dostosować. Aby dostosować wygląd edytora, użytkownik może przejść do opcji Narzędzia **>, a** następnie w obszarze Środowisko > Czcionki i kolory > **edytorze tekstu**.

### <a name="graphical-selection"></a>Wybór graficzny

#### <a name="interaction"></a>Interakcja
 Wybór obiektu graficznego może być złożony i zależy od wielu czynników:

- **Podstawowy model wyboru edytora.** Edytory zawierające obiekty graficzne mogą być również używane do edytowania tekstu lub siatek. Na przykład edytor może być edytorem tekstowym, który obsługuje również umieszczanie obiektów graficznych, takich jak Visual Studio XAML. Obsługa wielu typów obiektów może mieć wpływ na sposób, w jaki użytkownik wybiera grupy z różnych typów obiektów.

- **Obsługa podstawowych i pomocniczych stanów wyboru.** Edytor może zapewniać podstawowe i pomocnicze stany wyboru, dzięki czemu obiekty mogą być edytowane w trybie unison, wyrównane do siebie, zmieniane rozmiary i tak dalej.

- **Obsługa edytowania w miejscu.** Edytory mogą również zezwalać na edycję zawartości ich obiektów graficznych. Na przykład kształt prostokąta może również zawierać tekst wewnątrz, który może zostać zmieniony przez użytkownika. Ponadto ten tekst może być wyśrodkowany lub uzasadniony. Edytowanie w miejscu obejmuje bardziej szczegółowy poziom interakcji z użytkownikiem i dlatego wymaga odpowiedniego zestawu wizualnych wskaźników do prezentowania informacji o stanie użytkownikowi.

#### <a name="mouse-interaction"></a>Interakcja z myszą

|Dane wejściowe|Wynik|
|-----------|------------|
|Klikanie niezaznanego obiektu|Wybiera obiekt i wyświetla linię przerywaną i uchwyty zaznaczenia, jeśli można zmieniać ich rozmiaru.|
|Klikanie wybranego obiektu|Aktywuje edytowanie w miejscu, jeśli obiekt go obsługuje. Kliknięcie poza obiektem dezaktywuje tryb edycji w miejscu.|
|Dwukrotne kliknięcie obiektu|Otwiera kod obiektu do edycji i może wstawić domyślną obsługę zdarzeń, jeśli jest to konieczne.|
|Wskaż obiekt|Zmienia wskaźnik do kursora przenoszenia. Wygląd obiektu, taki jak jasność lub kolor, może ulec zmianie.|
|Wskaż uchwyt wyboru|Zmienia wskaźnik na kursor zmiany rozmiaru. W przypadku obiektów, które obsługują obrót, niektóre uchwyty zaznaczenia mogą zmienić wskaźnik na obracanie kursora, ponieważ wskaźnik jest umieszczony inaczej (na przykład przesunięty dalej) względem uchwytu zaznaczenia.|
|Przeciągnij|Nawet jeśli obiekt nie został wcześniej wybrany, zmienia wskaźnik do kursora przenoszenia i przenosi obiekt.|
|Edytor traci fokus|Dezaktywuje tryb edycji w miejscu, mimo że obiekt zachowuje zawartość i wygląd, które miał podczas ostatniej operacji/wyboru.|
|Wybór obiektu|Wskazywane przez obramowanie, linię kropkową lub inne wizualnie odrębne traktowanie w celu wyróżnienia granicy obiektu.|
|Zmienianie rozmiaru wybranego obiektu|Wskazywane przez uchwyty zaznaczenia.<br /><br /> Obiekt o zmienianiu rozmiaru ma osiem dojść reprezentujących każdy kierunek, w którym można zmienić jego rozmiar. Jeśli rozmiar obiektu można zmienić tylko w określonych kierunkach, można użyć mniejszej liczby dojść. Gdy użytkownik rozmiaruje obiekt w dół do miejsca, w którym osiem dojść nie byłoby interaktywnych, można użyć czterech dojść. Rozmiary dojścia powinny być powiązane z metrykami krawędzi i obramowania okna za pomocą funkcji interfejsu API **GetSystemMetrics,** aby rozmiar był proporcjonalny do rozdzielczości ekranu.<br /><br /> ![Zmienianie rozmiaru uchwytów](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Obracanie wybranego obiektu|![Obracanie uchwytów](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interakcja za pomocą klawiatury

|Dane wejściowe|Wynik|
|-----------|------------|
|Tab|Przenosi wskaźnik koncentracji uwagi między logiczną kolejnością obiektów w edytorze. Może to być od lewej do prawej lub od góry do dołu w zależności od wartości właściwości **TabIndex** (lub równoważnej), kolejności tworzenia obiektu i ogólnego przeznaczenia edytora. Klawisze Shift+Tab odwracają kierunek wskaźnika koncentracji uwagi.|
|Spacja|Aktywuje tryb przesuwania przy zachowaniu naciśnięcia klawisza. Dodatkowe dane wejściowe myszy są wymagane do przesuwania pozycji w panelu ekranu.|
|Ctrl+Spacja|Aktywuje tryb powiększenia przy zachowaniu naciśnięcia klawisza. Dodatkowe dane wejściowe myszy są wymagane do zwiększenia i zmniejszenia współczynnika powiększenia.|
|Ctrl+Alt+Minus Sign|Zmniejsza współczynnik powiększenia o jeden poziom.|
|Ctrl+Alt+Znak plus|Zwiększa współczynnik powiększenia o jeden poziom.|
|Shift LUB Ctrl|Dodaje obiekt do grupy wyboru. Klawisz Ctrl umożliwia również usuwanie obiektów indywidualnie z grupy wyboru.|
|Enter|Wykonuje domyślne polecenie dla obiektu (zazwyczaj Otwórz lub Edytuj).|
|F2|Aktywuje edytowanie w miejscu dla obiektu .|
|Klawisze strzałek|Przenosi wybrane obiekty w kierunku naciśnięcia klawisza strzałki w małych przyrostach (na przykład 1 piksel na raz)|
|Ctrl+klawisze strzałek|Przenosi wybrane obiekty w kierunku naciśnięcia klawisza strzałki w większych przyrostach (na przykład 10 pikseli na raz)|
|Shift + klawisze strzałek|Zmienia rozmiar wybranych obiektów w odpowiednim kierunku, w małych przyrostach (na przykład 1 piksel na raz)|
|Ctrl+Shift+klawisze strzałek|Zmienia rozmiar wybranych obiektów w odpowiednim kierunku, w większych przyrostach (na przykład 10 pikseli na raz)|

 Gdy użytkownicy edytują kontrolki w miejscu, może mieć sens automatyczne zmienianie rozmiaru obiektów za pomocą danych wejściowych użytkownika. Jeśli na przykład użytkownik edytuje kontrolkę etykiety, etykieta powinna rosnąć, aby wyświetlić tekst wpisany przez użytkownika. Jeśli nie zostanie to zrobione, użytkownik musi ręcznie zmienić rozmiar kontrolki po edytowaniu tekstu. Jeśli użytkownik ma wiele kontrolek, staje się to gnijącymi i bezproduktywnymi zadaniami.

#### <a name="graphical-containers"></a>Kontenery graficzne
 W niektórych przypadkach edytory graficzne zapewniają kontenery dla innych obiektów graficznych, takich jak Windows Forms Panel lub kontrolka Układ siatki w projektancie HTML. Jeśli edytor udostępnia kontenery dla innych obiektów graficznych, wówczas następujący model wyboru powinien być używany tylko dla kontenera (obiekty w kontenerze są zgodne z modelem standardowym zgodnie z powyższym opisem):

|Dane wejściowe|Wynik|
|-----------|------------|
|Pojedyncze kliknięcie kontenera|Wybiera obiekt kontenera bez bezpośredniego wybierania żadnego z zawartych obiektów. Kontener można przenieść i/lub zmienić rozmiar za pomocą standardowej myszy i klawiatury (zgodnie z powyższym opisem). Zawarte obiekty są przenoszone w odniesieniu do kontenera, ale zawarte obiekty nie są zmieniane, chyba że są również bezpośrednio wybrane.|
|Zatrzymaj wskaźnik myszy nad regionem granicy kontenera|Zamienia wskaźnik myszy w kursor przenoszenia wskazujący, że kontener można przenieść.|
|Przeciąganie regionu granic kontenera|Zmienia wskaźnik myszy na kursor przenoszenia i przenosi kontener (i zawarte w nim obiekty). Nie można przenieść kontenera bez wcześniejszego wyboru jednym kliknięciem.|
|Pojedyncze kliknięcie obiektu w kontenerze|Usuwa zaznaczenie kontenera (jeśli wybrano) i wybiera tylko klikony obiekt.|
|Shift + kliknięcie LUB Ctrl + kliknięcie zawartego obiektu i/lub kontenera|Dodaje klikony obiekt do istniejącej grupy wyboru lub zaznaczenia. Jeśli klikowany obiekt jest już członkiem grupy wyboru, zostanie usunięty z grupy wyboru.|

 Zawarte obiekty powinny być zgodne z podstawowym modelem wyboru zgodnie z opisem w poprzedniej sekcji. Po przetestowaniu użyteczności projektanta Windows Forms użytkownicy oczekiwali bezproblemowego dostępu do zawartych obiektów bez interwencji kroków (narzuconych przez obiekt zawierania).

#### <a name="disjoint-and-region-selections"></a>Wybory rozłączne i regionów
 Edytory obiektów graficznych powinny obsługiwać rozłączne wybory. Należy pamiętać, że ta grafika nie pokazuje wyglądu kontrolki dla Visual Studio. Zobacz [Wygląd wyboru obiektu graficznego,](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) aby uzyskać szczegółowe specyfikacje wizualizacji.

 ![Selektory rozłączne i regionów](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Rozłączny wybór**

 Edytory graficzne powinny również dostarczać opcje wyboru regionów ze wskaźnikiem wyboru typu kierunkowego. Jeśli edytor graficzny obsługuje inne typy obiektów (takie jak tekst), wybór regionów może być niemożliwe w zależności od ograniczeń tych innych typów obiektów.

 ![Wybór narzędzia Dosyć](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Wybór narzędzia Dosyć**

#### <a name="primary-and-secondary-selections"></a>Opcje podstawowy i pomocniczy
 Niektóre edytory obiektów graficznych umożliwiają użytkownikowi edytowanie lub wyrównywanie obiektów w grupach. W tym przypadku należy wprowadzić koncepcję wyboru podstawowego i pomocniczego. Wybór podstawowy jest obiektem, na który wszystkie inne obiekty odpowiadają na operacje grupy. Obiekt, który użytkownik najpierw wybiera, staje się główną kontrolką, a kolejne wybory stają się pomocniczym wyborem. Wybór podstawowy ma inne traktowanie wizualne niż wybory pomocnicze, aby wskazać, który obiekt jest obiektem podstawowym:

 ![Wybór podstawowy i pomocniczy](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Wybór podstawowy z dwoma wyborami pomocniczym**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Wygląd zaznaczenia obiektu graficznego
 Uchwyty zaznaczenia to kwadraty rysowane w prostokątnym wzorcu wokół pola granicznego obiektu. Na poniższym wykresie przedstawiono przykłady różnych stanów, które obiekt graficzny może mieć z uchwytem, wielkością i wyglądem edycji w miejscu. Rozmiar uchwytów powinien być powiązany z metrykami krawędzi i obramowania okna przy użyciu interfejsu API **GetSystemMetrics.**

| Stan | Wygląd | Szczegóły wizualizacji |
|-------------------------|---------------| - |
| **Niezaznaczone** | Domyślne | ![Domyślny stan przycisku](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Wybór podstawowy** | Resizable | ![Wybór podstawowy z uchwytami zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Wybór podstawowy** | Nie można zmieniać rozmiaru | ![Wybór podstawowy bez uchwytów zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Wybór podstawowy** | Zablokowano | ![Wybór podstawowy jest zablokowany](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Wybór pomocniczy** | Resizable | ![Wybór pomocniczy z uchwytami zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Wybór pomocniczy** | Nie można zmieniać rozmiaru | ![Wybór pomocniczy bez uchwytów zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Wybór pomocniczy** | Zablokowano | ![Wybór pomocniczy zablokowany](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Aktywny interfejs użytkownika** | Domyślne | ![Aktywny stan interfejsu użytkownika](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Wyświetlanie modeli wyboru

#### <a name="tree-view"></a>Widok drzewa
 Zaznaczenie w widoku drzewa jest wyświetlane z prostym wyróżnieniem. Jeśli użytkownik kliknie nazwę węzła lub ikonę węzła, węzeł zostanie wybrany. Trójkątne glify z lewej strony węzła rozwijają lub zawęzają kontrolkę drzewa, ale nie mają wpływu na wybór użytkownika, z jednym wyjątkiem: po zwijaniu węzła nadrzędnego, gdy wybór znajduje się w węźle podrzędnym, wybór jest przenoszony do węzła nadrzędnego.

 ![Typowy widok drzewa w Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Typowy widok drzewa w Visual Studio**

 Widoki drzewa mogą obsługiwać ciągłe i rozłączne wybory, nawet na wielu poziomach drzewa. W widocznych węzłach drzewa należy wybrać wiele opcji ciągłych lub rozłącznych. Jeśli węzeł jest zwinięty, rozłączny wybór zostanie utracony, a zwinięty węzeł uzyska wybór. W ten sposób użytkownik może zobaczyć węzły, na które będzie mieć wpływ operacja. Gdy węzły są zwinięte, staje się niejasne, na które węzły mogą mieć wpływ.

 Po wybraniu węzła nadrzędnego operacja powinna mieć zastosowanie do elementu nadrzędnego, chociaż mogą wystąpić przypadki, w których warto zastosować operację do elementu nadrzędnego i wszystkich jego dzieci. W takim przypadku podaj dodatkowy interfejs użytkownika podczas operacji, taki jak pole wyboru lub okno dialogowe potwierdzenia, aby opcja "Zastosuj do wszystkich elementów children" była jawna dla użytkownika.

##### <a name="renaming"></a>Zmienianie nazw
 Jeśli węzły w drzewie obsługują zmianę nazw, należy wykonać zmianę nazwy. Operacja w miejscu powinna być standardem dla wszystkich kontrolek drzewa w Visual Studio. Podaj polecenie zmiany nazwy, które natychmiast aktywuje tryb edycji w miejscu z zaznaczeniem tekstu obejmującym całą nazwę węzła i gotowe do zaakceptowania danych wejściowych użytkownika. Jeśli węzeł reprezentuje plik, nazwa pliku powinna zawierać rozszerzenie . Wyróżnienie zaznaczenia powinno zawierać tylko treść nazwy pliku, a nie rozszerzenie.

|Dane wejściowe|Wynik|
|-----------|------------|
|klawisz ENTER|Zatwierdza operację zmiany nazwy|
|Esc|Anuluje operację zmiany nazwy|
|Klikanie poza regionem edycji w miejscu|Zatwierdza operację zmiany nazwy|
|Cofnij|Łatwe cofanie operacji anulowania zmiany nazwy|

#### <a name="selection-within-lists-and-grid-controls"></a>Wybór w obrębie list i kontrolek siatki
 Kluczową koncepcją wyboru listy jest to, że jest ona oparta na wierszach, co oznacza, że po wybraniu całego wiersza jest wybierany jako jednostka. Z kolei siatki mogą zezwalać na wybrane konkretne komórki bez wpływu na żaden inny aspekt wiersza. Siatki mogą również zawierać hierarchię zagnieżdżonych wierszy (na przykład w treeGrid), która umożliwia zaznaczone i odznaczone całe gałęzie hierarchii przez interakcję z wierszami nadrzędnymi. Wybór na listach jest wyświetlany przez prosty kolor wyróżnienia w całym wierszu danych. Fokus jest wyświetlany za pomocą kropkowanego obramowania o jednym pikselu wokół bieżącego edytowalnego wiersza lub komórki (wiersz, jeśli wszystkie komórki są tylko do odczytu).

> [!NOTE]
> **Fokus** i **wybór to** różne pojęcia. *Fokus* to wskazanie, który element interfejsu użytkownika jest ukierunkowany na  odbieranie danych wejściowych, które nie są jawnie kierowane do innego obiektu, podczas gdy wybór odnosi się do stanu dołączania obiektu do zestawu obiektów, na którym mogą być wykonywane kolejne operacje.

 Wybory na listach mogą być ciągłe, rozłączne lub regionów. Gdy jest dozwolonych wiele wyborów, ciągłe i rozłączne zaznaczenie powinno być zawsze obsługiwane, a obsługa wyborów regionu (pola) jest opcjonalna. Wybory regionów są inicjowane przez przeciąganie białych spacji w treści listy.

| Obiekt | Wybór |
|--------|------------|
| Lista | Ciągłe |
| Lista | Rozłącznych |
| Lista | Region (Region) |

 Kliknięcie raz na liście wybiera wiersz, w którym wystąpiło kliknięcie. Jeśli użytkownik kliknie komórkę listy, która obsługuje edytowanie w miejscu, komórka zostanie również natychmiast aktywowana do edycji w miejscu. W przeciwnym razie cały wiersz zostanie natychmiast wybrany i zostanie wyróżnione.

 Przeciąganie treści listy powoduje jedną z trzech czynności:

- Inicjuje wybór regionu, jeśli lista go obsługuje, a wskaźnik myszy w dół znajduje się w białych odstępach

- Inicjuje operację przeciągania/upuszczania, jeśli komórka listy lub wiersz obsługuje przeciąganie źródła

- Wybiera bieżący wiersz

##### <a name="in-place-editing"></a>Edytowanie w miejscu
 Gdy edytowanie w miejscu jest dozwolone, istnieją dwa podstawowe modele: prosta kontrolka edycji i s wyboru właściwości. Dzięki prostej kontrolce edycji zawartość jest wyróżniona i gotowa do wprowadzania danych przez użytkownika natychmiast po aktywowaniu edycji w miejscu. Po zaimplementowaniu selektora właściwości przycisk wywołujący selektor właściwości jest wyświetlany po aktywowaniu trybu edycji w miejscu, a bieżący wybór nie jest wyróżniony. Przycisk s wyboru powinien być w komórce prawym przyciskiem myszy. Przykłady edytowania w miejscu można znaleźć w **oknie właściwości** **i Lista zadań** w Visual Studio.

##### <a name="keyboard-support"></a>Obsługa klawiatury
 Obsługa klawiatury do wyboru na listach i w siatkach jest zgodna ze standardową konwencją systemu Windows:

- Klawisze strzałek nawigają po liście, zaznaczając każdy wiersz/komórkę podczas przesuwania fokusu.

- Shift + strzałka wykonuje ciągły wybór w kierunku klawiszy strzałek.

- Ctrl + strzałka, po którym następuje spacja, przełącza się między dodawaniem i usuwaniem elementów listy z zaznaczenia, tworząc rozłączny wybór.

- W przypadku siatek zawierających zagnieżdżone hierarchie klawisz Strzałka w prawo rozwija wiersz nadrzędny, a klawisz Strzałka w lewo zwija jeden.

- Klawisz Tab przenosi fokus między komórkami w bieżącym wierszu, jeśli komórki można edytować.

- Klawisz Enter wykonuje domyślne polecenie dla elementu na liście (często **Otwórz**).

- Klawisz F2 aktywuje edytowanie w miejscu dla aktualnie wybranej komórki.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Ustawienia trwałości i zapisywania

### <a name="overview"></a>Omówienie
 Mimo że każdy składnik oprogramowania w programie Visual Studio jest zazwyczaj odpowiedzialny za własny stan i trwałość, program Visual Studio automatycznie zapisuje ustawienia w niektórych przypadkach, takich jak rozmiary i położenia okien. W poniższej tabeli przedstawiono kombinację ustawień zapisanych automatycznie i ustawień, które wymagają jawnego użytkownika lub zaprogramowanej akcji.

|Obiekt|Co zapisać|Kiedy należy zapisać|Gdzie zapisać|
|------------|------------------|------------------|-------------------|
|Selectable object (na przykład wiersz kodu)|Punkt przerwania w wierszu kodu<br /><br /> Skrót użytkownika skojarzony z wierszem kodu|Po zapisaniu projektu|Plik **opcji użytkownika (suo)** dla projektu|
|Okno dialogowe|Lokalizacja okna dialogowego, jeśli zostało przeniesione<br /><br /> Widok, który ostatnio był używany przez użytkownika w oknie dialogowym|Po zamknięciu okna dialogowego<br /><br /> Po Visual Studio sesji|W pamięci<br /><br /> Rejestr w **HKEY_Current_User**|
|Okno|Rozmiar i lokalizacja okna|Po zamknięciu okna<br /><br /> Gdy tryb Visual Studio zmienia się<br /><br /> Po Visual Studio sesji|Plik **opcji użytkownika (suo)** dla projektu<br /><br /> Plik opcji niestandardowych dla ustawień okna|
|Dokument|Bieżące zaznaczenie w dokumencie<br /><br /> Widok dokumentu<br /><br /> Kilka ostatnich miejsc odwiedzanych przez użytkownika|Po zapisaniu dokumentu|Plik **opcji użytkownika (suo)** dla projektu|
|Project|Odwołania do plików<br /><br /> Odwołania do katalogów na dysku<br /><br /> Odwołania do innego oprogramowania<br /><br /> Składniki<br /><br /> Stan informacji o samym projekcie|Po zapisaniu projektu|Plik projektu|
|Rozwiązanie|Odwołania do projektów<br /><br /> Odwołania do plików|Po zapisaniu projektu lub rozwiązania|Plik **rozwiązania (sln)**|
|Ustawienia w **narzędziach > opcje**|Dostosowania klawiatury<br /><br /> Dostosowania paska narzędzi<br /><br /> Schematy kolorów|Po **zamknięciu okna dialogowego > opcje** zarządzania<br /><br /> Po Visual Studio sesji|Rejestr w **HKEY_Current_User**|

 To, co robi użytkownik i kiedy to robi, decyduje o tym, czy ustawienie jest zapisywane w pamięci (podczas sesji), zapisywane na dysku (między sesjami jako ustawienie rejestru), jako część samego pliku projektu lub rozwiązania, jako część pliku opcji rozwiązania **(suo),** czy jako plik ustawień niestandardowych, o którym wie tylko ten składnik oprogramowania. W powyższej tabeli przedstawiono kilka zdarzeń, w których można zapisać ustawienia. Istnieją jednak inne momenty, w których można zapisać stan:

- Gdy użytkownik zmienia lokalizację w oknie dialogowym lub oknie

- Gdy użytkownik przenosi fokus do innego okna

- Gdy użytkownik przełącza się z trybu projektowania na tryb debugowania

- Gdy użytkownik wyloguje się ze swojego konta

- Gdy komputer przechodzi w stan hibernacji lub jest zamykany

- Gdy komputer/dysk twardy ma zostać ponownie sformatowany i ponownie ustawiony

### <a name="window-configurations"></a>Konfiguracje okien
 Konfiguracja okna jest podstawową prezentacją środowiska programowego — jest to schemat składający się z listy obecnych okien narzędzi i sposobu ich rozmieszczeń. W przypadku okien zarządzanych przez środowiska IDE (okna IDE) informacje o układzie są utrwalane dla każdego użytkownika, więc gdy użytkownik uruchamia ideę, układ okna jest taki sam jak podczas ostatniego zakończenia pracy Visual Studio. Stan i położenie okien IDE są utrwalane w pliku opcji niestandardowych w formacie XML. Okna narzędzi, które są tworzone przez pakiety załadowane do środowiska IDE, utrwalają informacje o stanie w rejestrze i mogą być dostępne dla 1 użytkownika lub nie.

#### <a name="profile-specific-layouts"></a>Układy specyficzne dla profilu
 Każdy profil **zawiera** układy okien narzędzi zorganizowane w sposób znany określonym deweloperom (deweloperzy Visual C++ oczekują, że projekt Eksplorator rozwiązań będzie widzieć po lewej stronie środowiska IDE, a deweloperzy języka C# oczekują, że będą widzieć Eksplorator rozwiązań **po** prawej stronie). Układy okien specyficzne dla profilu są ładowane, gdy użytkownik wybierze profil podczas uruchamiania. Autor pakietu powinien określić układ okna najbardziej odpowiedni dla doświadczenia klienta, wiedząc, że zmiany wprowadzone przez użytkownika w konfiguracji okna zostaną utrwalone.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Wprowadzanie dotykowe
 Użytkownicy coraz częściej korzystają z produktów programistywnych firmy Microsoft na urządzeniach dotykowych. Istnieją jednak bariery, które sprawiają, że korzystanie z narzędzi programistyczych na urządzeniach dotykowych jest trudne. Użytkownicy będą oczekiwać, że nasze produkty będą zapewniać niezawodne i precyzyjne środowisko dotykowe. Celem tych wytycznych jest podejmowanie decyzji dotyczących możliwości obsługi dotykowej, które należy włączyć, oraz wspieranie spójnego środowiska obsługi dotykowej w Visual Studio i powiązanych produktach.

### <a name="levels-of-experience"></a>Poziomy doświadczenia
 Poniższe poziomy doświadczenia mają służyć jako przewodnik ułatwiający zespołom decydowanie, które możliwości dotykowe mają być dostępne, na podstawie żądanego poziomu zainteresowania inwestycją w dotyk.

- Podstawowe **środowisko jest dostępne** dla zespołów, które chcą zapewnić możliwości obsługi dotykowej, aby nie było żadnych zakleszczeń w całej pracy.

- Zoptymalizowane **środowisko jest dla** zespołów, które chcą zapewnić najbardziej typowe funkcje dotykowe (na przykład te, które są zwykle dostępne w aplikacjach przeglądarki internetowej).

- Środowisko **z podwyższonym** poziomem uprawnień jest dostępne dla zespołów, które chcą dodać funkcje, takie jak gesty lub inne opcjonalne możliwości, które mogą sprawić, że ich aplikacje będą przyjazne dla użytkownika.

||Podstawowe doświadczenie|Zoptymalizowane środowisko|Środowisko z podwyższonym poziomem uprawnień|
|-|----------------------|--------------------------|-------------------------|
|**Umożliwia użytkownikom...**|Naprawianie odczytu na poziomie kodu i rozwiązania/projektu bez zakleszczeń|Wykonywanie zadań konserwacji, refaktorów i nawigacji|Działanie w spójnym, intuicyjnym i płynnym interfejsie z pewnością|
|**Edytor**|Przesuwanie i zaznaczanie dotykowe<br /><br /> Przesuwanie paska przewijania w celu skoku i naciśnięcia+ przeciągania|Uszczypnij powiększenie<br /><br /> Szybkie przewijanie<br /><br /> Wybór<br /><br /> Łatwe korzystanie z menu kontekstowego||
|**Najważniejsze okna narzędzi**|Przesuwanie listy<br /><br /> Wybór elementu<br /><br /> Przesuwanie paska przewijania w celu skoku i naciśnięcia+ przeciągania|Łatwe przewijanie i zaznaczanie elementów||
|**Windowing**||Okno Zmienianie rozmiaru<br /><br /> Szybki dostęp||
|**Dobrze udokumentuj**||Łatwa nawigacja między otwartymi plikami||
|**Gestów**||Zapewnianie, że typowe gesty działają w całym ide|Akcje oparte na gestach<br /><br /> Obsługa przeciągania i upuszczania oraz projektantów|
|**Inne zagadnienia**|||Niestandardowa klawiatura ekranowa|

#### <a name="gestures"></a>Gestów
 Gesty zapewniają użytkownikom skrót do poleceń, które w przeciwnym razie mogą wymagać bardziej skomplikowanej interakcji. Zapoznaj się z wytycznymi dla systemu Windows dotyczącymi typowych gestów dotykowych dla aplikacji klasycznych [i](/windows/desktop/wintouch/windows-touch-gestures-overview)postępuj zgodnie z tymi wskazówkami w przypadku większości gestów, w tym prostych gestów, takich jak przesuwanie i powiększanie.
