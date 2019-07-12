---
title: Ocena Tools for Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00668fdebdbc8fc6a26c30a8762aa6f03d6e2769
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824564"
---
# <a name="evaluation-tools-for-visual-studio"></a>Narzędzi programu Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista kontrolna craftsmanship programu Visual Studio
 Ta lista kontrolna umożliwia ocenę jakość środowiska użytkownika dla szczegółów wizualizacji i interakcji.

### <a name="overview"></a>Omówienie

- Upewnij się, że wszystkie polecenia spowoduje opinie, które informuje użytkowników przeprowadzane ich poleceń.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika i formanty są widoczne w wszystkie motywy oraz w trybie dużego kontrastu.

- Upewnij się, że wybór nieaktywne i aktywne zawsze są zróżnicowane, zarówno w wersjach standard i trybu wysokiego kontrastu.

- Sprawdź, że fokus jest zawsze widoczny i jawnego.

### <a name="performance"></a>Wydajność

- Sprawdź, niektóre rodzaju "zajęty" wskaźnik jest wyświetlany, jeśli polecenie ma więcej niż jedna sekunda, aby zakończyć.

- Sprawdź, czy polecenie ma więcej niż 10 sekund, pasek postępu jawne, albo określony (preferowany) lub niejasnego, jest wyświetlany.

### <a name="ui-text"></a>Tekst interfejsu użytkownika

- Sprawdź, czy wszystkie etykiety case zdania lub tytuł, a nie tekst wyłącznie małe litery.

    ||Popraw|Niepoprawne|
    |-|-------------|---------------|
    |**Tekst polecenia, (wszystko)**|Jak w zdaniu:<br /><br /> **Nazwa katalogu:**|Nazwa katalogu:|
    |**Tekst przycisku (klient)**|Wielkimi literami:<br /><br /> **[Ustaw jako domyślną]**|USTAW JAKO DOMYŚLNE|
    |**Tekst przycisku (online)**|Jak w zdaniu:<br /><br /> **Ustaw jako domyślny]**||

- Sprawdź, czy wszystkie etykiety, z wyjątkiem nagłówków grup i przycisków, kończyć dwukropkiem, a następnie poprzedzać kontrolkę, z którą są skojarzone.

- Sprawdź, czy przyciski, polecenia i linki polecenia, które Uruchom interfejs użytkownika do przechwycenia danych wejściowych użytkownika kończy się wielokropek **[...]** .

  Przykłady:

  - **[Zaawansowane...]**  przycisku w oknie dialogowym.

  - Opcje polecenia w menu Narzędzia (**Narzędzia > Opcje**) nie powinno być wyświetlane wielokropek, ponieważ uruchomienie okna dialogowego, sama jest celem polecenia.

- Sprawdź, czy interfejs użytkownika zawiera nie skróty, z wyjątkiem warunków będące standardami branżowymi. Na przykład HTML ani TCP/IP nie trzeba województw, chociaż za mało pamięci (mało pamięci) oraz dane osobowe (identyfikowalne dane osobowe) należy.

### <a name="keyboard-access"></a>Dostęp za pomocą klawiatury

- Sprawdź, czy jest to sposób wykonania poszczególnych zadań za pomocą klawiatury. Zazwyczaj jest to realizowane za pośrednictwem dostęp za pomocą klawiatury dla każdego formantu, ale niektóre bogatego obszarów jest dopuszczalne obejście tego problemu, takie jak przechodzenie do widoku kodu.

- Upewnij się, że można przełączać się między kontrolek w logicznej kolejności (od lewej do prawej i od góry do dołu). Jest to najlepsze rozwiązanie dla większości kontrolek, nie wszystkie formanty wymagają tego podejścia. Sprawdź na przykład, ten przycisk radiowy, które kontrolki znajdują się w grupie za pomocą tabulatorów.

- Sprawdź, że wszystkie formanty etykiet, a każda etykieta ma wartość (wyjątki obejmuje niektóre-etykietą kontrolki, które może skorzystać z etykietami kontroli na karcie).

- Sprawdź, czy nie występują żadne konflikty mnemoników.

### <a name="fonts"></a>Czcionki

