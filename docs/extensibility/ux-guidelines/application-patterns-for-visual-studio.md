---
title: Wzorce aplikacji dla programu Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55044df3898b452e87ec877f9ae10dd12a2b1110
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409104"
---
# <a name="application-patterns-for-visual-studio"></a>Wzorce aplikacji dla programu Visual Studio
## <a name="BKMK_WindowInteractions"></a>Interakcje okna

### <a name="overview"></a>Omówienie
Dostępne są dwa typy główne okno, używane w programie Visual Studio: edytory dokumentu i okna narzędzi. Rzadkich, ale to możliwe, są duże Niemodalne okna dialogowe. Mimo że są one wszystkie niemodalne w powłoce, ich wzorce są całkowicie innego. W tej sekcji omówiono różnice między oknami dokumentów, narzędziami i niemodalnymi oknach dialogowych. Wzorce dialogu modalnego są omówione w [oknach dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porównywanie wzorce użycia okna
**Okna dokumentów** są prawie zawsze wyświetlane w obszarze dokumentu. Dzięki temu Edytor dokumentów jest "etapem centrum", aby rozmieścić uzupełniające okna narzędzi.

**Okno narzędzi** jest najczęściej wyświetlane jako oddzielne, mniejsze okno zwinięte z krawędzią IDE. Może to być widoczne, ukryte lub autoukryte. Jednak czasami okna narzędzi są prezentowane w obszarze dokumentu, usuwając zaznaczenie **okna/dokowanie** właściwości w oknie. Skutkuje to więcej nieruchomości, ale również często decyzje projektowe: podczas próby zintegrowania programu Visual Studio, należy zdecydować, czy Twoja funkcja powinna zostać wyświetlona okno narzędzia lub okno dokumentu.

**Niemodalne okna dialogowe** nie są odradzane w programie Visual Studio. Większość niemodalnych okien dialogowych to przez definicję, ruchome okna narzędzi i należy je zaimplementować w ten sposób. Niemodalne okna dialogowe są dozwolone w przypadku, gdy rozmiar okna narzędzi normalne zadokowany po stronie powłoki będzie zbyt ograniczenie. Mogą one również w przypadku, gdy użytkownik prawdopodobnie przenieść okna dialogowego na drugi monitor.

Pomyśl, starannie informacje dotyczące typu kontenera należy. Typowe kwestie dotyczące wzorca użycia dotyczące projektowania interfejsu użytkownika znajdują się w poniższej tabeli.

||Okno dokumentu|Okna narzędzi|Niemodalnego okna dialogowego|
|-|---------------------|-----------------|---------------------|
| **Umieścić** | Zawsze dobrze umieszczony w obrębie dokumentu i nie zadokować wokół krawędzi środowiska IDE. Może to być "ściągane", tak aby przepływał niezależnie od głównej powłoki. | Ogólnie przy zadokowane kartę wokół krawędzi środowiska IDE, ale mogą być dostosowane do być przestawne, automatyczne ukrywane (nieprzypięte) lub dobrze zadokowane w dokumencie.|Duże przestawne okno niezależnie od środowiska IDE. |
| **Zatwierdź model** | *Opóźnione zatwierdzanie*<br /><br /> Aby zapisać dane w dokumencie, użytkownik musi wydać **plik &gt; Zapisz**, **Zapisz jako**lub **Zapisz wszystkie** polecenie. Okno dokumentu korzysta z koncepcji zawarte w nim jest "dirtied" dane, następnie nacisk na jeden z zapisu poleceń. Podczas zamykania okna dokumentu, cała zawartość są zapisywane na dysku lub utraty. | *Natychmiastowe zatwierdzenie*<br /><br /> Nie ma żadnych Zapisywanie modelu. Inspektor narzędzia systemu windows, które pomagają w edycji pliku plik musi być otwarty w aktywnego edytora lub projektanta i edytora lub projektanta jest właścicielem zapisu. | *Opóźnione lub natychmiastowe zatwierdzenie*<br /><br /> Najczęściej niemodalne okno dialogowe wymaga działania w celu zatwierdzenia zmian i zezwala na operację "Anuluj", co spowoduje wycofanie wszelkich zmian wprowadzonych w sesji okna dialogowego.  Odróżnia niemodalnego okna dialogowego z okna narzędzi, w tym narzędzia windows zawsze mają model natychmiastowego zatwierdzenia. |
| **Widoczność** | *Otwórz/Utwórz (plik) i Zamknij*<br /><br /> Otwarcie dokumentu z systemem windows odbywa się za pośrednictwem otwierania istniejącego dokumentu lub przy użyciu szablonu, aby utworzyć nowy dokument. Nie istnieje polecenie "Otwórz \<specyficzny dla edytora >". | *Ukryj i Pokaż*<br /><br /> Okna narzędzi w jednym wystąpieniu mogą ukryte lub pokazane. Zawartość i stanów w obrębie okna narzędzia zachować, czy w widoku lub ukryte. Obejmujące wiele wystąpień narzędzia windows może być zamknięte także ukryte. Po zamknięciu okna narzędzia obejmujące wiele wystąpień zawartości i stan w obrębie okna Narzędzie jest odrzucany. | *Uruchomiono za pomocą polecenia*<br /><br /> Okna dialogowe są uruchamiane z poleceniem opartego na zadaniach. |
| **Wystąpienia** | *Wiele wystąpień*<br /><br /> Kilka edytorów może być otwartych w tym samym czasie i edytować różne pliki, podczas gdy niektóre edytory umożliwiają również otwieranie tego samego pliku w więcej niż jednym edytorze (przy użyciu **okna &gt; nowe okno** polecenia).<br /><br /> Pojedynczy Edytor może edytować jednego lub wielu plików w tym samym czasie (Projektant projektu). | *Pojedyncze lub wiele wystąpień*<br /><br /> Zawartość zmienia się odzwierciedlić kontekstu (tak jak w przeglądarce właściwości) lub wypychania fokus/kontekstu do innego systemu windows (Lista zadań, Eksploratorze rozwiązań).<br /><br /> Zarówno w jednym wystąpieniu, jak i w wielu wystąpieniach narzędzia windows powinna być skojarzona z aktywnego okna dokumentu, chyba że istnieje istotny powód nie pozycji. | *Pojedyncze wystąpienie* |
| **Przykłady** | **Edytory tekstu**, takie jak edytor kodu<br /><br /> **Powierzchnie projektowe**, takie jak Projektant formularzy lub powierzchnia modelowania<br /><br /> **Układy formantów podobne do okien dialogowych**, takich jak projektant manifestu | **Eksplorator rozwiązań** zawiera rozwiązanie i projekty zawarte w rozwiązaniu<br /><br /> **Eksplorator serwera** zawiera hierarchiczny widok serwerów i połączeń danych, które użytkownik zdecyduje otworzyć w oknie. Otwierając obiekt z hierarchii bazy danych, na przykład zapytanie, otwiera okno dokumentu i zezwala użytkownikowi na edytowanie zapytania.<br /><br /> **Przeglądarka właściwości** wyświetla właściwości obiektu wybranego w oknie dokumentu lub w innym oknie narzędzi. Właściwości są prezentowane w widoku siatki hierarchiczne lub złożonych kontrolek podobne okno dialogowe i Zezwalaj użytkownikowi na ustawianie wartości tych właściwości. | |

## <a name="BKMK_ToolWindows"></a>Okna narzędzi

### <a name="overview"></a>Omówienie
Okna narzędzi obsługują pracę użytkownika, która odbywa się w oknach dokumentów. One może służyć do wyświetlania hierarchii, która reprezentuje obiekt główny podstawowych programu Visual Studio zapewniająca i manipulować.

Podczas wybierania nowego okna narzędzi w IDE, powinien autorzy:

- Odpowiednie zadanie istniejących narzędzi systemu windows ale nie tworzenie nowych o podobnych możliwościach. Nowe okna narzędzi należy tworzyć tylko wtedy, gdy oferują znacznie różne "Narzędzie" lub funkcje, których nie można zintegrować z podobnym oknem lub przez włączenie istniejącego okna do koncentratora przestawiania.

- Pasek poleceń standardowych, należy użyć, jeśli to konieczne, w górnej części okna narzędzia.

- Być zgodne ze wzorcami już istnieje w innych oknach narzędzi do kontroli nawigacji prezentacji i klawiatury.

- Być zgodne z prezentację kontrolki w innymi oknami narzędzi.

- W miarę możliwości ustaw funkcję autowidoczności okien narzędzi specyficznych dla dokumentu, tak aby były wyświetlane tylko wtedy, gdy dokument nadrzędny jest aktywowany.

- Upewnij się, że ich zawartość okna jest można nawigować przez klawiatury (klawisze strzałek pomocy technicznej).

#### <a name="tool-window-states"></a>Stany okien narzędzi
Okna narzędzi w usłudze Visual Studio mają różne stany, niektóre z nich, użytkownik aktywował (np. funkcję automatycznego ukrywania). Inne Stany, takie jak autovisible, Zezwalaj na wyświetlanie okien narzędzi w prawidłowym kontekście i ukrywanie, gdy nie jest to konieczne. Istnieje pięć stanów okna narzędzia w sumie.

- Okna narzędzi **zadokowanych/przypiętych** mogą być dołączone do dowolnych z czterech boków obszaru dokumentu. Ikona pinezki pojawia się na pasku tytułu okna narzędzia. Okno narzędzia może być zadokowane w poziomie lub pionie wzdłuż krawędzi powłoka i innymi oknami narzędzi, a także mogą być łączone przez karty.

- Okna narzędzi **z autoukrywaniem** nie są przypięte. Okno może wysunąć wzrok, pozostawiając kartę (z nazwą okna narzędzia i jego ikoną) na krawędzi obszaru dokumentu. Okno narzędzia wysuwa się, gdy użytkownik zatrzyma na karcie.

- **Automatyczne widoczne** okna narzędzi automatycznie pojawiają się, gdy działa inny element interfejsu użytkownika, taki jak edytor, jest uruchamiany lub ma fokus.

- **Zmiennoprzecinkowe** okno narzędziowe Umieść kursor poza IDE. Jest to przydatne w przypadku konfiguracji z wielu monitorów.

- Okna narzędzi **dokumentu z kartami** mogą być zadokowane w obszarze dokumentu. Jest to przydatne w przypadku dużych okien narzędzi, takich jak Przeglądarka obiektów, które potrzebują bardziej rzeczywistej nieruchomości niż dokowanie do krawędzi ramki.

![Stany okna narzędzi w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 — 01_ToolWindowStates")<br />Stany okna narzędzi w programie Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Jednym wystąpieniu i obejmujące wiele wystąpień
Okna narzędzi są jednego wystąpienia lub wielu wystąpień. Niektóre narzędzia w jednym wystąpieniu systemu windows może być skojarzony z oknem aktywnego dokumentu, podczas gdy obejmujące wiele wystąpień narzędzia windows może nie. Okna narzędzi z pojedynczym wystąpieniem odpowiadają na **okno &gt; nowe okno** , tworząc nowe wystąpienie okna. Na poniższym obrazie przedstawiono Włączanie polecenie nowe okno, gdy wystąpienie okno jest aktywne okna narzędzi:

![Okno narzędzia włączające polecenie "New window", gdy wystąpienie okna jest aktywne](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 — 02_ToolWindowEnablingCommand")<br />Okno narzędzia włączające polecenie "New window", gdy wystąpienie okna jest aktywne

Okien narzędzi w jednym wystąpieniu mogą ukryte lub pokazane, gdy wiele wystąpień narzędzia windows może być zamknięte, a także ukryte. Wszystkie okna narzędzi może być zadokowane łączone przez karty, zmiennoprzecinkowego lub Ustaw jako okna podrzędnego interfejsu wielu dokumentów (MDI) (podobnie do okna dokumentu). Wszystkie okna narzędzi powinna odpowiadać na polecenia zarządzania odpowiednie okna w menu Okno:

![Polecenia zarządzania oknem w menu okna programu Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 — 03_WindowManagementControls")<br />Polecenia zarządzania oknem w menu okna programu Visual Studio

#### <a name="document-specific-tool-windows"></a>Okna narzędzi specyficznych dla dokumentu
Niektóre narzędzia systemu windows są przeznaczone do zmienić w zależności od danego typu dokumentu. Te okna stale aktualizowana w celu odzwierciedlenia funkcje mające zastosowanie do aktywnego okna dokumentu w IDE.

Przykłady okien narzędzi, których zawartość zmieniać, aby odzwierciedlić wybrane edytora są przybornika i tworzenie konspektu dokumentu. Te okna Pokaż znak wodny, gdy Edytor ma fokus, oferuje kontekstu do okna.

#### <a name="navigable-list-tool-windows"></a>Listy można nawigować okien narzędzi
Niektóre narzędzia systemu windows, wyświetlanie listy można nawigować elementów, które użytkownik może interakcyjnie przeprowadzić. W tym typie okna zawsze należy opinie dla bieżącego elementu na liście, nawet jeśli okno jest nieaktywny. Lista powinna reagować na polecenia **GoToNextLocation** i **GoToPrevLocation** , zmieniając również aktualnie wybrany element w oknie

Przykłady okien narzędzi można nawigować listy Eksploratora rozwiązań i w oknie Znajdź wyniki.

### <a name="tool-window-types"></a>Typy okien narzędzi

#### <a name="common-tool-windows-and-their-functions"></a>Wspólne okna narzędzi i ich funkcje

**Okna narzędzi hierarchicznych**

| Okna narzędzi | Funkcja |
| --- | --- |
| Eksplorator rozwiązań | Hierarchiczne drzewo, które wyświetla listę dokumenty zawarte w projektach, różne pliki i elementy rozwiązania. Wyświetlanie elementów w obrębie projektów jest definiowany przez pakiet, który jest właścicielem tego typu projektu (na przykład typy na podstawie odwołania, na podstawie katalogu lub trybu mieszanego). |
| Widok klas | Hierarchiczne drzewo, klasy i różne elementy w zestawie roboczym dokumentów, niezależnie od same pliki. |
| Eksplorator serwera | Hierarchiczne drzewo, które wyświetla wszystkie połączenia serwerów i danych w rozwiązaniu. |
| Konspekt dokumentu | Hierarchiczna struktura aktywnego dokumentu. |

**Okna narzędzi siatki**

| Okna narzędzi | Funkcja |
| --- | --- |
| Właściwości | Siatka, który wyświetla listę właściwości dla wybranego obiektu, wraz z selektorami wartość, aby edytować te właściwości. |
| Lista zadań | Siatka, który umożliwia użytkownikowi tworzenie/edytowanie/usuwanie zadań i komentarzy. |

**Okna narzędzi zawartości**

| Okna narzędzi | Funkcja |
| --- | --- |
| Pomoc | Okno, które umożliwia użytkownikom dostęp do różnych metod uzyskiwania pomocy, od "jak?" wideo na forach MSDN. |
| Dynamiczna pomoc | Okna narzędzi, które wyświetla łącza, które ułatwiają — tematy mające zastosowanie do bieżącego zaznaczenia. |
| Przeglądarka obiektów | Zestaw ramek dwie kolumny z listy składników obiekt hierarchiczny, w okienku po lewej stronie i obiektu, właściwości i metod w prawej kolumnie. |

**Okna narzędzi dialogu**

| Okna narzędzi | Funkcja |
| --- | --- |
| Znajdowanie | Okno dialogowe, które umożliwia użytkownikom znajdowanie lub Znajdź i Zamień w różnych plików w ramach rozwiązania. |
| Wyszukiwanie zaawansowane | Okno dialogowe, które umożliwia użytkownikom znajdowanie lub Znajdź i Zamień w różnych plików w ramach rozwiązania. |

**Inne okna narzędzi**

::: moniker range="vs-2017"

| Okna narzędzi | Funkcja |
| --- | --- |
| Przybornik | Okno narzędzia używane do przechowywania elementów, które zostaną usunięte na powierzchni projektowania, zapewniając spójny źródła przeciągania dla wszystkich projektantów. |
| Strona początkowa | Portal użytkowników w programie Visual Studio, dostęp do źródeł wiadomości dla deweloperów, Pomoc programu Visual Studio i ostatnich projektów. Użytkownicy mogą również tworzyć niestandardowe strony startowe, kopiując plik StartPage. XAML z katalogu "Common7\IDE\StartPages\" Visual Studio Program Files do folderu restartpages w katalogu dokumenty programu Visual Studio, a następnie edytując kod XAML ręcznie lub otwierając go w programie Visual Studio lub innym edytorze kodu. |

::: moniker-end

::: moniker range=">=vs-2019"

| Okna narzędzi | Funkcja |
| --- | --- |
| Przybornik | Okno narzędzia używane do przechowywania elementów, które zostaną usunięte na powierzchni projektowania, zapewniając spójny źródła przeciągania dla wszystkich projektantów. |

::: moniker-end

**Okna narzędzi debugera**

| Okna narzędzi | Funkcja |
| --- | --- |
| Automatyczne ||
| Pośredni ||
| Dane wyjściowe | W oknie danych wyjściowych można zawsze wtedy, gdy masz zdarzenia tekstową lub stan, aby zadeklarować. |
| Memory (Pamięć) ||
| Punkty przerwania ||
| Działanie ||
| Dokumenty ||
| Stos wywołań ||
| Zmienne lokalne ||
| Czujki ||
| Dezasemblacji ||
| Rejestruje ||
| Wątki ||

## <a name="BKMK_DocumentEditorConventions"></a>Konwencje edytora dokumentów

### <a name="document-interactions"></a>Interakcje z dokumentu
"Dobrze dokumentu" największą ilość miejsca w środowisku IDE i jest, gdy użytkownik ma skupione ich uwagi w celu wykonania swoich zadań i wspierana przez dodatkowe narzędzia windows. Edytory dokumentu reprezentują podstawowych jednostek pracy, które użytkownik otwiera i zapisuje w programie Visual Studio. Zachowują silne poczucie wybór związany z Eksploratora rozwiązań lub innymi oknami aktywnej hierarchii. Użytkownik powinien móc wskazywały na jeden z tych oknach hierarchii i wiedzieć, gdzie znajduje się dokument i jej zależności do rozwiązania, projektu lub inny obiekt główny dostarczonej przez pakiet Visual Studio.

Edytowanie dokumentów wymaga spójne środowisko użytkownika. Aby umożliwić użytkownikowi skupić się na wykonywanego zadania zamiast zarządzania systemem Windows i znajdowanie poleceń, wybierz Udokumentowanie strategii widoku, która najlepiej pasuje do zadania użytkownika do edycji tego typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Typowe interakcje dobrze dokumentu

- Obsługuj spójny model interakcji w wspólnym **nowym pliku** i otwartych środowiskach **plików** .

- Zaktualizuj pokrewne funkcje w powiązanych systemach windows i menu, po otwarciu okna dokumentu.

- Polecenia menu są odpowiednio zintegrowane z typowymi menu, takimi jak **Edycja**, **Formatowanie**i **Wyświetlanie** menu. Jeśli jest dostępnych znaczna ilość wyspecjalizowanych poleceń, można utworzyć nowe menu. To nowe menu powinno być widoczne tylko wtedy, gdy dokument ma fokus.

- Osadzonym pasku narzędzi mogą być umieszczane w górnej części edytora. To jest posiadanie oddzielnych narzędzi, który pojawia się poza edytora.

- Zawsze zachować wybór w Eksploratorze rozwiązań lub podobne aktywne okno hierarchii.

- Dwukrotne kliknięcie dokumentu w Eksplorator rozwiązań powinno wykonać tę samą akcję co **otwarty**.

- Jeśli na typie dokumentu można użyć więcej niż jednego edytora, użytkownik powinien mieć możliwość przesłonięcia lub zresetowania akcji domyślnej dla danego typu dokumentu przy użyciu okna dialogowego **Otwórz za** pomocą, klikając prawym przyciskiem myszy plik, a następnie wybierając polecenie **Otwórz za pomocą** z menu skrótów.

- Nie Kompiluj kreatora w źródle dokumentu.

### <a name="user-expectations-for-specific-document-types"></a>Oczekiwania użytkowników dla określonych typów dokumentów
Istnieje kilka różnych typów podstawowych edytorów dokumentu, a każda ma zestaw interakcji, które są zgodne z innymi osobami z tego samego typu.

- **Edytor tekstu:** Edytor kodu, pliki dziennika

- **Powierzchnia projektowa:** Projektant formularzy WPF, formularze systemu Windows

- **Edytor stylu okna dialogowego:** Projektant manifestu, właściwości projektu

- **Projektant modeli:** Workflow Designer, codemap, diagram architektury, postęp

Istnieje kilka typów innych niż edytora, które również korzystają z dokumentu. Podczas nie edytuje samych dokumentach, muszą one wykonaj standardowych interakcji dla okna dokumentu.

- **Raporty:** Raport IntelliTrace, raport funkcji Hyper-V, raport profilera

- **Pulpit nawigacyjny:** Centrum diagnostyki

#### <a name="text-based-editors"></a>Edytory oparte na tekście

- Dokument uczestniczy w modelu kartę (wersja zapoznawcza), co umożliwia wyświetlenie podglądu dokumentu bez konieczności otwierania go.

- Strukturę dokumentu mogą być reprezentowane w ramach pomocnika okna narzędzi, takich jak konspekt dokumentu.

- Technologia IntelliSense (jeśli jest to konieczne) będzie działać spójnie przy użyciu innych edytorów kodu.

- Wyskakujące okienka lub pomocniczej interfejsu użytkownika wykonaj podobny — style i wzorców dla istniejących podobnym interfejsem użytkownika, takie jak funkcja CodeLens.

- Komunikaty dotyczące stanu dokumentu zostanie wyświetlony w kontrolce pasek informacyjny w górnej części dokumentu lub na pasku stanu.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu strony **narzędzi > opcje** , strony udostępnione czcionki i kolory albo jednej specyficznej dla edytora.

#### <a name="design-surfaces"></a>Powierzchnia projektu

- Pusty projektanta powinien mieć znak wodny na powierzchni wskazujący, jak rozpocząć pracę.

- Przełączanie widoku mechanizmów będą zgodne z istniejących wzorców, takich jak kliknij dwukrotnie, aby otworzyć Edytor kodu lub karty w oknie dokumentu, umożliwiając interakcje z obu okienka.

- Dodawanie elementów do powierzchni projektowej należy przeprowadzić za pomocą przybornika, chyba że okna narzędzi wysoce jest wymagana.

- Elementy na powierzchnię będą zgodne z modelu zaznaczenia spójne.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, nie typowe polecenia, takie jak **Zapisywanie**.

#### <a name="dialog-style-editors"></a>Edytory stylu okna dialogowego

- Układ formantu należy stosować konwencje układu okna dialogowego normalnego.

- Karty w edytorze nie powinny odpowiadać wygląd kart dokumentu, powinny one odpowiadać jeden z dwóch stylów dozwolonych kartę posługiwanie się nimi.

- Użytkownicy muszą mieć możliwość interakcji z kontrolkami, za pomocą klawiatury. albo przez aktywowanie edytora i tabulacji za pomocą kontrolki lub przy użyciu standardowych klawiszy skrótu.

- Projektant należy używać typowych Zapisz model. Nie Zapisz ogólny lub zatwierdzenia przyciski powinny zostać umieszczone na powierzchni, mimo że inne przyciski mogą być odpowiednie.

#### <a name="model-designers"></a>Model Designer

- Pusty projektanta powinien mieć znak wodny na powierzchni wskazujący, jak rozpocząć pracę.

- Dodawanie elementów do powierzchni projektu powinna być wykonywana za pomocą przybornika.

- Elementy na powierzchnię będą zgodne z modelu zaznaczenia spójne.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, nie typowe polecenia, takie jak **Zapisywanie**.

- Legenda może pojawić się na powierzchni indykatywne lub na znak wodny.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu strony **narzędzi > opcje** , strony udostępnione czcionki i kolory albo jednej specyficznej dla edytora.

#### <a name="reports"></a>Reports

- Raporty są zwykle tylko do odczytu i nie uczestniczą w modelu zapisu. Jednak mogą one obejmować interakcji, takie jak łącza do innych istotnych informacji lub sekcje, w których rozwijać i zwijać.

- Większość poleceń na powierzchni powinien być hiperlinki. Ponadto nie przyciski.

- Układ należy dołączyć nagłówek i postępuj zgodnie z wytycznymi układ raportu standardowego.

#### <a name="dashboards"></a>Pulpity nawigacyjne

- Pulpity nawigacyjne nie mają samego modelu interakcji, ale stanowią możliwość oferowania różnorodnych narzędzi.

- Nie uczestniczą w modelu zapisu.

- Użytkownicy muszą być możliwość interakcji z kontrolkami przy użyciu klawiatury, aktywacja w edytorze i tabulacji za pomocą kontrolki lub przy użyciu standardowych klawiszy skrótu.

## <a name="BKMK_Dialogs"></a>Oknach dialogowych

### <a name="introduction"></a>Wprowadzenie
Okien dialogowych w programie Visual Studio zazwyczaj powinna obsługiwać jedną jednostkę dyskretnych danego użytkownika, a następnie można odrzucić.

Jeśli już wiesz, że muszą się okno dialogowe, masz trzy opcje, w kolejności priorytetu:

1. Integracja funkcji do jednego z udostępnionego okien dialogowych w programie Visual Studio.

2. Utwórz własne okna dialogowego za pomocą wzorca w istniejących podobne okno dialogowe.

3. Utwórz nowe okno dialogowe, następujące interakcji i wytyczne dotyczące układu.

W tej sekcji opisano, jak wybrać poprawny wzorzec okna dialogowego w przepływach pracy programu Visual Studio i wspólnych konwencjach dla projektu okna dialogowego.

### <a name="themes"></a>Motywy
Okna dialogowe w programie Visual Studio, wykonaj jedną z dwa podstawowe style:

#### <a name="standard-unthemed"></a>Standard (unthemed)
Większość okna dialogowe są standardowe narzędzie okien dialogowych i powinny być unthemed. Nie nie szablon re wspólnych formantów ani próba utworzenia stylizowane "nowoczesnych typów" przycisków lub kontrolek. Kontrolki i wygląd Chrome są zgodne [ze wskazówkami dotyczącymi interakcji z pulpitem systemu Windows dla okien](/windows/desktop/uxguide/win-dialog-box)dialogowych.

#### <a name="themed"></a>Motywów
Specjalizacja "podpis" w oknach dialogowych, może być motywów. Motywem okien dialogowych mają charakterystyczny wygląd ma również niektóre wzorce interakcji specjalne skojarzonych ze stylem. Motyw okna dialogowego tylko wtedy, gdy spełnia następujące wymagania:

- To okno dialogowe jest typowym doświadczeniem, który będzie widoczny i używany często lub przez wielu użytkowników (na przykład okno dialogowe **Nowy projekt** .

- Okno dialogowe zawiera widoczne elementy marki produktu (na przykład okno dialogowe **Ustawienia konta** ).

- To okno dialogowe jest wyświetlane jako integralna część większego przepływu, który obejmuje inne okna dialogowe, na przykład okno dialogowe **Dodawanie połączonej usługi** .

- Okno dialogowe jest ważną częścią środowiska, które pełnią rolę strategiczną podwyższania poziomu lub rozróżnienie tych wersji produktu.

Podczas tworzenia tematu okna dialogowego, Użyj kolorów odpowiednie środowisko, a następnie postępuj zgodnie z poprawną układ i wzorce interakcji. (Zobacz [układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)).

### <a name="dialog-design"></a>Okno dialogowe projektu
Dobrze zaprojektowana okien dialogowych wziąć pod uwagę następujące elementy:

- Zadanie użytkownika ze wsparcia technicznego

- Okno dialogowe style tekstu, język i terminologia

- Konwencje dotyczące interfejsu użytkownika i kontrolki wyboru

- Układ wizualizacji specyfikacji i kontrola wyrównania

- Dostęp za pomocą klawiatury

#### <a name="content-organization"></a>Organizowanie zawartości
Należy wziąć pod uwagę różnice między te podstawowe rodzaje okien dialogowych:

- [Proste okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) prezentowanie kontrolek w jednym modalnym oknie. Prezentacja może obejmować zmian wzorców kontrolek złożonych, takimi jak formant pola wyboru lub pasek ikon.

- [Okna dialogowe z warstwami](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) służą do optymalnego wypełniania ekranu, gdy pojedynczy element interfejsu użytkownika obejmuje wiele grup kontrolek. Grupowania w oknie dialogowym są "warstwowe" za pomocą kontrolki karty, kontrolki listy lub przycisków, aby użytkownik może wybrać grupowania można wyświetlić w danej chwili.

- [Kreatory](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) są przydatne do kierowania użytkownika za pośrednictwem logicznej sekwencji kroków w kierunku ukończenia zadania. Szereg opcji są oferowane w panelach sekwencyjnych, czasami wprowadzenie do różnych przepływów pracy ("gałęzi") zależy od wybranej w poprzednim panelu.

#### <a name="BKMK_SimpleDialogs"></a>Proste okna dialogowe
Proste okno dialogowe jest prezentację kontrolki w pojedynczej modalny. W tej prezentacji mogą obejmować odmiany wzorców kontrolek złożonych, takie jak formant pola wyboru. W oknach dialogowych prosty postępuj zgodnie z standardowego układu ogólne, a także dowolnego określonego układu wymagane dla grupowań złożonego formantu.

![> tworzenia klucza silnej nazwy jest przykładem prostego okna dialogowego w programie Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 — 01_CreateStrongNameKey")<br />Tworzenie klucza silnej nazwy jest przykładem prostego okna dialogowego w programie Visual Studio.

#### <a name="BKMK_LayeredDialogs"></a>Okna dialogowe z warstwami
Okna dialogowe warstwowej obejmują karty, pulpity nawigacyjne i osadzone drzewa. Służą one do zmaksymalizowania nieruchomości, gdy istnieje wiele grup formantów oferowana w pojedynczy interfejs użytkownika. Grupowania są warstwowe, tak aby użytkownik może wybrać grupowania można zobaczyć w dowolnym momencie.

W najprostszym przypadku mechanizmu przełączania między grupowania jest formantem karty. Brak dostępnych kilka rozwiązań alternatywnych. Zobacz Ustawianie priorytetów i warstw dla jak wybrać najbardziej odpowiedni styl.

Okno dialogowe **opcje &gt; narzędzia** jest przykładem okna dialogowego z warstwą przy użyciu osadzonego drzewa:

![Narzędzia > Opcje są przykładem okna dialogowego z warstwą w programie Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 — 02_ToolsOptions")<br />Narzędzia > Opcje są przykładem okna dialogowego z warstwą w programie Visual Studio.

#### <a name="BKMK_Wizards"></a>Kreatorów
Kreatorzy są przydatne w przypadku kierowania użytkownika za pomocą Sekwencja logiczna kroków w celu wykonania zadania. Szereg opcji są oferowane w panelach sekwencyjnych, a użytkownik musi nadal za pośrednictwem danego kroku przed przejściem do następnego. Gdy dostępne są wystarczające wartości domyślne, przycisk **Zakończ** jest włączony.

 Modalne kreatory są używane do wykonywania zadań które:

- Zawiera Podręcznik rozgałęziania, w których różnych ścieżek są oferowane w zależności od wyborów użytkownika

- Zawierają zależności między krokami, w którym kolejne kroki zależą od dane wejściowe użytkownika z poprzednim czynności

- Wystarczająco skomplikowane, że interfejs użytkownika powinien być używany do wyjaśnienia z opcji dostępnych i możliwych wartości w każdym kroku

- Są transakcyjne wymagające zestaw kroków do wykonania w całości przed wszelkie zmiany zostaną zatwierdzone

### <a name="common-conventions"></a>Typowych konwersji
Aby osiągnąć optymalną i funkcjonalność usługi okna dialogowe, postępuj zgodnie z tych konwencji na rozmiar okna dialogowego, pozycja, standardów, konfiguracji kontroli i wyrównanie, interfejs użytkownika tekstu, paski tytułu, przycisków kontrolnych i klucze dostępu.

Aby uzyskać wytyczne dotyczące poszczególnych układów, zobacz [układ dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Rozmiar
Okna dialogowe powinien się zmieścić w ramach minimalna rozdzielczość ekranu 1024 x 768, a rozmiar okna dialogowego początkowa nie może przekraczać 900 x 700 pikseli. Okna dialogowe może być o zmiennym rozmiarze, ale nie jest wymagane.

Brak zaleceń dwóch w oknach dialogowych o zmiennych rozmiarach:

1. Minimalny rozmiar jest zdefiniowany dla okna dialogowego, Optymalizacja pod kątem zestaw formantów bez przycinania, a Dostosuj, aby pomieścić wzrostu uzasadnione lokalizacji.

2. Czy rozmiar skalowane użytkownika są utrwalane między sesjami. Na przykład jeśli użytkownik skaluje się okno dialogowe 150% kolejnym uruchomieniu okna dialogowego zostaną wyświetlone na 150%.

#### <a name="position"></a>Pozycja
Okna dialogowe musi znajdować się wyśrodkowany w środowisku IDE przy pierwszym uruchomieniu. Ostatnia pozycja okien dialogowych bez zmiany rozmiaru nie musi być utrwalona, więc będą one wyświetlane na wyśrodkowane w kolejnych uruchomieniach.

W oknach dialogowych o zmiennym rozmiarze rozmiar, powinny zostać utrwalone na kolejnych uruchomień. W przypadku modalnych okien dialogowych o zmiennym rozmiarze nie trzeba utrwalać pozycji. Wyświetlanie ich wyśrodkowany w IDE zapobiega możliwości okna dialogowego, które pojawiają się w pozycji nieprzewidywalne lub bezużyteczne po zmianie konfiguracji wyświetlania użytkownika.

W przypadku niemodalnych okien dialogowych, które mogą być zmieniane, pozycja użytkownika powinna być utrzymywana przy kolejnych uruchomieniach, ponieważ okno dialogowe może być używane często jako integralna część większego przepływu pracy.

Gdy okna dialogowe muszą być zduplikowane w innych oknach dialogowych, okno dialogowe powinno być kaskadowo z prawej strony i w dół od elementu nadrzędnego, aby było oczywiste dla użytkownika, który przeszedł do nowego miejsca.

#### <a name="modality"></a>Modalności
Trwa modalne oznacza, że wymagane do ukończenia, lub Anuluj okno dialogowe przed kontynuowaniem użytkowników. Ponieważ modalne okna dialogowe Zablokuj użytkownikowi możliwość interakcji z innymi częściami środowiska, przepływ zadań Twojej funkcji powinny być używane jako rzadko, jak to możliwe. Gdy konieczne jest operacją modalne, Visual Studio ma liczbę udostępnionych okien dialogowych, które można zintegrować funkcje do. Jeśli musisz utworzyć nowe okno dialogowe, oparte na wzorcu interakcji istniejącego okna dialogowego o podobnych możliwościach.

Gdy użytkownicy muszą wykonywać dwa działania jednocześnie, takie jak **Znajdowanie** i **zamienianie** podczas pisania nowego kodu, okno dialogowe powinno być niemodalne, aby użytkownik mógł łatwo przełączać się między nimi. Visual Studio zazwyczaj używa okien narzędzi dla tego rodzaju Obsługa edytora połączonego zadania.

#### <a name="control-configuration"></a>Konfiguracja kontroli
Być zgodne z istniejących konfiguracji kontroli, które osiągnąć to samo w programie Visual Studio.

#### <a name="title-bars"></a>Paski tytułu

- Tekst na pasku tytułu muszą odzwierciedlać nazwę polecenia, który go uruchomił.

- Brak ikony, należy używać w paski tytułu okna dialogowego. W przypadkach, w którym system wymaga jednego Użyj logo programu Visual Studio.

- Okna dialogowe nie powinny mieć minimalizowanie lub maksymalizowanie przycisków.

- Przyciski pomocy na pasku tytułu są przestarzałe. Nie należy dodawać ich do nowego okna dialogowe. Jeśli istnieją one powinien być uruchamiany tematu pomocy, koncepcyjnie odpowiednią do zadania.

  ![Specyfikacje wytycznych dla pasków tytułu w oknach dialogowych programu Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 — 03_TitleBarSpecs")<br />Specyfikacje wytycznych dla pasków tytułu w oknach dialogowych programu Visual Studio

#### <a name="control-buttons"></a>Kontrolki przycisków
W obszarze Ogólne przyciski **OK**, **Anuluj**i **Pomoc** powinny być ułożone poziomo w prawym dolnym rogu okna dialogowego. Alternatywne pionowy stos jest dozwolone, gdy okno dialogowe ma kilka przycisków w dolnej części okna dialogowego, które przedstawiałoby visual omyłkowe przycisków kontrolnych.

![Dopuszczalne konfiguracje przycisków sterowania w oknach dialogowych programu Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 — 04_ControlButtonConfig")<br />Dopuszczalne konfiguracje przycisków sterowania w oknach dialogowych programu Visual Studio

Okno dialogowe musi zawierać domyślnego formant przycisku. Aby określić najważniejsze polecenie, aby użyć domyślnej, należy wybrać spośród następujących opcji (wymienione w kolejności):

- Wybierz polecenie najbezpieczniejszy i najbardziej bezpieczne jako domyślny. Oznacza to, wybierając polecenie najbardziej prawdopodobne zapobiec utracie danych i uniknąć dostępu do systemu niezamierzone.

- Jeśli utrata danych i zabezpieczenia nie są czynniki, wybierz polecenie domyślne, w oparciu o wygody. Włączenie najbardziej najprawdopodobniej polecenia jako domyślnego spowoduje poprawienie przepływu pracy użytkownika, gdy okno dialogowe obsługuje częste lub powtarzające się zadania.

Należy unikać egzaminacyjnym trwale destrukcyjne dla domyślnego polecenia. Jeśli ma takiego polecenia, wybierz polecenie bezpieczniejsze jako domyślny.

#### <a name="access-keys"></a>Klawisze dostępu
Nie używaj kluczy dostępu dla przycisków **OK**, **Anuluj**lub **Pomoc** . Przyciski te są mapowane do klawiszy skrótów domyślnie:

| Nazwa przycisku | Skrót klawiaturowy |
| --- | --- |
| OK | Enter |
| Cancel | Esc |
| Pomoc | F1 |

#### <a name="imagery"></a>Obraz
Rzadko używać obrazów w oknach dialogowych. Nie używaj dużych ikon w oknach dialogowych tylko do wykorzystania miejsca. Używaj obrazów tylko wtedy, gdy są ważną częścią przekazywania wiadomości do użytkownika, takich jak ikony ostrzeżeń lub animacje stanu.

### <a name="BKMK_PrioritizingAndLayering"></a>Ustalanie priorytetów i warstwowe

#### <a name="prioritizing-your-ui"></a>Priorytetyzowanie interfejs użytkownika
Może być konieczne przenieść niektóre elementy interfejsu użytkownika na czele i umieścić zachowanie bardziej zaawansowane i (w tym polecenia zasłoniętej) opcje w oknach dialogowych. Ożyw najczęściej używane funkcje oprogramowania forefront ilości miejsca dla niego i oznaczania go jako widocznego domyślnie w Interfejsie użytkownika etykietę tekstową, gdy okno dialogowe jest wyświetlane.

#### <a name="layering-your-ui"></a>Układanie warstwowo interfejs użytkownika
Jeśli już wiesz, że okno dialogowe jest konieczne, ale powiązane funkcje, które mają być widoczne dla użytkownika wykracza poza mogą być wyświetlane w oknie dialogowym prostego, następnie należy warstwy interfejsu użytkownika. Najbardziej typowe metody warstwowe, które korzysta z programu Visual Studio są karty i korytarzach lub pulpitów nawigacyjnych. W niektórych przypadkach może być odpowiednie regiony, które można rozwijać i zwijać. Funkcje adaptacyjnego sterowania interfejsu użytkownika zwykle nie jest zalecane w programie Visual Studio.

Istnieją zalety i wady różnych metod przez kontrolę nad jak karta Układanie warstwowo interfejsu użytkownika. Przejrzyj listę, aby upewnić się, wybierają technika warstwowe, która jest odpowiednia do swojej sytuacji.

##### <a name="tabbing"></a>TAB

| Mechanizm przełączania | Zalety i właściwego użycia | Wady i nieodpowiednie użycie |
| --- | --- | --- |
| Kontrolki karty | Logiczne grupowanie stron okien dialogowych w powiązane zestawy<br /><br />Przydatne w przypadku mniej niż pięć (lub liczba kart, które mieszczą się w jednym wierszu w oknie dialogowym) stron pokrewnych formantów w oknie dialogowym<br /><br />Karta musi być krótki: jeden lub dwa wyrazy, które można łatwo zidentyfikować zawartości<br /><br />Typowe style okna dialogowego systemu<br /><br />Przykład: **Eksplorator plików &gt; właściwości elementu** | Wprowadzanie opisowymi etykietami krótki może okazać się trudne<br /><br />Na ogół nie skalować ostatnie pięć kart w jednym oknie dialogowym<br /><br />Nieodpowiedni, jeśli masz zbyt wiele kart dla jednego wiersza (Użyj alternatywnej techniki warstwowej)<br /><br />Nie jest rozszerzalna |
| Nawigacyjny pasek boczny | Proste przełączania urządzenia, które może obsłużyć więcej kategorii niż karty<br /><br />Niezhierarchizowana lista kategorii (bez hierarchii)<br /><br />Rozszerzalna<br /><br />Przykład: **Dostosuj... &gt; Dodaj polecenie** | Nie dobrze wykorzystane miejsce w poziomie, jeśli ma mniej niż trzy grup<br /><br />Zadanie może być lepiej dopasowany do listy rozwijanej |
| Kontrolka drzewa | Umożliwia nieograniczony kategorii<br /><br />Umożliwia grupowanie i/lub hierarchia kategorii<br /><br />Rozszerzalna<br /><br />Przykład: **narzędzia &gt; opcje** | Wielokrotnie zagnieżdżone hierarchie mogą powodować nadmierne przewijanie w poziomie<br /><br />Program Visual Studio zawiera overabundance widoków drzewa |
| Kreator | Pomaga w wykonywaniu zadania przez identyfikator GUID użytkownika w ramach zadań, sekwencyjnych kroków: Kreator reprezentuje zadanie wysokiego poziomu, a poszczególne panele reprezentują podzadania wymagane do wykonania ogólnego zadania<br /><br />Przydatne, gdy zadanie przekracza granice interfejsu użytkownika, jak po użytkownik przeciwnym razie byłoby trzeba użyć wielu edytory i narzędzi systemu windows do ukończenia zadania<br /><br />Przydatne, gdy zadanie wymaga rozgałęzianie<br /><br />Przydatne, gdy zadanie zawiera zależności między krokami<br /><br />Przydatne, gdy kilka podobnych zadań z jednym rozwidleniem decyzji można przedstawić w jednym oknie dialogowym, aby zmniejszyć liczbę różnych podobnych okien dialogowych | Nieodpowiednie dla każdego zadania, które nie wymaga sekwencyjnego przepływu pracy<br /><br />Użytkownicy mogą stać się przeciążeniu i mylić przez kreatora, za pomocą zbyt wiele kroków<br /><br />Kreatorzy założenia mają ograniczoną powierzchnię ekranu |

##### <a name="hallways-or-dashboards"></a>Korytarzach lub pulpitów nawigacyjnych
Korytarzach i pulpity nawigacyjne są okien dialogowych lub paneli, które służą jako uruchamianie punktów do innych okien dialogowych i systemu windows. Dobrze zaprojektowana "korytarzowych" prezentuje natychmiast tylko najbardziej typowe opcje, poleceń i ustawień, co pozwala na łatwe wykonywanie typowych zadań. Jak korytarzowych rzeczywistych zapewnia drzwi do dostępu do pomieszczenia za ich, w tym miejscu mniej znane interfejsu użytkownika są zbierane do oddzielnych "pomieszczeń" (często inne okna dialogowe) powiązanych funkcji, które są dostępne z głównym telewizora.

Alternatywnie interfejs użytkownika, który oferuje wszystkie funkcje dostępne w jednej kolekcji, zamiast refaktoryzacji mniej typowe funkcje w różnych lokalizacjach jest po prostu pulpitu nawigacyjnego.

![Holu koncepcji w celu udostępnienia dodatkowego interfejsu użytkownika w programie Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 — 08_Hallway")<br />Holu koncepcji w celu udostępnienia dodatkowego interfejsu użytkownika w programie Outlook

##### <a name="adaptive-ui"></a>Funkcje adaptacyjnego sterowania interfejsu użytkownika
Pokazywanie lub ukrywanie interfejsu użytkownika na podstawie użycia lub przez użytkownika samodzielnie zgłaszane jest innym sposobem przedstawiania niezbędne interfejsu użytkownika innych części są ukryte. Nie jest to zalecane w programie Visual Studio, ponieważ algorytmy decydujące o pokazywania lub ukrywania interfejsu użytkownika mogą być trudne, a reguły będą zawsze błędne dla niektórych zestawów przypadków.

## <a name="BKMK_Projects"></a>Projektami

### <a name="projects-in-the-solution-explorer"></a>Projekty w Eksploratorze rozwiązań
Większości projektów są klasyfikowane jako na podstawie odwołania, na podstawie katalogu lub mieszany. Wszystkie trzy rodzaje projektów są obsługiwane jednocześnie w Eksploratorze rozwiązań. Katalog główny środowiska użytkownika w pracy z projektami odbywa się wewnątrz tego okna. Mimo że inny projekt węzły są odwołania, katalogu lub projekty typu trybu mieszanego, istnieje wspólny wzorzec interakcji, które powinny być stosowane jako punktu wyjścia przed rozbieżnych do wzorców użytkownika specyficznych dla projektu.

Zawsze należy projektów:

- Obsługuje możliwość dodawania foldery projektu, aby zorganizować zawartość projektu

- Obsługa spójny model do trwałość projektu

Projekty należy także korzystać z modeli spójne interakcji:

- Usuwanie elementów projektu

- Zapisywanie dokumentów

- Edycja właściwości projektu

- Projekt w alternatywny widok do edycji

- Operacje przeciągania i upuszczania

### <a name="drag-and-drop-interaction-model"></a>Przeciągnij i upuść modelu
Projekty zazwyczaj klasyfikowania siebie jako na podstawie odwołania (możliwe do utrwalenia tylko odwołania do elementów projektu w magazynie) na poziomie katalogu (mógł zachować tylko elementy projektu fizycznie przechowywane w hierarchii projektu), lub mieszany (możliwe do utrwalenia odwołania lub elementów fizycznych). IDE uwzględnia wszystkie trzy typy projektów jednocześnie w **Eksplorator rozwiązań**.

W perspektywie typu "przeciągnij i upuść" należy zastosować następujące cechy do poszczególnych typów projektów w **Eksplorator rozwiązań**:

- **Projekt oparty na odwołaniach:** Najważniejszym punktem jest to, że projekt jest przeciągany wokół odwołania do elementu w magazynie. Jeśli odwołanie do projektu działa jako źródło dla operacji przenoszenia, go tylko należy usunąć odwołanie do elementu z projektu. Nie element faktycznie można usunąć z dysku twardego. Jeśli działa na podstawie odwołań projektu jako obiekt docelowy operacji przenoszenia (lub kopiowania), dodawaj odwołania do oryginalnego elementu źródłowego bez wprowadzania prywatną kopię elementu.

- **Projekt oparty na katalogu:** W punkcie przeciągania i upuszczania projekt jest przeciągany wokół elementu fizycznego, a nie do odwołania. Jeśli projekt na podstawie katalogu działa jako źródło dla operacji przenoszenia, powinny kończyć się się usunięcie elementu fizycznego z dysku twardego, a także usunięcie go z projektu. Jeśli działa na poziomie katalogu projektu jako obiekt docelowy operacji przenoszenia (lub kopiowania), jego Utwórz kopię elementu źródłowego, w lokalizacji docelowej.

- **Projekt mieszany:** W przypadku przeciągania i upuszczania punktu widzenia zachowanie tego typu projektu jest zależne od charakteru przeciąganego elementu (odwołanie do elementu w magazynie lub samego elementu). Poprawne zachowanie elementów fizycznych i odwołania do opisanych powyżej.

Jeśli w **Eksplorator rozwiązań**istniał tylko jeden typ projektu, operacje przeciągania i upuszczania byłyby proste. Ponieważ każdy system projektu ma możliwość definiowania zachowanie przeciągnij i upuść, niektóre wytyczne dotyczące (oparte na zachowanie przeciągnij i upuść Eksploratora Windows) powinna znajdować się zapewniają przewidywalne działanie:

- Niezmodyfikowana operacja przeciągania w **Eksplorator rozwiązań** (gdy nie są wciśnięte klawisze CTRL ani Shift), należy wykonać operację przenoszenia.

- Operacja przeciągania SHIFT również powinno spowodować operacji przenoszenia.

- Operacja przeciągania CTRL powinno spowodować operacji kopiowania.

- Systemy projektu odwołania i mieszanych obsługuje pojęcia dodanie link (lub odwołania) do elementu źródłowego. Gdy te projekty są elementem docelowym operacji przeciągania i upuszczania (naciśnięcie **klawiszy Ctrl + Shift** jest wyłączone), powinno to skutkować odwołaniem do elementu dodawanego do projektu.

Nie wszystkie operacje przeciągania i upuszczania są za pośrednictwem różnych kombinacji projekty na podstawie odwołania, na podstawie katalogu i mieszanych. W szczególności jest pozwala poudawać umożliwia operacji przenoszenia między projektu na podstawie katalogu źródłowego i docelowego na podstawie odwołań projektu, ponieważ projekt oparty na katalog źródłowy będzie trzeba usunąć elementu źródłowego po ukończeniu przenoszenia. Następnie pojawiłyby docelowy projekt odniesienia z odwołaniem do usuniętego elementu.

Jest to również mylące poudawać, aby zezwolić na operację kopiowania między tymi typami projektów, ponieważ docelowy projekt oparty na odwołaniach nie powinien tworzyć niezależnej kopii elementu źródłowego. Podobnie Ctrl + Shift, przeciągając go do projektu na podstawie katalog docelowy nie powinien być dozwolony ponieważ nie można utrwalić odwołania do katalogu projektu. W przypadkach, gdy operacja przeciągania i upuszczania nie jest obsługiwana IDE powinna nie zezwalaj na liście i pokazania użytkownika nieupuszczalny kursor (pokazane w poniższej tabeli wskaźnika).

Aby poprawnie zaimplementować zachowanie przeciągania i upuszczania, projekt źródłowy przeciągnięcia musi przekazywać swój charakter do projektu docelowego. (Na przykład czy jest on oparty na odwołaniach lub w katalogu?) Te informacje są wskazywane przez format schowka oferowany przez źródło. Jako źródło operacji przeciągania (lub kopiowania schowka) projekt powinien oferować odpowiednio `CF_VSREFPROJECTITEMS` lub `CF_VSSTGPROJECTITEMS`, w zależności od tego, czy projekt jest oparty na odwołaniach czy w katalogu. Oba te formaty mają tę samą zawartość danych, która jest podobna do formatu `CF_HDROP` systemu Windows, z wyjątkiem tego, że listy ciągów, zamiast nazw, są zakończonymi podwójnie`NULL` listą ciągów `Projref` (w sposób zwrócony z `IVsSolution::GetProjrefOfItem` lub `::GetProjrefOfProject` zgodnie z potrzebami).

Jako obiekt docelowy operacji usuwania (lub wklejania schowka), projekt powinien akceptować zarówno `CF_VSREFPROJECTITEMS`, jak i `CF_VSSTGPROJECTITEMS`, ale dokładna obsługa operacji przeciągania i upuszczania różni się w zależności od charakteru projektu docelowego i projektu źródłowego. Projekt źródłowy deklaruje swój charakter, wybierając `CF_VSREFPROJECTITEMS` lub `CF_VSSTGPROJECTITEMS`. Celem listy rozumie swój własny charakter i dlatego ma za mało informacji do podejmowania decyzji, aby, czy przenoszenie, kopiowanie lub łącze powinno być przeprowadzane. Użytkownik modyfikuje również kolejnej operacji przeciągania i upuszczania powinna być wykonywana przez naciśnięcie klawisza Ctrl, Shift, lub zarówno klawisze Ctrl i Shift. Ważne jest, aby miejsce docelowe upuszczania prawidłowo wskazywało, która operacja zostanie wykonana z wyprzedzeniem w `DragEnter` i `DragOver` metodach. **Eksplorator rozwiązań** automatycznie wie, czy projekt źródłowy i projekt docelowy są tego samego projektu.

Przeciąganie elementów projektu w wystąpieniach programu Visual Studio (na przykład z jednego wystąpienia devenv.exe do drugiego) specjalnie nie jest obsługiwane. **Eksplorator rozwiązań** również wyłącza je bezpośrednio.

Użytkownik powinien zawsze można ustalić skutek operacji przeciągania i upuszczania, wybierając element, przeciągając je do lokalizacji docelowej i przestrzegając następujących wskaźników myszy widocznego przed upuszczeniu elementu:

| Wskaźnik myszy | Polecenie | Opis |
| :---: | --- | --- |
| ![Ikona "Brak" myszy](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 — 01_MouseNoDrop") | Nie listy | Nie można usunąć elementu do określonej lokalizacji. |
| ![Ikona "Copy" myszy](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 — 02_MouseCopy") | Copy | Element zostanie skopiowany do lokalizacji docelowej. |
| ![Ikona "Przenieś" myszy](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 — 03_MouseMove") | Move | Element zostanie przeniesiony do lokalizacji docelowej. |
| ![Ikona myszy "Dodaj odwołanie"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 — 04_MouseAddRef") | Dodawanie odwołania | Odwołanie do wybranego elementu zostaną dodane do lokalizacji docelowej. |

#### <a name="reference-based-projects"></a>Projekty oparte na odwołanie
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które należy wykonać oparte na rodzaju źródła elementu i modyfikator klawiszy dla projektów docelowych na podstawie odwołania:

| Modyfikator | Kategoria | Element źródłowy: odwołania/łącze | Element źródłowy: fizyczny element lub system plików (`CF_HDROP`) |
| --- | --- | --- | --- |
| Nie modyfikatora | Akcja | Move | Link |
| Nie modyfikatora | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Nie modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Zachowuje oryginalnego elementu |
| Nie modyfikatora | Wynik | `DROPEFFECT_MOVE` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Shift + przeciągnięcie | Akcja | Move | Nie listy |
| Shift + przeciągnięcie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Nie listy |
| Shift + przeciągnięcie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Nie listy |
| Shift + przeciągnięcie | Wynik | `DROPEFFECT_MOVE` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | Nie listy |
| CTRL + przeciągnij | Akcja | Copy | Nie listy |
| CTRL + przeciągnij | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Nie listy |
| CTRL + przeciągnij | Element źródłowy | Odwołanie do elementu zachowuje | Nie listy |
| CTRL + przeciągnij | Wynik | `DROPEFFECT_COPY` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | Nie listy |
| Ctrl + Shift + przeciągnięcie | Akcja | Link | Link |
| Ctrl + Shift + przeciągnięcie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Ctrl + Shift + przeciągnięcie | Element źródłowy | Odwołanie do elementu zachowuje | Zachowuje oryginalnego elementu |
| Ctrl + Shift + przeciągnięcie | Wynik | `DROPEFFECT_LINK` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl + Shift + przeciągnięcie | Uwaga | Taka sama jak zachowanie przeciągnij i upuść skróty w Eksploratorze Windows. ||
| Wytnij/Wklej | Akcja | Move | Link |
| Wytnij/Wklej | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Wytnij/Wklej | Element źródłowy | Odwołanie do elementu zachowuje|Zachowuje oryginalnego elementu |
| Wytnij/Wklej | Wynik | Element pozostaje w pierwotnej lokalizacji w magazynie | Element pozostaje w pierwotnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Copy | Link |
| Kopiowanie/wklejanie | Element źródłowy | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Kopiowanie/wklejanie | Wynik | Odwołanie do elementu zachowuje | Zachowuje oryginalnego elementu |
| Kopiowanie/wklejanie | Akcja | Element pozostaje w pierwotnej lokalizacji w magazynie | Element pozostaje w pierwotnej lokalizacji w magazynie |

#### <a name="directory-based-projects"></a>Projekty oparte na katalog
Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane w oparciu o charakter źródło elementu i modyfikator klawiszy, w przypadku projektów opartych na katalog docelowy:

| Modyfikator | Kategoria | Element źródłowy: odwołania/łącze | Element źródłowy: fizyczny element lub system plików (`CF_HDROP`) |
|-----------------|----------| - | - |
| Nie modyfikatora | Akcja | Move | Move |
| Nie modyfikatora | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Nie modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa odwołanie do oryginalnego elementu |
| Shift + przeciągnięcie | Akcja | Move | Move |
| Shift + przeciągnięcie | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Shift + przeciągnięcie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Shift + przeciągnięcie | Wynik | `DROPEFFECT_MOVE` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_MOVE` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| CTRL + przeciągnij | Akcja | Copy | Copy |
| CTRL + przeciągnij | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| CTRL + przeciągnij | Element źródłowy | Odwołanie do elementu zachowuje | Odwołanie do elementu zachowuje |
| CTRL + przeciągnij | Wynik | `DROPEFFECT_COPY` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_COPY` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl + Shift + przeciągnięcie | | Nie listy | Nie listy |
| Wytnij/Wklej | Akcja | Move | Move |
| Wytnij/Wklej | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wytnij/Wklej | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wytnij/Wklej | Wynik | Element pozostaje w pierwotnej lokalizacji w magazynie | Element zostanie usunięty z oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Copy | Copy |
| Kopiowanie/wklejanie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie/wklejanie | Element źródłowy | Zachowuje oryginalnego elementu | Zachowuje oryginalnego elementu |
| Kopiowanie/wklejanie | Wynik | Element pozostaje w pierwotnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji dodatki magazynu |

#### <a name="mixed-target-projects"></a>Projektów docelowych mieszane
Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane w oparciu o charakter naciśnięto dla projektów docelowych mieszane klucze elementów i modyfikator źródła:

| Modyfikator | Kategoria | Element źródłowy: odwołania/łącze | Element źródłowy: fizyczny element lub system plików (`CF_HDROP`) |
| --- | --- | --- | --- |
| Nie modyfikatora | Akcja | Move | Move |
| Nie modyfikatora | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Nie modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa odwołanie do oryginalnego elementu |
| Nie modyfikatora | Wynik | `DROPEFFECT_ MOVE` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE` jest zwracana jako akcja z `::Drop`, a element zostanie usunięty z oryginalnej lokalizacji w magazynie |
| Shift + przeciągnięcie | Akcja | Move | Move |
| Shift + przeciągnięcie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Shift + przeciągnięcie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Shift + przeciągnięcie | Wynik | `DROPEFFECT_ MOVE` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE` jest zwracana jako akcja z `::Drop`, a element zostanie usunięty z oryginalnej lokalizacji w magazynie |
| CTRL + przeciągnij | Akcja | Copy | Copy |
| CTRL + przeciągnij | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| CTRL + przeciągnij | Element źródłowy | Odwołanie do elementu zachowuje | Zachowuje oryginalnego elementu |
| CTRL + przeciągnij | Wynik | `DROPEFFECT_ COPY` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ COPY` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl + Shift + przeciągnięcie | Akcja | Link | Link |
| Ctrl + Shift + przeciągnięcie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu źródłowego |
| Ctrl + Shift + przeciągnięcie | Element źródłowy | Odwołanie do elementu zachowuje | Zachowuje oryginalnego elementu |
| Ctrl + Shift + przeciągnięcie | Wynik | `DROPEFFECT_ LINK` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ LINK` jest zwracana jako akcja z `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Wytnij/Wklej | Akcja | Move | Move |
| Wytnij/Wklej | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wytnij/Wklej | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wytnij/Wklej | Wynik | Element pozostaje w pierwotnej lokalizacji w magazynie | Element zostanie usunięty z oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Copy | Copy |
| Kopiowanie/wklejanie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie/wklejanie | Element źródłowy | Zachowuje oryginalnego elementu | Zachowuje oryginalnego elementu |
| Kopiowanie/wklejanie | Wynik | Element pozostaje w pierwotnej lokalizacji w magazynie | Element pozostaje w pierwotnej lokalizacji w magazynie |

Te szczegóły należy wziąć pod uwagę podczas implementowania przeciągania w **Eksplorator rozwiązań**:

- Projektowanie pod kątem scenariuszy z wieloma zaznaczenia.

- Nazwy plików (pełna ścieżka) musi być unikatowa dla projektu docelowego lub listy nie powinien być dozwolony.

- Nazwy folderów muszą być unikatowe (bez uwzględniania wielkości liter) na poziomie są usuwane.

- Ma zachowanie różnic między plikami, które są otwarte lub zamknięte w czasie przeciągania (niewymienione w powyższych scenariuszy).

- Pliki najwyższego poziomu zachowywać się inaczej niż pliki w folderach.

Inny problem, aby wiedzieć, jest sposób obsługi operacji przenoszenia elementów, które mają otwartych oknach projektantów i edytorów. To oczekiwane zachowanie w następujący sposób (dotyczy to wszystkich typów projektów):

1. Jeśli Otwórz Edytor/projektanta nie ma wszystkie niezapisane zmiany, następnie w oknie Projektant/Edytor powinien zostać dyskretnie zamknięty.

2. Jeśli Otwórz Edytor/projektanta niezapisane zmiany, źródła przeciągania powinien Zaczekaj, aż upuszczania do wystąpienia, a następnie poproś użytkownika, aby zapisać niezatwierdzone zmiany w otwartych dokumentach przed zamknięciem okna z monit podobny do następującego :

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Dzięki temu użytkownik można zapisać pracę w toku, zanim obiekt docelowy sprawia, że jego kopii. Dodano nową metodę `IVsHierarchyDropDataSource2::OnBeforeDropNotify` w celu włączenia tej obsługi.

Następnie obiekt docelowy skopiuje stan elementu w postaci magazynu (bez uwzględnienia niezapisanych zmian w edytorze, jeśli użytkownik wybrał opcję **nie**). Po zakończeniu kopiowania (w `IVsHierarchyDropDataSource::Drop`) w miejscu docelowym można wykonać operację usuwania części operacji przenoszenia (w `IVsHierarchyDropDataSource::OnDropNotify`).

Wszelkie edytorów z niezapisanymi zmianami należy pozostawić otwarty. W tych dokumentach z niezapisanymi zmianami to oznacza, że odbędzie się kopiowania część operacji przenoszenia, ale część usuwania zostanie przerwane. W scenariuszu z wieloma wyborami, gdy użytkownik wybierze **nie**, te dokumenty z niezapisanymi zmianami nie powinny być zamykane ani usuwane, ale te bez niezapisanych zmian powinny być zamknięte i usunięte.