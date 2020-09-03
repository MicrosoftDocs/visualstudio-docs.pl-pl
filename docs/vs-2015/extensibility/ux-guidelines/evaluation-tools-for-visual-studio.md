---
title: Narzędzia do oceny
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24ea04e59178248c7a9795a2f928c311ba83db2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824076"
---
# <a name="evaluation-tools-for-visual-studio"></a>Narzędzia do oceny dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista kontrolna Craftsmanship dla programu Visual Studio
 Ta lista kontrolna służy do szacowania jakości środowiska użytkownika pod kątem szczegółów wizualizacji i interakcji.

### <a name="overview"></a>Omówienie

- Sprawdź, czy wszystkie polecenia powodują przesłanie opinii informujących użytkowników o przeprowadzeniu poleceń.

- Sprawdź, czy wszystkie elementy i kontrolki interfejsu użytkownika są widoczne we wszystkich kompozycjach i w trybie duży kontrast.

- Sprawdź, czy nieaktywny i aktywny wybór są zawsze zróżnicowane, zarówno w trybie standardowym, jak i duży kontrast.

- Sprawdź, czy fokus jest zawsze widoczny i oczywisty.

### <a name="performance"></a>Wydajność

- Sprawdź, czy jest wyświetlany jakiś rodzaj wskaźnika "zajęty", jeśli wykonanie polecenia trwa dłużej niż 1 sekunda.

- Upewnij się, że jeśli wykonanie polecenia trwa dłużej niż 10 sekund, zostanie wyświetlony jawny pasek postępu z wartością dekończ (preferowany) lub nieokreślony.

### <a name="ui-text"></a>Tekst interfejsu użytkownika

- Upewnij się, że wszystkie etykiety są zdaniami lub tytułem, a tekst nie jest całkowicie pisany małymi literami.

    ||Odpowiedź prawidłowa|Odpowiedź nieprawidłowa|
    |-|-------------|---------------|
    |**Tekst polecenia (wszystkie)**|Przypadek zdania:<br /><br /> **Nazwa katalogu:**|Nazwa katalogu:|
    |**Tekst przycisku (klient)**|Przypadek tytułu:<br /><br /> **[Ustaw jako domyślne]**|USTAW JAKO DOMYŚLNY|
    |**Tekst przycisku (online)**|Przypadek zdania:<br /><br /> **[Ustaw jako domyślne]**||

- Sprawdź, czy wszystkie etykiety, z wyjątkiem nagłówków i przycisków grup, kończą się dwukropkiem i poprzedzają kontrolkę, z którą są sparowane.

- Sprawdź, czy przyciski, polecenia i linki poleceń uruchamiające interfejs użytkownika umożliwiają przechwycenie danych wejściowych użytkownika w wielokropku **[...]**.

  Przykłady:

  - Przycisk **[Zaawansowane...]** w oknie dialogowym.

  - Opcje polecenia w menu Narzędzia (**narzędzia > opcje**) nie powinny mieć wielokropka, ponieważ uruchomienie okna dialogowego jest zamiarem polecenia.

- Sprawdź, czy interfejs użytkownika nie zawiera skrótów, z wyjątkiem standardowych warunków branżowych. Na przykład, nie należy sprawdzać pisowni ani HTML, ani TCP/IP, chociaż OOM (za mało pamięci) i dane OSOBowe (informacje umożliwiające identyfikację użytkownika).

### <a name="keyboard-access"></a>Dostęp za pomocą klawiatury

- Sprawdź, czy istnieje sposób, aby wykonać każde zadanie przy użyciu klawiatury. Zwykle jest to realizowane za pośrednictwem dostępu do klawiatury dla każdej kontrolki, ale w przypadku niektórych wysoce wizualnych obszarów, obejście takie jak przechodzenie do widoku kodu jest akceptowalne.

