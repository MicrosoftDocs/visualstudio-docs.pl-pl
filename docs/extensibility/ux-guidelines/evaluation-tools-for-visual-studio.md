---
title: Narzędzia ewaluacyjne dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698428"
---
# <a name="evaluation-tools-for-visual-studio"></a>Narzędzia do oceny dla programu Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista kontrolna rzemiosła dla programu Visual Studio
 Ta lista kontrolna służy do oceny jakości środowiska użytkownika pod kątem szczegółów wizualnych i interakcji.

### <a name="overview"></a>Omówienie

- Sprawdź, czy wszystkie polecenia powodują opinie informujące użytkowników, że ich polecenia zostały wykonane.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika i formanty są widoczne we wszystkich motywach i w trybie wysokiego kontrastu.

- Sprawdź, czy wybór nieaktywny i aktywny jest zawsze zróżnicowany, zarówno w trybie standardowym, jak i wysokim kontrastem.

- Sprawdź, czy fokus jest zawsze widoczny i widoczny.

### <a name="performance"></a>Wydajność

- Sprawdź, czy jakiś wskaźnik "zajęty" jest wyświetlany, jeśli polecenie trwa dłużej niż jedną sekundę.

- Sprawdź, czy jeśli polecenie trwa dłużej niż 10 sekund, wyświetlany jest jawny pasek postępu, określony (preferowany) lub nieokreślony.

### <a name="ui-text"></a>Tekst interfejsu użytkownika

- Sprawdź, czy wszystkie etykiety są zdania lub tytułu wielkości liter i czy żaden tekst nie jest całkowicie małe.

    ||Prawda|Odpowiedź nieprawidłowa|
    |-|-------------|---------------|
    |**Tekst polecenia (wszystkie)**|Przypadek zdania:<br /><br /> **Nazwa katalogu:**|Nazwa katalogu:|
    |**Tekst przycisku (klient)**|Przypadek tytułu:<br /><br /> **[ Ustaw jako domyślny ]**|USTAWIANI JAKO DOMYŚLNE|
    |**Tekst przycisku (online)**|Przypadek zdania:<br /><br /> **[ Ustaw jako domyślny ]**||

- Sprawdź, czy wszystkie etykiety, z wyjątkiem nagłówków grup i przycisków, kończą się dwukropkiem i poprzedzają formant, z którym są sparowane.

- Sprawdź, czy przyciski, polecenia i łącza poleceń, które uruchamiają interfejs użytkownika, aby przechwycić zakończenie wprowadzania danych użytkownika w wielokropku **[...]**.

  Przykłady:

  - Przycisk **[Zaawansowane...]** w oknie dialogowym.

  - Opcje polecenia w menu Narzędzia (**Narzędzia > Opcje**) nie powinny uzyskać wielokropek, ponieważ uruchomienie samego okna dialogowego jest intencją polecenia.

- Sprawdź, czy interfejs użytkownika nie zawiera skrótów, z wyjątkiem terminów standardowych dla branży. Na przykład nie trzeba określać ani kodu HTML, ani protokołu TCP/IP, chociaż OOM (brak pamięci) i informacje umożliwiające identyfikację użytkownika (informacje umożliwiające identyfikację użytkownika) powinny.

### <a name="keyboard-access"></a>Dostęp do klawiatury

- Sprawdź, czy istnieje sposób, aby wykonać każde zadanie za pomocą klawiatury. Ogólnie rzecz biorąc jest to realizowane za pomocą dostępu do klawiatury dla każdego formantu, ale dla niektórych obszarów bardzo wizualnych, obejście, takie jak przechodzenie do widoku kodu jest dopuszczalne.

- Sprawdź, czy można tabulatorów za pomocą kontrolek w logicznej kolejności (od lewej do prawej i od góry do dołu). Chociaż jest to najlepsze rozwiązanie dla większości formantów, nie wszystkie formanty wymagają tego podejścia. Na przykład sprawdź, czy kontrolki przycisków opcji znajdują się w grupie z pojedynczym tabulatorem.

