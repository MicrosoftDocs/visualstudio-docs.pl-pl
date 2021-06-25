---
title: Narzędzia do oceny dla Visual Studio | Microsoft Docs
description: Ta lista kontrolna umożliwia ocenę jakości obsługi użytkownika dla szczegółów wizualizacji i interakcji dla nowych funkcji, które projektuje się dla Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baee9f3e2eaefcd659f8428bd566711949d0fe90
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900762"
---
# <a name="evaluation-tools-for-visual-studio"></a>Narzędzia do oceny dla programu Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista kontrolna dla Visual Studio
 Ta lista kontrolna pozwala ocenić jakość obsługi użytkownika dla szczegółów wizualizacji i interakcji.

### <a name="overview"></a>Omówienie

- Sprawdź, czy wszystkie polecenia są wynikiem opinii, która informuje użytkowników, że ich polecenia zostały wykonane.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika i kontrolki są widoczne we wszystkich motywach i duży kontrast trybie.

- Sprawdź, czy nieaktywny i aktywny wybór są zawsze zróżnicowane, zarówno w trybie standardowym, jak i duży kontrast trybie.

- Sprawdź, czy fokus jest zawsze widoczny i widoczny.

### <a name="performance"></a>Wydajność

- Sprawdź, czy jest wyświetlany jakiś wskaźnik "zajęty", jeśli ukończenie polecenia trwa dłużej niż jedną sekundę.

- Sprawdź, czy jeśli ukończenie polecenia trwa dłużej niż 10 sekund, zostanie wyświetlony jawny pasek postępu określony (preferowany) lub nieokreślony.

### <a name="ui-text"></a>Tekst interfejsu użytkownika

- Sprawdź, czy wszystkie etykiety są zdaniami lub tytułami i czy tekst nie jest całkowicie małymi literami.

    ||Odpowiedź prawidłowa|Odpowiedź nieprawidłowa|
    |-|-------------|---------------|
    |**Tekst polecenia (wszystkie)**|Litera zdania:<br /><br /> **Nazwa katalogu:**|Nazwa katalogu:|
    |**Tekst przycisku (klient)**|Przypadek tytułu:<br /><br /> **[ Ustaw jako domyślny ]**|USTAW JAKO DOMYŚLNY|
    |**Tekst przycisku (online)**|Litera zdania:<br /><br /> **[ Ustaw jako domyślny ]**||

- Sprawdź, czy wszystkie etykiety, z wyjątkiem nagłówków grup i przycisków, kończą się dwukropkiem i poprzedzają kontrolkę, z którą są sparowane.

- Sprawdź, czy przyciski, polecenia i linki poleceń uruchamiają interfejs użytkownika w celu przechwycenia końca danych wejściowych użytkownika za pomocą wielokropka **[...]**.

  Przykłady:

  - Przycisk **[Zaawansowane...]** w oknie dialogowym.

  - Opcje polecenia w menu Narzędzia (Narzędzia **> Opcje**) nie powinny mieć wielokropka, ponieważ uruchomienie samego okna dialogowego jest intencją polecenia.

- Sprawdź, czy interfejs użytkownika nie zawiera skrótów, z wyjątkiem terminów branżowych. Na przykład nie trzeba pomylić ani kodu HTML, ani PROTOKOŁU TCP/IP, chociaż powinien być używany protokół OOM (za pamięci) i dane osobowe (dane osobowe).

### <a name="keyboard-access"></a>Dostęp za pomocą klawiatury

- Sprawdź, czy istnieje sposób wykonania każdego zadania za pomocą klawiatury. Zazwyczaj odbywa się to za pośrednictwem dostępu za pomocą klawiatury dla każdej kontrolki, ale w przypadku niektórych wysoce wizualnych obszarów akceptowalne jest obejście, takie jak przechodząc do widoku kodu.