- Sprawdź, czy można przełączać kontrolki w kolejności logicznej (od lewej do prawej i od góry do dołu). Chociaż jest to najlepsze rozwiązanie dla większości formantów, nie wszystkie formanty wymagają tego podejścia. Na przykład sprawdź, czy kontrolki przycisków radiowych znajdują się w grupie z pojedynczym tabulatorem.

- Upewnij się, że wszystkie kontrolki mają etykiety i że każda etykieta ma dowolną wartość (wyjątki zawierają niektóre kontrolki nieoznaczone etykietami, które mogą być zgodne z kontrolką kontrolki na karcie).

- Sprawdź, czy nie występują żadne konflikty.

### <a name="fonts"></a>Czcionki

- Sprawdź, czy wszystkie czcionki (na przykład, rozmiar, kolor) są używane spójnie i utrzymując hierarchię.

- Sprawdź, czy wszystkie elementy interfejsu użytkownika używają usługi czcionek środowiskowych. (Zobacz [czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Aby sprawdzić, czy usługa jest używana, przejdź do pozycji **narzędzia > opcje > czcionki i kolory**. Na liście rozwijanej ustawienia wybierz czcionkę środowiska i Zmień krój czcionki na coś stylistically różne (takie jak Harrington lub Comic Sans) i ustaw rozmiar na 12 punktów. Następnie kliknij przycisk OK. Może być konieczne ponowne uruchomienie IDE, ale większość interfejsu użytkownika zmieni się natychmiast. Obszary, które nie pobierają zmiany czcionki, nawet po ponownym uruchomieniu nie używają czcionki środowiskowej.

- Sprawdź, czy czcionki, które są zależne od usługi (na przykład tekst pogrubiony lub powiększony) zachowują rozmiar i formatowanie w odniesieniu do tekstu "normalny", gdy zmieniany jest rozmiar czcionki środowiska.

- Sprawdź, czy nie ma błędów przycinania z powodu rozszerzonych czcionek. Czcionki, które uzyskują przycinane wyniki, są raczej wynikiem kontroli stałej wysokości lub kontenerów o stałej wysokości.

### <a name="dialogs"></a>Okna dialogowe

- Sprawdź, czy tytuł okna dialogowego jest taki sam jak polecenie, które je uruchomiło.

- Upewnij się, że wszystkie kontrolki standardowe są spójne z systemem operacyjnym: kolor tła jest standardowy i żadna kontrolka nie powinna mieć specjalnego stylu ponownego szablonu, który sprawia, że różni się od kontrolek standardowych.

- Sprawdź, czy marginesy w formularzu powinny mieć 12 pikseli i powinny być jednorodne i spójne.

- Sprawdź, czy okna dialogowe są wyświetlane w środku powłoki IDE lub w oknie, które je pozostało.

- Gdy jest to przydatne, okna dialogowe powinny mieć zmienny rozmiar. W przypadku okien dialogowych, które są zmieniane, sprawdź, czy podczas zmiany rozmiaru odpowiednie kontrolki muszą zmienić rozmiar, gdy inne części okna dialogowego pozostają stałe.

- Sprawdź, czy okna dialogowe o zmiennym rozmiarze utrzymują dowolnie dostosowany przez użytkownika rozmiar (rozmiar, lokalizację, rozszerzenie kontrolki okna dialogowego itd.).

- Sprawdź, czy na pasku tytułu nie ma ikony.

- Sprawdź, czy na pasku tytułu nie ma przycisków Minimalizuj i Maksymalizuj.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Przyciski operacji okna dialogowego (tylko oprogramowanie VS Client)

- Sprawdź, czy przyciski operacji są w tej kolejności: **OK**, **Anuluj**, **Zastosuj**.

- Sprawdź, czy przyciski **OK** i **Anuluj** są standardowym rozmiarem: 75x23 pikseli.

- Sprawdź, czy przyciski **OK** i **Anuluj** mają równy rozmiar, niezależnie od długości ciągu.

- Jeśli etykieta na przycisku operacji wymaga, aby przycisk był szerszy niż standardowy, sprawdź, czy odpowiedni przycisk **anulowania** ma równy rozmiar.

- Sprawdź, czy między przyciskami i skojarzonymi kontrolkami jest dopełnienie 6 pikseli.

- Sprawdź, czy przyciski **OK** i **Anuluj** nie mają symboli (klawisze dostępu zdefiniowane przez podkreśloną literę).

- Sprawdź, czy jeden przycisk (zazwyczaj **OK**) ma domyślnie fokus.

- Sprawdź, czy **klawisz ESC** anuluje okno dialogowe

- Upewnij się, że **klawisz ENTER** wykonuje przycisk domyślny, jeśli fokus nie znajduje się w kontrolce, która przetwarza ENTER.

- Upewnij się, że przyciski **OK** i **Anuluj** są umieszczone w prawym dolnym rogu okna dialogowego. W rzadkich wyjątkach można je zamieścić w pionie w prawym górnym rogu.

- Sprawdź, czy konfiguracja pionowa jest używana tylko wtedy, gdy w oknie dialogowym znajdują się inne przyciski.

### <a name="control-standards"></a>Standardy kontroli

#### <a name="general"></a>Ogólne

- Sprawdź, czy gdy jest to możliwe, są dobre wartości domyślne, aby przyspieszyć interakcję z użytkownikiem i umożliwić użytkownikom bezpieczny lub typowy wynik.

- Sprawdź, czy standardowe kontrolki działają tak samo, aby użytkownicy wiedzieli, co się dzieje w oparciu o wcześniejsze środowisko.

#### <a name="label-controls"></a>Kontrolki etykiet

- Sprawdź, czy każda kontrolka ma etykietę i czy każda etykieta jest wizualnie sparowana z jej kontrolką (zazwyczaj w zakresie 4-6 pikseli) i jest bliżej odpowiadającej jej kontroli niż w przypadku innych kontrolek.

- Sprawdź, czy etykiety zostały umieszczone w lewo z lewej krawędzią kontrolki, jeśli są umieszczone powyżej i wyśrodkowane w poziomie, tak aby linia bazowa etykiety była wyrównana z linią bazową tekstu wejściowego, jeśli jest umieszczony w lewej.

- Sprawdź, czy w przypadku, gdy kilka kontrolek skumulowanych etykieta i wprowadzanie jest umieszczonych po lewej stronie kontrolki, etykiety są puste i równej odległości od brzegu okna dialogowego, nigdy nie Opróżniaj ani równej odległości od kontrolek. Pary powinny być równomiernie dystrybuowane, chyba że potrzebne są dodatkowe odstępy, aby wskazać grupowanie.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Kontrolki wejściowe (pola tekstowe i pola kombi)

- Sprawdź, czy w przypadku używania domyślnej czcionki środowiskowej wysokość wyświetlania pól tekstowych, pól kombi i przycisków to 23 pikseli.

- Jeśli jest używany tekst wskazówki, sprawdź, czy kolor jest ustawiony na `Environment.ControlEditHintText` Korzystanie z usługi Color Service.

- Jeśli pole jest polem wymaganym, które musi zostać zidentyfikowane jako takie, sprawdź:

  - czy tło jest ustawione na `Environment.ControlEditRequiredBackground` , a pierwszy plan jest ustawiony na `Environment.ControlEditRequiredHintText`

  - że znajduje się tekst wskazówki w kontrolce, która pojawia się jako **" \<Required> "**

#### <a name="button-controls"></a>formanty przycisków

- Upewnij się, że przyciski mają minimalny rozmiar 75x23 pikseli, chyba że zostanie przeszukany dłuższy tekst.

- Sprawdź, czy przyciski mają marginesy lewe i prawe 3-5 pikseli, a także dopełnienie zawartości.

- Można użyć małego kwadratowego przycisku z symbolem wielokropka **[...]** zamiast przycisku **[Przeglądaj...]** (lub podobną funkcją). Jeśli jest używany, sprawdź, czy przycisk ma 23x23 rozmiar.

- Jeśli w oknie dialogowym znajduje się więcej niż jeden przycisk " **Przeglądaj...]** , sprawdź, czy w polu wszystkie są używane skrócone wersje (tylko wielokropek **[...]**).

- Sprawdź, czy przyciski wielokropka **[...]** nie mają elementu. Gdy fokus znajduje się na kontrolce wprowadzania obok niej, jedna karta powinna przenieść fokus na przycisk wielokropka.

- Sprawdź, czy przyciski, polecenia i linki poleceń uruchamiające pomocniczy interfejs użytkownika, który przechwytuje więcej danych wprowadzonych przez użytkownika, muszą kończyć się wielokropkiem **[...]**.

#### <a name="hyperlinks"></a>Hiperlinki

- Sprawdź, czy kontrolka hiperłącza nigdy nie działa, gdy jest aktywna. Jest to wskaźnik, że usługa kolorów nie jest używana

- Sprawdź, czy używane kolory programu VS są następujące:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Sprawdź, czy hiperłącza są wyświetlane jako niebieskie bez podkreślenia, chyba że osadzony w akapicie.

#### <a name="check-boxes"></a>Pola wyboru

- Jeśli pole wyboru zawiera tekst wielowierszowy, sprawdź, czy pole jest wyrównane do pierwszego wiersza tekstu, a nie wyśrodkowane w pionie we wszystkich wierszach.

- Upewnij się, że pola wyboru zawsze wskazują na wybór binarny i nie Nawiguj do użytkownika ani nie otwieraj nowych okien ani stron.

- Jeśli pole wyboru przedstawia opcję powiązaną z kontrolką wejściową, sprawdź, czy jest ona ustawiona jako lewa, i blisko tej kontrolki, aby wskazać jej relację.

- Sprawdź, czy pole wyboru **nie jest nigdy** używane jako środek do włączenia całej zawartości okna dialogowego lub strony.

#### <a name="group-boxes"></a>Pola grup

- Upewnij się, że okno dialogowe nie zawiera pojedynczego pola grupy, które zawiera całą zawartość okna dialogowego.

- Upewnij się, że w każdym polu grupy istnieją co najmniej dwie kontrolki.

- Rzadko powinny znajdować się w oknie dialogowym więcej niż dwa pola grup.

- Sprawdź, czy nie ma zagnieżdżonych pól grup.

### <a name="icons"></a>Ikony

- Sprawdź, czy ikony są wyświetlane prawidłowo odwrócone w motywie ciemnym.

- Upewnij się, że wszystkie ikony są oparte na podstawowych pojęciach.

- Sprawdź, czy każda ikona jest odrębna, łatwa do rozpoznania i nie zawiera więcej niż dwóch koncepcji (bez modyfikatora stanu/języka).

- Sprawdź, czy ikona podstawowa pojawia się w środku obszaru.

- Upewnij się, że wszystkie ikony są widoczne jako czytelne w trybie duży kontrast.

- Sprawdź, czy używany kolor jest wyrównany do standardów użycia koloru.

- Sprawdź, czy nie ma żadnych otoczki (obramowania) wokół ikon. (Jeśli jest obecny, Otoczka powinna być zgodna z kolorem tła sąsiadującego interfejsu użytkownika).

### <a name="touch-enabled-ui"></a>Interfejs użytkownika obsługujący dotyk

- Upewnij się, że formanty interaktywne są wystarczająco duże, aby można je było łatwo zmieniać — minimalna **23x23 pikseli**

- Upewnij się, że najczęściej używane kontrolki mają rozmiar co najmniej **40x40 pikseli** .

- Sprawdź, czy formanty interaktywne mają co najmniej **5 pikseli** między nimi