- Sprawdź, czy wszystkie formanty mają etykiety i czy każda etykieta ma mnemoniczny (wyjątki obejmują niektóre formanty nieokażdą, które mogą być zgodne z etykietą formantu na karcie).

- Sprawdź, czy nie ma konfliktów mnemonicznych.

### <a name="fonts"></a>Czcionki

- Sprawdź, czy wszystkie czcionki (ściana, rozmiar, kolor) są używane spójnie i zachowaj hierarchię.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika korzystają z usługi czcionek środowiska. (Zobacz [czcionki i formatowanie programu Visual Studio)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)

     Aby sprawdzić, czy usługa jest używana, przejdź do **pozycji Narzędzia > Opcje > Czcionki i Kolory**. W menu rozwijanym Ustawienia wybierz opcję Czcionka środowiska i zmień czcionkę na inną stylistycznie (na przykład Harrington lub Comic Sans) i ustaw rozmiar na 12 pkt. Następnie kliknij przycisk OK. Może być konieczne ponowne uruchomienie IDE, ale większość interfejsu użytkownika zmieni się natychmiast. Obszary, które nie odbierają zmiany czcionki nawet po ponownym uruchomieniu, nie używają czcionki środowiskowej.

- Sprawdź, czy czcionki, które są pochodną usługi (na przykład pogrubiony lub powiększony tekst) zachowują swój rozmiar i formatowanie w odniesieniu do "normalnego" tekstu po zmianie rozmiaru czcionki środowiska.

- Sprawdź, czy nie ma żadnych błędów przycinania z powodu powiększonych czcionek. Czcionki, które zostaną przycięte, są prawdopodobnie wynikiem kontroli stałej wysokości lub kontenerów o stałej wysokości.

### <a name="dialogs"></a>Okna dialogowe

- Sprawdź, czy tytuł okna dialogowego jest taki sam jak polecenie, które go uruchomiło.

- Sprawdź, czy wszystkie standardowe formanty są zgodne z systemem operacyjnym: kolor tła jest standardem i żadne formanty nie powinny mieć specjalnego stylu ponownego szablonu, który sprawia, że wyglądają inaczej niż standardowe formanty.

- Sprawdź, czy marginesy w formularzu powinny wynosić 12 pikseli i powinny być jednolite i spójne.

- Sprawdź, czy okna dialogowe są wyświetlane wyśrodkowane w powłoce IDE lub w oknie, które je zrodziło.

- Gdy jest to przydatne, okna dialogowe powinny być o zmiennym rozmiarze. W przypadku okien dialogowych o zmiennym rozmiarze sprawdź, czy po zmianie rozmiaru odpowiednie formanty muszą zmienić rozmiar, podczas gdy inne części okna dialogowego pozostają stałe.

- Sprawdź, czy okna dialogowe o zmiennym rozmiarze utrzymują się w dowolnym rozmiarze dostosowanym przez użytkownika (rozmiar, lokalizacja, rozszerzenie kontrolek dialogowych itd.).

- Sprawdź, czy na pasku tytułu nie ma ikony.

- Sprawdź, czy na pasku tytułu nie ma przycisków Minimalizuj i Maksymalizuj.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Przyciski operacji okna dialogowego (tylko klient VS)

- Sprawdź, czy przyciski operacji są w tej kolejności: **OK**, **Anuluj**, **Zastosuj**.

- Sprawdź, czy przyciski **OK** i **Anuluj** mają rozmiar standardowy: 75x23 pikseli.

- Sprawdź, czy przyciski **OK** i **Anuluj** mają taki sam rozmiar, niezależnie od długości ciągu.

- Jeśli etykieta na przycisku operacji wymaga, aby przycisk był szerszy niż standardowy, sprawdź, czy odpowiedni przycisk **Anuluj** jest równy rozmiar.

