---
title: Wzorce aplikacji dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 036c95951fe3dc9e65a0f3338f75ae9867d721c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698596"
---
# <a name="application-patterns-for-visual-studio"></a>Wzorce aplikacji dla programu Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interakcje między oknami

### <a name="overview"></a>Omówienie
Dwa główne typy okien używane w programie Visual Studio są edytorami dokumentów i oknami narzędzi. Rzadkie, ale możliwe, są duże niemodless okna dialogowe. Chociaż wszystkie te są niemodless w powłoce, ich wzory są zasadniczo różne. Ta sekcja obejmuje różnicę między oknami dokumentów, oknami narzędzi i niemodytowymi oknami dialogowymi. Wzorce modalnego okna dialogowego są opisane w [oknach dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porównywanie wzorców użycia okien
**Okna dokumentów** są prawie zawsze wyświetlane w dokumencie dobrze. Daje to edytorowi dokumentów "centralny etap", aby rozmieścić dodatkowe okna narzędzi wokół.

**Okno narzędzia** jest najczęściej wyświetlane jako oddzielne, mniejsze okno zwinięte względem krawędzi IDE. Może to być widoczne, ukryte lub automatycznie ukryte. Jednak czasami okna narzędzi są dobrze prezentowane w dokumencie, odznaczając właściwość **Window/Docking** w oknie. Powoduje to więcej nieruchomości, ale także wspólną decyzję projektową: podczas próby integracji z programem Visual Studio, należy zdecydować, czy funkcja powinna być wyświetlana okno narzędzia lub okno dokumentu.

**Niemodytne okna dialogowe** są odradzane w programie Visual Studio. Większość niemodytowanych okien dialogowych są, z definicji, pływające okna narzędzi i powinny być realizowane w ten sposób. Niemodowe okna dialogowe są dozwolone w przypadkach, gdy rozmiar normalnego okna narzędzia zadokowanego z boku powłoki byłby zbyt ograniczający. Są one również dozwolone w przypadkach, gdy użytkownik może przenieść okno dialogowe do monitora pomocniczego.

Zastanów się dokładnie, jakiego typu kontenera potrzebujesz. Typowe zagadnienia wzorca użycia dla projektu interfejsu użytkownika znajdują się w poniższej tabeli.

||Okno Dokumentu|Okno narzędzia|Okno dialogowe trybowe|
|-|---------------------|-----------------|---------------------|
| **Pozycji** | Zawsze dobrze umieszczony w dokumencie i nie zadokuje wokół krawędzi IDE. Można go "zdjąć", aby unosił się oddzielnie od głównej skorupy. | Zazwyczaj tabulator zadokowany wokół krawędzi IDE, ale można dostosować do przestawnych, automatycznie ukryte (nieprzypięte) lub zadokowany w dokumencie dobrze.|Duże okno przestawne oddzielone od IDE. |
| **Zatwierdź model** | *Opóźnione zatwierdzenie*<br /><br /> Aby zapisać dane w dokumencie, użytkownik musi wydać polecenie **Zapisz &gt; plik,** **Zapisz jako**lub Zapisz **wszystko.** Okno dokumentu ma pojęcie danych w nim jest "dirtied", a następnie zobowiązała się do jednego z poleceń zapisz. Podczas zamykania okna dokumentu cała zawartość jest zapisywana na dysku lub tracona. | *Natychmiastowe zatwierdzenie*<br /><br /> Nie ma modelu zapisu. W przypadku okien narzędzi inspektora, które pomagają w edytowaniu pliku, plik musi być otwarty w aktywnym edytorze lub projektancie, a edytor lub projektant jest właścicielem zapisu. | *Opóźnione lub natychmiastowe zatwierdzenie*<br /><br /> Najczęściej duże niemodowe okno dialogowe wymaga akcji w celu zatwierdzenia zmian i umożliwia operację "Anuluj", która wycofuje wszelkie zmiany wprowadzone w sesji okna dialogowego.  To odróżnia niemodytowe okno dialogowe od okna narzędzia w tym oknie narzędzia, które zawsze mają natychmiastowy model zatwierdzania. |
| **Widoczność** | *Otwieranie/tworzenie (plik) i zamykanie*<br /><br /> Otwieranie okien dokumentu odbywa się poprzez otwarcie istniejącego dokumentu lub użycie szablonu do utworzenia nowego dokumentu. Nie ma polecenia \<"Otwórz określony edytor>". | *Ukrywanie i pokazy*<br /><br /> Okna narzędzi pojedynczego wystąpienia mogą być ukryte lub wyświetlane. Zawartość i stany w oknie narzędzia utrzymują się w widoku lub ukryte. Okna narzędziowe wielu wystąpień mogą być zamknięte, a także ukryte. Po zamknięciu okna narzędzia wielu wystąpień zawartość i stan w oknie narzędzia są odrzucane. | *Uruchomiono z polecenia*<br /><br /> Okna dialogowe są uruchamiane z polecenia opartego na zadaniach. |
| **Wystąpienia** | *Wieloadłek*<br /><br /> Kilka edytorów może być otwieranych w tym samym czasie i edytować różne pliki, podczas gdy niektóre edytory zezwalają również na otwarcie tego samego pliku w więcej niż jednym edytorze (za pomocą polecenia **Okno &gt; nowe okno).**<br /><br /> Jeden edytor może edytować jeden lub wiele plików w tym samym czasie (Projektant projektu). | *Pojedyncze lub wielowydajne*<br /><br /> Zawartość zmienia się w celu odzwierciedlenia kontekstu (jak w przeglądarce właściwości) lub wypychania fokusu/kontekstu do innych okien (lista zadań, Eksplorator rozwiązań).<br /><br /> Okna narzędzi pojedynczego wystąpienia i wielu wystąpień powinny być skojarzone z aktywnym oknem dokumentu, chyba że istnieje przekonujący powód, aby tego nie robić. | *Pojedyncze wystąpienie* |
| **Przykłady** | **Edytory tekstu**, takie jak edytor kodu<br /><br /> **Projektowanie powierzchni**, takich jak projektant formularzy lub powierzchnia modelowania<br /><br /> **Układy formantów podobne do okien dialogowych,** takie jak Projektant manifestów | **Eksplorator rozwiązań** zapewnia rozwiązanie i projekty zawarte w rozwiązaniu<br /><br /> **Eksplorator serwerów** udostępnia hierarchiczny widok serwerów i połączeń danych, które użytkownik zdecyduje się otworzyć w oknie. Otwarcie obiektu z hierarchii bazy danych, takiego jak kwerenda, otwiera okno dokumentu i umożliwia użytkownikowi edytowanie kwerendy.<br /><br /> **Przeglądarka właściwości** wyświetla właściwości obiektu wybranego w oknie dokumentu lub w innym oknie narzędzia. Właściwości są prezentowane w hierarchicznym widoku siatki lub w złożonych formantach podobnych do okna dialogowego i umożliwiają użytkownikowi ustawienie wartości dla tych właściwości. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Okna narzędzi

### <a name="overview"></a>Omówienie
Okna narzędzi obsługują pracę użytkownika, która odbywa się w oknach dokumentów. Mogą one służyć do wyświetlania hierarchii, która reprezentuje podstawowy obiekt główny, który udostępnia program Visual Studio i może manipulować.

Rozważając nowe okno narzędzia w IDE, autorzy powinni:

- Użyj odpowiednich do zadań istniejących okien narzędzi, a nie tworzenia nowych z podobną funkcjonalnością. Nowe okna narzędzi powinny być tworzone tylko wtedy, gdy oferują znacznie różne "narzędzie" lub funkcje, których nie można zintegrować z podobnym oknem lub przekształcając istniejące okno w koncentrator przestawny.

- W razie potrzeby użyj standardowego paska poleceń w górnej części okna narzędzia.

- Bądź zgodny z wzorami już obecnymi w innych oknach narzędzi do sterowania prezentacją i nawigacją za pomocą klawiatury.

- Bądź zgodny z prezentacją sterowania w innych oknach narzędzi.

- W miarę możliwości automatyczne włączanie okien za pomocą narzędzia specyficznego dla dokumentu, tak aby były wyświetlane tylko wtedy, gdy dokument nadrzędny jest aktywowany.

- Upewnij się, że ich zawartość okna jest żeglowna za pomocą klawiatury (klawisze strzałek obsługuje).

#### <a name="tool-window-states"></a>Stany okna narzędzia
Okna narzędzi programu Visual Studio mają różne stany, z których niektóre są aktywowane przez użytkownika (jak funkcja automatycznego ukrywania). Inne stany, takie jak automatyczne widoczne, umożliwiają wyświetlanie okien narzędzi w odpowiednim kontekście i ukrywanie, gdy nie jest to potrzebne. W sumie istnieje pięć stanów okna narzędzia.

- **Zadokowane/przypięte** okna narzędzi można przymocować do dowolnej z czterech stron obszaru dokumentu. Ikona pinezki pojawi się na pasku tytułu okna narzędzia. Okno narzędzia może być zadokowane poziomo lub pionowo wzdłuż krawędzi powłoki i innych okien narzędzi, a także może być połączone z kartą.

- **Automatycznie ukryte** okna narzędzi są odpinane. Okno może wysunąć się poza zasięg wzroku, pozostawiając kartę (z nazwą okna narzędzia i jego ikoną) na krawędzi obszaru dokumentu. Okno narzędzia wysuwa się, gdy użytkownik najedzie kursorem na kartę.

- **Automatycznie widoczne** okna narzędzi są automatycznie wyświetlane po uruchomieniu innego elementu interfejsu użytkownika, takiego jak edytor, lub nabraniu fokusu.

- **Przestawne** okna narzędzia unoszące się poza IDE. Jest to przydatne w przypadku konfiguracji z wieloma monitorami.

- Okna narzędzi **dokumentów z kartami** mogą być dobrze zadokowane w dokumencie. Jest to przydatne w przypadku dużych okien narzędzi, takich jak przeglądarka obiektów, które potrzebują więcej nieruchomości niż dokowanie do krawędzi ramki pozwala.

![Stany okna narzędzia w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Stany okna narzędzia w programie Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Pojedyncze i wieloadłowe wystąpienie
Okna narzędzi są pojedynczym wystąpieniem lub wieloma wystąpieniami. Niektóre okna narzędzi pojedynczego wystąpienia mogą być skojarzone z aktywnym oknem dokumentu, podczas gdy okna narzędzi wielu wystąpień mogą nie. Okna narzędzi wielu wystąpień odpowiadają na polecenie **Okno &gt; Nowe okno,** tworząc nowe wystąpienie okna. Na poniższej ilustracji przedstawiono okno narzędzia włączające polecenie Nowe okno, gdy aktywne jest wystąpienie okna:

![Okno narzędzia włączające polecenie "Nowe okno", gdy aktywne jest wystąpienie okna](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Okno narzędzia włączające polecenie "Nowe okno", gdy aktywne jest wystąpienie okna

Okna narzędzi pojedynczego wystąpienia mogą być ukryte lub wyświetlane, podczas gdy okna narzędziowe wielu wystąpień mogą być zamknięte, a także ukryte. Wszystkie okna narzędzi mogą być zadokowane, połączone z kartami, przestawne lub ustawione jako okno podrzędne interfejsu wielu dokumentów (MDI) (podobne do okna dokumentu). Wszystkie okna narzędzi powinny odpowiadać na odpowiednie polecenia zarządzania oknami w menu Okno:

![Polecenia zarządzania oknami w menu Okna programu Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Polecenia zarządzania oknami w menu Okna programu Visual Studio

#### <a name="document-specific-tool-windows"></a>Okna narzędzi specyficznych dla dokumentu
Niektóre okna narzędzi są przeznaczone do zmiany na podstawie danego typu dokumentu. Te okna stale aktualizować, aby odzwierciedlić funkcje mające zastosowanie do aktywnego okna dokumentu w IDE.

Przykładami okien narzędzi, których zawartość zmienia się w celu odzwierciedlenia zaznaczonego edytora, są Przybornik i Konspekt dokumentu. Te okna pokazują znak wodny, gdy edytor ma fokus, który nie oferuje kontekstu do okna.

#### <a name="navigable-list-tool-windows"></a>Okna narzędzi listy żeglownej
W niektórych oknach narzędzi wyświetlana jest lista elementów żeglownych, z którymi użytkownik może wchodzić w interakcje. W tym oknie typu zawsze powinna być informacja zwrotna dla bieżącego elementu na liście, nawet jeśli okno jest nieaktywne. Lista powinna odpowiadać na polecenia **GoToNextLocation** i **GoToPrevLocation,** zmieniając również aktualnie zaznaczony element w oknie

Przykładami okien narzędzi listy żeglownej są Eksplorator rozwiązań i okno Znajdź wyniki.

### <a name="tool-window-types"></a>Typy okien narzędzi

#### <a name="common-tool-windows-and-their-functions"></a>Typowe okna narzędzi i ich funkcje

**Hierarchiczne okna narzędzi**

| Okno narzędzia | Funkcja |
| --- | --- |
| Eksplorator rozwiązań | Drzewo hierarchiczne, w które jest wyświetlana lista dokumentów zawartych w projektach, różnych plikach i elementach rozwiązania. Wyświetlanie elementów w projektach jest definiowane przez pakiet, który jest właścicielem typu projektu (na przykład typy oparte na odwołaniu, oparte na katalogu lub w trybie mieszanym). |
| Widok klas | Hierarchiczne drzewo klas i różnych elementów w zestawie roboczym dokumentów, niezależnie od samych plików. |
| Eksplorator serwera | Hierarchiczne drzewo, które wyświetla wszystkie serwery i połączenia danych w rozwiązaniu. |
| Konspekt dokumentu | Hierarchiczna struktura aktywnego dokumentu. |

**Okna narzędzi Siatki**

| Okno narzędzia | Funkcja |
| --- | --- |
| Właściwości | Siatka, która wyświetla listę właściwości dla wybranego obiektu, wraz z selektorami wartości do edycji tych właściwości. |
| Lista zadań | Siatka umożliwiająca użytkownikowi tworzenie/edytowanie/usuwanie zadań i komentarzy. |

**Okna narzędzi zawartości**

| Okno narzędzia | Funkcja |
| --- | --- |
| Pomoc | Okno, które umożliwia użytkownikom dostęp do różnych metod uzyskiwania pomocy, z "Jak ja?" na forach MSDN. |
| Pomoc dynamiczna | Okno narzędzia, w które są wyświetlane łącza ułatwiające tematy dotyczące bieżącego zaznaczenia. |
| Przeglądarka obiektów | Dwukolumnowy zestaw ramek z listą składników obiektów hierarchicznych w lewym okienku oraz właściwościami i metodami obiektu w prawej kolumnie. |

**Okna narzędzia okna dialogowego**

| Okno narzędzia | Funkcja |
| --- | --- |
| Znajdowanie | Okno dialogowe, które pozwala użytkownikowi znaleźć lub znaleźć i zastąpić w różnych plikach w ramach rozwiązania. |
| Szukanie zaawansowane | Okno dialogowe, które pozwala użytkownikowi znaleźć lub znaleźć i zastąpić w różnych plikach w ramach rozwiązania. |

**Inne okna narzędziowe**

::: moniker range="vs-2017"

| Okno narzędzia | Funkcja |
| --- | --- |
| Przybornik | Okno narzędzia używane do przechowywania elementów, które zostaną upuszczone na powierzchnie projektowe, zapewniając spójne źródło przeciągania dla wszystkich projektantów. |
| Strona początkowa | Portal użytkownika do programu Visual Studio z dostępem do kanałów informacyjnych dla deweloperów, pomocy programu Visual Studio i najnowszych projektów. Użytkownicy mogą również tworzyć niestandardowe strony początkowe, kopiując plik StartPage.xaml z katalogu "Common7\IDE\StartPages\" Visual Studio program files directory do folderu StartPages w katalogu dokumentów programu Visual Studio, a następnie edytując kod XAML ręcznie lub otwierając go w programie Visual Studio lub innym edytorze kodu. |

::: moniker-end

::: moniker range=">=vs-2019"

| Okno narzędzia | Funkcja |
| --- | --- |
| Przybornik | Okno narzędzia używane do przechowywania elementów, które zostaną upuszczone na powierzchnie projektowe, zapewniając spójne źródło przeciągania dla wszystkich projektantów. |

::: moniker-end

**Okna narzędzi Debugera**

| Okno narzędzia | Funkcja |
| --- | --- |
| Autos ||
| Natychmiastowe ||
| Dane wyjściowe | Okno danych wyjściowych może służyć zawsze, gdy masz zdarzenia tekstowe lub stan do zadeklarowania. |
| Memory (Pamięć) ||
| Punkty przerwania ||
| Działanie ||
| Dokumenty ||
| Stos połączeń ||
| Mieszkańców ||
| Zegarki ||
| Demontażu ||
| Rejestrów ||
| Wątki ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Konwencje edytora dokumentów

### <a name="document-interactions"></a>Interakcje dokumentów
"Dokument dobrze" jest największą przestrzenią w IDE i jest, gdzie użytkownik ogólnie koncentruje swoją uwagę w celu wykonania swoich zadań, wspomagane przez dodatkowe okna narzędzi. Edytory dokumentów reprezentują podstawowe jednostki pracy, które użytkownik otwiera i zapisuje w programie Visual Studio. Zachowują silne poczucie wyboru związane z Eksploratorem rozwiązań lub innymi aktywnymi oknami hierarchii. Użytkownik powinien mieć możliwość wskażenia jednego z tych okien hierarchii i wiedzieć, gdzie dokument jest zawarty i jego relacji do rozwiązania, projektu lub innego obiektu głównego dostarczonego przez pakiet programu Visual Studio.

Edycja dokumentów wymaga spójnego środowiska użytkownika. Aby umożliwić użytkownikowi skupienie się na wykonywanym zadaniu, a nie na zarządzaniu oknami i znajdowaniu poleceń, wybierz strategię widoku dokumentu, która najlepiej pasuje do zadań użytkownika do edycji tego typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Typowe interakcje dla dokumentu dobrze

- Utrzymuj spójny model interakcji we wspólnych środowiskach **Nowy plik** i **Otwórz plik.**

- Aktualizowanie funkcji powiązanych w powiązanych oknach i menu po otwarciu okna dokumentu.

- Polecenia menu są odpowiednio zintegrowane ze wspólnymi menu, takimi jak **Menu Edycja,** **Format**i **Widok.** Jeśli dostępna jest znaczna ilość wyspecjalizowanych poleceń, można utworzyć nowe menu. To nowe menu powinno być widoczne tylko wtedy, gdy dokument ma fokus.

- Osadzony pasek narzędzi może być umieszczony w górnej części edytora. Jest to preferowane przy posiadaniu oddzielnego paska narzędzi, który pojawia się poza edytorem.

- Zawsze należy zachować zaznaczenie w Eksploratorze rozwiązań lub podobnej aktywnej hierarchii okna.

- Dwukrotne kliknięcie dokumentu w Eksploratorze rozwiązań powinno wykonać tę samą akcję co **Otwórz**.

- Jeśli w typie dokumentu można użyć więcej niż jednego edytora, użytkownik powinien mieć możliwość zastąpienia lub zresetowania akcji domyślnej dla danego typu dokumentu za pomocą okna dialogowego **Otwórz z,** klikając prawym przyciskiem myszy plik i wybierając **polecenie Otwórz za pomocą** z menu skrótów.

- Nie buduj kreatora w dokumencie dobrze.

### <a name="user-expectations-for-specific-document-types"></a>Oczekiwania użytkowników dotyczące określonych typów dokumentów
Istnieje kilka różnych podstawowych typów edytorów dokumentów i każdy ma zestaw interakcji, które są zgodne z innymi tego samego typu.

- **Edytor tekstowy:** edytor kodu, pliki dziennika

- **Powierzchnia projektowa:** Projektant formularzy WPF, formularze systemu Windows

- **Edytor w stylu okna dialogowego:** Projektant manifestów, właściwości projektu

- **Projektant modelu:** projektant przepływu pracy, mapa kodu, diagram architektury, postęp

Istnieje również kilka typów innych niż edytor, które dobrze używają dokumentu. Chociaż nie edytują samych dokumentów, muszą przestrzegać standardowych interakcji dla okien dokumentów.

- **Raporty:** Raport IntelliTrace, raport Funkcji Hyper-V, raport profilera

- **Pulpit nawigacyjny:** Centrum diagnostyki

#### <a name="text-based-editors"></a>Edytory tekstowe

- Dokument uczestniczy w modelu karty podglądu, co pozwala na podgląd dokumentu bez otwierania go.

- Struktura dokumentu może być reprezentowana w oknie narzędzia towarzyszącego, takim jak konspekt dokumentu.

- IntelliSense (w razie potrzeby) będzie zachowywać się zgodnie z innymi edytorami kodu.

- Wyskakujące okienka lub pomocniczy interfejs użytkownika są zgodne z podobnymi stylami i wzorcami dla istniejącego podobnego interfejsu użytkownika, takiego jak CodeLens.

- Komunikaty dotyczące stanu dokumentu będą prezentowane w formancie paska informacyjnego u góry dokumentu lub na pasku stanu.

- Użytkownik musi mieć możliwość dostosowywania wyglądu czcionek i kolorów za pomocą strony **Narzędzia > Opcje,** udostępnionej strony Czcionki i kolory lub strony specyficznej dla edytora.

#### <a name="design-surfaces"></a>Powierzchnie projektowe

- Pusty projektant powinien mieć znak wodny na powierzchni wskazujący, jak rozpocząć pracę.

- Mechanizmy przełączania widoku będą zgodne z istniejącymi wzorcami, takimi jak dwukrotne kliknięcie, aby otworzyć edytor kodu lub karty w oknie dokumentu umożliwiające interakcję z obu okienek.

- Dodawanie elementów do powierzchni projektowej powinno odbywać się za pośrednictwem przybornika, chyba że wymagane jest bardzo specyficzne okno narzędzia.

- Elementy na powierzchni będą zgodne z modelem wyboru.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, a nie typowe polecenia, takie jak **Zapisz**.

#### <a name="dialog-style-editors"></a>Edytory w stylu okna dialogowego

- Układ sterowania powinien być zgodny z konwencjami układu normalnego okna dialogowego.

- Karty w edytorze nie powinny pasować do wyglądu kart dokumentu, powinny odpowiadać jednemu z dwóch dozwolonych stylów kart wewnętrznych.

- Użytkownicy muszą mieć możliwość interakcji z formantami tylko za pomocą klawiatury; albo poprzez aktywację edytora i tabulatorowanie przez sterowanie lub za pomocą standardowych mnemonics.

- Projektant powinien używać wspólnego modelu zapisywania. Na powierzchni nie należy umieszczać żadnych ogólnych przycisków Zapisywania lub zatwierdzania, chociaż inne przyciski mogą być odpowiednie.

#### <a name="model-designers"></a>Projektanci modeli

- Pusty projektant powinien mieć znak wodny na powierzchni wskazujący, jak rozpocząć pracę.

- Dodawanie elementów do powierzchni projektowej powinno odbywać się za pośrednictwem przybornika.

- Elementy na powierzchni będą zgodne z modelem wyboru.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, a nie typowe polecenia, takie jak **Zapisz**.

- Na powierzchni może pojawić się legenda, orientacyjna lub znak wodny.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek/kolorów za pomocą strony **Narzędzia > Opcje,** udostępnionej strony Czcionki i Kolory lub strony specyficznej dla edytora.

#### <a name="reports"></a>Raporty

- Raporty są zazwyczaj tylko informacje i nie uczestniczą w modelu Zapisz. Mogą one jednak obejmować interakcje, takie jak łącza do innych istotnych informacji lub sekcji, które rozwijają się i zwijają.

- Większość poleceń na powierzchni powinna być hiperłączami, a nie przyciskami.

- Układ powinien zawierać nagłówek i postępować zgodnie ze standardowymi wytycznymi dotyczącymi układu raportu.

#### <a name="dashboards"></a>Pulpity nawigacyjne

- Pulpity nawigacyjne nie mają modelu interakcji, ale służą jako sposób na oferowanie wielu innych narzędzi.

- Nie uczestniczą w modelu Zapisz.

- Użytkownicy muszą być w stanie wchodzić w interakcje z formantami tylko za pomocą klawiatury, albo poprzez aktywację edytora i tabulatorowanie przez kontrolki lub za pomocą standardowych mnemonics.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Okien dialogowych

### <a name="introduction"></a>Wprowadzenie
Okna dialogowe w programie Visual Studio zazwyczaj powinny obsługiwać jedną jednostkę dyskretną pracy użytkownika, a następnie zostać odrzucone.

Jeśli stwierdzisz, że potrzebujesz okna dialogowego, masz trzy opcje, w kolejności preferencji:

1. Zintegruj funkcje z jednym z udostępnionych okien dialogowych w programie Visual Studio.

2. Utwórz własne okno dialogowe przy użyciu wzorca znajdującego się w istniejącym podobnym oknie dialogowym.

3. Utwórz nowe okno dialogowe zgodnie z wytycznymi dotyczącymi interakcji i układu.

W tej sekcji opisano sposób wybierania prawidłowego wzorca okna dialogowego w przepływach pracy programu Visual Studio i typowych konwencji dotyczących projektowania okien dialogowych.

### <a name="themes"></a>Motywy
Okna dialogowe w programie Visual Studio są zgodne z jednym z dwóch podstawowych stylów:

#### <a name="standard-unthemed"></a>Standard (bez sytema)
Większość okien dialogowych są standardowe okna dialogowe narzędzia i powinny być unthemed. Nie należy ponownie szablonować wspólnych formantów ani próbować tworzyć stylizowanych "nowoczesnych" przycisków lub formantów. Formanty i wygląd chrome są zgodne [ze standardowymi wskazówkami dotyczącymi interakcji pulpitu systemu Windows dla okien dialogowych](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Tematyczne
Specjalne okna dialogowe "podpisu" mogą być tematyce. Tematyce dialogowe mają wyraźny wygląd, który ma również pewne specjalne wzorce interakcji związane ze stylem. Motyw okna dialogowego tylko wtedy, gdy spełnia następujące wymagania:

- Okno dialogowe jest typowym doświadczeniem, które będzie widoczne i używane często lub przez wielu użytkowników (na przykład okno dialogowe **Nowy projekt.**

- Okno dialogowe zawiera widoczne elementy marki produktu (na przykład okno dialogowe **Ustawienia konta).**

- Okno dialogowe jest wyświetlane jako integralna część większego przepływu, która zawiera inne okna dialogowe tematyce (na przykład okno dialogowe **Dodaj połączoną usługę).**

- Okno dialogowe jest ważną częścią doświadczenia, które odgrywa strategiczną rolę w promowaniu lub różnicowaniu wersji produktu.

Podczas tworzenia okna dialogowego tematycznym należy użyć odpowiednich kolorów środowiska i postępować zgodnie z prawidłowym układem i wzorcami interakcji. (Zobacz [Układ dla programu Visual Studio.)](../../extensibility/ux-guidelines/layout-for-visual-studio.md)

### <a name="dialog-design"></a>Projekt okna dialogowego
Dobrze zaprojektowane okna dialogowe uwzględniają następujące elementy:

- Obsługiwane zadanie użytkownika

- Styl tekstu okna dialogowego, język i terminologia

- Wybór sterowania i konwencje interfejsu użytkownika

- Wizualna specyfikacja układu i wyrównanie formantu

- Dostęp do klawiatury

#### <a name="content-organization"></a>Organizacja zawartości
Należy wziąć pod uwagę różnice między tymi podstawowymi typami okien dialogowych:

- [Proste okna dialogowe prezentują](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) formanty w jednym oknie modalnym. Prezentacja może zawierać odmiany złożonych wzorców sterowania, w tym selektor pól lub pasek ikon.

- [Wielowarstwowe okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) są używane w celu jak najlepiej wykorzystać nieruchomości ekranu, gdy pojedynczy element interfejsu użytkownika składa się z wielu grup formantów. Grupowania okna dialogowego są "warstwowe" za pomocą kontrolek kart, elementów sterujących list nawigacji lub przycisków, dzięki czemu użytkownik może wybrać grupowanie, które ma być widoczne w danym momencie.

- [Kreatory](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) są przydatne do kierowania użytkownika za pomocą logicznej sekwencji kroków w kierunku zakończenia zadania. Seria opcji jest oferowana w panelach sekwencyjnych, czasami wprowadzając różne przepływy pracy ("gałęzie") w zależności od wyboru dokonanego w poprzednim panelu.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Proste okna dialogowe
Proste okno dialogowe to prezentacja formantów w jednym oknie modalnym. Ta prezentacja może zawierać odmiany złożonych wzorców kontroli, takich jak selektor pól. W przypadku prostych okien dialogowych należy postępować zgodnie ze standardowym układem ogólnym, a także dla określonego układu wymaganego dla złożonych grup kontrolnych.

![>Create Strong Name Key jest przykładem prostego okna dialogowego w programie Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Utwórz klucz silnej nazwy jest przykładem prostego okna dialogowego w programie Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Okna dialogowe warstwowe
Okna dialogowe warstwowe obejmują karty, pulpity nawigacyjne i drzewa osadzone. Są one używane do maksymalizacji nieruchomości, gdy istnieje wiele grup kontroli oferowanych w jednym kawałku interfejsu użytkownika. Grupowania są warstwowe, dzięki czemu użytkownik może wybrać grupowanie, które ma być widoczne w dowolnym momencie.

W najprostszym przypadku mechanizm przełączania między grupowania jest formantem karty. Dostępnych jest kilka alternatyw. Zobacz Ustalanie priorytetów i nakładanie warstw, aby dowiedzieć się, jak wybrać najbardziej odpowiedni styl.

Okno dialogowe **Opcje narzędzi &gt; ** jest przykładem okna dialogowego warstwowego przy użyciu drzewa osadzonego:

![Narzędzia > Opcje jest przykładem okna dialogowego warstwowego w programie Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Narzędzia > Opcje jest przykładem okna dialogowego warstwowego w programie Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Kreatorów
Kreatory są przydatne do kierowania użytkownika za pomocą logicznej sekwencji kroków w zakończeniu zadania. Seria opcji są oferowane w panelach sekwencyjnych, a użytkownik musi kontynuować przez każdy krok przed przejściem do następnego. Po udostępnieniu wystarczającej liczby wartości domyślnych przycisk **Zakończ** jest włączony.

 Kreatorzy modalnej są używane do zadań, które:

- Zawierają rozgałęzienia, gdzie różne ścieżki są oferowane w zależności od wyboru użytkownika

- Zawierają zależności między krokami, w których kolejne kroki zależą od danych wejściowych użytkownika z poprzedniego kroku(-ów)

- Są wystarczająco złożone, aby interfejs użytkownika był wykorzystywany do wyjaśniania oferowanych wyborów i możliwych wyników na każdym etapie

- Są transakcyjne, wymagające wykonania zestawu kroków w całości przed zatwierdzeniem jakichkolwiek zmian

### <a name="common-conventions"></a>Wspólne konwencje
Aby osiągnąć optymalny projekt i funkcjonalność za pomocą okien dialogowych, postępuj zgodnie z tymi konwencjami dotyczącymi rozmiaru okna dialogowego, położenia, standardów, konfiguracji i wyrównania sterowania, tekstu interfejsu użytkownika, pasków tytułu, przycisków sterujących i klawiszy dostępu.

Aby zapoznać się z wytycznymi dotyczącymi układu, zobacz [Układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Rozmiar
Okna dialogowe powinny mieścić się w rozdzielczości co najmniej 1024x768, a początkowy rozmiar okna dialogowego nie powinien przekraczać 900x700 pikseli. Okna dialogowe mogą być o zmiennym rozmiarze, ale nie jest to wymagane.

Istnieją dwa zalecenia dotyczące okien dialogowych o zmiennym rozmiarze:

1. Że minimalny rozmiar jest zdefiniowany dla okna dialogowego, które będzie optymalizować dla zestawu formantów bez przycinania i dostosować, aby pomieścić rozsądny wzrost lokalizacji.

2. Że rozmiar skalowany przez użytkownika będzie się powtarzał od sesji do sesji. Na przykład jeśli użytkownik skaluje okno dialogowe do 150%, kolejne uruchomienie okna dialogowego będzie wyświetlane na poziomie 150%.

#### <a name="position"></a>Pozycja
Okna dialogowe muszą być wyświetlane wyśrodkowany w IDE przy pierwszym uruchomieniu. Nie trzeba zachowywać ostatniej pozycji okien dialogowych o braku wielkości, więc będą one wyświetlane w centrum kolejnych uruchomień.

W przypadku okien dialogowych o zmiennym rozmiarze rozmiar powinien być zachowywany podczas kolejnych uruchomień. W przypadku okien dialogowych modalnych o zmiennym rozmiarze pozycja nie musi być zachowywana. Wyświetlanie ich wyśrodkowany w IDE zapobiega możliwość okna dialogowego pojawiające się w nieprzewidywalnej lub bezużytecznej pozycji, gdy konfiguracja wyświetlania użytkownika została zmieniona.

W przypadku niemodytowanych okien dialogowych, które można zmienić, pozycja użytkownika powinna być zachowana przy kolejnych uruchomieniach, ponieważ okno dialogowe może być często używane jako integralna część większego przepływu pracy.

Gdy okna dialogowe muszą odradzać inne okna dialogowe, najwyższe okno dialogowe powinno kaskadowo w prawo i w dół od nadrzędnego, tak aby dla użytkownika było oczywiste, że nawigowali do nowego miejsca.

#### <a name="modality"></a>Modalności
Modalne oznacza, że użytkownicy są zobowiązani do ukończenia lub anulowania okna dialogowego przed kontynuowaniem. Ponieważ modalne okna dialogowe blokują użytkownikowi interakcję z innymi częściami środowiska, przepływ zadań funkcji powinien używać ich tak oszczędnie, jak to możliwe. Gdy operacja modalna jest konieczne, Visual Studio ma wiele udostępnionych okien dialogowych, które można zintegrować funkcje do. Jeśli musisz utworzyć nowe okno dialogowe, postępuj zgodnie ze wzorcem interakcji istniejącego okna dialogowego o podobnej funkcjonalności.

Gdy użytkownicy muszą wykonać dwa działania naraz, takie jak **Znajdź** i **Zamień** podczas pisania nowego kodu, okno dialogowe powinno być niemodne, dzięki czemu użytkownik może łatwo przełączać się między nimi. Visual Studio zazwyczaj używa okien narzędzi dla tego rodzaju edytora obsługi połączone zadanie.

#### <a name="control-configuration"></a>Konfiguracja sterowania
Być zgodne z istniejącymi konfiguracjami kontroli, które osiągalą to samo w programie Visual Studio.

#### <a name="title-bars"></a>Paski tytułu

- Tekst na pasku tytułu musi odzwierciedlać nazwę polecenia, które go uruchomiło.

- Na paskach tytułów okna dialogowego nie należy używać żadnej ikony. W przypadkach, gdy system wymaga jednego, należy użyć logo programu Visual Studio.

- Okna dialogowe nie powinny minimalizować ani maksymalizować przycisków.

- Przyciski pomocy na pasku tytułu zostały przestarzałe. Nie należy dodawać ich do nowych okien dialogowych. Gdy istnieją, należy uruchomić temat Pomocy, który jest koncepcyjnie istotne dla zadania.

  ![Specyfikacje wytycznych dla pasków tytułu w oknach dialogowych programu Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Specyfikacje wytycznych dla pasków tytułu w oknach dialogowych programu Visual Studio

#### <a name="control-buttons"></a>Przyciski sterujące
Ogólnie rzecz biorąc, **przyciski OK**, **Cancel**i **Help** powinny być rozmieszczone poziomo w prawym dolnym rogu okna dialogowego. Alternatywny stos pionowy jest dozwolony, jeśli okno dialogowe ma kilka innych przycisków w dolnej części okna dialogowego, które przedstawiałyby błąd wizualny z przyciskami sterującymi.

![Dopuszczalne konfiguracje przycisków sterowania w oknach dialogowych programu Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Dopuszczalne konfiguracje przycisków sterowania w oknach dialogowych programu Visual Studio

Okno dialogowe musi zawierać domyślny przycisk sterowania. Aby określić najlepsze polecenie do użycia jako domyślne, wybierz jedną z następujących opcji (wymienionych w kolejności pierwszeństwa):

- Wybierz najbezpieczniejszą i najbezpieczniejszą komendę jako domyślną. Oznacza to wybranie polecenia, które najprawdopodobniej zapobiegnie utracie danych i uniknie niezamierzonych dostępu do systemu.

- Jeśli utrata danych i zabezpieczenia nie są czynnikami, wybierz polecenie domyślne na podstawie wygody. Włączenie najbardziej prawdopodobnego polecenia jako domyślnego poprawi przepływ pracy użytkownika, gdy okno dialogowe obsługuje częste lub powtarzalne zadania.

Unikaj wybierania akcji trwale destrukcyjnej dla polecenia domyślnego. Jeśli takie polecenie jest obecne, wybierz polecenie bezpieczniejsze jako polecenie domyślne.

#### <a name="access-keys"></a>Klawisze dostępu
Nie używaj klawiszy dostępu do przycisków **OK,** **Anuluj**ani **Pomocy.** Te przyciski są domyślnie mapowane na klawisze skrótów:

| Nazwa przycisku | Skrót klawiaturowy |
| --- | --- |
| OK | Enter |
| Cancel | Esc |
| Pomoc | F1 |

#### <a name="imagery"></a>Zdjęć
Obrazy są używane oszczędnie w oknach dialogowych. Nie używaj dużych ikon w oknach dialogowych tylko do wykorzystania miejsca. Obrazy należy używać tylko wtedy, gdy są one ważną częścią przekazywania wiadomości do użytkownika, takie jak ikony ostrzegawcze lub animacje stanu.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Ustalanie priorytetów i nakładanie warstw

#### <a name="prioritizing-your-ui"></a>Nadawanie priorytetu interfejsowi użytkownika
Może być konieczne wprowadzenie niektórych elementów interfejsu użytkownika na czele i miejsce bardziej zaawansowane zachowanie i opcje (w tym niejasnych poleceń) w oknach dialogowych. Przenieś powszechnie używane funkcje na pierwszy plan, robiąc dla niej miejsce i czyniąc ją domyślnie widoczną w interfejsie użytkownika z etykietą tekstową, gdy jest wyświetlane okno dialogowe.

#### <a name="layering-your-ui"></a>Nakładanie warstw interfejsu użytkownika
Jeśli ustalono, że okno dialogowe jest konieczne, ale powiązane funkcje, które chcesz przedstawić użytkownikowi wykracza poza to, co może być wyświetlane w prostym oknie dialogowym, należy warstwy interfejsu użytkownika. Najbardziej typowe metody nakładania warstw używane przez program Visual Studio to karty i korytarze lub pulpity nawigacyjne. W niektórych przypadkach regiony, które można rozwinąć i zwinąć może być odpowiednie. Adaptacyjny interfejs użytkownika zazwyczaj nie jest zalecane w programie Visual Studio.

Istnieją zalety i wady różnych metod warstw interfejsu użytkownika za pomocą formantów podobnych do karty. Przejrzyj poniższą listę, aby upewnić się, że wybierasz technikę warstw, która jest odpowiednia do twojej sytuacji.

##### <a name="tabbing"></a>Tabulatorem

| Mechanizm przełączania | Zalety i odpowiednie wykorzystanie | Wady i niewłaściwe użytkowanie |
| --- | --- | --- |
| Kontrolka tabulatora | Logicznie grupowanie stron dialogowych w zestawy pokrewne<br /><br />Przydatne dla mniej niż pięciu (lub liczby kart, które mieszczą się w jednym wierszu w oknie dialogowym) stron powiązanych formantów w oknie dialogowym<br /><br />Etykiety kart muszą być krótkie: jedno lub dwa słowa, które mogą łatwo identyfikować zawartość<br /><br />Typowy styl okna dialogowego systemu<br /><br />Przykład: **Właściwości &gt; elementu Eksploratora plików** | Tworzenie opisowych krótkich etykiet może być trudne<br /><br />Ogólnie nie skaluje ostatnich pięciu kart w jednym oknie dialogowym<br /><br />Nieodpowiednie, jeśli masz zbyt wiele kart dla jednego wiersza (użyj alternatywnej techniki warstw)<br /><br />Nierozszełowe |
| Nawigacja po pasku bocznym | Proste urządzenie przełączające, które może pomieścić więcej kategorii niż kart<br /><br />Płaska lista kategorii (bez hierarchii)<br /><br />Extensible<br /><br />Przykład: **Dostosuj... Dodaj &gt; polecenie** | Nie jest to dobre wykorzystanie przestrzeni poziomej, jeśli istnieje mniej niż trzy grupy<br /><br />Zadanie może być lepiej dostosowane do listy rozwijanej |
| Sterowanie drzewem | Pozwala na nieograniczoną liczbę kategorii<br /><br />Umożliwia grupowanie i/lub hierarchię kategorii<br /><br />Extensible<br /><br />Przykład: ** &gt; Opcje narzędzi** | Mocno zagnieżdżone hierarchie mogą powodować nadmierne przewijanie w poziomie<br /><br />Program Visual Studio ma nadmiar widoków drzewa |
| Kreatora | Pomaga w wypełnianie zadań, prowadząc użytkownika przez kroki sekwencyjne oparte na zadaniach: kreator reprezentuje zadanie wysokiego poziomu, a poszczególne panele reprezentują podzadania potrzebne do wykonania ogólnego zadania<br /><br />Przydatne, gdy zadanie przekracza granice interfejsu użytkownika, jak wtedy, gdy użytkownik musiałby użyć wielu edytorów i okien narzędzi, aby wykonać zadanie<br /><br />Przydatne, gdy zadanie wymaga rozgałęzienia<br /><br />Przydatne, gdy zadanie zawiera zależności między krokami<br /><br />Przydatne, gdy kilka podobnych zadań z jednym rozwidlikiem decyzyjnym można przedstawić w jednym oknie dialogowym, aby zmniejszyć liczbę różnych podobnych okien dialogowych | Nieodpowiednie dla każdego zadania, które nie wymaga sekwencyjnego przepływu pracy<br /><br />Użytkownicy mogą stać się przytłoczeni i zdezorientowani przez kreatora ze zbyt wieloma krokami<br /><br />Czarodzieje mają z natury ograniczony ekran nieruchomości |

##### <a name="hallways-or-dashboards"></a>Korytarze lub pulpity rozdzielcze
Korytarze i pulpity nawigacyjne to okna dialogowe lub panele, które służą jako punkty uruchamiania innych okien dialogowych i okien. Dobrze zaprojektowany "korytarz" natychmiast powierzchnie tylko najczęściej opcje, polecenia i ustawienia, dzięki czemu użytkownik łatwo wykonywać typowe zadania. Podobnie jak korytarz w świecie rzeczywistym zapewnia drzwi, aby uzyskać dostęp do pomieszczeń za nimi, tutaj mniej wspólny interfejs użytkownika jest zbierany w oddzielnych "pokojach" (często innych dialogach) o związanej z nimi funkcjonalności, do których można uzyskać dostęp z głównego korytarza.

Alternatywnie interfejsu użytkownika, który oferuje wszystkie dostępne funkcje w pojedynczej kolekcji, a nie refaktoryzacji mniej typowe funkcje do oddzielnych lokalizacji jest po prostu pulpit nawigacyjny.

![Koncepcja korytarza do ujawniania dodatkowego interfejsu użytkownika w programie Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Koncepcja korytarza do ujawniania dodatkowego interfejsu użytkownika w programie Outlook

##### <a name="adaptive-ui"></a>Adaptacyjny interfejs użytkownika
Pokazywanie lub ukrywanie interfejsu użytkownika na podstawie użycia lub samodzielnie zgłaszane doświadczenie użytkownika jest inny sposób prezentacji niezbędnego interfejsu użytkownika podczas ukrywania innych części. Nie jest to zalecane w programie Visual Studio, ponieważ algorytmy do podejmowania decyzji, kiedy pokazać lub ukryć interfejs użytkownika może być trudne, a reguły zawsze będą błędne dla niektórych zestaw przypadków.

## <a name="projects"></a><a name="BKMK_Projects"></a>Projektów

### <a name="projects-in-the-solution-explorer"></a>Projekty w Eksploratorze rozwiązań
Większość projektów jest klasyfikowana jako oparta na odwołaniach, oparta na katalogu lub mieszana. Wszystkie trzy typy projektów są obsługiwane jednocześnie w Eksploratorze rozwiązań. Katalog główny środowiska użytkownika w pracy z projektami odbywa się w tym oknie. Chociaż różne węzły projektu są projektami referencyjnymi, katalogowymi lub typumie tryb mieszany, istnieje wspólny wzorzec interakcji, który powinien zostać zastosowany jako punkt wyjścia przed rozbieżniem w wzorce użytkowników specyficznych dla projektu.

Projekty powinny zawsze:

- Obsługa możliwości dodawania folderów projektu w celu organizowania zawartości projektu

- Obsługa spójnego modelu trwałości projektu

Projekty powinny również utrzymywać spójne modele interakcji dla:

- Usuwanie elementów projektu

- Zapisywanie dokumentów

- Edycja właściwości projektu

- Edytowanie projektu w widoku alternatywnym

- Operacje przeciągania i upuszczania

### <a name="drag-and-drop-interaction-model"></a>Model interakcji przeciąganie i upuszczanie
Projekty zazwyczaj klasyfikują się jako oparte na odwołaniach (mogą być zachowywane tylko odwołania do elementów projektu w magazynie), oparte na katalogu (mogą być przechowywane tylko elementy projektu fizycznie przechowywane w hierarchii projektu) lub mieszane (mogą być zachowywane odwołania lub elementy fizyczne). IDE obsługuje wszystkie trzy typy projektów jednocześnie w ramach **Eksploratora rozwiązań.**

Z punktu widzenia przeciągania i upuszczania do każdego typu projektu w **Eksploratorze rozwiązań**należy zastosować następujące właściwości:

- **Projekt oparty na odniesieniach:** Kluczowym punktem jest to, że projekt przeciąga się wokół odwołania do elementu w magazynie. Gdy projekt oparty na odwołaniu działa jako źródło operacji przenoszenia, należy usunąć tylko odwołanie do elementu z projektu. Element nie powinien być faktycznie usuwany z dysku twardego. Gdy projekt oparty na odwołaniu działa jako obiekt docelowy dla operacji przenoszenia (lub kopiowania), należy dodać odwołanie do oryginalnego elementu źródłowego bez tworzenia prywatnej kopii elementu.

- **Projekt oparty na katalogu:** Z punktu widzenia przeciągania i upuszczania projekt przeciąga się wokół elementu fizycznego, a nie odniesienia. Gdy projekt oparty na katalogu działa jako źródło operacji przenoszenia, powinno skończyć się usunięciem elementu fizycznego z dysku twardego, a także usunięciem go z projektu. Gdy projekt oparty na katalogu działa jako obiekt docelowy dla operacji przenoszenia (lub kopiowania), należy wykonać kopię elementu źródłowego w lokalizacji docelowej.

- **Projekt o mieszanym celu:** Z punktu widzenia przeciągania i upuszczania zachowanie tego typu projektu opiera się na charakterze przeciąganego elementu (odwołanie do elementu w magazynie lub samego elementu). Prawidłowe zachowanie odwołań i elementów fizycznych są opisane powyżej.

Jeśli w **Eksploratorze rozwiązań**istnieje tylko jeden typ projektu, operacje przeciągania i upuszczania byłyby proste. Ponieważ każdy system projektu ma możliwość definiowania własnego zachowania przeciągania i upuszczania, należy przestrzegać pewnych wytycznych (opartych na zachowaniu przeciągania i upuszczania Eksploratora Windows), aby zapewnić przewidywalne środowisko użytkownika:

- Niezmodyfikowana operacja przeciągania w **Eksploratorze rozwiązań** (gdy klawisze Ctrl ani Shift nie są przytrzymywalone) powinna spowodować operację przenoszenia.

- Operacja przeciągnij z wciśniętym klawiszem Shift powinna również spowodować operację przenoszenia.

- Operacja przeciągania ctrl powinna spowodować operację kopiowania.

- Oparte na odniesieniach i mieszane systemy projektów obsługują pojęcie dodawania łącza (lub odwołania) do elementu źródłowego. Gdy te projekty są celem operacji przeciągania i upuszczania (gdy **ctrl + shift** jest przytrzymywany), powinno to spowodować odwołanie do elementu dodawany do projektu

Nie wszystkie operacje przeciągania i upuszczania są rozsądne w przypadku kombinacji projektów opartych na odwołaniach, opartych na katalogach i mieszanych. W szczególności jest problematyczne udawać, aby zezwolić na operację przenoszenia między projektem źródłowym opartym na katalogu i projekt docelowy oparty na odwołaniu, ponieważ projekt oparty na katalogu źródłowym będzie musiał usunąć element źródłowy po zakończeniu przenoszenia. Docelowy projekt oparty na odwołani będzie następnie kończy się odwołaniem do usuniętego elementu.

Jest również mylące udawać, aby zezwolić na operację kopiowania między tymi typami projektów, ponieważ docelowy projekt oparty na odwołaniu nie powinien tworzyć niezależną kopię elementu źródłowego. Podobnie ctrl + Shift przeciąganie do projektu docelowego opartego na katalogu nie powinno być dozwolone, ponieważ projekt oparty na katalogu nie może utrwalić odwołań. W przypadkach, gdy operacja przeciągania i upuszczania nie jest obsługiwana, IDE powinien nie zezwalać na upuszczenie i pokazać użytkownikowi kursor bez upuszczania (pokazany w poniższej tabeli wskaźników).

Aby prawidłowo zaimplementować zachowanie przeciągania i upuszczania, projekt źródłowy przeciągania musi komunikować swój charakter do projektu docelowego. (Na przykład, czy jest to odniesienie lub oparte na katalogu?) Te informacje są wskazywane przez format schowka, który jest oferowany przez źródło. Jako źródło operacji przeciągania (lub kopiowania schowka) projekt powinien oferować jedną `CF_VSREFPROJECTITEMS` lub `CF_VSSTGPROJECTITEMS` odpowiednio, w zależności od tego, czy projekt jest oparty na odwołaniu, czy na podstawie katalogu. Oba te formaty mają tę samą zawartość danych, która jest podobna do formatu `CF_HDROP` systemu Windows, z`NULL` tą różnicą, że listy ciągów, zamiast nazwy plików, są podwójnie zakończonym listą `Projref` ciągów (zwracanych z `IVsSolution::GetProjrefOfItem` lub `::GetProjrefOfProject` odpowiednio).

Jako cel operacji wklejania kropli (lub schowka) projekt powinien akceptować zarówno `CF_VSREFPROJECTITEMS` i `CF_VSSTGPROJECTITEMS`, chociaż dokładna obsługa operacji przeciągania i upuszczania różni się w zależności od charakteru projektu docelowego i projektu źródłowego. Projekt źródłowy deklaruje swój charakter `CF_VSREFPROJECTITEMS` poprzez `CF_VSSTGPROJECTITEMS`to, czy oferuje lub . Cel zrzutu rozumie swój własny charakter i w związku z tym ma wystarczającą ilość informacji, aby podjąć decyzje, czy należy wykonać ruch, kopię lub łącze. Użytkownik modyfikuje również, które operacji przeciągania i upuszczania powinny być wykonywane przez naciśnięcie klawiszy Ctrl, Shift lub zarówno Ctrl i Shift klawiszy. Ważne jest, aby cel upuszczania prawidłowo wskazał, która `DragEnter` operacja `DragOver` zostanie wykonana z wyprzedzeniem w jego i metodach. **Eksplorator rozwiązań** automatycznie wie, czy projekt źródłowy i projekt docelowy są tym samym projektem.

Przeciąganie elementów projektu przez wystąpienia programu Visual Studio (na przykład z jednego wystąpienia devenv.exe do innego) nie jest specjalnie obsługiwane. **Eksplorator rozwiązań** również bezpośrednio wyłącza to.

Użytkownik powinien zawsze być w stanie określić efekt operacji przeciągania i upuszczania, zaznaczając element, przeciągając go do lokalizacji docelowej i obserwując, które z następujących wskaźników myszy pojawia się przed upuszczeniem elementu:

| Wskaźnik myszy | Polecenie | Opis |
| :---: | --- | --- |
| ![Ikona myszy "bez upuszczania"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Bez kropli | Nie można upuścić elementu do określonej lokalizacji. |
| ![Ikona "kopiuj" myszy](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copy | Element zostanie skopiowany do lokalizacji docelowej. |
| ![Ikona "przenoszenia" myszy](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Move | Element zostanie przeniesiony do lokalizacji docelowej. |
| ![Ikona myszy "dodaj odwołanie"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Dodawanie odwołania | Odwołanie do wybranego elementu zostanie dodane do lokalizacji docelowej. |

#### <a name="reference-based-projects"></a>Projekty oparte na odniesieniach
 W poniższej tabeli podsumowano operacje przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane na podstawie charakteru elementu źródłowego i klawiszy modyfikatora wciśniętych dla projektów docelowych opartych na odwołaniach:

| Modyfikator | Kategoria | Element źródłowy: Odwołanie/Łącze | Element źródłowy: Element fizyczny lub system plików (`CF_HDROP`) |
| --- | --- | --- | --- |
| Brak modyfikatora | Akcja | Move | Link |
| Brak modyfikatora | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Brak modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Zachowuje oryginalny element |
| Brak modyfikatora | Wynik | `DROPEFFECT_MOVE`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie |
| Shift+Przeciągnij | Akcja | Move | Bez kropli |
| Shift+Przeciągnij | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Bez kropli |
| Shift+Przeciągnij | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Bez kropli |
| Shift+Przeciągnij | Wynik | `DROPEFFECT_MOVE`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | Bez kropli |
| Ctrl+Przeciąganie | Akcja | Copy | Bez kropli |
| Ctrl+Przeciąganie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Bez kropli |
| Ctrl+Przeciąganie | Element źródłowy | Zachowuje odwołanie do oryginalnego towaru | Bez kropli |
| Ctrl+Przeciąganie | Wynik | `DROPEFFECT_COPY`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | Bez kropli |
| Ctrl+Shift+Przeciągnij | Akcja | Link | Link |
| Ctrl+Shift+Przeciągnij | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Ctrl+Shift+Przeciągnij | Element źródłowy | Zachowuje odwołanie do oryginalnego towaru | Zachowuje oryginalny element |
| Ctrl+Shift+Przeciągnij | Wynik | `DROPEFFECT_LINK`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Shift+Przeciągnij | Uwaga | Tak samo jak zachowanie przeciągania i upuszczania skrótów w Eksploratorze Windows. ||
| Wytnij/Wklej | Akcja | Move | Link |
| Wytnij/Wklej | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Wytnij/Wklej | Element źródłowy | Zachowuje odwołanie do oryginalnego towaru|Zachowuje oryginalny element |
| Wytnij/Wklej | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Copy | Link |
| Kopiowanie/wklejanie | Element źródłowy | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu |
| Kopiowanie/wklejanie | Wynik | Zachowuje odwołanie do oryginalnego towaru | Zachowuje oryginalny element |
| Kopiowanie/wklejanie | Akcja | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |

#### <a name="directory-based-projects"></a>Projekty oparte na katalogu
W poniższej tabeli podsumowano operacje przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane na podstawie charakteru elementu źródłowego i klawiszy modyfikatorów wciśniętych dla projektów docelowych opartych na katalogu:

| Modyfikator | Kategoria | Element źródłowy: Odwołanie/Łącze | Element źródłowy: Element fizyczny lub system plików (`CF_HDROP`) |
|-----------------|----------| - | - |
| Brak modyfikatora | Akcja | Move | Move |
| Brak modyfikatora | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Brak modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa odwołanie do oryginalnego elementu |
| Shift+Przeciągnij | Akcja | Move | Move |
| Shift+Przeciągnij | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Shift+Przeciągnij | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Shift+Przeciągnij | Wynik | `DROPEFFECT_MOVE`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_MOVE`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Przeciąganie | Akcja | Copy | Copy |
| Ctrl+Przeciąganie | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Ctrl+Przeciąganie | Element źródłowy | Zachowuje odwołanie do oryginalnego towaru | Zachowuje odwołanie do oryginalnego towaru |
| Ctrl+Przeciąganie | Wynik | `DROPEFFECT_COPY`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_COPY`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Shift+Przeciągnij | | Bez kropli | Bez kropli |
| Wytnij/Wklej | Akcja | Move | Move |
| Wytnij/Wklej | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wytnij/Wklej | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wytnij/Wklej | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element jest usuwany z oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Copy | Copy |
| Kopiowanie/wklejanie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie/wklejanie | Element źródłowy | Zachowuje oryginalny element | Zachowuje oryginalny element |
| Kopiowanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji ins przechowywania |

#### <a name="mixed-target-projects"></a>Projekty o mieszanych celach
W poniższej tabeli podsumowano operacje przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane na podstawie charakteru elementu źródłowego i klawiszy modyfikatora wciśniętych dla projektów o mieszanym celu:

| Modyfikator | Kategoria | Element źródłowy: Odwołanie/Łącze | Element źródłowy: Element fizyczny lub system plików (`CF_HDROP`) |
| --- | --- | --- | --- |
| Brak modyfikatora | Akcja | Move | Move |
| Brak modyfikatora | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Brak modyfikatora | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa odwołanie do oryginalnego elementu |
| Brak modyfikatora | Wynik | `DROPEFFECT_ MOVE`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE`jest zwracany `::Drop` jako akcja z i element jest usuwany z oryginalnej lokalizacji w magazynie |
| Shift+Przeciągnij | Akcja | Move | Move |
| Shift+Przeciągnij | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Shift+Przeciągnij | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Shift+Przeciągnij | Wynik | `DROPEFFECT_ MOVE`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE`jest zwracany `::Drop` jako akcja z i element jest usuwany z oryginalnej lokalizacji w magazynie |
| Ctrl+Przeciąganie | Akcja | Copy | Copy |
| Ctrl+Przeciąganie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Ctrl+Przeciąganie | Element źródłowy | Zachowuje odwołanie do oryginalnego towaru | Zachowuje oryginalny element |
| Ctrl+Przeciąganie | Wynik | `DROPEFFECT_ COPY`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ COPY`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl+Shift+Przeciągnij | Akcja | Link | Link |
| Ctrl+Shift+Przeciągnij | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Dodaje odwołanie do oryginalnego elementu źródłowego |
| Ctrl+Shift+Przeciągnij | Element źródłowy | Zachowuje odwołanie do oryginalnego towaru | Zachowuje oryginalny element |
| Ctrl+Shift+Przeciągnij | Wynik | `DROPEFFECT_ LINK`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ LINK`jest zwracany `::Drop` jako akcja z i element pozostaje w oryginalnej lokalizacji w magazynie |
| Wytnij/Wklej | Akcja | Move | Move |
| Wytnij/Wklej | Środowisko docelowe | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wytnij/Wklej | Element źródłowy | Usuwa odwołanie do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wytnij/Wklej | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element jest usuwany z oryginalnej lokalizacji w magazynie |
| Kopiowanie/wklejanie | Akcja | Copy | Copy |
| Kopiowanie/wklejanie | Środowisko docelowe | Dodaje odwołanie do oryginalnego elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie/wklejanie | Element źródłowy | Zachowuje oryginalny element | Zachowuje oryginalny element |
| Kopiowanie/wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |

Te szczegóły powinny być brane pod uwagę podczas wdrażania przeciągania w **Eksploratorze rozwiązań:**

- Projektowanie dla wielu scenariuszy wyboru.

- Nazwy plików (pełna ścieżka) muszą być unikatowe w całym projekcie docelowym lub spadek nie powinien być dozwolony.

- Nazwy folderów muszą być unikatowe (bez uwzględniania wielkości liter) na poziomie, na jaki są usuwane.

- Istnieją różnice w zachowaniu między plikami, które są otwarte lub zamknięte w czasie przeciągania (nie wymienione w scenariuszach powyżej).

- Pliki najwyższego poziomu zachowują się nieco inaczej niż pliki w folderach.

Innym problemem, o którym należy pamiętać, jest sposób obsługi operacji przenoszenia elementów, które mają otwartych projektantów lub edytorów. Oczekiwane zachowanie jest następujące (dotyczy to wszystkich typów projektów):

1. Jeśli otwarty edytor/projektant nie ma żadnych niezapisanych zmian, okno edytora/projektanta powinno być dyskretnie zamknięte.

2. Jeśli otwarty edytor/projektant ma niezapisane zmiany, źródło przeciągania powinien czekać na spadek występuje, a następnie poprosić użytkownika, aby zapisać niezatwierdzone zmiany w otwartych dokumentach przed zamknięciem okna z monitem podobnym do następującego:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Daje to użytkownikowi możliwość zapisania pracy w toku, zanim obiekt docelowy utworzy jego kopie. Dodano nową `IVsHierarchyDropDataSource2::OnBeforeDropNotify` metodę, aby włączyć tę obsługę.

Obiekt docelowy skopiuje następnie stan elementu w magazynie (z wyłączeniem niezapisanych zmian w edytorze, jeśli użytkownik wybrał **no**). Po zakończeniu kopiowania obiektu docelowego (w) `IVsHierarchyDropDataSource::Drop`źródło ma możliwość ukończenia części operacji `IVsHierarchyDropDataSource::OnDropNotify`usuwania (w ).

Wszelkie edytory z niezapisanych zmian powinny pozostać otwarte. W przypadku tych dokumentów z niezapisanych zmian, oznacza to, że część kopiowania operacji przenoszenia zostanie wykonana, ale część usuwania zostanie przerwana. W scenariuszu wielokrotnego wyboru, gdy użytkownik wybierze **nie**, te dokumenty z niezapisanymi zmianami nie powinny być zamykane ani usuwane, ale te bez niezapisanych zmian powinny zostać zamknięte i usunięte.
