---
title: Wzorce złożone dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07a2e38f38ca5e9414f5ab6b416eb0ca888131f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866910"
---
# <a name="composite-patterns-for-visual-studio"></a>Wzorce złożone dla programu Visual Studio
Wzorce złożone łączenie elementów interakcji i Projekt w różnych konfiguracjach. Oto niektóre z najważniejszych wzorce złożone w programie Visual Studio, w odniesieniu do spójności:  

-   [Wizualizacja danych](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  

-   [Interfejs użytkownika i wgląd w obiekcie](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  

-   [Wybór modeli](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  

-   [Trwałość i zapisywanie ustawień](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  

-   [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  

##  <a name="BKMK_DataVisualization"></a> Wizualizacja danych  

### <a name="overview"></a>Omówienie  
 Wykresy są wizualne przedstawienie do zagregowania i wizualizowanie danych w celu zwiększenia proces podejmowania decyzji. Pomagają użytkownikom zmierzyła się z dużą ilością danych, ale oznacza niewielkie Zobacz, co wymaga uwagi i co może wymagać ponownego akcji.  

 Użytkownik będzie korzystna wykresu w przypadku spełnienia dowolnego z następujących warunków:  

-   Wykres pomoże użytkownikom w identyfikacji zadania, którymi można pracować?  

-   Wykres umożliwi użytkownikom prognozy konsekwencje potencjalne zmiany?  

-   Wykres ułatwią użytkownikom wykryć trendy i zidentyfikować wzorce?  

-   Wykres pozwoli użytkownikom na podejmowanie lepszych decyzji?  

-   Wykres pomoże odpowiedzi na konkretne pytanie, które użytkownicy mogą w danym kontekście?  

#### <a name="general-rules-for-charts"></a>Ogólne zasady dla wykresów  

-   Wyraźnie etykiety danych. Ilustracje bez wyjaśnienie są po prostu wygląda obrazów.  

-   Rozpocznij osi od zera, aby uniknąć pochylanie proporcji. Rozmiar linii długość i paskiem są ważnych podpowiedzi wizualne dla zrozumienia, relacje między punktami danych.  

-   Tworzenie wykresów, nie grafika informacyjna o systemie. Grafika informacyjna o systemie są artystyczny reprezentacje danych, a ich podstawowym celem jest narracja visual. Wykresy można i należy być atrakcyjne wizualnie, ale dane same przemówiły.  

-   Należy unikać skeumorphism, połączyć wykresy słupkowe, hashmarks kontrast i inne grafika informacyjna ma.  

-   Nie należy używać jako element dekoracyjne efekty 3W. Ich używać tylko wtedy, gdy są naprawdę integralną częścią zdolność użytkownika zrozumienie informacji.  

-   Należy unikać wielu linii i wypełnień, zgodnie z więcej niż dwóch kolorów może utrudnić tego typu wykresu odczytać i zinterpretować.  

-   Nie należy używać wykresu (lub dowolnej ilustracja) jako jedyny sposób opis koncepcji lub interakcji z danymi. To stanowi trudności dla użytkowników niedowidzących.  

-   Nie należy używać wykresów jako nieodpłatnych lub dekoracyjne elementów na stronie. Innymi słowy Jeśli wykres nie dodać wszystkich użytkowników wartość lub pomoc rozwiązania problemu, nie używaj go.  

### <a name="chart-types"></a>Typy wykresów  
 Typy wykresów używane w programie Visual Studio obejmują wykresy słupkowe, wykresy liniowe, modyfikacji wykres kołowy, znane jako wykresów kołowych lub "wykres pierścieniowy," osi czasu, wykres punktowy powierzchni (zwane również "klaster wykresy") i wykresy Gantta. Każdy typ wykresu jest przydatne do komunikowania się na inny rodzaj informacji.  

### <a name="other-charting-considerations"></a>Inne zagadnienia wykresów  

#### <a name="color"></a>Kolor  
 Ma określonych palety kolorów zdefiniowanych do użytku w programie Visual Studio wykresów. Palety jest dostępny dla głównych typów ruchu kolorów i mogą być rozróżniane kolory, nawet wtedy, gdy jest używany jako kolor bardzo małym wycinków. Można używać tych kolorów w dowolnej kombinacji dla dowolnego typu wykresu lub grafu w interfejsie użytkownika. Nie trzeba używać wszystkich siedem kolorów, jeśli nie potrzebujesz tak wielu odrębnych kolorów. Te kolory nie były przeznaczone do użycia z wszelkie elementy pierwszego planu, więc nie należy umieszczać tekst lub symbole, na podstawie tych kolorów. Te odcieni powinien być zakodowane i narażony na dostosowywanie użytkownika w obszarze **Narzędzia > Opcje** (zobacz [udostępnianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  

|Próbki|szesnastkowy|RGB|  
|------------|---------|---------|  
|![Próbka 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Próbka BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Próbka FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Próbka 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Próbka 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Próbka 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Próbka B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  

##  <a name="BKMK_OnObjectUI"></a> Interfejs użytkownika i wgląd w obiekcie  
 Ta sekcja umożliwia kontekstu do wgląd, znany także jako widok podglądu kodu typu UI na obiekcie unikatowe dla programu Visual Studio.  

### <a name="overview"></a>Omówienie  

- Interfejsu użytkownika na obiekcie należy przyznać użytkownikowi więcej informacji lub interaktywność bez szkody dla swojego głównego zadania.  

- Wzorzec głównego interfejsu użytkownika na obiekcie, w programie Visual Studio jest znany jako "informacje o punkcie uwagi".  

- Interfejsu na obiekt użytkownika w programie Visual Studio albo wbudowany lub liczb zmiennoprzecinkowych i niezawodny lub jest przejściowy.  

  -   Widok podglądu kodu, typu UI na obiekcie w programie Visual Studio jest wbudowane i niezawodny.  

  -   CodeLens, typu UI na obiekcie w programie Visual Studio jest przejściowy i zmiennoprzecinkowych  

  Zrozumienie sposobu działania fragment kodu lub znajdowania szczegółowe informacje dotyczące tego kodu, często wymaga zatem programistą, aby przełączyć kontekst, a następnie przejdź do innej zawartości lub innego okna. Może być uciążliwe, te zmiany w kontekście, ponieważ użytkownicy mogą utracić skoncentrować się na ich oryginalnym zadaniem, gdy opuszczają ich głównego okna. Ponadto pobieranie, że oryginalna zwrotnego kontekstu może być trudne, szczególnie w przypadku, jeśli przełączanie między oknami spowodowane oryginalny kod, aby być zasłonięte przez inne interfejs użytkownika.  

  Na obiekt interfejsu użytkownika jest zgodna ze wzorcem o nazwie "informacje o punkcie uwagi". Te komunikaty, wyskakujące okienka i okna dialogowe użytkownikom dodatkowych, odpowiednie informacje, które dodaje wyjaśnienie lub interakcyjność nie zapominając o ich głównym zadaniem. Przykłady interfejsu użytkownika na obiekcie wyskakujących okienek, które są wyświetlane, gdy użytkownik zatrzyma wskaźnik ikony w obszarze powiadomień, czerwona fala błędnie napisane słowa i wyświetlanie podglądu wprowadzone w programie Visual Studio 2013.  

### <a name="decision-points"></a>Decyzje  
 W programie Visual Studio istnieje kilka sposobów użycia tego wzorca informacje o punkcie uwagi. Wybieranie mechanizmu prawo i jego implementacji w spójnej i przewidywalnej metody jest atrakcyjniejsze środowisko pracy. W przeciwnym razie użytkownicy może być przedstawiany w środowisku mylące lub niekonsekwentnie źle wpływa fokus z samej zawartości.  

#### <a name="relationships-between-master-and-detail-content"></a>Relacje między węzłem głównym i szczegółów zawartości  
 Informacje o punkcie uwagi służy do wyświetlania relacji między zawartości, czy użytkownik jest koncentruje się na (zawartość "główną") wraz z dodatkowymi powiązana zawartość (zawartość "szczegóły"). W tym wzorcu zawartości szczegółów jest wyraźnie związane z zawartością, użytkownik pracuje z i mogą być wyświetlane w pobliżu głównej zawartości. Informacje uzupełniające lub informacje, które nie można podsumować w bez przeciążenia wzorca zawartości powinien być zgodny z innego wzorca, takich jak okna narzędzi.  

-   **Zawsze** wyświetlanie zawartości szczegółów w bliskim sąsiedztwie do głównej zawartości.  

-   **Zawsze** upewnij się, że zawartość szczegółów nadal umożliwiają użytkownikom zachowanie stanu koncentruje się na głównej zawartości. Często najlepszym sposobem osiągnięcia tego jest do renderowania zawartości szczegółów jak blisko wzorca zawartości, jak to możliwe. Można to zrobić przez renderowania zawartości szczegółów w oknie podręcznym obok wzorca zawartości lub renderowania szczegółów zawartość w tekście poniżej głównej zawartości.  

-   **Nigdy nie** informacjom punkcie uwagi, który przyjmuje użytkownika od wzorca zawartości. Jeśli użytkownicy potrzebują do wyświetlania zawartości szczegółów oddzielnie, narażony konkretne działanie, który umożliwia użytkownikowi to zrobić.  

#### <a name="design-details"></a>Szczegóły projektu  
 Po określeniu, czy interfejs użytkownika na obiekcie jest właściwym wyborem, istnieją cztery główne zagadnienia:  

1. **Stan trwały:** zawartość powinna być trwałe lub przejściowym?   
   Użytkownicy będą widoczne informacje można znaleźć lub interakcji z? Czy będą użytkownicy chcą szybko Uzyskaj wgląd w informacje, a następnie kontynuuj za pomocą swojego głównego zadania?  

2. **Typ zawartości:** zawartość będzie informacyjny, informacje z możliwością działania lub nawigacyjnych?   
   Użytkownik musi dodatkowe szczegóły dotyczące wzorca zawartości? Czy użytkownik musi wykonać zadanie, które ma wpływ na głównej zawartości? Lub użytkownik musi być kierowane do innego zasobu?  

3. **Typ wskaźnika:** ma otoczenia wskaźnik sensu?   
   Informacje można podsumować w wygodny sposób i wyświetlane bez przeciążenia głównej zawartości?  

4. **Gesty:** co gesty będzie służyć do wywołania i odrzucić interfejsu użytkownika?   
   Jak będzie użytkownika wyświetlenie zawartości szczegółów i wysłać go natychmiast? Występuje wartość Dodawanie gestów takich jak przypinania, aby przełączyć się między Stanami błędy przejściowe i trwałe?  

   Każda z tych czterech decyzje będzie miało wpływ na temat głównych składników interfejsu użytkownika na obiekcie.  

### <a name="on-object-ui-components"></a>Składniki interfejsu użytkownika na obiekcie  

1.  Typ kontenera (prezentera zawartości)  

    -   Zmiennoprzecinkowe  

    -   wbudowane  

2.  Typ zawartości  

    -   Komunikat o charakterze informacyjnym: dane, które mogą być statyczne lub dynamiczne  

    -   Informacje z możliwością działania: poleceń, które zmienia głównej zawartości  

    -   Nawigacja: linki, które prowadzą użytkownika do innego okna lub aplikacji, takich jak MSDN  

3.  Gestów  

    -   Wywołania  

    -   Zwolnienia  

    -   Przypinanie  

    -   Inne interakcje  

4.  Model stanu trwałego i zatwierdzenia  

    -   Przejściowe  

    -   trwałe  

    -   Automatyczne  

    -   Na żądanie  

5.  Wskaźniki otoczenia (opcjonalnie)  

    -   Podkreślenie fala  

    -   Ikona tagów inteligentnych  

    -   Inne wskaźniki otoczenia  

#### <a name="container-content-presenter-type"></a>Typ kontenera (prezentera zawartości)  
 Istnieją dwie główne opcje dostępne do prezentowania zawartości w punkcie uwagi:  

1.  **Śródwierszowe:** prezentera wbudowane, takie jak widok wglądu, który wprowadzono w programie Visual Studio 2013 edytorze kodu, sprawia, że miejsce dla nowej zawartości przez przesunięcie istniejącej zawartości.  

    -   **Preferuj** przedstawić Prezenterzy wbudowanych, jeśli oczekujesz, że użytkownicy będą spędzać znaczną ilość czasu, odnoszące się do lub interakcji z zawartością.  

    -   **Należy unikać** Prezenterzy wbudowanych, jeśli oczekujesz, że użytkownicy będą chcieli Uzyskaj wgląd w informacje, można przedstawić, a następnie kontynuuj ich główne zadania przy minimalnym zakłóceniu.  

2.  **Zmiennoprzecinkowa:** prezentera zmiennoprzecinkowy jest umieszczony maksymalnie zbliżone do wybranej zawartości, jak to możliwe, ale nie zmienia układ istniejącej zawartości. Różne strategie można zastosować, takich jak wyświetlanie ruchomego panelu zawartości za pośrednictwem najbliższego dostępnego miejsca biały na wybrany symbol.  

    -   **Preferuj** liczb zmiennoprzecinkowych Prezenterzy, jeśli oczekujesz, że użytkownicy będą chcieli Uzyskaj wgląd w informacje, można przedstawić, a następnie kontynuuj ich główne zadania przy minimalnym zakłóceniu.  

    -   **Należy unikać** liczb zmiennoprzecinkowych Prezenterzy, jeśli oczekujesz, że użytkownicy będą chcieli do wydania znaczną ilość czasu, odnoszące się do lub interakcji z zawartością możesz obecne.  

#### <a name="content-type"></a>Typ zawartości  
 Istnieją trzy główne typy zawartości, które mogą być wyświetlane w dowolnym kontenerze interfejsu użytkownika na obiekcie. Mogą być wyświetlane dowolnej kombinacji tych typów informacji. Są trzy typy:  

1.  **Komunikat o charakterze informacyjnym:** kontenery interfejs użytkownika wyświetli pewnego rodzaju zawartość informacyjna na obiekcie dla większości. Zawartość może reprezentować informacji na temat obecnego stanu środowiska, lub może reprezentować, informacje o potencjalnych przyszły stan środowiska. Na przykład można użyć aby pokazać efekt określonego polecenia, takie jak Refaktoryzacja, na istniejący kod.  

    -   **Zawsze** Użyj canonical reprezentacja możesz wyświetlić informacje. Na przykład kod powinien wyglądać podobnie do kodu z wyróżnianiem składni i należy przestrzegać, niezależnie od czcionek i inne ustawienia środowiska, ustawionych przez użytkownika.  

    -   **Zawsze** należy rozważyć obsługę wszystkich działań nad zawartością informacyjny, który może wystąpić, jeśli te same informacje są prezentowane jako głównej zawartości. Na przykład jeśli prezentowanie istniejący kod w kontenerze interfejsu użytkownika na obiekcie, zdecydowanie należy rozważyć obsługę możliwość przeglądania i modyfikowania kodu.  

    -   **Zawsze** należy rozważyć użycie inny kolor tła, jeśli prezentacja informacyjny zawartości, która reprezentuje potencjalnych przyszłych stan.  

2.  Informacje z możliwością działania: niektóre kontenery interfejsu użytkownika na obiekcie zapewni możliwość wykonywania akcji głównej zawartości, takie jak wykonanie operacji refaktoryzacji.  

    -   **Zawsze** umieść informacje z możliwością działania polecenia niezależnie od informacyjny zawartości.  

    -   **Zawsze** włączać i wyłączać akcji, gdy jest to konieczne.  

    -   **Zawsze** odnoszą się do standardowych wytycznych do reprezentowania polecenia w oknach dialogowych.  

    -   **Zawsze** zachować minimalną liczbę akcji, które są dostępne w pojemniku na obiekt interfejsu użytkownika na poziomie. Wchodzenie w interakcje przy użyciu interfejsu użytkownika na obiekcie powinna być lekkie, szybkie środowisko. Użytkownik nie powinien mieć do rozwiń energii na zarządzaniu sam pojemnik interfejsu użytkownika na obiekcie.  

    -   **Zawsze** należy wziąć pod uwagę, jak i kiedy pojemniku interfejsu użytkownika na obiekcie zostaną zamknięte lub odrzucony. Najlepszym rozwiązaniem jest dowolną akcję, która zawiera dialog między węzłem głównym i szczegółów zawartości powinien też zamknąć kontenera interfejsu użytkownika na obiekcie po wywołaniu tej akcji.  

3.  **Nawigacja:** niektóre na obiekcie kontenery interfejsu użytkownika zawierać linki, które prowadzą użytkownika do innego okna lub aplikacji, takich jak otwieranie artykuł w witrynie MSDN w przeglądarce sieci web.  

    -   **Zawsze** dołączana dowolne łącze nawigacyjne za pomocą "Otwórz", dzięki czemu użytkownicy będą nie oczekiwano, przez do niektórych innej zawartości.  

    -   **Zawsze** oddzielić łączy nawigacyjnych od łączy informacje z możliwością działania.  

#### <a name="ambient-indicators-optional"></a>Wskaźniki otoczenia (opcjonalnie)  
 Wskaźniki otoczenia można subtelne, łącznie z tekstem prezentowane w kolorze kontrastowym od pozostałej części kodu, lub oczywiste, łącznie z symbolami tickler, takich jak podkreślenia wężyk i ikony tagu inteligentnego. Wskaźniki otoczenia komunikują się dostępność dodatkowych i istotnych informacji. W idealnym przypadku zawierają przydatne informacje, nawet bez konieczności interakcji z użytkownikiem przez użytkownika.  

-   **Zawsze** umieść wskaźnik otoczenia, tak, aby nie przeszkadzać ani nie przeciąży użytkownika. Jeśli nie jest możliwe umieścić wskaźnik otoczenia w taki sposób, należy rozważyć inne rozwiązanie.  

-   **Zawsze** umieść wskaźnik otoczenia jak najbardziej zbliżony do zawartości, która jest powiązana.  

-   **Zawsze** spróbuj utworzyć wskaźnik, który zawiera podsumowanie informacji o dostępnych. Rozważ podanie liczbę elementów danych dostępnych (na przykład, "3 odwołania do" zamiast po prostu odwołania do"") lub traktować inny sposób podsumowywania danych.  

    -   W przypadkach, gdy dane dla wskaźnika nie zawsze być obliczane i wyświetlane natychmiast należy wziąć pod uwagę opiniowania progresywnego jako wartości są obliczane. Na przykład należy wziąć pod uwagę animowanie zmian, które odzwierciedlają aktualizacji dostępnych danych, podobnie jak sposób, w jaki Kafelek na żywo poczty e-mail na Windows Phone odświeża jako liczba wzrasta nieprzeczytanych wiadomości e-mail.  

-   **Nigdy nie** dodanie wskaźników więcej niż użytkownik rozsądnie może zająć do danego elementu zawartości. Wskaźniki otoczenia powinny być przydatne bez konieczności interakcji użytkownika. Wskaźniki utratę ich otoczenie, jeśli wymagają one przepełnienie i inne formanty zarządzania w celu dostosowania ich do widoku.  

#### <a name="gestures"></a>Gestów  
 Jest kluczowym aspektem umożliwienie użytkownikowi Obsługa skoncentrować się na głównej zawartości dzięki obsłudze prawo gestów do otwierania i odrzucić zawartość dodatkowe szczegóły.  

-   **Zawsze** wymaga od użytkownika do wykonania niektórych jawne gest, aby otworzyć dodatkowej zawartości. Typowe gestów Otwórz obejmują:  

    -   **Po wskazaniu wskaźnikiem:** etykietki narzędzi lub nieinterakcyjnych informacyjny zawartości  

    -   **Polecenie jawne:** prezentera wbudowane  

    -   **Kliknij dwukrotnie otoczenia wskaźnika:** Okno podręczne CodeLens  

-   **Zawsze** odrzucić zawartość szczegółów zawsze wtedy, gdy użytkownik naciśnie klawisz Esc.  

-   **Zawsze** należy wziąć pod uwagę kontekstu interfejsu użytkownika na obiekcie. Dla zawartości Prezenterzy, które umożliwiają interakcję w kontenerze dokładnie rozważ, czy są wyświetlane dodatkowe informacje po najechaniu wskaźnikiem, czyli może być szkodliwe do przepływu pracy użytkownika.  

-   **Nigdy nie** wyświetlania zawartości po najechaniu wskaźnikiem, które można edytować lub zaprasza interakcji z użytkownikiem. To zachowanie może frustrować użytkowników, jeśli użytkownik próbuje Przesuń kursor nad zawartością szczegółów standardowe zachowanie dla etykietki narzędzia jest natychmiast zamknąć po umieszczeniu kursora nie jest już główną zawartości, który go.  

##  <a name="BKMK_SelectionModels"></a> Wybór modeli  

### <a name="overview"></a>Omówienie  
 Wybór modelu to mechanizm służący do wskazywania i upewnij się, operacje na co najmniej jeden interesujące obiekty interfejsu użytkownika. W tym temacie omówiono wzorce interakcji zaznaczenia w ramach edytory dokumentu programu Visual Studio: edytory tekstów, projektów i powierzchnie modelowania.  

 Użytkownicy muszą mieć sposób wskazujący do programu Visual Studio, zajmują się i programu Visual Studio musi odpowiedzieć w przewidywalny opinii użytkowników o działa na. Różnice lub nieporozumienia między użytkownikiem i interfejs użytkownika może skutkować użytkownika nie obserwowanie akcję, która może mieć niezamierzone konsekwencje. Często ten błąd przechodzi niezauważona, dopóki użytkownik zobaczy czegoś brakuje lub została zmieniona. Zaznaczenie modele są w związku z tym jednym z najważniejszych elementów projektu interfejsu użytkownika. Chociaż wybór modeli w programie Visual Studio są spójne z Windows, mogą występować niewielkie różnice.  

 W programie Visual Studio, jak Windows modele wybór różnią się w zależności od kontekstu, w której występuje interakcji. Wybór może wystąpić w cztery rodzaje obiektów:  

- Tekst  

- Obiekty graficzne  

- Listy i drzewa  

- Siatki  

  W ramach tych obiektów istnieją trzy typy opcji:  

- Ciągłe  

- Rozłączne  

- Region  

#### <a name="scope"></a>Zakres  
 Najważniejszym składnikiem zaznaczenie jest zapewnienie, że użytkownik wie, w jakim oknie pracują (aktywacji) i gdzie koncentruje się (wybór). Program Visual Studio rozszerza funkcje zarządzania okna w Windows, ale schemat aktywacji jest taki sam: interakcja z oknem Przełącza fokus do okna. Program Visual Studio zawiera dwa wskaźniki do aktywacji: jeden dla systemu windows w dokumencie i jeden dla okien narzędzi.  

 Dla systemu windows w dokumencie aktywne okno jest wskazywany przez kartę okna dokumentu do przodu i zmieniając jego kolor tła:  

 ![Wybór aktywną kartę w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 01_ActiveTab")  

 **Wybieranie karty aktywne**  

 Dla okien narzędzi aktywne okno jest wskazywany przez zmianę koloru obszar paska tytułu okna narzędzi:  

 ![Wybór okna aktywnego narzędzia w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 02_ActiveToolWindow")  

 **Aktywnego okna narzędzi przedstawiający zaznaczenia głównego węzła**  

 ![Wybór okna narzędzia nieaktywne w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 03_InactiveToolWindow")  

 **Okno narzędzia nieaktywne wyświetlanie ukrytego wybór węzła**  

 Po uaktywnieniu okna jego fokus jest wskazywany zgodnie z modeli wybór opisanych w tej sekcji wytycznych dotyczących języka.  

#### <a name="context"></a>Kontekst  
 Visual Studio został zaprojektowany w celu zachowania silne pojęcia kontekstu, śledzenia, z których użytkownik pracuje. Tylko jedno okno jest aktywne, czy jest ono okno narzędzia lub dokumentu. W oknie dokumentu najwyższego poziomu zachowuje zawsze ukryte zaznaczenia. Mimo że fokus może znajdować się w oknie narzędzia, okno dokumentu, który był ostatni aktywny Wyświetla zaznaczenie, nawet w przypadku stanu braku aktywności. Odbywa się to do przechowania w kontekście użytkownika w dokumencie, który ich edytowania, pokazujący, że Visual Studio została zachowana ich stan tak, aby powrócić i bezproblemowo przesunięcia między oknami narzędzi i oknami dokumentu.  

### <a name="text-selection"></a>Zaznaczanie tekstu  
 Edytory wizualne Studio, które są ściśle tekstową, takich jak edytor tekstu wbudowanych, użyj tego samego modelu zaznaczenia tekstu i wygląd opisane w [myszą oraz wskaźniki](/windows/desktop/uxguide/inter-mouse) Windows User Experience Interaction Guidelines na stronie MSDN. Fokus wprowadzania w edytorze tekstu jest wskazywany przez pionowy pasek o nazwie punktu wstawiania. Punkt wstawiania jest piksela grubości i kolorowe jako odwrotność pojawia się niezależnie od rodzaju związanych z nim. Miga, według stawki ustalanej przez **częstotliwość migania kursora** w **szybkość** karcie **klawiatury** apletu w Panelu sterowania.  

#### <a name="contiguous-and-disjoint-selection"></a>Ciągłe i rozłączne zaznaczenia  
 Wybór w edytorze tekstu jest tylko ciągłych. Rozłączne tekstu, opcje nie są dozwolone, ale powinny być kierowane w edytorach obiektu graficznego. Gdy wskaźnik myszy użytkownika znajduje się nad obszar tekstu, zmiany dwuteownik. Jednym kliknięciem umieszcza kursor w edytorze tekstu w lokalizacji kliknij. Przytrzymując przycisk myszy uruchamia wyróżnienie wybór i zwolnieniem przycisku myszy kończy się zaznaczenie wyróżnienia.  

#### <a name="region-selection-box-selection"></a>Pole Region (pole zaznaczenia)  
 Program Visual Studio obsługuje opcje regionu w edytorze tekstów, a jest to pole wyboru. Pole wyboru umożliwia użytkownikowi wybrania regionu na tekst, który nie jest zgodna z strumienia zwykły tekst. Podobnie jak w przypadku zaznaczenia tekstu standardowego, wybór musi być ciągłe. Pole wyboru jest inicjowane, przytrzymując klawisz Alt podczas przeciągania myszą. Pole wyboru można także inicjować, przytrzymując klawisz Alt i klawisze Shift podczas przy użyciu klawiszy strzałek, aby wskazać region zaznaczenia. Pole wyboru używa wyróżnienie wybór normalne i pokazuje kursora punkt wstawiania migająca dioda na końcu obszaru zaznaczenia.  

 ![Regionalne &#40;pole&#41; zaznaczenie w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 04_BoxSelection")  

 **Pole Region (pole) w programie Visual Studio**  

#### <a name="text-selection-appearance"></a>Wygląd zaznaczenia tekstu  
 Można dostosować kolory używane dla aktywnych i nieaktywnych zaznaczenia w edytorze. Aby dostosować wygląd edytora, użytkownika, można przejść do **Narzędzia > Opcje**, a następnie sprawdź w obszarze **środowiska > czcionki i kolory > Edytor tekstu**.  

### <a name="graphical-selection"></a>Wybór graficzne  

#### <a name="interaction"></a>Interakcji  
 Wybieranie obiektu graficznego może być skomplikowane i zależy od kilku czynników:  

-   **Edytor modelu zaznaczenia głównego.** Edytory, które zawierają obiekty graficzne można również edytować tekst lub siatkach. Na przykład edytor może być oparte na tekście edytor, który również obsługuje umieszczanie obiektów graficznych, takich jak projektant XAML usługi Visual Studio. Obsługuje wiele typów obiektów może mieć wpływ na sposób użytkownik wybiera grupy składające się z różnymi typami obiektów.  

-   **Obsługa Stany wyboru podstawowego i pomocniczego.** Edytor może zapewnić podstawowe i pomocnicze wybór dokonany stany tak, aby obiekty mogą być edytowane spójnie, dostosowane do siebie nawzajem, ze zmienionym rozmiarem ze sobą, i tak dalej.  

-   **Obsługa edycji w miejscu.** Edytory można również zezwolić zawartość ich obiektów graficznych do edycji. Na przykład kształt prostokąta mogą również zawierać tekst wewnątrz, które mogą być zmieniane przez użytkownika. Ponadto ten tekst może wyśrodkowany lub uzasadnione. Edycji w miejscu polega na bardziej szczegółowym interakcji z użytkownikiem i w związku z tym wymaga odpowiedniego zestawu podpowiedzi wizualne przedstawienie informacji o stanie użytkownika.  

#### <a name="mouse-interaction"></a>Interakcji z myszą  

|Dane wejściowe|Wynik|  
|-----------|------------|  
|Kliknij wybrany obiekt|Wybiera obiekt i wyświetla linię przerywaną, co i uchwyty, jeśli obiekt jest o zmiennym rozmiarze.|  
|Kliknij wybrany obiekt|Aktywuje edycji w miejscu, jeśli obiekt obsługuje tę funkcję. Klikając poza obiekt dezaktywuje tryb edycji w miejscu.|  
|Kliknij dwukrotnie obiekt|Otwiera kod związany z obiektu do edycji i wstawić domyślny program obsługi zdarzeń, jeśli to stosowne.|  
|Wskaż obiektu|Wskaźnik zmienia się na przeniesienie kursora. Wygląd obiektu, takie jak jego jasność lub kolor, mogą ulec zmianie.|  
|Wskaż uchwyt zaznaczenia|Wskaźnik zmienia się na kursor zmiany rozmiaru. Dla obiektów, które obsługują obrotu niektóre uchwytami może zmienić wskaźnik do obracania kursora po umieszczeniu wskaźnika inaczej (na przykład przenieść dalej od komputera) względem uchwyt zaznaczenia.|  
|Przeciągnij|Nawet jeśli nie wybrano wcześniej obiektu, zmienia się wskaźnik do kursora przenoszenia i przenosi obiekt.|  
|Edytor traci fokus|Dezaktywuje tryb edycji w miejscu, mimo że obiekt przechowuje zawartość i wygląd, jaką miała w swoim ostatnim stanie operacji i wyboru.|  
|Wybieranie obiektów|Wskazuje obramowanie, linia kropkowana lub innych wizualnie distinct traktowania, aby wyróżnić granic obiektu.|  
|Zmiana rozmiaru wybranego obiektu|Oznaczone za pomocą uchwytów zaznaczenia.<br /><br /> Obiekt o zmiennym rozmiarze ma osiem uchwytów, reprezentujący każdego kierunku, w którym można go zmienić. Można użyć mniejszej liczby dojść, jeśli obiekt można zmienić tylko w niektórych kierunkach. Gdy użytkownik rozmiarach obiekt, do której osiem uchwytów nie jest interaktywny, mogą być używane cztery uchwyty. Rozmiary uchwyt należy powiązać z metryki obramowanie i krawędź okna z **GetSystemMetrics** funkcji interfejsu API, aby rozmiar proporcjonalnie rozdzielczość ekranu.<br /><br /> ![Uchwyty zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 05_ResizeHandles")|  
|Obróć wybranego obiektu|![Uchwyty obracania](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 06_Rotate")|  

#### <a name="keyboard-interaction"></a>Interakcji klawiatury  

|Dane wejściowe|Wynik|  
|-----------|------------|  
|Tab|Przesuwa wskaźnik fokus między logiczne kolejność obiektów w edytorze. Może to być od lewej do prawej lub od góry do dołu w zależności od **TabIndex** (lub równoważnego) wartość właściwości, kolejność tworzenia obiektów i ogólnego przeznaczenia edytora. Shift + Tab odwraca kierunek wskaźnika fokus.|  
|SPACJA|Aktywuje Tryb przesuwania, gdy jest utrzymywany przez naciśnięcie klawisza. Wejście myszy dodatkowe jest wymagany do Przesuwanie pozycji okienka ekranu.|  
|Ctrl+Spacja|Aktywuje tryb powiększenia, gdy jest utrzymywany przez naciśnięcie klawisza. Wejście myszy dodatkowe jest wymagany do zwiększenia lub zmniejszenia współczynnika powiększenia.|  
|Ctrl + Alt + znak Minus|Zmniejsza to powiększeniu o jeden poziom.|  
|Ctrl + Alt + znak Plus|Zwiększa powiększeniu o jeden poziom.|  
|Ctrl lub SHIFT|Dodaje obiekt do grupy zaznaczenia. CTRL umożliwia również usunąć obiekty indywidualnie z grupy zaznaczenia.|  
|Enter|Wykonuje polecenie domyślne dla obiektu (zazwyczaj Otwórz lub Edytuj).|  
|F2|Aktywuje edycji w miejscu dla obiektu.|  
|Klawisze strzałek|Przenosi wybrane obiekty w kierunku klawisz naciśnięty w małych odstępach (na przykład 1 piksel w czasie)|  
|CTRL + klawisze strzałek|Przenosi wybrane obiekty w kierunku klawisz naciśnięty wielokrotność większa (na przykład 10 pikseli w czasie)|  
|Shift + Strzałka kluczy|Zmienia rozmiar wybrane obiekty w odpowiednich kierunku, w małych odstępach (na przykład 1 piksel w czasie)|  
|Ctrl + Shift + klawisze strzałek|Zmienia rozmiar wybrane obiekty w odpowiednich kierunku, w przyrostach większa (na przykład 10 pikseli w czasie)|  

 Gdy użytkownicy edycji wzbogaconej w miejscu, może być uzasadnione dla obiektów automatycznie zmienić rozmiar z danymi wejściowymi użytkownika. Na przykład jeśli użytkownik edytuje formant etykiety, etykiety powinny Rozwijaj do wyświetlania tekstu, po prostu wpisany przez użytkownika. Jeśli nie zostanie to zrobione, użytkownik musi zmienić rozmiar formantu ręcznie po zakończeniu edycji tekstu. Jeśli użytkownik ma wiele formantów, staje się on rote i nieproduktywne zadań.  

#### <a name="graphical-containers"></a>Graficzny kontenerów  
 W niektórych przypadkach edytory graficzne zapewniają kontenery dla innych graficzne obiekty, takie jak formant panelu formularzy Windows lub Układ tabelaryczny formantu w Projektancie HTML. Jeśli Edytor zapewnia kontenery dla innych obiektów graficznych, następujący model wyboru należy użyć tylko kontenera (obiekty w ramach wykonaj kontenera standardowego modelu, jak opisano powyżej):  

|Dane wejściowe|Wynik|  
|-----------|------------|  
|Jednym kliknięciem w kontenerze|Wybiera obiekt kontenera bez bezpośrednio wybierając dowolną z zawartych obiektów. Kontener może być przeniesiona i/lub ze zmienionym rozmiarem za pomocą standardowej myszki i klawiatury (zgodnie z opisem powyżej). Zawarte obiekty są przenoszone w stosunku do kontenera, ale zawarte obiekty nie są rozmiaru, chyba że są zaznaczone także bezpośrednio.|  
|Umieść kursor nad region granic kontenera|Przycisk myszy jest przekształcany kursora przenoszenia, wskazującą, czy można przenieść kontener.|  
|Przeciągnij region granic kontenera|Zmiany przeniesienie kursora myszy, a następnie przenosi kontenerowi (i zawarte obiekty w ramach). Nie można przenieść kontener bez uprzedniego są wybrane za pomocą jednego kliknięcia.|  
|Jednym kliknięciem do obiektu w kontenerze|Odznacza kontenera (jeśli zostały wybrane) i wybiera kliknięto obiektu.|  
|SHIFT + kliknij opcję lub kombinację klawiszy Ctrl + kliknięcie zawartego w nim obiektu i/lub kontenera|Dodaje obiekt kliknięto istniejące zaznaczenie lub grupie zaznaczenia. Jeśli kliknięto obiekt jest już członkiem grupy zaznaczenia, spowoduje jego usunięcie z grupy wyboru.|  

 Zawarte obiekty powinny stosować się do modelu zaznaczenia podstawowe, zgodnie z opisem w poprzedniej sekcji. Z użytecznością testowania projektanta Windows Forms, użytkownicy oczekiwano bezproblemowy dostęp do zawartych obiektów bez interwencji kroków (nałożone przez obiekt zawierania).  

#### <a name="disjoint-and-region-selections"></a>Rozłączne i wyboru regionu  
 Edytory graficzne obiektu powinien obsługiwać rozłączne wybrane opcje. Należy pamiętać, że ta grafika nie są wyświetlane wyglądu kontrolki dla programu Visual Studio. Zobacz [graficznego obiektu wyboru wygląd](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) szczegółowe specyfikacje visual.  

 ![Rozłączne i regionu selektory](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 07_DisjointRegionSelectors")  

 **Rozłączne zaznaczenia**  

 Edytory graficzne powinien również udostępniać region zaznaczeń Wskaźnik zaznaczenia zaznaczenia typu. Jeśli edytor graficzny obsługuje inne typy obiektów (takich jak tekst), następnie wybory region może nie być możliwe w zależności od ograniczeń tych innych obiektów.  

 ![Ramki zaznaczenia](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 08_MarqueeSelection")  

 **Ramki zaznaczenia**  

#### <a name="primary-and-secondary-selections"></a>Opcje podstawowe i pomocnicze  
 Niektóre edytory graficzne obiekt umożliwia użytkownikowi edytowanie lub wyrównywanie obiektów w grupach. W tym przypadku koncepcji głównych i dodatkowych opcji musi zostać wprowadzony. Wybór podstawowego jest obiekt, do której inne obiekty reagowania w przypadku operacji grupy. Obiekt, który użytkownik wybierze pierwszy staje się kontrolki podstawowej, a kolejne zaznaczenia stają się dodatkowych opcji. Wybór podstawowego ma od pomocniczego wybory, aby wskazać, obiektu, który jest kluczem podstawowym różne podejścia visual:  

 ![Wybór podstawowego i pomocniczego](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 09_PrimarySecondary")  

 **Zaznaczenie główne z dwóch opcji dodatkowych**  

####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Wygląd Wybieranie obiektu graficznego  
 Uchwyty są kwadratów rysowane we wzorcu prostokątny wokół pola ograniczenia obiektu. Na wykresie poniżej przedstawiono przykłady różnych stanów, które obiekt graficzny może mieć z uchwyt zmiany rozmiaru i wygląd edycji w miejscu. Rozmiar uchwytów należy powiązać z krawędź okna i przy użyciu metryk brzegowych **GetSystemMetrics** interfejsu API.  


| Stan | Wygląd | Szczegóły dotyczące programu Visual |
|-------------------------|---------------| - |
| **Niezaznaczone** | Domyślny | ![Domyślny stan klawisza](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 10_DefaultState") |
| **Wybór podstawowego** | O zmiennych rozmiarach | ![Uchwyty zmiany rozmiaru zaznaczenie główne z](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 11_PrimaryResize") |
| **Wybór podstawowego** | Nie o zmiennych rozmiarach | ![Uchwyty zmiany rozmiaru zaznaczenia głównego bez](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 13_PrimaryNoResize") |
| **Wybór podstawowego** | Zablokowane | ![Wybór podstawowego zablokowane](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 15_PrimaryLocked") |
| **Wybór dodatkowej** | O zmiennych rozmiarach | ![Uchwyty zmiany rozmiaru pomocniczej zaznaczenie za pomocą](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 17_SecondaryResize") |
| **Wybór dodatkowej** | Nie o zmiennych rozmiarach | ![Wybór dodatkowej bez uchwyty zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 19_SecondaryNoResize") |
| **Wybór dodatkowej** | Zablokowane | ![Wybór dodatkowej zablokowane](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 21_SecondaryLocked") |
| **Aktywne interfejsu użytkownika** | Domyślny | ![Stan aktywny UI](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 23_UIActive") |

### <a name="view-selection-models"></a>Wyświetl modele zaznaczenia  

#### <a name="tree-view"></a>Widok drzewa  
 Zaznaczenie w widoku drzewa jest wyświetlany za pomocą prostego wyróżnienia. Jeśli użytkownik kliknie na nazwę węzła lub ikony węzła, staje się wybrany węzeł. Trójkątna symbole znajdujące się po lewej stronie węzła rozwiń węzeł lub kontrakt formantu drzewa, ale nie wpływają na wybranych przez użytkownika, z jednym wyjątkiem: od Zwijanie węzła nadrzędnego, gdy wybór korzysta z elementem podrzędnym tego węzła, Zaznaczenie przesuwa się do elementu nadrzędnego.  

 ![Typowy widok drzewa w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 25_TreeView")  

 **Typowy widok drzewa w programie Visual Studio**  

 Widok drzewa może obsługiwać wybory ciągłych i rozłączny, nawet na wielu poziomach, w drzewie. Ciągłe ani odłączonego wielokrotny musi nastąpić w węzłach drzewa widoczne. Jeśli węzeł jest zwinięte, rozłączne zaznaczenie zostanie utracone, a węzeł, który sbalil uzyskuje zaznaczenia. Dzięki temu użytkownik może wyświetlić węzły, które będą objęte operacją. Węzły są zwinięte, staje się jasne węzły, które może to mieć wpływ.  

 Po wybraniu węzła nadrzędnego operacja stosuje się do elementu nadrzędnego, chociaż może się zdarzyć, gdzie sens dla operacji stosuje się do obiektu nadrzędnego i wszystkie jego elementy podrzędne. W takim przypadku należy dostarczyć dodatkowy interfejs użytkownika podczas operacji, takich jak pola wyboru lub okno dialogowe potwierdzenia dokonać opcję "Zastosuj do wszystkich obiektów podrzędnych" jawne użytkownika.  

##### <a name="renaming"></a>Zmiana nazwy  
 Jeśli węzłów w drzewie obsługuje, zmiana nazwy, zmiana nazwy powinny odbywać się w miejscu. Operacja w miejscu powinien być standardowych we wszystkich kontrolkach drzewa w programie Visual Studio. Podaj polecenie zmiany nazwy, które natychmiast aktywuje tryb edycji w miejscu z zaznaczonego tekstu, obejmujących całą nazwę węzła, gotowy do przyjęcia danych wejściowych użytkownika. Jeśli węzeł reprezentuje plik, nazwa_pliku powinna zawierać rozszerzenia. Wyróżnienie wybór powinno obejmować tylko treść nazwę pliku i nie rozszerzenia.  

|Dane wejściowe|Wynik|  
|-----------|------------|  
|klawisz ENTER|Zatwierdza operacji zmiany nazwy|  
|Klawisz ESC|Anuluje operację zmiany nazwy|  
|Klikając poza obszarem edycji w miejscu|Zatwierdza operacji zmiany nazwy|  
|Cofnij|Zapewnia łatwe Cofnij, aby anulować operację zmiany nazwy|  

#### <a name="selection-within-lists-and-grid-controls"></a>Wybór w obrębie listy i formanty siatki  
 Kluczową koncepcją w opcji wyboru z listy jest, że jest ona oparta na wierszu, co oznacza, że po dokonaniu wyboru cały wiersz został wybrany jako jednostka. Z drugiej strony siatki umożliwia komórki, aby wybrać bez wywierania wpływu na innych aspektów wiersza. Siatki mogą również zawierać hierarchia zagnieżdżonych wierszy (np. kontrolki TreeGrid) umożliwiające gałęzie całej hierarchii, które można wybrać i niezaznaczone przez interakcję z wierszy nadrzędnych. Wybór na listach jest wyświetlane przez kolor wyróżnienia prostego na cały wiersz danych. Fokus jest pokazywana przez jednopikselowego kropkowana obramowanie wokół bieżącego można edytować wiersza lub komórki (wiersz, jeśli wszystkie komórki są tylko do odczytu).  

> [!NOTE]
>  **Fokus** i **wybór** różne zagadnienia. *Fokus* wskazanie, które interfejsu użytkownika elementu jest przeznaczona dla danych wejściowych nie zostały jawnie skierowany przeciwko innego obiektu, podczas gdy *wybór* odwołuje się do stanu włączenia obiektu w zestawie obiektów, na którym kolejne operacje może mieć miejsce.  

 Wybrane opcje na listach może być ciągłe, rozłączny, lub regionu. Gdy wiele zaznaczeń dozwolonych, ciągłym i wybór rozłączne powinna być zawsze obsługiwana, podczas obsługi opcji region (pole) jest opcjonalny. Opcje regionu są inicjowane za pomocą przeciągania biały treści listy.  


| Obiekt | Wybór |
|--------|------------|
| Lista | Ciągłe |
| Lista | Rozłączne |
| Lista | Region |

 Kliknij raz na liście zaznacza wiersz, w którym wystąpiło kliknięcie. Jeśli użytkownik stanie się kliknij w komórce listy, która obsługuje edycję w miejscu, komórki jest również natychmiast aktywowany do edycji w miejscu. W przeciwnym razie cały wiersz natychmiast jest zaznaczone i przedstawia wyróżnienie.  

 Przeciąganie w treści listy wykonuje jedną z trzech czynności:  

-   Inicjuje wyboru regionu, jeśli lista obsługuje tę funkcję i w dół myszy jest białych znaków  

-   Inicjuje operację przeciągania i upuszczania, jeśli komórki listy lub wiersza obsługuje on źródła przeciągania  

-   Wybiera bieżącego wiersza.  

##### <a name="in-place-editing"></a>Edytowanie w miejscu  
 W przypadku edycji w miejscu jest dozwolona, istnieją dwa podstawowe modele: selektora prostego edycji kontrolki i właściwości. Za pomocą kontrolki edycji proste zawartość jest wyróżniony i gotowe wprowadzania zaraz po edycji w miejscu aktywowaniu przez użytkownika. W przypadku, gdy wybór właściwości jest implementowana, przycisk, który wywołuje wybór właściwości jest wyświetlana po aktywowaniu tryb edycji w miejscu i bieżącego zaznaczenia nie są wyróżnione. Przycisk selektora powinny być wyrównany do prawej komórce. Aby uzyskać przykłady edycji w miejscu, zobacz **okno właściwości** i **listy zadań** w programie Visual Studio.  

##### <a name="keyboard-support"></a>Obsługa klawiatury  
 Obsługa klawiatury do wyboru na listach i w siatkach zgodna z konwencjami standardowa Windows:  

-   Klawisze strzałek powodują przechodzenie listę, wybierając każdej wiersza/komórki, ponieważ fokus zostanie przeniesiony.  

-   Shift + Strzałka wykonuje wyboru ciągłego, w kierunku klawiszy strzałek.  

-   CTRL + STRZAŁKA następuje Spacja Przełącza między Dodawanie i usuwanie elementów listy z zaznaczenia, tworzenie rozłączne zaznaczenia.  

-   Siatki, zawierających zagnieżdżone hierarchie klawisz Strzałka w prawo rozwija wiersza nadrzędnego i Strzałka w lewo zwija jeden.  

-   Klawisz Tab przesuwa fokus między komórkami w bieżącym wierszu, jeśli komórki są edytowalne.  

-   Klawisz Enter wykonywane domyślne na element na liście (często **Otwórz**).  

-   Klawisz F2 aktywuje edycji w miejscu dla aktualnie zaznaczonej komórki.  

##  <a name="BKMK_PersistenceAndSavingSettings"></a> Trwałość i zapisywanie ustawień  

### <a name="overview"></a>Omówienie  
 Mimo że każdy składnik oprogramowania w programie Visual Studio jest zazwyczaj odpowiedzialny za własne stan i stan trwały, Visual Studio automatycznie zapisuje ustawienia w niektórych przypadkach, takich jak za pomocą okna rozmiary i położenie. W poniższej tabeli jest kombinacją ustawienia zapisywane automatycznie i ustawienia, które wymagają użytkownika lub zaprogramowane podjęcia działania.  

|Obiekt|Co należy zapisać|Kiedy należy zapisać|Miejsce zapisania|  
|------------|------------------|------------------|-------------------|  
|Można wybrać obiekt (na przykład wiersz kodu)|Punkt przerwania w wierszu kodu<br /><br /> Skrót użytkownika skojarzonego z wierszem kodu|Gdy projekt jest zapisany|**Opcje użytkownika (suo)** plik projektu|  
|Okno dialogowe|Lokalizacja okno dialogowe, jeśli ma on przeniesiony<br /><br /> Widok, który użytkownik ostatnio w oknie dialogowym|Po zamknięciu okna dialogowego<br /><br /> Kiedy kończy się sesja programu Visual Studio|W pamięci<br /><br /> Rejestr w **HKEY_Current_User**|  
|Okno|Rozmiar i położenie okna|Po zamknięciu okna<br /><br /> Podczas zmiany trybu programu Visual Studio<br /><br /> Kiedy kończy się sesja programu Visual Studio|**Opcje użytkownika (suo)** plik projektu<br /><br /> Plik opcji niestandardowe okno ustawień|  
|dokument|Bieżące zaznaczenie w dokumencie<br /><br /> Widok dokumentu<br /><br /> Ostatnich kilku miejscach odwiedzony przez użytkownika|Gdy dokument zostanie zapisany|**Opcje użytkownika (suo)** plik projektu|  
|Projekt|Odwołania do plików<br /><br /> Odwołania do katalogów na dysku<br /><br /> Odwołania do innego oprogramowania<br /><br /> Składniki<br /><br /> Informacje o stanie o samym projekcie|Gdy projekt jest zapisany|Plik projektu|  
|Rozwiązanie|Odwołania do projektów<br /><br /> Odwołania do plików|Po zapisaniu projektu lub rozwiązania|**Rozwiązania (.sln)** pliku|  
|Ustawienia w **Narzędzia > Opcje**|Dostosowania klawiatury<br /><br /> Dostosowania paska narzędzi<br /><br /> Schematy kolorów|Gdy **Narzędzia > Opcje** zamyka okno dialogowe<br /><br /> Kiedy kończy się sesja programu Visual Studio|Rejestr w **HKEY_Current_User**|  

 Co użytkownik robi i gdy robią, mówią, czy ustawienia są zapisywane w pamięci (w trakcie sesji), zapisane na dysku (między sesjami jako ustawienie rejestru), jako część projektu lub rozwiązania sam plik, w ramach programu **rozwiązania Opcje (suo)** pliku lub zgodnie z ustawień niestandardowych plików tylko do tego składnika oprogramowania zna. Powyższej tabeli przedstawiono kilka zdarzeń, w których można zapisać ustawień. Istnieją jednak czasami, w których warto zapisać stan:  

-   Gdy użytkownik zmienia lokalizację, w obrębie okna dialogowego lub okna  

-   Gdy użytkownik przenosi fokus do innego okna  

-   Gdy użytkownik zmienia się od projektowania do tryb debugowania  

-   Po wylogowaniu się użytkownika swojego konta  

-   Gdy komputer przechodzi w stan hibernacji lub wyłączania  

-   Gdy komputer/dysku jest chcesz sformatować i ponownie skonfigurować aplikację  

### <a name="window-configurations"></a>Konfiguracje okien  
 Konfigurację okna jest podstawowe prezentacji środowiska deweloperskiego — jest schemat, składający się z listy obecnych okien narzędzi i sposobu, w którym są uporządkowane. Dla systemu windows zarządzany przez środowisko IDE (system windows IDE) informacji o układzie jest trwały dla każdego użytkownika, więc po użytkownik zostanie uruchomiona, IDE, układ okna pojawi się taka sama jak gdy trwają zakończył działanie programu Visual Studio. Stan i położenie okna środowiska IDE są utrwalane w pliku opcji niestandardowych w formacie XML. Okien narzędzi, które są tworzone przez pakiety załadowana do środowiska IDE utrwalić informacje o ich stanie, w rejestrze i może być lub może się różnić dla poszczególnych użytkowników.  

#### <a name="profile-specific-layouts"></a>Układy specyficzne dla danego profilu  
 Każdy profil zawiera układy okien narzędzi, zorganizowanych w sposób znane deweloperów określonych osób (deweloperów Visual C++ powinny być widoczne **Eksploratora rozwiązań** po lewej stronie IDE, podczas gdy deweloperów języka C#, powinny być widoczne  **Eksplorator rozwiązań** po prawej stronie). Układy okien specyficzne dla danego profilu są ładowane po użytkownik wybierze profilu przy uruchamianiu. Autor pakietu, należy określić układ okna najbardziej odpowiednie dla obsługi swoich klientów, wiedząc, że zmiany wprowadzone przez użytkownika w konfiguracji okna zostaną następnie utrwalone.  

##  <a name="BKMK_TouchInput"></a> Wprowadzanie dotykowe  
 Użytkownicy są coraz bardziej przy użyciu rozwoju firmy na urządzeniach dotykowych. Istnieją jednak bariery, które utrudniają używać narzędzi programistycznych dostępnych na urządzeniach dotykowych. Użytkownicy będą oczekiwać, że nasze produkty, aby zapewnić środowisko touch wiarygodne i dokładne. Celem tych wytycznych ma ułatwić podjęcie decyzji o możliwości touch zestawowi i zachęcania touch spójne środowisko dla programu Visual Studio i powiązanych produktów.  

### <a name="levels-of-experience"></a>Poziomy doświadczenia  
 Następujące poziomy środowisko są przeznaczone do służyć jako przewodnik dotyczący pomagają zespołom zdecydować, które oferują możliwości touch na podstawie ich żądanego poziomu zainteresowania inwestycji w kontakcie.  

-   **Podstawowe doświadczenie w zakresie** jest dla zespołów, które chcesz udostępnić touch możliwości, więc nie końce dead w całej swojej pracy.  

-   **Zoptymalizowane pod kątem obsługi** jest przeznaczona dla zespołów, które mają być możliwości najbardziej typowe touch (na przykład te zwykle dostępne w aplikacji przeglądarki internetowe).  

-   **z podwyższonym poziomem uprawnień środowisko** dla zespołów, które chcesz dodać funkcje, takie jak gesty lub inne opcjonalne funkcje, które mogą ułatwić ich stosowania wyświetlaczy dotykowych przyjazna.  

||Podstawowe doświadczenie w zakresie|Zoptymalizowane środowisko|Środowisko z podwyższonym poziomem uprawnień|  
|-|----------------------|--------------------------|-------------------------|  
|Umożliwia użytkownikom...|Napraw kod i rozwiązania/projektu-odczytywanie bez dead kończy się|Wykonywanie zadań konserwacji, refactors i nawigacja|Działać w spójny, intuicyjny i płynny interfejs, bez obaw|  
|Edytor|Wybieranie i przesuwanie dotykowe<br /><br /> Dotknij paska przewijania, aby przejść i naciśnij klawisz + przeciągnij|Ściśnięcie powiększenia<br /><br /> Szybkie przewijanie<br /><br /> Wybór<br /><br /> Łatwe korzystanie z menu kontekstowego||  
|Najważniejsze okien|Przesuwanie listy<br /><br /> Wybór elementu<br /><br /> Dotknij paska przewijania, aby przejść i naciśnij klawisz + przeciągnij|Łatwe elementu przewijanie i wybieranie||  
|Obsługi okien||Zmień rozmiar okna<br /><br /> Szybki dostęp||  
|Dobrze dokumentu||Ułatwiających przechodzenie między otwartych plików||  
|Gestów||Upewnij się, że gestów wspólnej pracy w środowisku IDE|Czynności na podstawie gestu<br /><br /> Obsługa przeciągania i upuszczania oraz projektantów|  
|Inne zagadnienia|||Niestandardowych klawiatur ekranowych|  

#### <a name="gestures"></a>Gestów  
 Gesty użytkownikom skrótów do poleceń, które w przeciwnym razie mogą wymagać bardziej skomplikowanych interakcji. Zapoznaj się z wytycznymi dotyczącymi Windows na [powszechnych gestów dotykowych dla aplikacji komputerowych](/windows/desktop/wintouch/windows-touch-gestures-overview)i postępuj zgodnie z tych wskazówkach dotyczących większości gestów, łącznie z prostych gestów takich jak przesuwać i powiększać.