- Sprawdź, czy między przyciskami i skojarzonymi formantami znajduje się 6-pikselowa dopełnienie.

- Sprawdź, czy przyciski **OK** i **Anuluj** nie mają mnemoniki (klawisze dostępu zdefiniowane przez podkreśloną literę).

- Sprawdź, czy jeden przycisk (zazwyczaj **OK)** ma fokus domyślnie.

- Sprawdź, czy **esc** anuluje okno dialogowe

- Sprawdź, czy **klawisz Enter** wykonuje przycisk domyślny, jeśli fokus nie znajduje się w formancie przetwarzanym przez program Enter.

- Sprawdź, czy przyciski **OK** i **Anuluj** znajdują się w prawym dolnym rogu okna dialogowego. W rzadkich wyjątkach jest dopuszczalne dla nich być ułożone pionowo w prawym górnym rogu.

- Sprawdź, czy konfiguracja pionowa jest używana tylko wtedy, gdy inne przyciski znajdują się w poziomym wyrównaniu w oknie dialogowym.

### <a name="control-standards"></a>Standardy kontroli

#### <a name="general"></a>Ogólne

- Sprawdź, czy, jeśli to możliwe, istnieją dobre wartości domyślne, aby przyspieszyć interakcję z użytkownikiem i skierować użytkowników w kierunku bezpiecznego lub wspólnego wyniku.

- Sprawdź, czy standardowe formanty zachowują się tak samo, aby użytkownicy wiedzieli, co się stanie na podstawie wcześniejszego środowiska.

#### <a name="label-controls"></a>Kontrolki etykiet

- Sprawdź, czy każdy formant ma etykietę i czy każda etykieta jest wizualnie sparowana z jej formantem (zazwyczaj w zakresie 4-6 pikseli) i jest bliższa jego odpowiedniemu formancie niż innym formantom.

- Sprawdź, czy etykiety są umieszczone równo w lewo z lewą krawędzią formantu, jeśli są umieszczone powyżej i wyśrodkowane poziomo, tak aby linia bazowa etykiety była wyrównana z linią bazową tekstu wejściowego, jeśli jest mieszczona po lewej stronie.

- Sprawdź, czy jeśli kilka skumulowanych etykiet i formantów wejściowych są umieszczone po lewej stronie formantu, etykiety są opróżniane w lewo i równej odległości od krawędzi okna dialogowego, nigdy nie opróżniać w prawo i równej odległości od formantów. Pary powinny być równomiernie rozłożone, chyba że potrzebują dodatkowych odstępów, aby wskazać grupowanie.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Formanty wprowadzania (pola tekstowe i pola kombi)

- Sprawdź, czy w przypadku korzystania z domyślnej czcionki środowiska wysokość wyświetlania pól tekstowych, pól kombi i przycisków wynosi 23 piksele.

- Jeśli używany jest tekst wskazówki, sprawdź, czy kolor jest ustawiony na `Environment.ControlEditHintText` korzystanie z usługi kolorów.

- Jeśli pole jest polem wymaganym, które musi być zidentyfikowane jako takie, sprawdź:

  - ustawiono tło `Environment.ControlEditRequiredBackground` i pierwszy plan jest ustawiony na`Environment.ControlEditRequiredHintText`

  - że w formancie znajduje się tekst podpowiedzi, który pojawia się jako **"\<Wymagany>"**

#### <a name="button-controls"></a>formanty przycisków

- Sprawdź, czy przyciski mają minimalny rozmiar 75x23 pikseli, chyba że są to dłuższe teksty.

- Sprawdź, czy przyciski mają lewy i prawy margines 3-5 pikseli, a także dopełnienie zawartości.

- Dopuszczalne jest użycie małego kwadratowego przycisku z tylko wielokropek **[...]** na nim zamiast przycisku **[Przeglądaj...]** (lub podobnej funkcjonalności). Jeśli jest używany, sprawdź, czy przycisk ma rozmiar 23x23.