- Sprawdź, czy wszystkie czcionki (rozpoznawania twarzy, rozmiar, kolor) są stosowane konsekwentnie i Obsługa hierarchii.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika korzystają z usługi czcionka środowiska. (Zobacz [czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Aby sprawdzić, jeśli usługa jest używana, przejdź do **Narzędzia > Opcje > czcionki i kolory**. Na liście rozwijanej Ustawienia wybierz czcionkę środowiska Zmień krój czcionki stylistically inny (na przykład Mochnacki lub sieci SAN Comic) i ustaw rozmiar do 12 (czas pacyficzny). Kliknij przycisk OK. Może być konieczne ponowne uruchomienie środowiska IDE, ale większość interfejsu użytkownika zmieni się natychmiast. Obszary, nie należy zbierać zmiana czcionki, nawet w przypadku ponownego uruchomienia, które nie korzystają z czcionka środowiska.

- Upewnij się, że czcionek, które są pochodną usługi (na przykład tekst pogrubiony lub rozszerzonej) zachowują ich rozmiar i formatowania w odniesieniu do tekstu "normal", po zmianie rozmiaru czcionki w środowisku.

- Upewnij się, że nie błędy wycinka z powodu rozszerzonej czcionki. Czcionki, które Pobierz przycięte prawdopodobnie są wynikiem stałą wysokość kontrolek lub stałą wysokość kontenerów.

### <a name="dialogs"></a>Okna dialogowe

- Sprawdź, czy tytuł okna dialogowego jest taka sama jak polecenia, który go uruchomił.

- Sprawdź, czy wszystkie formanty standardowe są zgodne z systemem operacyjnym: kolor tła jest standardowy i brak kontrolek powinien mieć specjalne styl z szablonem re, który sprawia, że będą pojawiać się różni się od standardowych kontrolek.

- Sprawdź, czy marginesy w formularzu powinny być 12 pikseli, a powinien zostać wyświetlony jednolite i spójne.

- Sprawdź, czy wyśrodkowany w powłoce środowiska IDE lub okno, które je zduplikowany okien dialogowych.

- Gdy jest to przydatne, okna dialogowe powinna być o zmiennym rozmiarze. W oknach dialogowych, które są o zmiennym rozmiarze Sprawdź, czy po zmianie rozmiaru kontrole należy zmienić rozmiar, podczas gdy inne części okna dialogowego pozostał bez zmian.

- Sprawdź, czy o zmiennym rozmiarze w oknach dialogowych utrwalić dowolnej wielkości dostosowane przez użytkownika (rozmiar, lokalizację, rozszerzenia formantów okna dialogowego i tak dalej).

- Sprawdź, czy brak ikony na pasku tytułu.

- Upewnij się, że nie przyciski na pasku tytułu.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Okno dialogowe operacji przycisków (tylko w przypadku klienta programu VS)

- Sprawdź, czy przyciski operacji w podanej kolejności: **OK**, **anulować**, **zastosować**.

- Upewnij się, że **OK** i **anulować** przyciski są standardowy rozmiar: 75 x 23 pikseli.

- Upewnij się, że **OK** i **anulować** przyciski są w taki sam rozmiar, niezależnie od długości ciągu.

- Jeśli etykieta na przycisku operacja wymaga przycisk za większy niż standardowe, upewnij się, że odpowiednie **anulować** przycisk jest taki sam rozmiar.

- Sprawdź, czy uzupełnienie 6 pikseli, między przycisków i skojarzonych formantów.

- Upewnij się, że **OK** i **anulować** przyciski nie mają mnemonik (klucze dostępu zdefiniowane przez podkreślona litera).

- Sprawdź, że jeden przycisk (zazwyczaj **OK**) domyślnie ma fokus.

- Upewnij się, że **Esc** anuluje okna dialogowego

- Upewnij się, że **Enter** przycisk domyślny jest wykonywany, jeśli zespół nie znajduje się w formant, który przetwarza Enter.

- Upewnij się, że **OK** i **anulować** przyciski są umieszczone w prawym dolnym rogu okna dialogowego. W wyjątkowych przypadkach jest dopuszczalna być ułożone pionowo w prawym górnym rogu.

- Sprawdź, czy pionowy jest ona używana tylko wtedy, gdy inne przyciski znajdują się w wyrównanie w poziomie w oknie dialogowym.

### <a name="control-standards"></a>Standardy kontroli

#### <a name="general"></a>Ogólne

- Sprawdź, czy, jeśli to możliwe, wartości domyślne dobre, aby przyspieszyć interakcji z użytkownikiem i poinstruować użytkowników kierunku wynik bezpiecznych lub wspólnej.

- Upewnij się, że standardowych kontrolek działają tak samo, tak aby użytkownicy wiedzieli, co się stanie, na podstawie wcześniejszych doświadczeń.

#### <a name="label-controls"></a>Formanty etykiet

- Sprawdź, czy każda kontrolka ma etykietę, i czy każda etykieta wizualnie wraz z jego sterowania (zazwyczaj w zakresie pikseli 4 – 6), a następnie znajduje się bliżej niż jego odpowiedni formant do innych kontrolek.

- Sprawdź, czy etykiety są rozmieszczone opróżnić po lewej stronie, za pomocą kontrolki lewej krawędzi, jeśli jest umieszczana powyżej i wyśrodkowane w poziomie, dzięki czemu linii bazowej etykiety jest wyrównana z linią bazową elementu wejściowego tekstu, jeśli umieszczony po lewej stronie.

- Sprawdź, czy w przypadku kilku skumulowany etykiety i formanty wejściowe są umieszczone po lewej stronie kontrolki, etykiety jest wyrównany do lewej, a odległości od krawędzi okna dialogowego, nigdy nie opróżniania po prawej stronie i odległości od kontrolek. Pary powinny równomiernie rozłożony, chyba że potrzebują dodatkowych odstępów, aby wskazać grupowania.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Kontrolki wejściowe (pola tekstowe i pola kombi)

- Sprawdź, czy korzystając z domyślną czcionkę środowiska, wysokość wyświetlaną dla pola tekstowe, pola kombi i przyciski wszystkie piksele 23.

- Jeśli jest używany tekst wskazówki, sprawdź, czy jest ustawiony kolor `Environment.ControlEditHintText` przy użyciu usługi kolorów.

- Jeśli pole jest wymagane pola, które muszą być określone jako takie, sprawdź:

  - tło ustawioną na `Environment.ControlEditRequiredBackground` i ustawiono pierwszego planu `Environment.ControlEditRequiredHintText`

  - czy jest tekst wskazówki w kontrolce, która jest wyświetlana jako **"\<wymagane >"**

#### <a name="button-controls"></a>formanty przycisków

- Sprawdź, czy przyciski minimalny rozmiar 75 x 23 pikseli, chyba że ograniczanych dłużej tekstu.

- Sprawdź, czy przyciski zostały lewą i prawą marginesy 3 – 5 pikseli, a także dopełnienie zawartości.

- Dopuszcza się mały kwadratowy przycisk za pomocą tylko wielokropek **[...]**  na nim zamiast **[Przeglądaj …]**  przycisk (lub podobne funkcje). Jeśli używane, sprawdź, czy przycisk jest 23 x 23 rozmiar.

- Jeśli istnieje więcej niż jedna **[Przeglądaj …]**  znajdujący się w oknie dialogowym, a następnie upewnij się, że wersja (tylko do wielokropka **[...]** ) jest używane dla wszystkich.

- Sprawdź, że wielokropka **[...]**  przyciski nie mają wartość. Gdy fokus jest ustawiony na kontrolki wprowadzania obok niej, jednej karty powinny Przenieś fokus do przycisku wielokropka.

- Sprawdź, czy przyciski, polecenia i linki polecenia, które Uruchom pomocniczy interfejs użytkownika, który przechwytuje dane wejściowe użytkownika więcej może kończyć się wielokropek **[...]** .

#### <a name="hyperlinks"></a>Hiperłącza

- Upewnij się, że kontrolki hiperlinku nigdy nie pojawi się czerwony, gdy jest ona aktywna. Jest to wskaźnik usługi kolorów nie jest użycie

- Sprawdź, czy kolory programu VS, używane są:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Sprawdź, czy hiperłącza niebieski podkreślony nie, chyba że osadzony w akapicie.

#### <a name="check-boxes"></a>Pola wyboru

- Jeśli pole wyboru ma tekstu wielowierszowego, sprawdź, czy pole jest wyrównywany z pierwszego wiersza tekstu, nie wyśrodkowane w pionie w obrębie wszystkich wierszy.

- Sprawdź, czy pola wyboru zawsze wskazywać charakter binarne i nie użytkownik lub otwieranie nowych okien lub stron.

- Jeśli pole wyboru opcji związanych z kontrolkę wejściową, sprawdź, czy jest umieszczony opróżnić z lewej i bardzo blisko w ramach tej kontrolki, aby wskazać jej relacji.

- Sprawdź, czy pole wyboru jest **nigdy nie** jako środek umożliwiają całą zawartość okna dialogowego lub strony.

#### <a name="group-boxes"></a>Pola grupy

- Sprawdź, czy okno dialogowe zawiera pole pojedynczej grupy znajdujący się w nim, który zawiera całą zawartość okna dialogowego.

- Upewnij się, że co najmniej dwóch kontrolek w obrębie każdego pola grupy.

- Rzadko powinny istnieć więcej niż dwa pola grupy w oknie dialogowym.

- Upewnij się, że nie zagnieżdżone pola grupy.

### <a name="icons"></a>Ikony

- Sprawdź, czy ikony są wyświetlane poprawnie odwróconą w ciemnego motywu.

- Upewnij się, że wszystkie ikony opierają się na podstawowych pojęć.

- Sprawdź, czy każda ikona distinct, łatwa do rozpoznania i nie zawiera więcej niż dwoma pojęciami (bez stanu modyfikator/język).

- Sprawdź, czy ikona podstawowej znajduje się wyśrodkowane w obszarze.

- Sprawdź, czy wszystkie ikony są wyświetlane w trybie dużego kontrastu do odczytania.

- Upewnij się, każdy kolor używany jest wyrównywany z normami użycia kolor.

- Upewnij się, że nie otoczki (obramowanie) wokół ikon. (Jeśli jest obecny, obwódki powinna odpowiadać kolor tła sąsiadujących interfejsu użytkownika).

### <a name="touch-enabled-ui"></a>Interfejs użytkownika z obsługą dotykową

- Sprawdź, czy kontrolki interaktywne wystarczająco duży, aby był łatwo touchable — minimalna **pikseli 23 x 23** rozmiaru

- Sprawdź, czy są najczęściej używane kontrolki co najmniej **40 40 pikseli** rozmiar.

- Sprawdź, czy kontrolki interaktywne mają co najmniej **5 pikseli odstępy** między nimi
