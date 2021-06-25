---
title: Wzorce aplikacji dla Visual Studio | Microsoft Docs
description: Dowiedz się więcej o różnicach między oknami dokumentów, oknami narzędzi i oknami dialogowymi nie modeless, w tym wzorcami użycia okien dla nowych funkcji Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2726c7096bbf4606fbab2c32b01ffd197549e13c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899189"
---
# <a name="application-patterns-for-visual-studio"></a>Wzorce aplikacji dla programu Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interakcje okna

### <a name="overview"></a>Omówienie
Dwa główne typy okien używane w Visual Studio to edytory dokumentów i okna narzędzi. Sporadyczne, ale możliwe, są dużymi oknami dialogowymi bez moderowania. Mimo że wszystkie te typy są nie moderowe w powłoki, ich wzorce są zasadniczo różne. Ta sekcja zawiera różnicę między oknami dokumentów, oknami narzędzi i oknami dialogowymi nie modeless. Wzorce modalnych okien dialogowych są uwzględnione w [oknie dialogowym](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porównywanie wzorców użycia okien
**Okna dokumentów** są prawie zawsze wyświetlane w obszarze dokumentu. Daje to edytorowi dokumentów "środkowy etap", który pozwala rozmieścić dodatkowe okna narzędzi.

Okno **narzędzi jest** najczęściej wyświetlane jako oddzielne, mniejsze okno zwinięte na krawędzi środowiska IDE. Może być widoczna, ukryta lub automatycznie ukryta. Jednak czasami okna narzędzi są prezentowane w obszarze dokumentu przez usunięcie zaznaczenia właściwości **Window/Docking** w oknie. Skutkuje to większą nieruchomością, ale również częstą decyzją projektową: podczas próby integracji z usługą Visual Studio należy zdecydować, czy funkcja powinna wyświetlać okno narzędzi, czy okno dokumentu.

**Nie jest zalecane tworzenie nie** moderowych okien dialogowych Visual Studio. Większość nie moderowych okien dialogowych to z definicji przestawne okna narzędzi, które powinny być implementowane w ten sposób. Okna dialogowe modeless są dozwolone w przypadkach, gdy rozmiar normalnego okna narzędzi zadokowanych do boku powłoki byłby zbyt ograniczany. Są one również dozwolone w przypadkach, gdy użytkownik prawdopodobnie przeniesie okno dialogowe do monitora pomocniczego.

Zastanów się dokładnie, jakiego typu kontenera potrzebujesz. W poniższej tabeli przedstawiono typowe zagadnienia dotyczące wzorca użycia dotyczące projektowania interfejsu użytkownika.

||Okno dokumentu|Okno narzędzi|Okno dialogowe nie modeless|
|-|---------------------|-----------------|---------------------|
| **Pozycja** | Zawsze znajduje się w obszarze dokumentu i nie dokuje krawędzi środowiska IDE. Można go "ściągnąć", aby zmiennoprzecinkowy był zmiennoprzecinkowy niezależnie od powłoki głównej. | Zazwyczaj zadokowane tabulatorami krawędzie środowiska IDE, ale można je dostosować tak, aby były przestawne, automatycznie ukryte (odpięte) lub zadokowane w obszarze dokumentu.|Duże okno zmiennoprzecincze oddzielone od środowiska IDE. |
| **Zatwierdzanie modelu** | *Opóźnione zatwierdzenie*<br /><br /> Aby zapisać dane w dokumencie, użytkownik musi wydać polecenie Zapisz **plik, &gt;** Zapisz **jako** lub **Zapisz wszystko.** W oknie dokumentu zatwierdzona jest koncepcja danych, które się w nim znajduje, a następnie są one zatwierdzone w jednym z poleceń zapisywania. Podczas zamykania okna dokumentu cała zawartość jest zapisywana na dysku lub utracona. | *Natychmiastowe zatwierdzenie*<br /><br /> Nie ma żadnego modelu zapisywania. W przypadku okien narzędzi inspektora, które pomagają w edytowaniu pliku, plik musi być otwarty w aktywnym edytorze lub projektancie, a edytor lub projektant jest właścicielem zapisu. | *Opóźnione lub natychmiastowe zatwierdzenie*<br /><br /> Najczęściej duże nie moderowe okno dialogowe wymaga akcji w celu zatwierdzenia zmian i umożliwia operację "Anuluj", która wycofuje wszystkie zmiany wprowadzone w sesji okna dialogowego.  Odróżnia to nie modeless okno dialogowe od okna narzędzi w tych oknach narzędzi zawsze ma model natychmiastowego zatwierdzania. |
| **Widoczność** | *Otwieranie/tworzenie (plik) i zamykanie*<br /><br /> Otwieranie okien dokumentów odbywa się przez otwarcie istniejącego dokumentu lub użycie szablonu do utworzenia nowego dokumentu. Nie ma polecenia \<specific editor> "Otwórz". | *Ukrywanie i pokazywanie*<br /><br /> Okna narzędzi pojedynczego wystąpienia mogą być ukryte lub wyświetlane. Zawartość i stany w oknie narzędzia są utrwalane w widoku lub ukryte. Okna narzędzi o wielu wystąpieniach można zamykać i ukrywać. Po zamknięciu okna narzędzi o wielu wystąpieniach zawartość i stan w tym oknie są odrzucane. | *Uruchomione z polecenia*<br /><br /> Okna dialogowe są wyświetlane z polecenia opartego na zadaniach. |
| **Wystąpienia** | *Wiele wystąpień*<br /><br /> W tym samym czasie można otworzyć kilka edytorów i edytować różne pliki, podczas gdy niektóre edytory zezwalają również na otwieranie tego samego pliku w więcej niż jednym edytorze (przy użyciu polecenia Nowe okno **okna). &gt;**<br /><br /> Pojedynczy edytor może równocześnie edytować jeden lub wiele plików (Projektant projektu). | *Jedno lub wiele wystąpień*<br /><br /> Zawartość zmienia się w celu odzwierciedlenia kontekstu (jak w przeglądarce właściwości) lub wypychania fokusu/kontekstu do innych okien (Lista zadań, Eksplorator rozwiązań).<br /><br /> Okna narzędzi z jednym wystąpieniem i wieloma wystąpieniami powinny być skojarzone z aktywnym oknem dokumentu, chyba że istnieje ważny powód, aby tego nie wiedzieć. | *Jedno wystąpienie* |
| **Przykłady** | **Edytory tekstów,** takie jak edytor kodu<br /><br /> **Projektowanie powierzchni,** takich jak projektant formularzy lub powierzchnia modelowania<br /><br /> **Układy kontrolek podobne do okien dialogowych,** takich jak Projektant manifestu | Ten **Eksplorator rozwiązań** rozwiązanie i projekty zawarte w rozwiązaniu<br /><br /> Interfejs **Eksplorator serwera** hierarchiczny widok serwerów i połączeń danych, które użytkownik wybierze do otwarcia w oknie. Otwarcie obiektu z hierarchii bazy danych, takiego jak zapytanie, powoduje otwarcie okna dokumentu i umożliwia użytkownikowi edytowanie zapytania.<br /><br /> Przeglądarka **właściwości wyświetla** właściwości obiektu wybranego w oknie dokumentu lub innym oknie narzędzia. Właściwości są prezentowane w widoku siatki hierarchicznej lub w złożonych kontrolkach podobnych do okien dialogowych i umożliwiają użytkownikowi ustawianie wartości tych właściwości. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Okna narzędzi

### <a name="overview"></a>Omówienie
Okna narzędzi obsługują pracę użytkownika, która odbywa się w oknach dokumentów. Mogą służyć do wyświetlania hierarchii, która reprezentuje podstawowy obiekt główny, który Visual Studio udostępnia i może manipulować.

Podczas rozważania nowego okna narzędzi w idee autorzy powinni:

- Użyj istniejących okien narzędzi odpowiednich dla zadań i nie twórz nowych okien o podobnych funkcjach. Nowe okna narzędzi powinny być tworzone tylko wtedy, gdy oferują znacznie inne "narzędzie" lub funkcje, których nie można zintegrować w podobnym oknie lub przez przekształcenie istniejącego okna w centrum przestawne.

- W razie potrzeby użyj standardowego paska poleceń w górnej części okna narzędzia.

- Należy zapewnić spójność z wzorcami już obecnymi w innych oknach narzędzi do prezentacji sterowania i nawigacji za pomocą klawiatury.

- Spójna prezentacja kontrolek w innych oknach narzędzi.

- Jeśli to możliwe, okna narzędzi specyficzne dla dokumentu powinny być automatycznie widoczne, tak aby były wyświetlane tylko po aktywowaniu dokumentu nadrzędnego.

- Upewnij się, że nawigacja w zawartości okna jest nawigowalna za pomocą klawiatury (obsługują klawisze strzałek).

#### <a name="tool-window-states"></a>Stany okna narzędzi
Visual Studio narzędzi mają różne stany, z których niektóre są aktywowane przez użytkownika (na przykład funkcja automatycznego ukrywania). Inne stany, takie jak automatycznie widoczne, umożliwiają pojawianie się okien narzędzi w poprawnym kontekście i ukrywanie ich w razie potrzeby. Istnieje łącznie pięć stanów okna narzędzi.

- **Zadokowane/przypięte** okna narzędzi można dołączyć do dowolnej z czterech stron obszaru dokumentu. Ikona pinezki jest wyświetlana na pasku tytułu okna narzędzi. Okno narzędzi może być zadokowane w poziomie lub w pionie wzdłuż krawędzi powłoki i innych okien narzędzi, a także może być połączone tabulatorami.

- **Automatycznie ukryte okna** narzędzi są odpinane. Okno może wysuwać się poza wzrok, pozostawiając kartę (z nazwą okna narzędzia i jego ikoną) na krawędzi obszaru dokumentu. Okno narzędzi wysuwa się, gdy użytkownik najedzie kursorem na kartę.

- **Automatycznie widoczne okna** narzędzi są automatycznie wyświetlane, gdy zostanie uruchomiony inny element interfejsu użytkownika, taki jak edytor, lub uzyska fokus.

- **Przestawne** okna narzędzi zatrzymają wskaźnik myszy poza ideą IDE. Jest to przydatne w przypadku konfiguracji z wieloma monitorami.

- **Okna narzędzi dokumentów** z kartami można zadokować w obszarze dokumentu. Jest to przydatne w przypadku dużych okien narzędzi, takich jak przeglądarka obiektów, które wymagają więcej powierzchni niż umożliwia dokowanie do krawędzi ramki.

![Stany okna narzędzi w Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Stany okna narzędzi w Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Jedno wystąpienie i wiele wystąpień
Okna narzędzi to jedno wystąpienie lub wiele wystąpień. Niektóre okna narzędzi z jednym wystąpieniem mogą być skojarzone z aktywnym oknem dokumentu, podczas gdy okna narzędzi o wielu wystąpieniach mogą nie być. Okna narzędzi o wielu wystąpieniach reagują na polecenie **Nowe &gt; okno okna,** tworząc nowe wystąpienie okna. Na poniższej ilustracji przedstawiono okno narzędzi umożliwiające polecenie Nowe okno, gdy wystąpienie okna jest aktywne:

![Okno narzędzi umożliwiające polecenie "Nowe okno", gdy wystąpienie okna jest aktywne](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Okno narzędzi umożliwiające polecenie "Nowe okno", gdy wystąpienie okna jest aktywne

Okna narzędzi z jednym wystąpieniem mogą być ukryte lub wyświetlane, podczas gdy okna narzędzi o wielu wystąpieniach mogą być zamknięte, a także ukryte. Wszystkie okna narzędzi mogą być zadokowane, połączone tabulatorami, przestawne lub ustawiane jako okno podrzędne interfejsu Multiple-Document (MDI) (podobnie jak okno dokumentu). Wszystkie okna narzędzi powinny odpowiadać na odpowiednie polecenia zarządzania oknami w menu Okno:

![Polecenia zarządzania oknami w Visual Studio okna](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Polecenia zarządzania oknami w Visual Studio okna

#### <a name="document-specific-tool-windows"></a>Okna narzędzi specyficzne dla dokumentów
Niektóre okna narzędzi są przeznaczone do zmiany na podstawie danego typu dokumentu. Te okna są stale aktualizowane w celu odzwierciedlenia funkcji mających zastosowanie do aktywnego okna dokumentu w idee.

Przykładami okien narzędzi, których zawartość zmienia się w celu odzwierciedlenia wybranego edytora, są przybornik i konspekt dokumentu. Te okna pokazują znak wodny, gdy edytor ma fokus, który nie oferuje kontekstu okna.

#### <a name="navigable-list-tool-windows"></a>Okna narzędzi listy nawigacji
Niektóre okna narzędzi wyświetlają listę elementów nawigacji, z których użytkownik może korzystać. W tym typie okna zawsze powinna być informacja zwrotna dla bieżącego elementu na liście, nawet jeśli okno jest nieaktywne. Lista powinna odpowiadać na polecenia **GoToNextLocation** i **GoToPrevLocation,** zmieniając również aktualnie zaznaczony element w oknie

Przykładami okien narzędzi listy nawigacji są okna Eksplorator rozwiązań i Znajdź wyniki.

### <a name="tool-window-types"></a>Typy okien narzędzi

#### <a name="common-tool-windows-and-their-functions"></a>Typowe okna narzędzi i ich funkcje

**Hierarchiczne okna narzędzi**

| Okno narzędzi | Funkcja |
| --- | --- |
| Eksplorator rozwiązań | Drzewo hierarchiczne, które wyświetla listę dokumentów zawartych w projektach, różnych plikach i elementach rozwiązania. Wyświetlanie elementów w projektach jest definiowane przez pakiet, który jest właścicielem typu projektu (na przykład typy oparte na odwołaniach, oparte na katalogach lub w trybie mieszanym). |
| Widok klas | Drzewo hierarchiczne klas i różnych elementów w zestawie pracy dokumentów, niezależnie od samych plików. |
| Eksplorator serwera | Drzewo hierarchiczne, które wyświetla wszystkie serwery i połączenia danych w rozwiązaniu. |
| Konspekt dokumentu | Struktura hierarchiczna aktywnego dokumentu. |

**Okna narzędzi siatki**

| Okno narzędzi | Funkcja |
| --- | --- |
| Właściwości | Siatka, która wyświetla listę właściwości wybranego obiektu wraz z selektorami wartości w celu edytowania tych właściwości. |
| Lista zadań | Siatka, która umożliwia użytkownikowi tworzenie/edytowanie/usuwanie zadań i komentarzy. |

**Okna narzędzi zawartości**

| Okno narzędzi | Funkcja |
| --- | --- |
| Help | Okno, które umożliwia użytkownikom dostęp do różnych metod uzyskiwania pomocy w oknie "Jak mogę?" na forach MSDN. |
| Pomoc dynamiczna | Okno narzędzia, w którym są wyświetlane linki do tematów pomocy dotyczących bieżącego wyboru. |
| Przeglądarka obiektów | Dwu kolumnowy zestaw ramek z listą składników obiektu hierarchicznego w okienku po lewej stronie oraz właściwościami i metodami obiektu w prawej kolumnie. |

**Okna narzędzi dialogowych**

| Okno narzędzi | Funkcja |
| --- | --- |
| Znajdowanie | Okno dialogowe, które umożliwia użytkownikowi znajdowanie lub znajdowanie i zastępowanie w różnych plikach w rozwiązaniu. |
| Szukanie zaawansowane | Okno dialogowe, które umożliwia użytkownikowi znajdowanie lub znajdowanie i zastępowanie w różnych plikach w rozwiązaniu. |

**Inne okna narzędzi**

::: moniker range="vs-2017"

| Okno narzędzi | Funkcja |
| --- | --- |
| Przybornik | Okno narzędzi używane do przechowywania elementów, które zostaną porzucone na powierzchni projektowych, zapewniając spójne źródło przeciągania dla wszystkich projektantów. |
| Strona początkowa | Portal użytkownika do uzyskiwania dostępu Visual Studio do kanałów informacyjnych wiadomości dla deweloperów, Visual Studio pomocy i ostatnich projektów. Użytkownicy mogą również tworzyć niestandardowe strony startowe, kopiując plik StartPage.xaml z katalogu "Common7\IDE\StartPages Visual Studio program files do folderu StartPages w katalogu dokumentów programu Visual Studio, a następnie ręcznie edytując kod XAML lub otwierając go w programie Visual Studio lub innym edytorze \" kodu. |

::: moniker-end

::: moniker range=">=vs-2019"

| Okno narzędzi | Funkcja |
| --- | --- |
| Przybornik | Okno narzędzi używane do przechowywania elementów, które zostaną porzucone na powierzchni projektowych, zapewniając spójne źródło przeciągania dla wszystkich projektantów. |

::: moniker-end

**Okna narzędzi debugera**

| Okno narzędzi | Funkcja |
| --- | --- |
| Autos ||
| Natychmiastowe ||
| Dane wyjściowe | Okna danych wyjściowych można używać zawsze, gdy masz zdarzenia tekstowe lub stan do zadeklarowania. |
| Pamięć ||
| Punkty przerwania ||
| Uruchomienie ||
| Dokumenty ||
| Stos wywołań ||
| Mieszkańców ||
| Zegarki ||
| Demontażu ||
| Rejestrów ||
| Wątki ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Konwencje edytora dokumentów

### <a name="document-interactions"></a>Interakcje dokumentów
"Obszar dokumentu" to największa przestrzeń w obrębie środowiska IDE, w której użytkownik zwykle skupia swoją uwagę w celu wykonywania zadań, wspomagane przez dodatkowe okna narzędzi. Edytory dokumentów reprezentują podstawowe jednostki pracy, które użytkownik otwiera i zapisuje w Visual Studio. Zachowują one silne poczucie wyboru powiązane z Eksplorator rozwiązań lub innymi oknami hierarchii aktywnej. Użytkownik powinien być w stanie wskazać jeden z tych okien hierarchii i wiedzieć, gdzie znajduje się dokument oraz jaka jest jego relacja z rozwiązaniem, projektem lub innym obiektem głównym dostarczonym przez pakiet Visual Studio plików.

Edytowanie dokumentów wymaga spójnego interfejsu użytkownika. Aby umożliwić użytkownikowi skoncentrowanie się na zadaniach, a nie na zarządzaniu oknami i znajdowaniu poleceń, wybierz strategię widoku dokumentu, która najlepiej pasuje do zadań użytkownika do edytowania tego typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Typowe interakcje dotyczące listy dokumentów

- Zachowanie spójnego modelu interakcji we wspólnych **doświadczeniach z** nowym plikiem **i otwieraniem** pliku.

- Zaktualizuj powiązane funkcje w powiązanych oknach i menu po otworze okna dokumentu.

- Polecenia menu są odpowiednio zintegrowane z wspólnymi menu, np. **Menu Edytuj,** **Formatuj** **i** Wyświetl. Jeśli dostępna jest znaczna liczba wyspecjalizowanych poleceń, można utworzyć nowe menu. To nowe menu powinno być widoczne tylko wtedy, gdy dokument ma fokus.

- Osadzony pasek narzędzi można umieścić w górnej części edytora. Preferowane jest użycie oddzielnego paska narzędzi wyświetlanego poza edytorem.

- Zawsze zachowaj zaznaczenie w oknie Eksplorator rozwiązań podobnej aktywnej hierarchii.

- Dwukrotne kliknięcie dokumentu w oknie Eksplorator rozwiązań powinno wykonać tę samą akcję co polecenie **Otwórz.**

- Jeśli dla typu dokumentu można użyć więcej niż jednego edytora, użytkownik powinien mieć możliwość przesłonięcia lub zresetowania domyślnej akcji dla danego typu dokumentu przy użyciu okna dialogowego Otwórz za pomocą, klikając plik prawym przyciskiem myszy i wybierając polecenie **Otwórz** za pomocą z menu skrótów. 

- Nie należy tworzyć kreatora w dokumencie.

### <a name="user-expectations-for-specific-document-types"></a>Oczekiwania użytkowników dotyczące określonych typów dokumentów
Istnieje kilka różnych podstawowych typów edytorów dokumentów, a każdy z nich ma zestaw interakcji, które są spójne z innymi tego samego typu.

- **Edytor tekstowy: edytor** kodu, pliki dziennika

- **Powierzchnia projektowa:** Projektant formularzy WPF, formularze systemu Windows

- **Edytor w stylu okna dialogowego:** Manifest Designer, właściwości projektu

- **Projektant modelu: projektant** przepływu pracy, mapa kodu, diagram architektury, postęp

Istnieje również kilka typów innych niż edytora, które używają dobrze dokumentu. Chociaż nie edytują dokumentów samodzielnie, muszą stosować standardowe interakcje dla okien dokumentów.

- **Raporty:** Raport IntelliTrace, raport funkcji Hyper-V, raport profilera

- **Pulpit nawigacyjny:** Centrum diagnostyki

#### <a name="text-based-editors"></a>Edytory tekstowe

- Dokument uczestniczy w modelu karty podglądu, umożliwiając podgląd dokumentu bez jego otwierania.

- Struktura dokumentu może być reprezentowana w oknie narzędzi towarzyszących, takim jak konspekt dokumentu.

- Funkcja IntelliSense (w razie potrzeby) będzie działać spójnie z innymi edytorami kodu.

- Wyskakujące okienka lub interfejs użytkownika z asystą są zgodne z podobnymi stylami i wzorcami dla istniejącego podobnego interfejsu użytkownika, takiego jak CodeLens.

- Komunikaty dotyczące stanu dokumentu będą wyświetlane w kontrolce paska informacji w górnej części dokumentu lub na pasku stanu.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu strony Narzędzia **> Opcje,** udostępnionej strony Czcionki i kolory lub strony specyficznej dla edytora.

#### <a name="design-surfaces"></a>Powierzchnie projektowe

- Pusty projektant powinien mieć na powierzchni znak wodny wskazujący, jak rozpocząć pracę.

- Mechanizmy przełączania widoków będą zgodne z istniejącymi wzorcami, takimi jak dwukrotne kliknięcie, aby otworzyć edytor kodu lub karty w oknie dokumentu umożliwiające interakcję z obu okienek.

- Dodawanie elementów do powierzchni projektowej powinno odbywać się za pośrednictwem przybornika, chyba że wymagane jest wysoce szczegółowe okno narzędzi.

- Elementy na powierzchni będą zgodne ze spójnym modelem wyboru.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, a nie typowe polecenia, takie jak **Zapisz**.

#### <a name="dialog-style-editors"></a>Edytory w stylu okna dialogowego

- Układ kontrolek powinien być zgodne z normalnymi konwencjami układu okna dialogowego.

- Karty w edytorze nie powinny odpowiadać wyglądowi kart dokumentów. Powinny one być zgodne z jednym z dwóch dozwolonych stylów wewnętrznych kart.

- Użytkownicy muszą mieć możliwość interakcji z kontrolkami tylko przy użyciu klawiatury; aktywując edytor i tabulatory za pomocą kontrolek lub używając standardowych mnemonik.

- Projektant powinien używać typowego modelu Zapisz. Na powierzchni nie powinny być umieszczane żadne ogólne przyciski Zapisz lub Zat zatwierdzanie, chociaż inne przyciski mogą być odpowiednie.

#### <a name="model-designers"></a>Projektanci modeli

- Pusty projektant powinien mieć na powierzchni znak wodny wskazujący, jak rozpocząć pracę.

- Dodawanie elementów do powierzchni projektowej powinno odbywać się za pośrednictwem przybornika.

- Elementy na powierzchni będą zgodne ze spójnym modelem wyboru.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, a nie typowe polecenia, takie jak **Zapisz**.

- Na powierzchni może pojawić się legenda z informacjami lub znakiem wodny.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek/kolorów przy użyciu strony Opcje narzędzi **>,** udostępnionej strony Czcionki i kolory lub strony specyficznej dla edytora.

#### <a name="reports"></a>Raporty

- Raporty są zwykle tylko informacjami i nie uczestniczą w zapisywanych modelach. Mogą one jednak obejmować interakcje, takie jak linki do innych istotnych informacji lub sekcji, które rozwijają się i zwijają.

- Większość poleceń na powierzchni powinna być hiperlinkami, a nie przyciskami.

- Układ powinien zawierać nagłówek i być zgodne ze standardowymi wytycznymi dotyczącymi układu raportu.

#### <a name="dashboards"></a>Pulpity nawigacyjne

- Pulpity nawigacyjne nie mają modelu interakcji, ale służą jako środek do zaoferowania różnych innych narzędzi.

- Nie uczestniczą w zapisywanych modelach.

- Użytkownicy muszą mieć możliwość interakcji z kontrolkami tylko przy użyciu klawiatury, aktywując edytor i tabulatory za pomocą kontrolek lub używając standardowych mnemonik.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Okien dialogowych

### <a name="introduction"></a>Wprowadzenie
Okna dialogowe Visual Studio zwykle obsługiwać jedną odrębną jednostkę pracy użytkownika, a następnie zostać odrzucone.

Jeśli określono, że potrzebujesz okna dialogowego, masz trzy opcje w kolejności preferencji:

1. Integruj funkcje w jednym z udostępnionych okien dialogowych w Visual Studio.

2. Utwórz własne okno dialogowe przy użyciu wzorca znalezionego w istniejącym podobnym oknie dialogowym.

3. Utwórz nowe okno dialogowe zgodnie z wytycznymi dotyczącymi interakcji i układu.

W tej sekcji opisano sposób wyboru poprawnego wzorca okna dialogowego w Visual Studio przepływów pracy i typowe konwencje dotyczące projektowania okien dialogowych.

### <a name="themes"></a>Motywy
Okna dialogowe w Visual Studio są zgodne z jednym z dwóch podstawowych stylów:

#### <a name="standard-unthemed"></a>Standardowa (bez omięć)
Większość okien dialogowych to standardowe okna dialogowe narzędzi, które powinny być niezauważone. Nie należy ponownie szablonować typowych kontrolek ani próbować tworzyć stylizowanych "nowoczesnych" przycisków lub kontrolek. Kontrolki i wygląd chrome są zgodne ze [standardowymi wytycznymi dotyczącymi](/windows/desktop/uxguide/win-dialog-box)interakcji z pulpitem systemu Windows dla okien dialogowych .

#### <a name="themed"></a>Tematyczne
Specjalne okna dialogowe "podpisu" mogą mieć temat. Okna dialogowe z tematami mają odrębny wygląd, który również ma pewne specjalne wzorce interakcji skojarzone ze stylem. Motywowanie okna dialogowego tylko wtedy, gdy spełnia następujące wymagania:

- Okno dialogowe to typowe środowisko, które będzie często lub często używane przez wielu użytkowników (na przykład okno **dialogowe Nowy** projekt.

- Okno dialogowe zawiera ważne elementy marki produktu (na przykład **okno dialogowe Ustawienia** konta).

- Okno dialogowe jest wyświetlane jako integralna część większego przepływu, który zawiera inne okna dialogowe z tematami (na przykład okno dialogowe Dodawanie usługi **połączonej).**

- Okno dialogowe jest ważną częścią doświadczenia, które odgrywa strategiczną rolę w podsycaniu lub rozróżnić wersję produktu.

Podczas tworzenia okna dialogowego z tematami użyj odpowiednich kolorów środowiska i postępuj zgodnie z prawidłowymi wzorcami układu i interakcji. (Zobacz [Układ dla Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)).

### <a name="dialog-design"></a>Projekt okna dialogowego
Dobrze zaprojektowane okna dialogowe biorą pod uwagę następujące elementy:

- Obsługiwane zadanie użytkownika

- Styl, język i terminologia tekstu okna dialogowego

- Kontrola wyboru i konwencje interfejsu użytkownika

- Specyfikacja układu wizualizacji i wyrównanie kontrolki

- Dostęp za pomocą klawiatury

#### <a name="content-organization"></a>Organizacja zawartości
Weź pod uwagę różnice między tymi podstawowymi typami okien dialogowych:

- [Proste okna dialogowe prezentują](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) kontrolki w jednym oknie modalnego. Prezentacja może zawierać odmiany złożonych wzorców kontrolek, w tym s wyboru pola lub paska ikon.

- [Warstwy okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) są używane do jak największego korzystania z powierzchni ekranu, gdy pojedynczy element interfejsu użytkownika składa się z wielu grup kontrolek. Grupowania w oknie dialogowym są "warstwowe" za pomocą kontrolek kart, kontrolek listy nawigacji lub przycisków, dzięki czemu użytkownik może wybrać grupowanie do zobaczenia w dowolnym momencie.

- [Kreatory](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) są przydatne do kierowania użytkownika przez logiczną sekwencję kroków w kierunku ukończenia zadania. W panelach sekwencyjnych oferowanych jest szereg opcji, które czasami wprowadzają różne przepływy pracy ("gałęzie") w zależności od wyboru dokonanego w poprzednim panelu.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Proste okna dialogowe
Proste okno dialogowe to prezentacja kontrolek w jednym oknie modalnego. Ta prezentacja może zawierać odmiany złożonych wzorców kontrolek, takich jak s wyboru pól. W przypadku prostych okien dialogowych należy przestrzegać standardowego układu ogólnego, a także dowolnego określonego układu wymaganego dla złożonych grup kontrolek.

![>Tworzenie klucza silnej nazwy jest przykładem prostego okna dialogowego w Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Tworzenie klucza silnej nazwy jest przykładem prostego okna dialogowego w Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Okna dialogowe warstwowe
Okna dialogowe warstwowe obejmują karty, pulpity nawigacyjne i osadzone drzewa. Są one używane do maksymalizowania nieruchomości, gdy w jednym interfejsie użytkownika jest oferowanych wiele grup kontrolek. Grupowania są warstwowe, dzięki czemu użytkownik może wybrać grupowanie do zobaczenia w dowolnym momencie.

W najprostszym przypadku mechanizmem przełączania się między grupowaniami jest kontrolka karty. Dostępnych jest kilka alternatyw. Zobacz Określanie priorytetów i warstw, aby dowiedzieć się, jak wybrać najbardziej odpowiedni styl.

Okno **dialogowe &gt; Opcje narzędzi** jest przykładem okna dialogowego warstwowego z osadzonym drzewem:

![Narzędzia > Opcje to przykład warstwowego okna dialogowego w Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Narzędzia > Opcje to przykład warstwowego okna dialogowego w Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Kreatorów
Kreatory są przydatne do kierowania użytkownika przez logiczną sekwencję kroków w ukończeniu zadania. Szereg opcji jest oferowanych w panelach sekwencyjnych, a użytkownik musi przejść przez każdy krok przed kontynuowaniem do następnego. Gdy są dostępne wystarczające wartości domyślne, przycisk **Zakończ** jest włączony.

 Kreatory modalne są używane do zadań, które:

- Zawierają rozgałęzienia, w których są oferowane różne ścieżki w zależności od wyborów użytkownika

- Zawiera zależności między krokami, gdzie kolejne kroki zależą od danych wejściowych użytkownika z poprzednich kroków

- Są wystarczająco złożone, aby interfejs użytkownika był używany do wyjaśnienia oferowanych opcji i możliwych wyników w każdym kroku

- Są transakcyjne i wymagają, aby zestaw czynności został ukończony w całości, zanim zostaną zatwierdzone jakiekolwiek zmiany

### <a name="common-conventions"></a>Typowe konwencje
Aby uzyskać optymalny projekt i funkcjonalność okien dialogowych, postępuj zgodnie z tymi konwencjami dotyczącymi rozmiaru okna dialogowego, położenia, standardów, konfiguracji i wyrównania kontrolek, tekstu interfejsu użytkownika, pasków tytułu, przycisków sterowania i kluczy dostępu.

Aby uzyskać wskazówki dotyczące układu, zobacz [Układ dla Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Rozmiar
Okna dialogowe powinny mieścić się w rozdzielczości co najmniej 1024 x 768 pikseli, a początkowy rozmiar okna dialogowego nie powinien przekraczać 900 x 700 pikseli. Okna dialogowe mogą być zmieniane, ale nie jest to wymagane.

Istnieją dwa zalecenia dotyczące okien dialogowych o zmienianym rozmiaru:

1. Minimalny rozmiar jest zdefiniowany dla okna dialogowego, które zostanie zoptymalizowane pod kątem zestawu kontrolek bez przycinania i dostosowane do odpowiedniego wzrostu lokalizacji.

2. Rozmiar skalowany przez użytkownika będzie się powtarzać z sesji na sesję. Jeśli na przykład użytkownik skaluje okno dialogowe do 150%, kolejne uruchomienie okna dialogowego będzie wyświetlane w 150%.

#### <a name="position"></a>Położenie
Przy pierwszym uruchomieniu okna dialogowe muszą być wyśrodkowane w obrębie środowiska IDE. Nie trzeba utrwalać ostatniej pozycji okien dialogowych, których nie można zmieniać, więc będą one wyświetlane wyśrodkowanie przy kolejnych startach.

W przypadku okien dialogowych, które można zmieniać, rozmiar powinien być utrwalany przy kolejnych startach. W przypadku modalnych okien dialogowych, które można zmieniać, pozycja nie musi być utrwalana. Ich wyśrodkowanie w idee zapobiega sytuacji, w których okno dialogowe jest wyświetlane w nieprzewidywalnej lub nienadajnej sytuacji, gdy konfiguracja wyświetlania użytkownika została zmieniona.

W przypadku nie moderowanych okien dialogowych, które można zmienić, pozycja użytkownika powinna być zachowywana przy kolejnych uruchomieniach, ponieważ okno dialogowe może być często używane jako integralna część większego przepływu pracy.

Gdy okna dialogowe muszą dużeć inne okna dialogowe, najwyższe okno dialogowe powinno być kaskadowo po prawej stronie i w dół od elementu nadrzędnego, aby dla użytkownika było oczywiste, że użytkownik nawigował do nowego miejsca.

#### <a name="modality"></a>Modalności
Tryb oznacza, że użytkownicy muszą ukończyć lub anulować okno dialogowe przed kontynuowaniem. Ponieważ modalne okna dialogowe blokują interakcję użytkownika z innymi częściami środowiska, przepływ zadań funkcji powinien używać ich tak oszczędnie, jak to możliwe. Gdy operacja modalna jest konieczna, Visual Studio ma wiele udostępnionych okien dialogowych, z których można zintegrować funkcje. Jeśli musisz utworzyć nowe okno dialogowe, postępuj zgodnie ze wzorcem interakcji istniejącego okna dialogowego o podobnej funkcjonalności.

Gdy podczas pisania nowego kodu  użytkownicy  muszą wykonywać dwa działania naraz, takie jak Znajdź i Zamień, okno dialogowe powinno być nie moderowe, aby użytkownik może łatwo się między nimi przełączać. Visual Studio używa okien narzędzi do tego rodzaju zadania połączonego z obsługą edytora.

#### <a name="control-configuration"></a>Konfiguracja kontrolki
Należy zapewnić spójność z istniejącymi konfiguracjami kontrolek, które osiągną ten sam Visual Studio.

#### <a name="title-bars"></a>Paski tytułu

- Tekst na pasku tytułu musi odzwierciedlać nazwę polecenia, które go uruchomiło.

- Na paski tytułu okna dialogowego nie należy używać żadnej ikony. W przypadkach, gdy system go wymaga, użyj Visual Studio logo.

- Okna dialogowe nie powinny mieć przycisków minimalizowania ani maksymalizowania.

- Przyciski Pomocy na pasku tytułu zostały wycofane. Nie należy dodawać ich do nowych okien dialogowych. Gdy już istnieją, powinni uruchomić temat pomocy, który jest koncepcyjnie istotny dla zadania.

  ![Specyfikacje wytycznych dotyczące pasków tytułu w oknach Visual Studio dialogowych](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Specyfikacje wytycznych dotyczące pasków tytułu w oknach Visual Studio dialogowych

#### <a name="control-buttons"></a>Przyciski sterowania
Ogólnie rzecz biorąc, przyciski  **OK,** **Anuluj** i Pomoc powinny być ułożone w poziomie w prawym dolnym rogu okna dialogowego. Alternatywny pionowy stos jest dozwolony, jeśli w dolnej części okna dialogowego znajduje się kilka innych przycisków, które mogą pomylić wizualizację z przyciskami sterowania.

![Dopuszczalne konfiguracje przycisków sterowania w Visual Studio oknach dialogowych](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Dopuszczalne konfiguracje przycisków sterowania w Visual Studio oknach dialogowych

Okno dialogowe musi zawierać domyślny przycisk sterowania. Aby określić najlepsze polecenie do użycia jako domyślne, wybierz jedną z następujących opcji (wymienione w kolejności pierwszeństwa):

- Wybierz najbezpieczniejsze i najbezpieczniejsze polecenie jako domyślne. Oznacza to, że wybranie polecenia najprawdopodobniej zapobiegnie utracie danych i zapobiegnie niezamierzonemu dostępowi do systemu.

- Jeśli utrata danych i bezpieczeństwo nie są czynnikami, wybierz polecenie domyślne na podstawie wygody. Ustawienie najbardziej prawdopodobnego polecenia jako domyślnego usprawni przepływ pracy użytkownika, gdy okno dialogowe obsługuje częste lub powtarzalne zadania.

Unikaj wybierania akcji trwale destrukcyjnej dla polecenia domyślnego. Jeśli takie polecenie jest obecne, zamiast tego wybierz bezpieczniejsze polecenie jako domyślne.

#### <a name="access-keys"></a>Klawisze dostępu
Nie używaj kluczy dostępu dla przycisków **OK,** **Anuluj** **ani Pomocy.** Te przyciski są domyślnie mapowane na klawisze skrótów:

| Nazwa przycisku | Skrót klawiaturowy |
| --- | --- |
| OK | Enter |
| Anuluj | Esc |
| Help | F1 |

#### <a name="imagery"></a>Zdjęć
Używaj obrazów oszczędnie w oknach dialogowych. Nie używaj dużych ikon w oknach dialogowych tylko w celu wykorzystania miejsca. Obrazów należy używać tylko wtedy, gdy są one ważną częścią przekazywania komunikatu do użytkownika, na przykład ikon ostrzeżeń lub animacji stanu.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Określanie priorytetów i warstw

#### <a name="prioritizing-your-ui"></a>Określanie priorytetów interfejsu użytkownika
Może być konieczne wymuś pewne elementy interfejsu użytkownika na pierwszy plan i umieść bardziej zaawansowane zachowanie i opcje (w tym przesłanianie poleceń) w oknach dialogowych. Przywniosz na pierwszy plan często używane funkcje, robiąc miejsce na nie i przez ustawienie jej jako widocznej domyślnie w interfejsie użytkownika z etykietą tekstową, gdy zostanie wyświetlone okno dialogowe.

#### <a name="layering-your-ui"></a>Warstwowanie interfejsu użytkownika
Jeśli określono, że okno dialogowe jest niezbędne, ale powiązane funkcje, które chcesz przedstawić użytkownikowi, wykraczają poza to, co można wyświetlić w prostym oknie dialogowym, musisz utworzyć warstwę interfejsu użytkownika. Najczęściej używane metody Visual Studio to karty i holi lub pulpity nawigacyjne. W niektórych przypadkach regiony, które można rozwinąć i zwinąć, mogą być odpowiednie. Adaptacyjny interfejs użytkownika zazwyczaj nie jest zalecany w Visual Studio.

Istnieją zalety i wady różnych metod warstw interfejsu użytkownika za pomocą kontrolek podobnych do kart. Przejrzyj listę poniżej, aby upewnić się, że wybierasz technikę warstwową, która jest odpowiednia dla Twojej sytuacji.

##### <a name="tabbing"></a>Tabulatorem

| Mechanizm przełączania | Zalety i odpowiednie użycie | Wady i niewłaściwe użycie |
| --- | --- | --- |
| Tab, kontrolka | Logiczne grupowanie stron okna dialogowego w powiązane zestawy<br /><br />Przydatne w przypadku mniej niż pięciu (lub liczby kart, które mieszczą się w jednym wierszu w oknie dialogowym) stron powiązanych kontrolek w oknie dialogowym<br /><br />Etykiety kart muszą być krótkie: jeden lub dwa wyrazy, które mogą łatwo zidentyfikować zawartość<br /><br />Wspólny styl okna dialogowego systemu<br /><br />Przykład: **Eksplorator plików &gt; właściwości elementu** | Tworzenie opisowych krótkich etykiet może być trudne<br /><br />Zwykle nie skaluje ostatnich pięciu kart w jednym oknie dialogowym<br /><br />Nieodpowiednie, jeśli masz zbyt wiele kart dla jednego wiersza (użyj alternatywnej techniki warstw)<br /><br />Nie rozszerzalne |
| Nawigacja na pasku bocznym | Proste urządzenie przełączające, które może pomieścić więcej kategorii niż karty<br /><br />Płaska lista kategorii (bez hierarchii)<br /><br />Extensible<br /><br />Przykład: **Dostosowywanie... &gt; Dodaj polecenie** | Użycie przestrzeni poziomej nie jest dobrym rozwiązaniem, jeśli istnieje mniej niż trzy grupy<br /><br />Zadanie może być lepiej dopasowane do listy rozwijanej |
| Kontrolka drzewa | Zezwala na nieograniczoną liczbę kategorii<br /><br />Umożliwia grupowanie i/lub hierarchię kategorii<br /><br />Extensible<br /><br />Przykład: **Opcje &gt; narzędzi** | Silnie zagnieżdżone hierarchie mogą powodować nadmierne przewijanie w poziomie<br /><br />Visual Studio zbyt wiele widoków drzewa |
| Kreatora | Ułatwia ukończenie zadań przez prowadzenie użytkownika przez kroki sekwencyjne oparte na zadaniach: kreator reprezentuje zadanie wysokiego poziomu, a poszczególne grupy reprezentują podzadań wymagane do wykonania całego zadania<br /><br />Przydatne, gdy zadanie przekracza granice interfejsu użytkownika, tak jak wtedy, gdy użytkownik musiałby użyć wielu edytorów i okien narzędzi w celu ukończenia zadania<br /><br />Przydatne, gdy zadanie wymaga rozgałęzienia<br /><br />Przydatne, gdy zadanie zawiera zależności między krokami<br /><br />Przydatne, gdy w jednym oknie dialogowym można zaprezentować kilka podobnych zadań z jednym forkem decyzyjnym w celu zmniejszenia liczby różnych podobnych okien dialogowych | Nieodpowiednie dla każdego zadania, które nie wymaga sekwencyjnego przepływu pracy<br /><br />Użytkownicy mogą stać się przytłoczeni i pomyleni przez kreatora ze zbyt wieloma krokami<br /><br />Kreatorzy mają z założenia ograniczoną ilość dostępnego ekranu |

##### <a name="hallways-or-dashboards"></a>Sale lub pulpity nawigacyjne
Saly i pulpity nawigacyjne to okna dialogowe lub panele, które służą jako punkty uruchamiania do innych okien i okien dialogowych. Dobrze zaprojektowany "hol" natychmiast zapewnia dostęp tylko do najbardziej typowych opcji, poleceń i ustawień, dzięki czemu użytkownik może łatwo wykonywać typowe zadania. Podobnie jak w rzeczywistym holu zapewnia drzwi dostępu do pomieszczeń za nimi, w tym miejscu rzadziej używany interfejs użytkownika jest zbierany w oddzielnych "pomieszczeniach" (często innych oknach dialogowych) powiązanych funkcji, do których można uzyskać dostęp z głównego pokoju.

Alternatywnie interfejs użytkownika, który oferuje wszystkie dostępne funkcje w jednej kolekcji, zamiast refaktoryzacji rzadziej występujących funkcji w oddzielnych lokalizacjach jest po prostu pulpitem nawigacyjnym.

![Koncepcja hallwaya do uwsłaniania dodatkowego interfejsu użytkownika w programie Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Koncepcja hallwaya do uwsłaniania dodatkowego interfejsu użytkownika w programie Outlook

##### <a name="adaptive-ui"></a>Adaptacyjny interfejs użytkownika
Pokazywanie lub ukrywanie interfejsu użytkownika na podstawie użycia lub własnego doświadczenia użytkownika to inny sposób prezentowania niezbędnego interfejsu użytkownika przy ukrywaniu innych części. Nie jest to zalecane w Visual Studio, ponieważ algorytmy podejmowania decyzji o tym, kiedy pokazać lub ukryć interfejs użytkownika, mogą być trudne, a reguły zawsze będą nieprawidłowe w niektórych przypadkach.

## <a name="projects"></a><a name="BKMK_Projects"></a> Projektów

### <a name="projects-in-the-solution-explorer"></a>Projekty w Eksplorator rozwiązań
Większość projektów jest klasyfikowana jako projekty oparte na odwołaniach, oparte na katalogach lub mieszane. Wszystkie trzy typy projektów są obsługiwane jednocześnie w Eksplorator rozwiązań. W tym oknie znajduje się katalog główny środowiska użytkownika podczas pracy z projektami. Mimo że różne węzły projektu są projektami referencyjnymi, katalogami lub projektami w trybie mieszanym, istnieje wspólny wzorzec interakcji, który należy zastosować jako punkt początkowy przed rozbiciem na wzorce użytkownika specyficzne dla projektu.

Projekty powinny być zawsze:

- Obsługa możliwości dodawania folderów projektu w celu organizowania zawartości projektu

- Utrzymywanie spójnego modelu trwałości projektu

Projekty powinny również utrzymywać spójne modele interakcji dla:

- Usuwanie elementów projektu

- Zapisywanie dokumentów

- Edytowanie właściwości projektu

- Edytowanie projektu w widoku alternatywnym

- Operacje przeciągania i upuszczania

### <a name="drag-and-drop-interaction-model"></a>Model interakcji przeciągania i upuszczania
Projekty zwykle klasyfikują się jako oparte na odwołaniach (mogą utrwalać tylko odwołania do elementów projektu w magazynie), oparte na katalogach (mogą utrwalać tylko elementy projektu fizycznie przechowywane w hierarchii projektu) lub mieszane (mogą utrwalać odwołania lub elementy fizyczne). Ide uwzględnia wszystkie trzy typy projektów jednocześnie w Eksplorator rozwiązań **.**

Z perspektywy przeciągania i upuszczania następujące cechy powinny mieć zastosowanie do każdego typu projektu w **Eksplorator rozwiązań**:

- **Projekt oparty na odwołaniach:** Kluczowym punktem jest to, że projekt przeciąga odwołanie do elementu w magazynie. Gdy projekt oparty na odwołaniach działa jako źródło dla operacji przenoszenia, powinien usuwać tylko odwołanie do elementu z projektu. Element nie powinien być w rzeczywistości usunięty z dysku twardego. Gdy projekt oparty na odwołaniach działa jako element docelowy operacji przenoszenia (lub kopiowania), należy dodać odwołanie do oryginalnego elementu źródłowego bez tworzenia prywatnej kopii elementu.

- **Projekt oparty na katalogu:** Z punktu widzenia przeciągania i upuszczania projekt przeciąga element fizyczny, a nie odwołanie. Gdy projekt oparty na katalogu działa jako źródło dla operacji przenoszenia, powinien usuwać element fizyczny z dysku twardego, a także usuwać go z projektu. Gdy projekt oparty na katalogu działa jako element docelowy operacji przenoszenia (lub kopiowania), powinien wykonać kopię elementu źródłowego w swojej lokalizacji docelowej.

- **Projekt mieszany::** Z punktu widzenia przeciągania i upuszczania zachowanie tego typu projektu zależy od charakteru przeciąganego elementu (odwołania do elementu w magazynie lub samego elementu). Poprawne zachowanie odwołań i elementów fizycznych opisano powyżej.

Gdyby w pliku był tylko jeden typ projektu **Eksplorator rozwiązań**, operacje przeciągania i upuszczania byłyby proste. Ponieważ każdy system projektu ma możliwość definiowania własnego zachowania przeciągania i upuszczania, należy przestrzegać pewnych wytycznych (na podstawie zachowania przeciągania i upuszczania w systemie Eksplorator Windows), aby zapewnić przewidywalne środowisko użytkownika:

- Niezmodyfikowana operacja przeciągania w Eksplorator rozwiązań **(gdy** nie są wstrzymujące się klawisze Ctrl ani Shift) powinna spowodować operację przenoszenia.

- Operacja przeciągania na przesunięciach powinna również spowodować operację przenoszenia.

- Operacja przeciągania z naciśniętym klawiszem Ctrl powinna spowodować operację kopiowania.

- Systemy projektów opartych na odwołaniach i projektach mieszanych obsługują sposób dodawania linku (lub odwołania) do elementu źródłowego. Gdy te projekty są obiektem docelowym operacji przeciągania i upuszczania (gdy wciśnięty jest klawisz **Ctrl +Shift),** powinno to spowodować odwołanie do elementu dodawanego do projektu

Nie wszystkie operacje przeciągania i upuszczania są sensowne w przypadku kombinacji projektów opartych na odwołaniach, opartych na katalogach i mieszanych. W szczególności problematyczne jest udanie, że zezwala na operację przenoszenia między projektem źródłowym opartym na katalogu i projektem docelowym opartym na odwołaniach, ponieważ projekt źródłowy oparty na katalogu będzie musiał usunąć element źródłowy po zakończeniu przenoszenia. Następnie docelowy projekt oparty na odwołaniach będzie miał odwołanie do usuniętego elementu.

Mylące jest również udawanie, że zezwala na operację kopiowania między tymi typami projektów, ponieważ docelowy projekt oparty na odwołaniach nie powinien dawać niezależnej kopii elementu źródłowego. Podobnie przeciąganie Ctrl +Shift do projektu docelowego opartego na katalogu nie powinno być dozwolone, ponieważ projekt oparty na katalogu nie może utrwalić odwołań. W przypadkach, gdy operacja przeciągania i upuszczania nie jest obsługiwana, idee powinny nie zezwalać na upuszczanie i pokazywać użytkownikowi kursor bez upuszczania (pokazany w tabeli wskaźników poniżej).

Aby prawidłowo zaimplementować zachowanie przeciągania i upuszczania, projekt źródłowy przeciągania musi przekazać charakter do projektu docelowego. (Na przykład, czy jest on oparty na odwołaniach lub katalogach?) Te informacje są wskazywane przez format schowka, który jest oferowany przez źródło. Jako źródło operacji przeciągania (lub kopiowania schowka) projekt powinien oferować odpowiednio lub w zależności od tego, czy projekt jest oparty na odwołaniach, czy na `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` katalogach. Oba te formaty mają taką samą zawartość danych, co jest podobne do formatu systemu Windows z tą różnicą, że listy ciągów, zamiast nazw plików, są podwójnie zakończoną listą ciągów (zwracaną z lub zgodnie z `CF_HDROP` `NULL` `Projref` `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` potrzebami).

Jako element docelowy operacji upuszczania (lub wklejania schowka) projekt powinien akceptować zarówno opcje , jak i , chociaż dokładna obsługa operacji przeciągania i upuszczania różni się w zależności od charakteru projektu docelowego i projektu `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` źródłowego. Projekt źródłowy deklaruje swój charakter przez to, czy oferuje `CF_VSREFPROJECTITEMS` lub `CF_VSSTGPROJECTITEMS` . Cel dropu rozumie swój własny charakter i dlatego ma wystarczająco dużo informacji, aby podjąć decyzje dotyczące tego, czy należy wykonać przeniesienie, kopię lub link. Użytkownik modyfikuje również operację przeciągania i upuszczania, naciskając klawisze Ctrl, Shift lub Ctrl oraz Shift. Ważne jest, aby miejsce docelowe upuszczania prawidłowo wskazywało, która operacja zostanie wykonana z wyprzedzeniem w jej `DragEnter` metodach `DragOver` i . Projekt **Eksplorator rozwiązań** automatycznie wie, czy projekt źródłowy i projekt docelowy są tym samym projektem.

Przeciąganie elementów projektu między wystąpieniami Visual Studio (na przykład z jednego wystąpienia devenv.exe do innego) nie jest obsługiwane. Ta **Eksplorator rozwiązań** również bezpośrednio to wyłącza.

Użytkownik powinien zawsze mieć możliwość określenia wpływu operacji przeciągania i upuszczania, zaznaczając element, przeciągając go do lokalizacji docelowej i obserwując, który z następujących wskaźników myszy pojawia się przed usunięciem elementu:

| Wskaźnik myszy | Polecenie | Opis |
| :---: | --- | --- |
| ![Ikona myszy "brak upuszczania"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Brak spadku | Nie można usunąć elementu do określonej lokalizacji. |
| ![Ikona "kopiuj" myszy](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopiuj | Element zostanie skopiowany do lokalizacji docelowej. |
| ![Ikona "przenieś" myszy](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Move | Element zostanie przeniesiony do lokalizacji docelowej. |
| ![Ikona "Dodaj odwołanie" myszy](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Dodawanie odwołania | Odwołanie do wybranego elementu zostanie dodane do lokalizacji docelowej. |

#### <a name="reference-based-projects"></a>Projekty oparte na odwołaniach
 W poniższej tabeli podsumowano operacje przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane na podstawie charakteru elementu źródłowego i klawiszy modyfikujące naciśniętych dla projektów docelowych opartych na odwołaniach:

| Modyfikator | Kategoria | Element źródłowy: odwołanie/link | Element źródłowy: element fizyczny lub system plików ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Brak modyfikatora | Akcja | Move | Link |
| Brak modyfikatora | Cel | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Brak modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Zachowuje oryginalny element |
| Brak modyfikatora | Wynik | `DROPEFFECT_MOVE` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie |
| Shift + przeciąganie | Akcja | Move | Brak spadku |
| Shift + przeciąganie | Cel | Dodaje odwołanie do oryginalnego elementu | Brak spadku |
| Shift + przeciąganie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Brak spadku |
| Shift + przeciąganie | Wynik | `DROPEFFECT_MOVE` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie | Brak spadku |
| Ctrl+Przeciągnij | Akcja | Kopiuj | Brak spadku |
| Ctrl+Przeciągnij | Cel | Dodaje odwołanie do oryginalnego elementu | Brak spadku |
| Ctrl+Przeciągnij | Element źródłowy | Zachowuje odwołanie do oryginalnego elementu | Brak spadku |
| Ctrl+Przeciągnij | Wynik | `DROPEFFECT_COPY` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie | Brak spadku |
| Ctrl+Shift+Przeciągnij | Akcja | Link | Link |
| Ctrl+Shift+Przeciągnij | Cel | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Ctrl+Shift+Przeciągnij | Element źródłowy | Zachowuje odwołanie do oryginalnego elementu | Zachowuje oryginalny element |
| Ctrl+Shift+Przeciągnij | Wynik | `DROPEFFECT_LINK` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Shift+Przeciągnij | Uwaga | Takie samo jak zachowanie przeciągania i upuszczania dla skrótów w Eksplorator Windows. ||
| Wycinanie/wklejanie | Akcja | Move | Link |
| Wycinanie/wklejanie | Cel | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Wycinanie/wklejanie | Element źródłowy | Zachowuje odwołanie do oryginalnego elementu|Zachowuje oryginalny element |
| Wycinanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Kopiuj | Link |
| Kopiowanie/wklejanie | Element źródłowy | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Kopiowanie/wklejanie | Wynik | Zachowuje odwołanie do oryginalnego elementu | Zachowuje oryginalny element |
| Kopiowanie/wklejanie | Akcja | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |

#### <a name="directory-based-projects"></a>Projekty oparte na katalogach
W poniższej tabeli podsumowano operacje przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane na podstawie charakteru elementu źródłowego i naciśniętych klawiszy modyfikujące dla projektów docelowych opartych na katalogu:

| Modyfikator | Kategoria | Element źródłowy: odwołanie/link | Element źródłowy: element fizyczny lub system plików ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Brak modyfikatora | Akcja | Move | Move |
| Brak modyfikatora | Cel | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Brak modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa odwołanie do oryginalnego elementu |
| Shift + przeciąganie | Akcja | Move | Move |
| Shift + przeciąganie | Cel | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Shift + przeciąganie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Shift + przeciąganie | Wynik | `DROPEFFECT_MOVE` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_MOVE` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Przeciąganie | Akcja | Kopiuj | Kopiuj |
| Ctrl+Przeciąganie | Cel | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Ctrl+Przeciąganie | Element źródłowy | Zachowuje odwołanie do oryginalnego elementu | Zachowuje odwołanie do oryginalnego elementu |
| Ctrl+Przeciąganie | Wynik | `DROPEFFECT_COPY` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_COPY` element jest zwracany jako akcja z elementu , a element `::Drop` pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Shift+Przeciągnij | | Brak spadku | Brak spadku |
| Wycinanie/wklejanie | Akcja | Move | Move |
| Wycinanie/wklejanie | Cel | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wycinanie/wklejanie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wycinanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element został usunięty z oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Kopiuj | Kopiuj |
| Kopiowanie/wklejanie | Cel | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie/wklejanie | Element źródłowy | Zachowuje oryginalny element | Zachowuje oryginalny element |
| Kopiowanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie ins |

#### <a name="mixed-target-projects"></a>Mieszane projekty docelowe
W poniższej tabeli podsumowano operacje przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane na podstawie charakteru elementu źródłowego i klawiszy modyfikujące naciśniętych dla projektów mieszanych elementów docelowych:

| Modyfikator | Kategoria | Element źródłowy: odwołanie/link | Element źródłowy: element fizyczny lub system plików ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Brak modyfikatora | Akcja | Move | Move |
| Brak modyfikatora | Cel | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Brak modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa odwołanie do oryginalnego elementu |
| Brak modyfikatora | Wynik | `DROPEFFECT_ MOVE` element jest zwracany jako akcja z elementu `::Drop` , a element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE` jest zwracany jako akcja z , `::Drop` a element jest usuwany z oryginalnej lokalizacji w magazynie |
| Shift + przeciąganie | Akcja | Move | Move |
| Shift + przeciąganie | Cel | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Shift + przeciąganie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Shift + przeciąganie | Wynik | `DROPEFFECT_ MOVE` element jest zwracany jako akcja z elementu `::Drop` , a element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE` jest zwracany jako akcja z , `::Drop` a element jest usuwany z oryginalnej lokalizacji w magazynie |
| Ctrl+Przeciągnięcie | Akcja | Kopiuj | Kopiuj |
| Ctrl+Przeciągnięcie | Cel | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Ctrl+Przeciągnięcie | Element źródłowy | Zachowuje odwołanie do oryginalnego elementu | Zachowuje oryginalny element |
| Ctrl+Przeciągnięcie | Wynik | `DROPEFFECT_ COPY` element jest zwracany jako akcja z elementu `::Drop` , a element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ COPY` element jest zwracany jako akcja z elementu `::Drop` , a element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Shift+Przeciąganie | Akcja | Link | Link |
| Ctrl+Shift+Przeciąganie | Cel | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu źródłowego |
| Ctrl+Shift+Przeciąganie | Element źródłowy | Zachowuje odwołanie do oryginalnego elementu | Zachowuje oryginalny element |
| Ctrl+Shift+Przeciąganie | Wynik | `DROPEFFECT_ LINK` element jest zwracany jako akcja z elementu `::Drop` , a element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ LINK` element jest zwracany jako akcja z elementu `::Drop` , a element pozostaje w oryginalnej lokalizacji w magazynie |
| Wycinanie/wklejanie | Akcja | Move | Move |
| Wycinanie/wklejanie | Cel | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wycinanie/wklejanie | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wycinanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element został usunięty z oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Kopiuj | Kopiuj |
| Kopiowanie/wklejanie | Cel | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie/wklejanie | Element źródłowy | Zachowuje oryginalny element | Zachowuje oryginalny element |
| Kopiowanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |

Te szczegóły należy wziąć pod uwagę podczas implementowania przeciągania w Eksplorator rozwiązań **:**

- Projektuj dla scenariuszy wielokrotnego wyboru.

- Nazwy plików (pełna ścieżka) muszą być unikatowe w projekcie docelowym. W przypadku tego typu upuszczanie nie powinno być dozwolone.

- Nazwy folderów muszą być unikatowe (bez uwzględniania liter) na poziomie, na którym są porzucane.

- Istnieją różnice zachowania między plikami, które są otwarte lub zamknięte podczas przeciągania (nie o których wspomniano w powyższych scenariuszach).

- Pliki najwyższego poziomu zachowują się nieco inaczej niż pliki w folderach.

Innym problemem, o który należy pamiętać, jest sposób obsługi operacji przenoszenia elementów, które mają otwartych projektantów lub edytorów. Oczekiwane zachowanie jest następujące (dotyczy wszystkich typów projektów):

1. Jeśli otwarty edytor/projektant nie ma żadnych niezapisanych zmian, okno edytora/projektanta powinno zostać zamknięte w trybie dyskretnym.

2. Jeśli otwarty edytor/projektant zawiera niezapisane zmiany, źródło przeciągania powinno czekać na upuszczenie, a następnie poprosić użytkownika o zapisanie niezatwierdzonych zmian w otwartych dokumentach przed zamknięciem okna z monitem podobnym do następującego:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Daje to użytkownikowi możliwość zapisania pracy w toku, zanim obiekt docelowy tworzy jego kopie. Dodano `IVsHierarchyDropDataSource2::OnBeforeDropNotify` nową metodę w celu włączenia tej obsługi.

Element docelowy skopiuje stan elementu w stanie, w którym znajduje się w magazynie (bez niezapisanych zmian w edytorze, jeśli użytkownik wybrał **pozycję Nie).** Po zakończeniu kopiowania obiektu docelowego (w pliku ) źródło ma możliwość ukończenia części usuwania operacji `IVsHierarchyDropDataSource::Drop` przenoszenia (w `IVsHierarchyDropDataSource::OnDropNotify` pliku ).

Wszystkie edytory z niezapisanych zmian powinny być otwarte. W przypadku dokumentów z niezapisanych zmian oznacza to, że część kopiowania operacji przenoszenia zostanie wykonana, ale część usuwania zostanie przerwana. W scenariuszu wielokrotnego wyboru, gdy użytkownik wybierze pozycję **Nie,** dokumenty z niezapisaną zmianą nie powinny być zamykane ani usuwane, ale dokumenty bez niezapisanych zmian powinny być zamykane i usuwane.