- Jeśli w oknie dialogowym znajduje się więcej niż jeden przycisk **[Przeglądaj...],** sprawdź, czy skrócona wersja (tylko wielokropek **[...]**) jest używana dla wszystkich.

- Sprawdź, czy wielokropek **[...]** przyciski nie mają mnemonic. Gdy fokus znajduje się na formancie wejściowym obok niego, jedna karta powinna przenieść fokus do przycisku wielokropka.

- Sprawdź, czy przyciski, polecenia i łącza poleceń, które uruchamiają pomocniczy interfejs użytkownika, który przechwytuje więcej danych wejściowych użytkownika, muszą kończyć się wielokropkami **[...]**.

#### <a name="hyperlinks"></a>Hiperlinki

- Sprawdź, czy kontrolka hiperłącza nigdy nie miga na czerwono, gdy jest aktywna. Jest to wskaźnik, że usługa kolorowa nie jest używana

- Sprawdź, czy używane kolory VS są następujące:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Sprawdź, czy hiperłącza są wyświetlane na niebiesko bez podkreślenia, chyba że są osadzone w akapicie.

#### <a name="check-boxes"></a>Pola wyboru

- Jeśli pole wyboru zawiera tekst wielowierszowy, sprawdź, czy pole jest wyrównywałe z pierwszym wierszem tekstu, a nie wyśrodkowanym pionowo we wszystkich liniach.

- Sprawdź, czy pola wyboru zawsze wskazują wybór binarny i nie nawigują po użytkowniku ani nie otwierają nowych okien lub stron.

- Jeśli pole wyboru przedstawia opcję związaną z formantem wejściowym, sprawdź, czy jest ona mieszczona w lewo i bardzo blisko pod tą kontrolą, aby wskazać jego relację.

- Sprawdź, czy pole wyboru **nigdy nie** jest używane jako środek umożliwiający włączenie całej zawartości okna dialogowego lub strony.

#### <a name="group-boxes"></a>Pola grupowe

- Sprawdź, czy okno dialogowe nie zawiera w nim pojedynczego pola grupy zawierającego całą zawartość okna dialogowego.

- Sprawdź, czy w każdym polu grupy znajdują się co najmniej dwa formanty.

- Rzadko powinno być więcej niż dwa pola grupy w oknie dialogowym.

- Sprawdź, czy nie ma żadnych zagnieżdżonych pól grup.

### <a name="icons"></a>Ikony

- Sprawdź, czy ikony są poprawnie odwrócone w ciemnym motywie.

- Sprawdź, czy wszystkie ikony są oparte na podstawowych pojęciach.

- Sprawdź, czy każda ikona jest odrębna, łatwa do rozpoznania i nie zawiera więcej niż dwóch pojęć (bez modyfikatora stanu/języka).

- Sprawdź, czy ikona podstawowa jest wyświetlana wyśrodkowany w przestrzeni.

- Sprawdź, czy wszystkie ikony są czytelne w trybie wysokiego kontrastu.

- Sprawdź, czy dowolny użyty kolor jest zgodny ze standardami użycia kolorów.

- Sprawdź, czy wokół ikon nie ma aureoli (obramowań). (Jeśli występuje, halo powinno pasować do koloru tła sąsiedniego interfejsu użytkownika).

### <a name="touch-enabled-ui"></a>Interfejs użytkownika z obsługą dotykową

- Sprawdź, czy interaktywne elementy sterujące są wystarczająco duże, aby można je było łatwo dotykać — rozmiar minimum **23x23 pikseli**

- Sprawdź, czy najczęściej używane formanty mają rozmiar co najmniej **40x40 pikseli.**

- Sprawdź, czy interaktywne kontrolki mają co najmniej **5 pikseli odstępów** między nimi