- Sprawdź, czy możesz przechodzić za pomocą klawisza Tab za pomocą kontrolek w kolejności logicznej (od lewej do prawej i od góry do dołu). Chociaż jest to najlepsze rozwiązanie w przypadku większości kontrolek, nie wszystkie kontrolki wymagają tego podejścia. Na przykład sprawdź, czy kontrolki przycisku radiowego znajdują się w grupie z pojedynczym zatrzymaniem tabulatora.

- Sprawdź, czy wszystkie kontrolki mają etykiety i czy każda etykieta ma mnemonik (wyjątki obejmują niektóre kontrolki bez etykiet, które mogą być zgodne z kontrolką oznaczoną na karcie).

- Sprawdź, czy nie występują konflikty mnemoniczne.

### <a name="fonts"></a>Czcionki

- Sprawdź, czy wszystkie czcionki (twarz, rozmiar, kolor) są używane spójnie i utrzymują hierarchię.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika korzystają z usługi czcionek środowiska. (Zobacz [Czcionki i formatowanie dla Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Aby sprawdzić, czy usługa jest używana, przejdź do tematu Narzędzia > opcje > **czcionki i kolory.** Na liście rozwijanej Ustawienia wybierz pozycję Czcionka środowiska i zmień rozmiar czcionki na inną w stylu stylistycznym (na przykład Harr przekrój lub Przejmij sans) i ustaw rozmiar na 12 punktów. Następnie kliknij przycisk OK. Może być konieczne ponowne uruchomienie środowiska IDE, ale większość interfejsu użytkownika zmieni się natychmiast. Obszary, w których czcionka nie jest zmieniana nawet po ponownym uruchomieniu, nie są używane przez czcionkę środowiska.

- Sprawdź, czy czcionki, które są pochodnymi usługi (na przykład pogrubiony lub powiększony tekst), zachowują rozmiar i formatowanie w odniesieniu do "normalnego" tekstu, gdy rozmiar czcionki środowiska zostanie zmieniony.

- Sprawdź, czy nie ma żadnych usterek przycinania spowodowanych powiększoną czcionką. Czcionki, które są obcinane, są prawdopodobnie wynikiem kontrolek o stałej wysokości lub kontenerów o stałej wysokości.

### <a name="dialogs"></a>Okna dialogowe

- Sprawdź, czy tytuł okna dialogowego jest taki sam jak polecenie, które go uruchomiło.

- Sprawdź, czy wszystkie kontrolki standardowe są zgodne z systemem operacyjnym: kolor tła jest standardowy i żadne kontrolki nie powinny mieć specjalnego stylu ponownie z szablonem, który sprawia, że wyglądają one inaczej niż kontrolki standardowe.

- Sprawdź, czy marginesy w formularzu powinny mieć 12 pikseli i powinny być jednolite i spójne.

- Sprawdź, czy okna dialogowe są wyświetlane wyśrodkowane w obrębie powłoki IDE lub okna, które je zduplikowało.

- Jeśli jest to przydatne, okna dialogowe powinny mieć zmienianą rozmiaru. W przypadku okien dialogowych, które można zmieniać, sprawdź, czy po zmianie rozmiaru odpowiednie kontrolki muszą zmieniać rozmiar, podczas gdy inne części okna dialogowego pozostają stałe.

- Sprawdź, czy okna dialogowe z możliwością zmiany rozmiaru utrwalą dowolny rozmiar dostosowany przez użytkownika (rozmiar, lokalizacja, rozszerzenie kontrolek okien dialogowych itd.).

- Sprawdź, czy na pasku tytułu nie ma ikony.

- Sprawdź, czy na pasku tytułu nie ma przycisków Minimalizuj i Maksymalizuj.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Przyciski operacji okna dialogowego (tylko klient PROGRAMU VS)

- Sprawdź, czy przyciski operacji są w tej kolejności: **OK,** **Anuluj,** **Zastosuj.**

- Sprawdź, **czy przyciski OK** i **Anuluj** mają standardowy rozmiar: 75 x 23 piksele.

- Sprawdź, **czy przyciski OK** i **Anuluj** mają taki sam rozmiar niezależnie od długości ciągu.

- Jeśli etykieta na przycisku operacji wymaga, aby przycisk był szerszy niż standardowy, sprawdź, czy odpowiedni przycisk **Anuluj** ma taki sam rozmiar.

- Sprawdź, czy między przyciskami i skojarzonymi kontrolkami znajduje się wypełnienie o 6 pikselach.

- Sprawdź, czy **przyciski OK** i **Anuluj** nie mają mnemonik (klucze dostępu są zdefiniowane za pomocą podkreślonej litery).

- Sprawdź, czy jeden przycisk (zazwyczaj **OK)** ma domyślnie fokus.

- Sprawdź, **czy esc** anuluje okno dialogowe

- Sprawdź, **czy klawisz Enter** wykonuje przycisk domyślny, jeśli fokus nie znajduje się w kontrolce, która przetwarza klawisz Enter.

- Sprawdź, czy **przyciski OK** i **Anuluj** znajdują się w prawym dolnym rogu okna dialogowego. W rzadkich wyjątkach dopuszczalne jest ich układanie w pionie w prawym górnym rogu.

- Sprawdź, czy konfiguracja pionowa jest używana tylko wtedy, gdy inne przyciski są wyrównane w poziomie w oknie dialogowym.

### <a name="control-standards"></a>Standardy kontroli

#### <a name="general"></a>Ogólne

- Sprawdź, czy jeśli to możliwe, istnieją dobre wartości domyślne, aby przyspieszyć interakcję z użytkownikiem i skierować użytkowników w kierunku bezpiecznego lub wspólnego wyniku.

- Sprawdź, czy standardowe kontrolki zachowują się tak samo, aby użytkownicy wiedzieli, co się stanie w oparciu o wcześniejsze doświadczenie.

#### <a name="label-controls"></a>Kontrolki etykiet

- Sprawdź, czy każda kontrolka ma etykietę i czy każda etykieta jest wizualnie sparowana z kontrolką (zazwyczaj w zakresie 4–6 pikseli) i jest bliżej odpowiadającej jej kontrolki niż do innych kontrolek.

- Sprawdź, czy etykiety są wyrównane do lewej krawędzi kontrolki, jeśli są wyrównane powyżej i wyśrodkowane w poziomie, tak aby punkt odniesienia etykiety był wyrównany do linii bazowej tekstu wejściowego, jeśli znajduje się w lewo.

- Sprawdź, czy jeśli po lewej stronie kontrolki jest umieszczonych kilka kontrolek skumulowanych i wejściowych, etykiety są opróżniane w lewo i w równej odległości od krawędzi okna dialogowego, nigdy nie opróżniaj w prawo i w równej odległości od kontrolek. Pary powinny być dystrybuowane równomiernie, chyba że potrzebują dodatkowych odstępów w celu wskazania grupowania.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Kontrolki wejściowe (pola tekstowe i pola kombi)

- Sprawdź, czy w przypadku korzystania z domyślnej czcionki środowiska wysokość wyświetlania pól tekstowych, pól kombi i przycisków wynosi 23 piksele.

- Jeśli jest używany tekst wskazówki, sprawdź, czy kolor jest ustawiony na `Environment.ControlEditHintText` przy użyciu usługi kolorów.

- Jeśli pole jest polem wymaganym, które musi zostać zidentyfikowane jako takie, sprawdź:

  - ustawiono tło, `Environment.ControlEditRequiredBackground` a na pierwszym planie ustawiono wartość `Environment.ControlEditRequiredHintText`

  - że w kontrolce znajduje się tekst wskazówki wyświetlany jako **" \<Required> "**

#### <a name="button-controls"></a>formanty przycisków

- Sprawdź, czy przyciski mają minimalny rozmiar 75 x 23 piksele, chyba że mają dłuższy tekst.

- Sprawdź, czy przyciski mają lewy i prawy margines o szerokości 3–5 pikseli, a także wypełnienie zawartości.

- Dopuszczalne jest użycie małego przycisku kwadratowego z wielokropem **[...]** zamiast przycisku **[Przeglądaj...]** (lub podobnej funkcjonalności). Jeśli jest używany, sprawdź, czy przycisk ma rozmiar 23x23.

- Jeśli w oknie dialogowym znajduje się więcej niż jeden przycisk **[Przeglądaj...],** sprawdź, czy skrócona wersja (tylko wielokropek **[...]**) jest używana dla wszystkich.

- Sprawdź, czy przyciski wielokropka **[...]** nie mają mnemonika. Gdy fokus znajduje się obok kontrolki wprowadzania, jedna karta powinna przenieść fokus na przycisk wielokropka.

- Sprawdź, czy przyciski, polecenia i linki poleceń, które uruchamiają pomocniczy interfejs użytkownika, który przechwytuje więcej danych wejściowych użytkownika, muszą kończyć się wielokropkami **[...]**.

#### <a name="hyperlinks"></a>Hiperlinki

- Sprawdź, czy kontrolka hiperlinku nigdy nie pulsuje na czerwono, gdy jest aktywna. Jest to wskaźnik, że usługa kolorów nie jest w użyciu

- Sprawdź, czy używane są kolory programu VS:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Sprawdź, czy hiperlinki są wyświetlane na niebiesko bez podkreślenia, chyba że zostaną osadzone w akapicie.

#### <a name="check-boxes"></a>Pola wyboru

- Jeśli pole wyboru zawiera tekst wielo wierszowy, sprawdź, czy pole jest wyrównane do pierwszego wiersza tekstu, a nie wyśrodkowane w pionie we wszystkich wierszach.

- Sprawdź, czy pola wyboru zawsze wskazują opcje binarne i nie nawigują po użytkowniku ani nie otwierają nowych okien ani stron.

- Jeśli pole wyboru zawiera opcję powiązaną z kontrolką wejściową, sprawdź, czy jest ona wyrównana do lewej i bardzo blisko tej kontrolki, aby wskazać jej relację.

- Sprawdź, czy pole wyboru nigdy **nie** jest używane jako sposób włączania całej zawartości okna dialogowego lub strony.

#### <a name="group-boxes"></a>Pola grupowania

- Sprawdź, czy okno dialogowe nie zawiera jednego pola grupy zawierającego całą zawartość okna dialogowego.

- Sprawdź, czy w każdym polu grupy znajdują się co najmniej dwie kontrolki.

- Rzadko w oknie dialogowym powinny być wyświetlane więcej niż dwa pola grup.

- Sprawdź, czy nie ma żadnych zagnieżdżonych pól grupy.

### <a name="icons"></a>Ikony

- Sprawdź, czy ikony są prawidłowo odwrócone w przypadku ciemnego motywu.

- Sprawdź, czy wszystkie ikony są oparte na podstawowych pojęciach.

- Sprawdź, czy każda ikona jest odrębna, łatwa do rozpoznania i nie zawiera więcej niż dwóch pojęć (bez modyfikatora stanu/języka).

- Sprawdź, czy ikona podstawowa jest wyświetlana wyśrodkowana w obszarze.

- Sprawdź, czy wszystkie ikony są czytelne duży kontrast trybie.

- Sprawdź, czy dowolny używany kolor jest wyrównany ze standardami użycia kolorów.

- Sprawdź, czy nie ma obwódek (obramowań) wokół ikon. (Jeśli jest obecny, obwódka powinna odpowiadać kolorowi tła sąsiadującego interfejsu użytkownika).

### <a name="touch-enabled-ui"></a>Interfejs użytkownika z obsługą dotyku

- Sprawdź, czy kontrolki interaktywne są wystarczająco duże, aby można je było łatwo dotykać — rozmiar co najmniej **23 x 23** piksele

- Sprawdź, czy najczęściej używane kontrolki mają rozmiar co najmniej **40 x 40** pikseli.

- Sprawdź, czy interakcyjne kontrolki mają odstępy co najmniej **5** pikseli między nimi
