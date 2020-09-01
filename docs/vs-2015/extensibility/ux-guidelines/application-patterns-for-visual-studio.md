---
title: Wzorce aplikacji
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc14aadfafb16fcae571ab66e5811ea465cb55a9
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284419"
---
# <a name="application-patterns-for-visual-studio"></a>Wzorce aplikacji dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interakcje okna

### <a name="overview"></a>Omówienie
 Dwa typy główne okna używane w programie Visual Studio to edytory dokumentów i okna narzędzi. Rzadkimi, ale możliwymi, są duże Niemodalne okna dialogowe. Chociaż są one całkowicie niemodalne w powłoce, ich wzorce są zasadniczo różne. W tym temacie omówiono różnice między oknami dokumentów, narzędziami i niemodalnymi oknach dialogowych. Wzorce dialogu modalnego są omówione w [oknach dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porównywanie wzorców użycia okna
 **Okna dokumentów** są prawie zawsze wyświetlane w obszarze dokumentu. Dzięki temu Edytor dokumentów jest "etapem centrum", aby rozmieścić uzupełniające okna narzędzi.

 **Okno narzędzi** jest najczęściej wyświetlane jako oddzielne, mniejsze okno, które może być widoczne, ukryte lub autoukryte — zwinięte względem krawędzi IDE. Jednak czasami są one prezentowane w obszarze dokumentu, usuwając zaznaczenie **okna/dokowanie** właściwości w oknie. Powoduje to bardziej rzeczywistą widoczność, ale również wspólną decyzję projektową: przy próbie integracji z Visual Studio należy zdecydować, czy funkcja powinna wyświetlać okno narzędzi czy okno dokumentu.

 **Niemodalne okna dialogowe** nie są zachęcane w programie Visual Studio. W dużym stopniu są to przenoszone przez definicje okna narzędzi i powinny być zaimplementowane jako takie. Niemodalne okna dialogowe są dozwolone w przypadkach, gdy rozmiar okna standardowego narzędzia zadokowanego po stronie powłoki zostanie zbyt ograniczony. Są one również dozwolone w przypadkach, gdy użytkownik może przenieść okno dialogowe do monitora pomocniczego.

 Uważnie zapoznaj się z żądanym typem kontenera. Typowe zagadnienia dotyczące wzorców użycia dotyczące projektowania interfejsu użytkownika znajdują się w poniższej tabeli.

||Okno dokumentu|Okno narzędzia|Niemodalne okno dialogowe|
|-|---------------------|-----------------|---------------------|
|**Pozycja**|Zawsze umieszczaj w dokumencie i nie są zadokowane wokół krawędzi IDE. Może to być "ściągane", tak aby przepływał niezależnie od głównej powłoki.|Na ogół karta jest zadokowana wokół krawędzi IDE, ale można ją dostosować do wartości zmiennoprzecinkowych, autoukrytych (odpiętych) lub zadokowanych w obszarze dokumentu.|Duże przestawne okno oddzielone od IDE.|
|**Zatwierdź model**|*Opóźnione zatwierdzanie*<br /><br /> Aby zapisać dane w dokumencie, użytkownik musi wydać polecenie Zapisz plik, Zapisz jako lub Zapisz wszystkie. Okno dokumentu ma koncepcję danych w ramach elementu "'dirtied", następnie została zatwierdzona do jednego z poleceń zapisu. Po zamknięciu okna dokumentu cała zawartość jest zapisywana na dysku lub utracona.|*Natychmiastowe zatwierdzenie*<br /><br /> Nie istnieje model zapisywania. W przypadku okien narzędzi inspektora, które ułatwiają edytowanie pliku, plik musi być otwarty w aktywnym Edytorze lub projektancie, a Edytor lub Projektant jest właścicielem zapisywania.|*Opóźnione lub natychmiastowe zatwierdzenie*<br /><br /> Najczęściej niemodalne okno dialogowe wymaga działania w celu zatwierdzenia zmian i zezwala na operację "Anuluj", co spowoduje wycofanie wszelkich zmian wprowadzonych w sesji okna dialogowego.  To odróżnia niemodalne okno dialogowe z okna narzędzi w tym narzędziu, który zawsze ma bezpośredni model zatwierdzania.|
|**Widoczność**|*Otwórz/Utwórz (plik) i Zamknij*<br /><br /> Otwieranie okna dokumentu odbywa się za pośrednictwem otwierania istniejącego dokumentu lub przy użyciu szablonu, aby utworzyć nowy dokument. Brak polecenia "Otwórz \<specific editor> ".|*Ukryj i Pokaż*<br /><br /> Okna narzędzi z jednym wystąpieniem mogą być ukryte lub pokazywane. Zawartość i Stany w oknie narzędzi są utrwalane w widoku lub ukrytym. Okna narzędzi z wiele wystąpień można zamknąć, a także ukryć. Po zamknięciu okna narzędzia z obsługą wiele wystąpień zawartość i stan w oknie narzędzia są odrzucane.|*Uruchomiono za pomocą polecenia*<br /><br /> Okna dialogowe są uruchamiane przy użyciu polecenia opartego na zadaniach.|
|**Wystąpienia**|*Wiele wystąpień*<br /><br /> Kilka edytorów może być otwartych w tym samym czasie i edytować różne pliki, podczas gdy niektóre edytory umożliwiają również otwieranie tego samego pliku w więcej niż jednym edytorze (przy użyciu **okna > nowe okno** polecenia).<br /><br /> Jeden edytor może edytować jeden lub wiele plików jednocześnie (Projektant projektu).|*Pojedyncze lub wiele wystąpień*<br /><br /> Zawartość zmienia się w celu odzwierciedlenia kontekstu (jak w przeglądarce właściwości) lub wypychanie fokusu/kontekstu do innych okien (Lista zadań, Eksplorator rozwiązań).<br /><br /> Zarówno jedno wystąpienie, jak i wiele wystąpień systemu Windows powinno być skojarzone z oknem aktywnego dokumentu, chyba że istnieje uzasadniony powód, aby nie.|*Pojedyncze wystąpienie*|
|**Przykłady**|**Edytory tekstu**, takie jak edytor kodu<br /><br /> **Powierzchnie projektowe**, takie jak Projektant formularzy lub powierzchnia modelowania<br /><br /> **Układy formantów podobne do okien dialogowych**, takich jak projektant manifestu|**Eksplorator rozwiązań** zawiera rozwiązanie i projekty zawarte w rozwiązaniu<br /><br /> **Eksplorator serwera** zawiera hierarchiczny widok serwerów i połączeń danych, które użytkownik zdecyduje otworzyć w oknie. Otwierając obiekt z hierarchii bazy danych, na przykład zapytania, otwiera okno dokumentu i zezwala użytkownikowi na edytowanie zapytania.<br /><br /> **Przeglądarka właściwości** wyświetla właściwości obiektu wybranego w oknie dokumentu lub w innym oknie narzędzi. Właściwości są prezentowane w hierarchicznym widoku siatki lub w złożonych kontrolkach, takich jak kontrolki podobne do okna dialogowego i umożliwiają użytkownikowi ustawianie wartości tych właściwości.||

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Okna narzędzi

### <a name="overview"></a>Omówienie
 Okna narzędzi obsługują działania użytkownika, które są wykonywane w oknach dokumentów. Mogą one służyć do wyświetlania hierarchii reprezentującej podstawowy obiekt główny, który program Visual Studio udostępnia i może manipulować.

 Gdy rozważasz nowe okno narzędzi w IDE, autorzy powinni:

- Używaj istniejących okien narzędzi, które są odpowiednie dla zadań i nie twórz nowych przy użyciu podobnych funkcji. Nowe okna narzędzi należy tworzyć tylko wtedy, gdy oferują znacznie różne "Narzędzie" lub funkcje, których nie można zintegrować z podobnym oknem lub przez włączenie istniejącego okna do koncentratora przestawiania.

- W razie konieczności Użyj standardowego paska poleceń w górnej części okna narzędzi.

- Być spójne ze wzorcami już obecnymi w oknach narzędzi do sterowania prezentacją i nawigowaniem po klawiaturze.

- Być spójne z prezentacją kontrolną w innych oknach narzędzi.

- Okna narzędzi specyficzne dla dokumentu powinny być autowidoczne, gdy jest to możliwe, aby były widoczne tylko wtedy, gdy dokument nadrzędny jest aktywowany.

- Upewnij się, że zawartość okna jest wyświetlona przez klawiaturę (klawisze strzałek pomocy technicznej).

#### <a name="tool-window-states"></a>Stany okna narzędzi
 Okna narzędzi programu Visual Studio mają różne stany, a niektóre z nich są aktywowane przez użytkownika (takie jak funkcja Autoukrywanie). Inne Stany, takie jak autovisible, Zezwalaj na wyświetlanie okien narzędzi w prawidłowym kontekście i ukrywanie, gdy nie jest to konieczne. W sumie znajduje się pięć Stanów okna narzędzi.

- Okna narzędzi **zadokowanych/przypiętych** mogą być dołączone do dowolnych z czterech boków obszaru dokumentu. Ikona pinezki pojawia się na pasku tytułu okna narzędzi. Okno narzędzi może być zadokowane w poziomie lub w pionie wzdłuż krawędzi powłoki i innych okien narzędzi, a także może być połączone z kartami.

- Okna narzędzi **z autoukrywaniem** nie są przypięte. Okno może wysunąć wzrok, pozostawiając kartę (z nazwą okna narzędzia i jego ikoną) na krawędzi obszaru dokumentu. Okno narzędzia prowadzi do slajdu, gdy użytkownik umieści wskaźnik myszy na karcie.

- **Automatyczne widoczne** okna narzędzi automatycznie pojawiają się, gdy działa inny element interfejsu użytkownika, taki jak edytor, jest uruchamiany lub ma fokus.

- **Zmiennoprzecinkowe** okno narzędziowe Umieść kursor poza IDE. Jest to przydatne w przypadku konfiguracji z obsługą kilku monitorów.

- Okna narzędzi **dokumentu z kartami** mogą być zadokowane w obszarze dokumentu. Jest to przydatne w przypadku dużych okien narzędzi, takich jak Przeglądarka obiektów, które potrzebują bardziej rzeczywistej nieruchomości niż dokowanie do krawędzi ramki.

  ![Stany okna narzędzi w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702 — 01_ToolWindowStates")

  **Stany okna narzędzi w programie Visual Studio**

#### <a name="single-instance-and-multi-instance"></a>Pojedyncze wystąpienie i wiele wystąpień
 Okna narzędzi to pojedyncze wystąpienia lub wiele wystąpień. Niektóre okna narzędzi z jednym wystąpieniem mogą być skojarzone z oknem aktywnego dokumentu, natomiast okna narzędzi z obsługą wiele wystąpień mogą nie działać. Okna narzędzi z pojedynczym wystąpieniem odpowiadają na polecenie Window/New window, tworząc nowe wystąpienie okna. Na poniższej ilustracji przedstawiono okno narzędzi, w którym jest włączone nowe okno, gdy wystąpienie okna jest aktywne:

 ![Okno narzędziowe umożliwiające Włączanie poleceń w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702 — 02_ToolWindowEnablingCommand")

 **Okno narzędzia włączające polecenie "New window", gdy wystąpienie okna jest aktywne**

 Okna narzędzi z jednym wystąpieniem można ukrywać lub pokazywać, natomiast w przypadku okien narzędzi z obsługą wiele wystąpień można zamknąć, a także ukryć. Wszystkie okna narzędzi mogą być zadokowane, połączone z kartami, zmiennoprzecinkowe lub ustawione jako okno podrzędne interfejsu wielu dokumentów (MDI) (podobne do okna dokumentu). Wszystkie okna narzędzi powinny reagować na odpowiednie polecenia zarządzania oknami w menu okno:

 ![Polecenia zarządzania oknem w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702 — 03_WindowManagementControls")

 **Polecenia zarządzania oknem w menu okna programu Visual Studio**

#### <a name="document-specific-tool-windows"></a>Okna narzędzi specyficzne dla dokumentu
 Niektóre okna narzędzi są przeznaczone do zmiany w oparciu o dany typ dokumentu. Te okna są ciągle aktualizowane w celu odzwierciedlenia funkcji mających zastosowanie do okna aktywnego dokumentu w IDE.

 Przykłady okien narzędzi, których zawartość zmienia się w celu odzwierciedlenia wybranego edytora, to Przybornik i Konspekt dokumentu. Te okna pokazują znak wodny, gdy Edytor ma fokus, który nie oferuje kontekstu do okna.

#### <a name="navigable-list-tool-windows"></a>Okna narzędzi listy nawigacji
 Niektóre okna narzędzi wyświetlają listę elementów nawigacji, z którymi użytkownik może korzystać. W tym typie okna powinna być zawsze dostępna opinia dla bieżącego elementu na liście, nawet jeśli okno jest nieaktywne. Lista powinna reagować na polecenia **GoToNextLocation** i **GoToPrevLocation** , zmieniając również aktualnie wybrany element w oknie

 Przykłady okien narzędzi do nawigacji z listą to Eksplorator rozwiązań i wyszukiwanie wyników.

### <a name="tool-window-types"></a>Typy okien narzędzi

#### <a name="common-tool-windows-and-their-functions"></a>Typowe okna narzędzi i ich funkcje

|Typ|Okno narzędzia|Funkcja|
|----------|-----------------|--------------|
|**Hierarchiczn**|Eksplorator rozwiązań|Hierarchiczne drzewo, które wyświetla listę dokumentów zawartych w projektach, różne pliki i elementy rozwiązania. Wyświetlanie elementów w ramach projektów jest definiowane przez pakiet, który jest właścicielem typu projektu (na przykład typów opartych na odwołaniach, opartych na katalogach lub trybach mieszanych).|
|**Hierarchiczn**|Widok klas|Hierarchiczne drzewo klas i różne elementy w zestawie roboczym dokumentów, niezależnie od samych plików.|
|**Hierarchiczn**|Eksplorator serwera|Hierarchiczne drzewo, które wyświetla wszystkie serwery i połączenia danych w rozwiązaniu.|
|**Hierarchiczn**|Konspekt dokumentu|Hierarchiczna struktura aktywnego dokumentu.|
|**Siatka**|Właściwości|Siatka wyświetlająca listę właściwości dla wybranego obiektu wraz z selektorami wartości, aby edytować te właściwości.|
|**Siatka**|Lista zadań|Siatka umożliwiająca użytkownikowi tworzenie/Edytowanie/usuwanie zadań i komentarzy.|
|**Zawartość**|Pomoc|Okno, które umożliwia użytkownikom dostęp do różnych metod uzyskiwania pomocy, od "jak?" Filmy wideo na forach MSDN.|
|**Zawartość**|Dynamiczna pomoc|Okno narzędzi, które wyświetla linki do tematów pomocy mających zastosowanie do bieżącego zaznaczenia.|
|**Zawartość**|Przeglądarka obiektów|Dwukolumnowy zestaw ramek z listą hierarchicznych składników obiektów w lewym okienku oraz właściwościami i metodami obiektu w prawej kolumnie.|
|**Oknie dialogowym**|Znajdź, zaawansowane Znajdowanie|Okno dialogowe, które umożliwia użytkownikowi znalezienie lub znalezienie i zastępowanie różnych plików w rozwiązaniu.|
|**Inne**|Przybornik|Okno narzędzia służące do przechowywania elementów, które zostaną usunięte na powierzchnie projektowe, zapewniając spójne źródło przeciągania dla wszystkich projektantów.|
|**Inne**|Strona początkowa|Portal użytkownika do programu Visual Studio, z dostępem do źródeł wiadomości dla deweloperów, pomocy programu Visual Studio i ostatnich projektów. Użytkownicy mogą również tworzyć niestandardowe strony startowe, kopiując plik StartPage. XAML z katalogu "Common7\IDE\StartPages\" programu Visual Studio Program Files do folderu restartpages w katalogu dokumenty programu Visual Studio, a następnie edytując kod XAML ręcznie lub otwierając go w programie Visual Studio lub w innym edytorze kodu.|
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Automatyczne||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Bezpośredniego||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Dane wyjściowe|Okno dane wyjściowe może być używane za każdym razem, gdy masz zdarzenia tekstowe lub status do zadeklarowania.|
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Pamięć||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Punkty przerwania||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Uruchomiono||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Dokumenty||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Stos wywołań||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Zmienne lokalne||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Serwuje||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Dezasemblacji||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Liczby||
|**Debuger:** Grupa systemu Windows specyficzna dla zadań debugowania i działań monitorowania|Wątki||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Konwencje edytora dokumentów

### <a name="document-interactions"></a>Interakcje dokumentów
 "Źródło dokumentu" to największe miejsce w środowisku IDE i polega na tym, że użytkownik ma ogólnie ustawioną uwagę na realizację swoich zadań, wspomagany przez uzupełniające okna narzędzi. Edytory dokumentów reprezentują podstawowe jednostki pracy, które użytkownik otwiera i zapisuje w programie Visual Studio. Zachowują one silny wybór związany z Eksplorator rozwiązańami lub innymi aktywnymi oknami hierarchii. Użytkownik powinien mieć możliwość wskazywania na jednym z tych okien hierarchii i dowiedzieć się, gdzie znajduje się dokument, oraz jego relacji z rozwiązaniem, projektem lub innym obiektem głównym dostarczanym przez pakiet programu Visual Studio.

 Edytowanie dokumentów wymaga spójnego środowiska użytkownika. Aby umożliwić użytkownikowi skoncentrowanie się na zadaniu, a nie na zarządzaniu oknem i znajdowaniu poleceń, wybierz strategię widoku dokumentu, która najlepiej pasuje do zadań użytkownika w celu edytowania tego typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Często spotykane interakcje dla dokumentu

- Obsługuj spójny model interakcji w wspólnym **nowym pliku** i otwartych środowiskach **plików** .

- Aktualizuj powiązane funkcje w pokrewnych oknach i w menu po otwarciu okna dokumentu.

- Polecenia menu są odpowiednio zintegrowane z typowymi menu, takimi jak **Edycja**, **Formatowanie**i menu **widoku** . Jeśli jest dostępnych znaczna ilość wyspecjalizowanych poleceń, można utworzyć nowe menu, które jest widoczne tylko wtedy, gdy dokument ma fokus.

- Osadzony pasek narzędzi może być umieszczony w górnej części edytora. Jest to preferowany pasek narzędzi, który pojawia się poza edytorem.

- Zawsze zachowuj zaznaczenie w Eksplorator rozwiązań lub podobnej aktywnej hierarchii okna.

- Dwukrotne kliknięcie dokumentu w Eksplorator rozwiązań powinno wykonać tę samą akcję co **otwarty**.

- Jeśli na typie dokumentu można użyć więcej niż jednego edytora, użytkownik powinien mieć możliwość przesłonięcia lub zresetowania akcji domyślnej dla danego typu dokumentu przy użyciu okna dialogowego **Otwórz za** pomocą, klikając prawym przyciskiem myszy plik, a następnie wybierając polecenie **Otwórz za pomocą** z menu skrótów.

- Nie Kompiluj kreatora w źródle dokumentu.

### <a name="user-expectations-for-specific-document-types"></a>Oczekiwania użytkowników na określone typy dokumentów
 Istnieje kilka różnych typów podstawowych edytorów dokumentów, a każdy z nich ma zestaw interakcji, które są spójne z innymi tego samego typu.

- **Edytor tekstu:** Edytor kodu, pliki dziennika

- **Powierzchnia projektowa:** Projektant formularzy WPF, formularze systemu Windows

- **Edytor stylu okna dialogowego:** Projektant manifestu, właściwości projektu

- **Projektant modeli:** Workflow Designer, codemap, diagram architektury, postęp

  Istnieje również kilka typów nieedytorów, które używają tego dokumentu. Chociaż nie edytują samych dokumentów, muszą one być zgodne ze standardowymi interakcjami dla okien dokumentów.

- **Raporty:** Raport IntelliTrace, raport funkcji Hyper-V, raport profilera

- **Pulpit nawigacyjny:** Centrum diagnostyki

#### <a name="text-based-editors"></a>Edytory tekstowe

- Dokument jest częścią modelu karty podglądu, umożliwiając Podgląd dokumentu bez jego otwierania.

- Struktura dokumentu może być reprezentowana w oknie narzędzia pomocnika, takim jak Konspekt dokumentu.

- Technologia IntelliSense (jeśli to konieczne) będzie spójna z innymi edytorami kodu.

- Okienka wyskakujące lub pomocniczy interfejs użytkownika są zgodne z podobnymi stylami i wzorcami dla istniejącego podobnego interfejsu użytkownika, takiego jak CodeLens.

- Komunikaty o stanie dokumentu zostaną wyświetlone w kontrolce paska narzędzi w górnej części dokumentu lub na pasku stanu.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu strony **narzędzi > opcje** , strony udostępnione czcionki i kolory albo jednej specyficznej dla edytora.

#### <a name="design-surfaces"></a>Powierzchnie projektowe

- Pusty Projektant powinien mieć znak wodny na powierzchni wskazujący, jak zacząć pracę.

- Mechanizmy przełączania widoku będą zgodne z istniejącymi wzorcami, takimi jak dwukrotne kliknięcie, aby otworzyć Edytor kodu lub karty w oknie dokumentu umożliwiające interakcję z obydwoma okienkami.

- Dodawanie elementów do powierzchni projektowej powinno odbywać się za pośrednictwem przybornika, chyba że wymagane jest okno z wysoce określonymi narzędziami.

- Elementy na powierzchni będą zgodne ze spójnym modelem wyboru.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, nie typowe polecenia, takie jak **Zapisywanie**.

#### <a name="dialog-style-editors"></a>Edytory stylów okna dialogowego

- Układ formantu powinien być zgodny z normalnymi konwencjami układu okna dialogowego.

- Karty w edytorze nie powinny być zgodne z wyglądem kart dokumentu, powinny być zgodne z jednym z dwóch dozwolonych stylów kart wewnętrznych.

- Użytkownicy muszą mieć możliwość korzystania z formantów tylko przy użyciu klawiatury. przez aktywowanie edytora i tabulacji za pośrednictwem kontrolek lub przy użyciu standardowych symboli.

- Projektant powinien używać wspólnego modelu zapisu. Na powierzchni nie powinny znajdować się ogólne przyciski Zapisz lub Zatwierdź, chociaż inne przyciski mogą być odpowiednie.

#### <a name="model-designers"></a>Projektanci modeli

- Pusty Projektant powinien mieć znak wodny na powierzchni wskazujący, jak zacząć pracę.

- Dodawanie elementów do powierzchni projektowej powinno odbywać się za pośrednictwem przybornika.

- Elementy na powierzchni będą zgodne ze spójnym modelem wyboru.

- Osadzone paski narzędzi zawierają tylko polecenia specyficzne dla dokumentu, nie typowe polecenia, takie jak **Zapisywanie**.

- Legenda może pojawić się na powierzchni, indykatywny lub znak wodny.

- Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu strony **narzędzi > opcje** , strony udostępnione czcionki i kolory albo jednej specyficznej dla edytora.

#### <a name="reports"></a>Raporty

- Raporty są zwykle tylko do odczytu i nie uczestniczą w modelu zapisu. Mogą jednak obejmować interakcje, takie jak linki do innych istotnych informacji lub sekcji, które rozszerzają i zwijają.

- Większość poleceń na powierzchni powinna być hiperłącze, a nie przyciski.

- Układ powinien zawierać nagłówek i przestrzegać standardowych wytycznych dotyczących układu raportu.

#### <a name="dashboards"></a>Pulpity nawigacyjne

- Pulpity nawigacyjne nie mają samego modelu interakcji, ale stanowią możliwość oferowania różnorodnych narzędzi.

- Nie uczestniczą w modelu zapisu.

- Użytkownicy muszą być w stanie korzystać z formantów tylko przy użyciu klawiatury, aktywując Edytor i przechodząc do karty za pośrednictwem formantów lub używając standardowych symboli.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Oknach dialogowych

### <a name="introduction"></a>Wprowadzenie
 Okna dialogowe w programie Visual Studio zwykle obsługują jedną dyskretną jednostkę pracy użytkownika, a następnie są odrzucane.

 Jeśli określisz, że potrzebujesz okna dialogowego, masz trzy opcje w kolejności preferencji:

1. Zintegruj swoje funkcje w jedno z udostępnionych okien dialogowych w programie Visual Studio.

2. Utwórz własne okno dialogowe przy użyciu wzorca znalezionego w istniejącym podobnym oknie dialogowym.

3. Utwórz nowe okno dialogowe, postępując zgodnie z zasadami interakcji i układu.

   W tym temacie opisano sposób wybierania prawidłowego wzorca okna dialogowego w ramach przepływów pracy programu Visual Studio i wspólnych Konwencji dla projektu okna dialogowego.

### <a name="themes"></a>Motywy
 Okna dialogowe w programie Visual Studio mają jeden z dwóch podstawowych stylów:

#### <a name="standard-unthemed"></a>Standardowa (niemotywnie)
 Większość okien dialogowych to standardowe okna dialogowe, które powinny być odnoszące się do nich. Nie wykonuj ponownie szablonu wspólnych kontrolek ani nie próbuj tworzyć stylizowanych przycisków lub kontrolek "nowoczesny". Kontrolki i wygląd Chrome są zgodne [ze wskazówkami dotyczącymi interakcji z pulpitem systemu Windows dla okien](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)dialogowych.

#### <a name="themed"></a>Tematyczne
 Mogą być należeć specjalne okna dialogowe "podpis". Okna dialogowe z motywami mają różne elementy wyglądu, które również mają specjalne wzorce interakcji skojarzone ze stylem. Motyw okna dialogowego, tylko wtedy, gdy spełnia następujące wymagania:

- To okno dialogowe jest typowym doświadczeniem, który będzie widoczny i używany często lub przez wielu użytkowników (na przykład okno dialogowe **Nowy projekt** .

- Okno dialogowe zawiera widoczne elementy marki produktu (na przykład okno dialogowe **Ustawienia konta** ).

- To okno dialogowe jest wyświetlane jako integralna część większego przepływu, który obejmuje inne okna dialogowe, na przykład okno dialogowe **Dodawanie połączonej usługi** .

- To okno dialogowe jest ważną częścią środowiska, które odgrywa strategiczną rolę w promocji lub rozróżniania wersji produktu.

  Podczas tworzenia okna dialogowego z motywem Użyj odpowiednich kolorów środowiska i postępuj zgodnie z prawidłowymi wzorcami interakcji i układu. (Zobacz [układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>Projekt okna dialogowego
 Dobrze zaprojektowane okna dialogowe uwzględniają następujące zagadnienia:

- Obsługiwane zadanie użytkownika

- Styl tekstu, język i terminologia okna dialogowego

- Wybór kontroli i konwencje interfejsu użytkownika

- Specyfikacja układu wizualizacji i wyrównanie formantów

- Dostęp za pomocą klawiatury

#### <a name="content-organization"></a>Organizacja zawartości
 Należy wziąć pod uwagę różnice między tymi podstawowymi typami okien dialogowych:

- [Proste okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) prezentowanie kontrolek w jednym modalnym oknie. Prezentacja może zawierać różne wzorce kontrolek złożonych, w tym selektor pól lub pasek ikon.

- [Okna dialogowe z warstwami](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) służą do optymalnego wypełniania ekranu, gdy pojedynczy element interfejsu użytkownika obejmuje wiele grup kontrolek. Grupowania okna dialogowego są "warstwowymi" za pomocą kontrolek karty, kontrolek listy nawigacji lub przycisków, aby użytkownik mógł wybrać grupowanie, które ma być widoczne w danym momencie.

- [Kreatory](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) są przydatne do kierowania użytkownika za pośrednictwem logicznej sekwencji kroków w kierunku ukończenia zadania. Serie wyborów są oferowane w kolejnych panelach, czasami wprowadzając różne przepływy pracy ("gałęzie") zależnie od wyboru dokonanego w poprzednim panelu.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Proste okna dialogowe
 Proste okno dialogowe jest prezentacją formantów w jednym modalnym oknie. Ta prezentacja może obejmować wahania wzorców kontrolek złożonych, takich jak selektor pól. W przypadku prostych okien dialogowych postępuj zgodnie ze standardowym układem ogólnym, a także dowolnym określonym układem wymaganym dla złożonych grup formantów.

 ![Proste okno dialogowe w programie Visual Studio](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704 — 01_CreateStrongNameKey")

 **Tworzenie klucza silnej nazwy jest przykładem prostego okna dialogowego w programie Visual Studio.**

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Okna dialogowe z warstwami
 Okna dialogowe z warstwami obejmują karty, pulpity nawigacyjne i osadzone drzewa. Są one używane do maksymalizowania nieruchomości, gdy istnieje wiele grup kontrolek oferowanych w pojedynczym interfejsie użytkownika. Grupowanie odbywa się w warstwach, dzięki czemu użytkownik może wybrać grupowanie, które ma być widoczne w dowolnym momencie.

 W najbardziej prostym przypadku mechanizm przełączania między grupami jest formantem tabulacji. Dostępne są różne alternatywy. Zobacz ustalanie priorytetów i warstwowe, aby wybrać najbardziej odpowiedni styl.

 Okno dialogowe **opcje > narzędzia** jest przykładem okna dialogowego z warstwą przy użyciu osadzonego drzewa:

 ![Okno dialogowe z warstwą w programie Visual Studio](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704 — 02_ToolsOptions")

 **Narzędzia > opcje są przykładem okna dialogowego z warstwą w programie Visual Studio.**

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Kreatorów
 Kreatory są przydatne do kierowania użytkownika za pośrednictwem logicznej sekwencji kroków w celu wykonania zadania. Seria opcji jest oferowana w kolejnych panelach, a użytkownik musi przejść przez każdy krok przed przejściem do następnego. Gdy dostępne są wystarczające wartości domyślne, przycisk **Zakończ** jest włączony.

 Kreatory modalne są używane do zadań, które:

- Zawiera rozgałęzienie, w którym są oferowane różne ścieżki w zależności od opcji wybranych przez użytkownika

- Zawiera zależności między krokami, w których kolejne kroki zależą od danych wprowadzonych przez użytkownika z powyższych kroków

- Są wystarczająco skomplikowane, aby interfejs użytkownika był używany do wyjaśnienia oferowanych opcji i możliwych wyników w każdym kroku

- Są transakcyjne, wymagając zestawu kroków do wykonania w całości przed zatwierdzeniem jakichkolwiek zmian

### <a name="common-conventions"></a>Wspólne konwencje
 Aby osiągnąć optymalny projekt i funkcjonalność przy użyciu okien dialogowych, postępuj zgodnie z tymi konwencjami w oparciu o rozmiar okna dialogowego, pozycję, standardy, konfigurację kontroli i wyrównanie, tekst interfejsu użytkownika, paski tytułu, przyciski sterowania i klucze dostępu.

 Aby uzyskać wytyczne dotyczące poszczególnych układów, zobacz [układ dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Rozmiar
 Okna dialogowe powinny pasować do minimalnej rozdzielczości ekranu 1024x768, a początkowy rozmiar okna dialogowego nie powinien przekraczać 900x700 pikseli. Okna dialogowe mogą mieć zmienny rozmiar, ale nie jest to wymagane.

 Istnieją dwa zalecenia dotyczące okien dialogowych o zmiennym rozmiarze:

1. Minimalny rozmiar jest zdefiniowany dla okna dialogowego, które zostanie zoptymalizowane dla zestawu kontrolek bez obcinania, i dostosowanie w celu uwzględnienia rozsądnego wzrostu lokalizacji.

2. Że rozmiar skalowany przez użytkownika jest zachowywany z sesji na sesję. Na przykład jeśli użytkownik skaluje okno dialogowe do 150%, kolejne uruchomienie okna dialogowego zostanie wyświetlone o 150%.

#### <a name="position"></a>Położenie
 Okna dialogowe muszą pojawić się w środku IDE podczas pierwszego uruchomienia. W przypadku okien dialogowych bez zmiany rozmiaru nie jest wymagane, aby ostatnie położenie okna dialogowego było utrwalane, więc będzie ono wyświetlane w trakcie następnego uruchomienia. W przypadku okien dialogowych o zmiennym rozmiarze rozmiar powinien być utrwalany przy kolejnych uruchomieniach. W przypadku okien dialogowych o zmiennym rozmiarze, które są modalne, pozycja nie musi być utrwalona. Wyświetlanie ich w centrum IDE zapobiega możliwości wyświetlania okna dialogowego w nieprzewidywalnym lub niezdatnym do użycia w przypadku zmiany konfiguracji wyświetlania użytkownika. W przypadku niemodalnych okien dialogowych, które mogą być zmieniane, pozycja użytkownika powinna być utrzymywana przy kolejnych uruchomieniach, ponieważ okno dialogowe może być używane często jako integralna część większego przepływu pracy.

 Gdy okna dialogowe muszą być zduplikowane w innych oknach dialogowych, okno dialogowe powinno być kaskadowo z prawej strony i w dół od elementu nadrzędnego, aby było oczywiste, że użytkownik przeszedł do nowego miejsca.

#### <a name="modality"></a>Modaln
 Modalne oznacza, że użytkownicy są zobowiązani do ukończenia lub anulowania okna dialogowego przed kontynuowaniem. Ponieważ modalne okna dialogowe blokują możliwość współdziałania z innymi częściami środowiska, przepływ zadań funkcji powinien korzystać z nich tak, jak to możliwe. Gdy konieczna jest operacja modalna, program Visual Studio zawiera wiele udostępnionych okien dialogowych, które można zintegrować z usługą. Jeśli musisz utworzyć nowe okno dialogowe, postępuj zgodnie ze wzorcem interakcji istniejącego okna dialogowego z podobnymi funkcjami.

 Gdy użytkownicy muszą wykonać dwa działania jednocześnie, takie jak **Znajdź** i **Zamień** podczas pisania nowego kodu, okno dialogowe powinno być niemodalne, aby użytkownik mógł łatwo przełączać się między nimi. Program Visual Studio ogólnie używa okien narzędzi dla tego rodzaju zadania połączonego z edytorem.

#### <a name="control-configuration"></a>Konfiguracja kontroli
 Być spójne z istniejącymi konfiguracjami kontrolek, które mają tę samą wartość w programie Visual Studio.

#### <a name="title-bars"></a>Paski tytułu

- Tekst na pasku tytułu musi odzwierciedlać nazwę polecenia, które je uruchomiło.

- Ikona nie powinna być używana w paskach tytułu okna dialogowego. W przypadkach, gdy system wymaga jednego z nich, użyj logo programu Visual Studio.

- Okna dialogowe nie powinny mieć przycisków Minimalizuj lub Maksymalizuj.

- Przyciski pomocy na pasku tytułu zostały wycofane. Nie należy dodawać ich do nowych okien dialogowych. Jeśli istnieją, powinny uruchamiać temat pomocy, który jest koncepcyjnie istotny dla zadania.

  ![Specyfikacje paska tytułu dla programu Visual Studio](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704 — 03_TitleBarSpecs")

  **Specyfikacje wytycznych dla pasków tytułu w oknach dialogowych programu Visual Studio.**

#### <a name="control-buttons"></a>Przyciski sterujące
 Ogólnie rzecz biorąc **,** / **Cancel** / przyciski**Pomoc** Anuluj powinny być ułożone poziomo w prawym dolnym rogu okna dialogowego. Alternatywny stos pionowy jest dozwolony, jeśli okno dialogowe zawiera kilka innych przycisków w dolnej części okna dialogowego, które zaprezentowanie wizualnej pomyłek przy użyciu przycisków sterowania.

 ![Konfiguracje przycisków sterowania w programie Visual Studio](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704 — 04_ControlButtonConfig")

 **Dopuszczalne konfiguracje przycisków sterowania w oknach dialogowych programu Visual Studio**

 Okno dialogowe musi zawierać domyślny przycisk kontrolki. Aby określić najlepsze polecenie, które ma być używane jako domyślne, wybierz jedną z następujących opcji (zgodnie z kolejnością pierwszeństwa):

- Wybierz najbezpieczniejsze i najbezpieczniejsze polecenie jako domyślne. Oznacza to, że wybranie polecenia najprawdopodobniej uniemożliwi utratę danych i uniknięcie niezamierzonego dostępu do systemu.

- Jeśli utrata danych i zabezpieczenia nie są czynnikami, wybierz polecenie domyślne w zależności od wygody. Włączenie najbardziej najprawdopodobniej polecenia jako domyślnego spowoduje poprawienie przepływu pracy użytkownika, gdy okno dialogowe obsługuje częste lub powtarzające się zadania.

  Unikaj wyboru trwałej destrukcyjnej akcji dla polecenia domyślnego. Jeśli takie polecenie jest obecne, wybierz bezpieczniejsze polecenie jako domyślne.

#### <a name="access-keys"></a>Klawisze dostępu
 Nie używaj kluczy dostępu dla przycisków **OK** / **Anuluj** / **Pomoc** . Te przyciski są domyślnie mapowane na klawisze skrótów:

|Nazwa przycisku|Skrót klawiaturowy|
|-----------------|-----------------------|
|OK|Enter|
|Anuluj|Esc|
|Pomoc|F1|

#### <a name="imagery"></a>Obrazach
 Oszczędne używanie obrazów w oknach dialogowych. Nie używaj dużych ikon w oknach dialogowych tylko do wykorzystania miejsca. Używaj obrazów tylko wtedy, gdy są ważną częścią przekazywania wiadomości do użytkownika, takich jak ikony ostrzeżeń lub animacje stanu.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Ustalanie priorytetów i warstwowe

#### <a name="prioritizing-your-ui"></a>Określanie priorytetów interfejsu użytkownika
 Może być konieczne przekazanie pewnych elementów interfejsu użytkownika do programu Forefront i umieszczenie bardziej zaawansowanych zachowań i opcji (w tym przesłanianie poleceń) do okien dialogowych. Przenosząc powszechnie używane funkcje do programu Forefront, tworząc w ten sposób pomieszczenie, i przez udostępnienie go domyślnie w interfejsie użytkownika z etykietą tekstową, gdy okno dialogowe jest wyświetlane.

#### <a name="layering-your-ui"></a>Warstwowy interfejs użytkownika
 Jeśli określono, że okno dialogowe jest niezbędne, ale powiązane funkcje, które mają być obecne dla użytkownika wykraczają poza to, co można wyświetlić w prostym oknie dialogowym, należy utworzyć warstwę interfejsu użytkownika. Najpopularniejsze metody warstw są używane przez program Visual Studio to karty i korytarzach lub pulpity nawigacyjne. W niektórych przypadkach mogą być odpowiednie regiony, które można rozwijać i zwijać. W programie Visual Studio zazwyczaj nie zaleca się stosowania adaptacyjnego interfejsu użytkownika.

 Istnieją zalety i wady różnych metod korzystania z warstwowego interfejsu użytkownika za poorednictwem kontrolek przypominających karty. Zapoznaj się z listą poniżej, aby upewnić się, że wybierasz technikę warstwową, która jest odpowiednia dla danej sytuacji.

##### <a name="tabbing"></a>Klawisza Tab

|Mechanizm przełączania|Zalety i odpowiednie użycie|Wady i nieodpowiednie użycie|
|-------------------------|------------------------------------|-----------------------------------------|
|Kontrolka karta|Logicznie Grupuj strony okna dialogowego w powiązane zestawy<br /><br /> Przydatne w przypadku mniej niż pięciu (lub liczby kart, które mieszczą się w jednym wierszu okna dialogowego) stron powiązanych kontrolek w oknie dialogowym<br /><br /> Etykiety kart muszą być krótkie: jedno lub dwa wyrazy, które mogą łatwo identyfikować zawartość<br /><br /> Typowy styl okna dialogowego systemu<br /><br /> Przykład: **Eksplorator plików > właściwości elementu**|Wykonywanie krótkich etykiet z opisami może być trudne<br /><br /> Zwykle nie skaluje ostatnich pięciu kart w jednym oknie dialogowym<br /><br /> Nieodpowiedni, jeśli masz zbyt wiele kart dla jednego wiersza; Użyj alternatywnej techniki warstwowej<br /><br /> Nie rozszerzalny|
|Nawigacja po pasku bocznym|Proste przełączanie urządzenia, które może obsługiwać więcej kategorii niż karty<br /><br /> Płaska lista kategorii (bez hierarchii)<br /><br /> Extensible<br /><br /> Przykład: **Dostosuj... > Dodaj polecenie**|Nie jest dobrym miejscem w poziomie, jeśli istnieje mniej niż trzy grupy<br /><br /> Zadanie może być lepiej dopasowane do listy rozwijanej|
|Kontrolka drzewa|Zezwala na nieograniczoną kategorię<br /><br /> Zezwala na grupowanie i/lub hierarchię kategorii<br /><br /> Extensible<br /><br /> Przykład: **narzędzia > opcje**|Silnie zagnieżdżone hierarchie mogą spowodować nadmierne przewijanie w poziomie<br /><br /> Program Visual Studio ma zbyt dużej ilości widoków drzewa|
|Kreatora|Pomoc w wypełnianiu zadania przez identyfikatory GUID przez wykonywanie kroków krok po kroku. Kreator reprezentuje zadanie wysokiego poziomu, a poszczególne panele reprezentują podzadania, które są konieczne do wykonania ogólnego zadania.<br /><br /> Przydatne, gdy zadanie przekroczy granice interfejsu użytkownika, tak jak w przypadku, gdy użytkownik będzie musiał użyć wielu edytorów i okien narzędzi do wykonania zadania<br /><br /> Przydatne, gdy zadanie wymaga rozgałęziania<br /><br /> Przydatne, gdy zadanie zawiera zależności między krokami<br /><br /> Przydatne, gdy w jednym oknie dialogowym można przedstawić kilka podobnych zadań z jednym rozwidleniem decyzji, aby zmniejszyć liczbę różnych podobnych okien dialogowych.|Nieodpowiednie dla każdego zadania, które nie wymaga sekwencyjnego przepływu pracy<br /><br /> Użytkownicy mogą zostać przeciążni i pomylić kreatora ze zbyt dużą liczbą kroków<br /><br /> Kreatorzy mają nieodłączną nieruchomość ekranu|

##### <a name="hallways-or-dashboards"></a>Korytarzach lub pulpity nawigacyjne
 Korytarzach i pulpity nawigacyjne to okna dialogowe lub panele służące jako uruchamianie punktów w innych oknach dialogowych i oknach. Dobrze zaprojektowane polecenie "holu" natychmiast wyświetla tylko najbardziej typowe opcje, polecenia i ustawienia, umożliwiając użytkownikowi łatwe wykonywanie typowych zadań. Podobnie jak w przypadku rzeczywistych holu, zapewnia Doorways do uzyskiwania dostępu do pomieszczeń za nimi. w tym przypadku mniej typowy interfejs użytkownika jest zbierany do oddzielnych "pokojów" (często innych okien dialogowych) powiązanych funkcji, do których można uzyskać dostęp z głównego holu.

 Alternatywnie, interfejs użytkownika, który oferuje wszystkie dostępne funkcje w pojedynczej kolekcji, a nie refaktoryzację mniej typowych funkcji w oddzielnych lokalizacjach, jest po prostu pulpitem nawigacyjnym.

 ![Koncepcja holu w programie Outlook](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704 — 08_Hallway")

 **Holu koncepcji w celu udostępnienia dodatkowego interfejsu użytkownika w programie Outlook**

##### <a name="adaptive-ui"></a>Adaptacyjny interfejs użytkownika
 Wyświetlanie lub ukrywanie interfejsu użytkownika w oparciu o użycie lub samodzielne środowisko użytkownika jest innym sposobem przedprezentowania niezbędnego interfejsu użytkownika podczas ukrywania innych części. Nie jest to zalecane w programie Visual Studio jako algorytmy podejmowania decyzji o tym, kiedy pokazać lub ukryć interfejs użytkownika może być kłopotliwy, a reguły będą zawsze błędne dla niektórych zestawów przypadków.

## <a name="projects"></a><a name="BKMK_Projects"></a> Projektami

### <a name="projects-in-the-solution-explorer"></a>Projekty w Eksplorator rozwiązań
 Większość projektów jest klasyfikowana jako oparty na odwołaniach, opartych na katalogach lub mieszanych. Wszystkie trzy typy projektów są obsługiwane jednocześnie w Eksplorator rozwiązań. Katalog główny środowiska użytkownika w pracy z projektami odbywa się w tym oknie. Chociaż różne węzły projektu są projektami referencyjnymi, katalogowymi lub w trybie mieszanym, istnieje typowy wzorzec interakcji, który powinien zostać zastosowany jako punkt wyjścia przed rozbieżnością wzorców użytkownika specyficznych dla projektu.

 Projekty powinny zawsze:

- Obsługa możliwości dodawania folderów projektu do organizowania zawartości projektu

- Utrzymywanie spójnego modelu na potrzeby trwałości projektu

  Projekty powinny również obsługiwać spójne modele interakcji dla:

- Usuwanie elementów projektu

- Zapisywanie dokumentów

- Edytowanie właściwości projektu

- Edytowanie projektu w widoku alternatywnym

- Operacje przeciągania i upuszczania

### <a name="drag-and-drop-interaction-model"></a>Model interakcji przeciągnij i upuść
 Projekty zwykle klasyfikują się jako oparte na odwołaniach (w celu utrwalenia tylko odwołań do elementów projektu w magazynie), oparte na katalogach (z możliwością utrwalania tylko elementów projektu fizycznie przechowywanych w hierarchii projektu) lub mieszanego (z możliwością utrwalania odwołań lub elementów fizycznych). IDE uwzględnia wszystkie trzy typy projektów jednocześnie w **Eksplorator rozwiązań**.

 W perspektywie typu "przeciągnij i upuść" należy zastosować następujące cechy do poszczególnych typów projektów w **Eksplorator rozwiązań**:

- **Projekt oparty na odwołaniach:** Najważniejszym punktem jest to, że projekt jest przeciągany wokół odwołania do elementu w magazynie. Gdy projekt oparty na odwołaniach działa jako źródło dla operacji przenoszenia, należy usunąć tylko odwołanie do tego elementu z projektu. Element nie powinien faktycznie zostać usunięty z dysku twardego. Gdy projekt oparty na odwołaniach działa jako element docelowy dla operacji przenoszenia (lub kopiowania), powinien dodać odwołanie do oryginalnego elementu źródłowego bez tworzenia prywatnej kopii elementu.

- **Projekt oparty na katalogu:** W punkcie przeciągania i upuszczania projekt jest przeciągany wokół elementu fizycznego, a nie do odwołania. Gdy projekt oparty na katalogu działa jako źródło dla operacji przenoszenia, powinien on zakończyć usuwanie elementu fizycznego z dysku twardego, a także usunąć go z projektu. Gdy projekt oparty na katalogu działa jako element docelowy dla operacji przenoszenia (lub kopiowania), powinien wykonać kopię elementu źródłowego w lokalizacji docelowej.

- **Projekt mieszany:** W przypadku przeciągania i upuszczania punktu widzenia zachowanie tego typu projektu jest zależne od charakteru przeciąganego elementu (odwołanie do elementu w magazynie lub samego elementu). Powyższym zachowaniem dotyczącym odwołań i elementów fizycznych opisano powyżej.

  Jeśli w **Eksplorator rozwiązań**istniał tylko jeden typ projektu, operacje przeciągania i upuszczania byłyby proste. Ponieważ każdy system projektu ma możliwość zdefiniowania własnego zachowania przeciągania i upuszczania, należy przestrzegać pewnych wytycznych (w oparciu o zachowanie przy przeciąganiu i upuszczaniu w Eksploratorze Windows), aby zapewnić przewidywalne środowisko użytkownika:

- Niezmodyfikowana operacja przeciągania w **Eksplorator rozwiązań** (gdy nie są wciśnięte klawisze CTRL ani Shift), należy wykonać operację przenoszenia.

- Operacja Shift-przeciągnij również powinna powodować operację przenoszenia.

- Operacja przeciągania Ctrl-przeciągnij powinna spowodować operację kopiowania.

- Systemy projektów oparte na odwołaniach i mieszanych obsługują pojęcie dodawania linku (lub odwołania) do elementu źródłowego. Gdy te projekty są elementem docelowym operacji przeciągania i upuszczania (naciśnięcie **klawiszy Ctrl + Shift** jest wyłączone), powinno to skutkować odwołaniem do elementu dodawanego do projektu.

  Nie wszystkie operacje przeciągania i upuszczania są rozsądne dla różnych kombinacji projektów opartych na odwołaniach, opartych na katalogach i mieszanych. W szczególności jest to problematyczne poudawać, aby zezwolić na operację przenoszenia między projektem źródłowym opartym na katalogu i projektem docelowym opartym na odwołaniach, ponieważ źródłowy projekt oparty na katalogu będzie musiał usunąć element źródłowy po zakończeniu przenoszenia. Docelowy projekt oparty na odwołaniach będzie następnie kończyć się odwołaniem do usuniętego elementu.

  Jest to również mylące poudawać, aby zezwolić na operację kopiowania między tymi typami projektów, ponieważ docelowy projekt oparty na odwołaniach nie powinien tworzyć niezależnej kopii elementu źródłowego. Podobnie naciśnięcie klawiszy Ctrl + Shift w projekcie docelowym opartym na katalogu nie powinno być dozwolone, ponieważ projekt oparty na katalogu nie może utrwalać odwołań. W przypadkach, gdy operacja przeciągania i upuszczania nie jest obsługiwana, IDE powinien nie zezwalać na upuszczanie i wyświetlanie przez użytkownika kursora No-Drop (pokazanego w tabeli wskaźnik poniżej).

  Aby poprawnie zaimplementować zachowanie przeciągania i upuszczania, projekt źródłowy przeciągnięcia musi komunikować swój charakter (na przykład jest odwołaniem lub katalogiem?) do projektu docelowego. Te informacje są wskazywane przez format schowka oferowany przez źródło. Jako źródło operacji przeciągania (lub kopiowania schowka) projekt powinien oferować odpowiednio **CF_VSREFPROJECTITEM**S lub **CF_VSSTGPROJECTITEMS** , w zależności od tego, czy projekt jest oparty na odwołaniach czy w katalogu. Oba te formaty mają tę samą zawartość danych, która jest podobna do formatu **CF_HDROP** systemu Windows, z wyjątkiem tego, że listy ciągów, zamiast nazw, są zakończonymi podwójnie**null** listą ciągów **Projref** (zwracanymi z **IVsSolution:: GetProjrefOfItem** lub **:: GetProjrefOfProject** , zgodnie z potrzebami).

  Jako obiekt docelowy operacji usuwania (lub wklejania schowka), projekt powinien akceptować zarówno **CF_VSREFPROJECTITEMS** , jak i **CF_VSSTGPROJECTITEMS**, ale dokładna obsługa operacji przeciągania i upuszczania różni się w zależności od charakteru projektu docelowego i projektu źródłowego. Projekt źródłowy deklaruje swój charakter, wybierając **CF_VSREFPROJECTITEMS** lub **CF_VSSTGPROJECTITEMS**. Obiekt docelowy porzucania rozumie swój własny charakter i w związku z tym ma wystarczające informacje, aby podejmować decyzje dotyczące tego, czy przeniesienie, kopiowanie lub łączenie ma zostać wykonane. Użytkownik modyfikuje także, które operacje przeciągania i upuszczania należy wykonać przez naciśnięcie klawiszy CTRL, Shift lub CTRL i Shift. Ważne jest, aby miejsce docelowe upuszczania prawidłowo wskazywało, która operacja zostanie wykonana z wyprzedzeniem w metodach **DragEnter** i **DragOver** . **Eksplorator rozwiązań** automatycznie wie, czy projekt źródłowy i projekt docelowy są tego samego projektu.

  Przeciąganie elementów projektu między wystąpieniami programu Visual Studio (na przykład z jednego wystąpienia devenv.exe na inny) nie jest obsługiwane. **Eksplorator rozwiązań** również wyłącza je bezpośrednio.

  Użytkownik powinien zawsze być w stanie określić efekt operacji przeciągania i upuszczania, zaznaczając element, przeciągając go do lokalizacji docelowej i obserwując następujące wskaźniki myszy pojawiające się przed porzuceniem elementu:

|Wskaźnik myszy|Polecenie|Opis|
|-------------------|-------------|-----------------|
|![Ikona "Brak" myszy](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706 — 01_MouseNoDrop")|Brak porzucenia|Nie można porzucić elementu w określonej lokalizacji.|
|![Ikona "Copy" myszy](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706 — 02_MouseCopy")|Kopiuj|Element zostanie skopiowany do lokalizacji docelowej.|
|![Ikona "Przenieś" myszy](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706 — 03_MouseMove")|Move|Element zostanie przeniesiony do lokalizacji docelowej.|
|![Ikona myszy "Dodaj odwołanie"](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706 — 04_MouseAddRef")|Dodawanie odwołania|Odwołanie do wybranego elementu zostanie dodane do lokalizacji docelowej.|

#### <a name="reference-based-projects"></a>Projekty oparte na odwołaniach
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (jak również Wycinanie/kopiowanie/wklejanie), które powinny być wykonywane na podstawie rodzaju elementu źródłowego i klawiszy modyfikujących naciśniętych dla projektów docelowych opartych na odwołaniach:

|||Element źródłowy: odwołanie/łącze|Element źródłowy: fizyczny element lub system plików (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Brak modyfikatora|Akcja|Move|Łącze|
|Brak modyfikatora|Cel|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Brak modyfikatora|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Zachowuje oryginalny element|
|Brak modyfikatora|Wynik|**DROPEFFECT_MOVE** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_LINK** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Shift + przeciągnij|Akcja|Move|Brak porzucenia|
|Shift + przeciągnij|Cel|Dodaje odwołanie do oryginalnego elementu|Brak porzucenia|
|Shift + przeciągnij|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Brak porzucenia|
|Shift + przeciągnij|Wynik|**DROPEFFECT_MOVE** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|Brak porzucenia|
|Ctrl + przeciągnij|Akcja|Kopiuj|Brak porzucenia|
|Ctrl + przeciągnij|Cel|Dodaje odwołanie do oryginalnego elementu|Brak porzucenia|
|Ctrl + przeciągnij|Element źródłowy|Zachowuje odwołanie do oryginalnego elementu|Brak porzucenia|
|Ctrl + przeciągnij|Wynik|**DROPEFFECT_COPY** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|Brak porzucenia|
|Ctrl + Shift + przeciągnij|Akcja|Łącze|Łącze|
|Ctrl + Shift + przeciągnij|Cel|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Ctrl + Shift + przeciągnij|Element źródłowy|Zachowuje odwołanie do oryginalnego elementu|Zachowuje oryginalny element|
|Ctrl + Shift + przeciągnij|Wynik|**DROPEFFECT_LINK** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_LINK** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Ctrl + Shift + przeciągnij|Uwaga|Analogicznie jak zachowanie metodą "przeciągnij i upuść" dla skrótów w Eksploratorze Windows.||
|Wytnij/Wklej|Akcja|Move|Łącze|
|Wytnij/Wklej|Cel|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Wytnij/Wklej|Element źródłowy|Zachowuje odwołanie do oryginalnego elementu|Zachowuje oryginalny element|
|Wytnij/Wklej|Wynik|Element pozostaje w oryginalnej lokalizacji w magazynie|Element pozostaje w oryginalnej lokalizacji w magazynie|
|Kopiowanie/wklejanie|Akcja|Kopiuj|Łącze|
|Kopiowanie/wklejanie|Element źródłowy|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Kopiowanie/wklejanie|Wynik|Zachowuje odwołanie do oryginalnego elementu|Zachowuje oryginalny element|
|Kopiowanie/wklejanie|Akcja|Element pozostaje w oryginalnej lokalizacji w magazynie|Element pozostaje w oryginalnej lokalizacji w magazynie|

#### <a name="directory-based-projects"></a>Projekty oparte na katalogu
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (jak również Wycinanie/kopiowanie/wklejanie), które powinny być wykonywane na podstawie rodzaju elementu źródłowego i klawiszy modyfikujących naciśniętych dla projektów docelowych opartych na katalogu:

|||Element źródłowy: odwołanie/łącze|Element źródłowy: fizyczny element lub system plików (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Brak modyfikatora|Akcja|Move|Move|
|Brak modyfikatora|Cel|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Brak modyfikatora|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Usuwa odwołanie do oryginalnego elementu|
|Brak modyfikatora|Wynik|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Shift + przeciągnij|Akcja|Move|Move|
|Shift + przeciągnij|Cel|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Shift + przeciągnij|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Shift + przeciągnij|Wynik|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Ctrl + przeciągnij|Akcja|Kopiuj|Kopiuj|
|Ctrl + przeciągnij|Cel|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Ctrl + przeciągnij|Element źródłowy|Zachowuje odwołanie do oryginalnego elementu|Zachowuje odwołanie do oryginalnego elementu|
|Ctrl + przeciągnij|Wynik|**Kopia DROPEFFECT_** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**Kopia DROPEFFECT_** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Ctrl + Shift + przeciągnij||Brak porzucenia|Brak porzucenia|
|Wytnij/Wklej|Akcja|Move|Move|
|Wytnij/Wklej|Cel|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Wytnij/Wklej|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Wytnij/Wklej|Wynik|Element pozostaje w oryginalnej lokalizacji w magazynie|Element został usunięty z oryginalnej lokalizacji w magazynie|
|Kopiowanie/wklejanie|Akcja|Kopiuj|Kopiuj|
|Kopiowanie/wklejanie|Cel|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Kopiowanie/wklejanie|Element źródłowy|Zachowuje oryginalny element|Zachowuje oryginalny element|
|Kopiowanie/wklejanie|Wynik|Element pozostaje w oryginalnej lokalizacji w magazynie|Element pozostaje w pierwotnej lokalizacji w magazynie|

#### <a name="mixed-target-projects"></a>Projekty mieszane dla obiektów docelowych
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (jak również Wycinanie/kopiowanie/wklejanie), które powinny być wykonywane na podstawie rodzaju elementu źródłowego i klawiszy modyfikujących naciśniętych dla projektów mieszanych:

|||Element źródłowy: odwołanie/łącze|Element źródłowy: fizyczny element lub system plików (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Brak modyfikatora|Akcja|Move|Move|
|Brak modyfikatora|Cel|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Brak modyfikatora|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Usuwa odwołanie do oryginalnego elementu|
|Brak modyfikatora|Wynik|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element zostanie usunięty z oryginalnej lokalizacji w magazynie|
|Shift + przeciągnij|Akcja|Move|Move|
|Shift + przeciągnij|Cel|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Shift + przeciągnij|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Shift + przeciągnij|Wynik|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_ przenoszenia** jest zwracany jako akcja z **::D ROP** i element zostanie usunięty z oryginalnej lokalizacji w magazynie|
|Ctrl + przeciągnij|Akcja|Kopiuj|Kopiuj|
|Ctrl + przeciągnij|Cel|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Ctrl + przeciągnij|Element źródłowy|Zachowuje odwołanie do oryginalnego elementu|Zachowuje oryginalny element|
|Ctrl + przeciągnij|Wynik|**Kopia DROPEFFECT_** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**Kopia DROPEFFECT_** jest zwracana jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Ctrl + Shift + przeciągnij|Akcja|Łącze|Łącze|
|Ctrl + Shift + przeciągnij|Cel|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu źródłowego|
|Ctrl + Shift + przeciągnij|Element źródłowy|Zachowuje odwołanie do oryginalnego elementu|Zachowuje oryginalny element|
|Ctrl + Shift + przeciągnij|Wynik|**DROPEFFECT_ link** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|**DROPEFFECT_ link** jest zwracany jako akcja z **::D ROP** i element pozostaje w oryginalnej lokalizacji w magazynie|
|Wytnij/Wklej|Akcja|Move|Move|
|Wytnij/Wklej|Cel|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Wytnij/Wklej|Element źródłowy|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Wytnij/Wklej|Wynik|Element pozostaje w oryginalnej lokalizacji w magazynie|Element został usunięty z oryginalnej lokalizacji w magazynie|
|Kopiowanie/wklejanie|Akcja|Kopiuj|Kopiuj|
|Kopiowanie/wklejanie|Cel|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Kopiowanie/wklejanie|Element źródłowy|Zachowuje oryginalny element|Zachowuje oryginalny element|
|Kopiowanie/wklejanie|Wynik|Element pozostaje w oryginalnej lokalizacji w magazynie|Element pozostaje w oryginalnej lokalizacji w magazynie|

 Te szczegóły należy wziąć pod uwagę podczas implementowania przeciągania w **Eksplorator rozwiązań**:

- Projektuj dla scenariuszy z wieloma wyborami.

- Nazwy plików (Pełna ścieżka) muszą być unikatowe w projekcie docelowym lub upuszczenie nie powinno być dozwolone.

- Nazwy folderów muszą być unikatowe (bez uwzględniania wielkości liter) na poziomie, w którym są usuwane.

- Istnieją różnice między plikami, które są otwarte lub zamknięte w czasie przeciągania (nie zostały wymienione w scenariuszach powyżej).

- Pliki najwyższego poziomu działają nieco inaczej niż pliki w folderach.

  Innym problemem należy wiedzieć, jak obsługiwać operacje przenoszenia na elementach, które mają otwarte projektanci lub redaktorzy. Oczekiwane zachowanie jest następujące (dotyczy wszystkich typów projektów):

1. Jeśli otwarty Edytor/projektant nie ma niezapisanych zmian, wówczas okno Edytor/Projektant powinno być zamknięte w trybie dyskretnym.

2. Jeśli otwarty Edytor/Projektant ma niezapisane zmiany, Źródło przeciągania powinno oczekiwać na wystąpienie, a następnie poprosi użytkownika o zapisanie niezatwierdzonych zmian w otwartych dokumentach przed zamknięciem okna z monitem podobnym do poniższego:

   ```
   ==========================================================
        One or more open documents have unsaved changes.
   Do you want to save uncommitted changes before proceeding?
                     [Yes]  [No]  [Cancel]
   ==========================================================
   ```

   Umożliwia to użytkownikowi zapisanie pracy w toku przed wykonaniem kopii przez element docelowy. Dodano nową metodę **IVsHierarchyDropDataSource2:: OnBeforeDropNotify** w celu włączenia tej obsługi.

   Następnie obiekt docelowy skopiuje stan elementu w postaci magazynu (bez uwzględnienia niezapisanych zmian w edytorze, jeśli użytkownik wybrał opcję **nie**). Po zakończeniu kopiowania przez element docelowy (w **IVsHierarchyDropDataSource::D ROP**), Źródło otrzymuje szansę wykonania operacji usuwania części Operacja przenoszenia (w **IVsHierarchyDropDataSource:: OnDropNotify**).

   Wszystkie redaktorzy z niezapisanymi zmianami powinny pozostać otwarte. W przypadku dokumentów z niezapisanymi zmianami oznacza to, że część kopiowania operacji przenoszenia zostanie wykonana, ale część usuwania zostanie przerwana. W scenariuszu z wieloma wyborami, gdy użytkownik wybierze **nie**, te dokumenty z niezapisanymi zmianami nie powinny być zamykane ani usuwane, ale te bez niezapisanych zmian powinny być zamknięte i usunięte.
