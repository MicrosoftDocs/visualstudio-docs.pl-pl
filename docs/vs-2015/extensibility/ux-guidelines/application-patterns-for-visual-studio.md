---
title: Wzorce aplikacji
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0deaad86e5b14bfd0dee4d73c9ceb51916231ff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060399"
---
# <a name="application-patterns-for-visual-studio"></a>Wzorce aplikacji dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_WindowInteractions"></a> Okno interakcji

### <a name="overview"></a>Omówienie
 Dostępne są dwa typy główne okno, używane w programie Visual Studio: edytory dokumentu i okna narzędzi. Rzadkich, ale to możliwe, są duże Niemodalne okna dialogowe. Mimo że są one wszystkie niemodalne w powłoce, ich wzorce są całkowicie innego. W tym temacie opisano różnicę między okna dokumentów, okien narzędzi i Niemodalne okna dialogowe. Modalne okno dialogowe wzorce są objęte [okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porównywanie wzorce użycia okna
 **Dokumentowanie windows** prawie zawsze są wyświetlane w obrębie dokumentu na dobrze. Daje to edytor dokumentów "center etap" Aby rozmieścić dodatkowe okna wokół.

 A **okna narzędzia** w większości przypadków jest wyświetlany jako oddzielne, mniejsze okna — które mogą być widoczne, ukryte lub ukryte automatycznie — zwinięta względem krawędzi środowiska IDE. Jednak czasami są przedstawione w tym dokumencie dobrze, usuwając **okno/dokowanie** właściwości w oknie. Skutkuje to więcej nieruchomości, ale również często decyzje projektowe: podczas próby zintegrowania programu Visual Studio, należy zdecydować, czy Twoja funkcja powinna zostać wyświetlona okno narzędzia lub okno dokumentu.

 **Niemodalne okna dialogowe** zachęcamy nie w programie Visual Studio. W dużym stopniu są zgodnie z definicją — narzędzie okna przestawne i powinny być zrealizowane w związku z tym. Niemodalne okna dialogowe są dozwolone w przypadku, gdy rozmiar okna narzędzi normalne zadokowany po stronie powłoki będzie zbyt ograniczenie. Mogą one również w przypadku, gdy użytkownik prawdopodobnie przenieść okna dialogowego na drugi monitor.

 Pomyśl, starannie informacje dotyczące typu kontenera należy. Typowe kwestie dotyczące wzorca użycia dotyczące projektowania interfejsu użytkownika znajdują się w poniższej tabeli.

||Okno dokumentu|Okna narzędzi|Niemodalnego okna dialogowego|
|-|---------------------|-----------------|---------------------|
|**Stanowisko**|Zawsze dobrze umieszczony w obrębie dokumentu i nie zadokować wokół krawędzi środowiska IDE. Go mogą być "ściągane", aby oddzielnie pojawia się z głównym powłoki.|Ogólnie przy zadokowane kartę wokół krawędzi środowiska IDE, ale mogą być dostosowane do być przestawne, automatyczne ukrywane (nieprzypięte) lub dobrze zadokowane w dokumencie.|Duże przestawne okno niezależnie od środowiska IDE.|
|**Zatwierdź modelu**|*Opóźnione zatwierdzenia*<br /><br /> Aby można było zapisać dane w dokumencie, użytkownik musi wydać polecenie pliku/zapisywanie, Zapisz jako lub Zapisz wszystko. Okno dokumentu korzysta z koncepcji zawarte w nim jest "dirtied" dane, następnie nacisk na jeden z zapisu poleceń. Podczas zamykania okna dokumentu, cała zawartość są zapisywane na dysku lub utraty.|*Natychmiastowe zatwierdzenia*<br /><br /> Nie ma żadnych Zapisywanie modelu. Inspektor narzędzia systemu windows, które pomagają w edycji pliku plik musi być otwarty w aktywnego edytora lub projektanta i edytora lub projektanta jest właścicielem zapisu.|*Opóźnione lub natychmiastowe zatwierdzenia*<br /><br /> W większości przypadków dużych niemodalnego okna dialogowego wymaga zdefiniowania akcji, aby zatwierdzić zmiany i pozwala na operację "Anuluj", który powoduje wycofanie wszelkich zmian wprowadzonych w ramach sesji okna dialogowego.  Odróżnia niemodalnego okna dialogowego z okna narzędzi, w tym narzędzia windows zawsze mają model natychmiastowego zatwierdzenia.|
|**Widoczność**|*Otwórz/tworzenie (plik), a następnie zamknij*<br /><br /> Otwarcie dokumentu z systemem windows odbywa się za pośrednictwem otwierania istniejącego dokumentu lub przy użyciu szablonu, aby utworzyć nowy dokument. Istnieje nie "Otwórz \<określonego edytora >" polecenie.|*Ukrywanie i pokazywanie*<br /><br /> Okna narzędzi w jednym wystąpieniu mogą ukryte lub pokazane. Zawartość i stanów w obrębie okna narzędzia zachować, czy w widoku lub ukryte. Obejmujące wiele wystąpień narzędzia windows może być zamknięte także ukryte. Po zamknięciu okna narzędzia obejmujące wiele wystąpień zawartości i stan w obrębie okna Narzędzie jest odrzucany.|*Uruchomione z poleceniem*<br /><br /> Okna dialogowe są uruchamiane z poleceniem opartego na zadaniach.|
|**Wystąpienia**|*Obejmujące wiele wystąpień*<br /><br /> Kilka edytorów może być otwarte na tym samym czasie i na edycję różnych plików, podczas gdy niektóre edytory Zezwalaj na tym samym pliku muszą być otwarte więcej niż jeden z nich (przy użyciu **okna > nowe okno** polecenie).<br /><br /> Pojedynczy Edytor może edytować jednego lub wielu plików w tym samym czasie (Projektant projektu).|*Instance jednego lub wielu*<br /><br /> Zawartość zmienia się odzwierciedlić kontekstu (tak jak w przeglądarce właściwości) lub wypychania fokus/kontekstu do innego systemu windows (Lista zadań, Eksploratorze rozwiązań).<br /><br /> Zarówno w jednym wystąpieniu, jak i w wielu wystąpieniach narzędzia windows powinna być skojarzona z aktywnego okna dokumentu, chyba że istnieje istotny powód nie pozycji.|*Jednego wystąpienia*|
|**Przykłady**|**Edytory tekstów**, takich jak Edytor kodu<br /><br /> **Projektowanie powierzchnie**, takie jak projektant formularzy czy powierzchnia modelowania<br /><br /> **Kontrolowanie układy podobne do okien dialogowych**, takie jak projektant manifestów|**Eksploratora rozwiązań** zapewnia rozwiązanie i projekty zawartych w rozwiązaniu<br /><br /> **Eksploratora serwera** udostępnia hierarchiczny widok połączenia serwerów i dane, które użytkownik zdecyduje, aby otworzyć okno. Otwieranie obiektów z hierarchii bazy danych, takich jak zapytania, zostanie otwarte okno dokumentu i umożliwia użytkownikowi edytowanie zapytania.<br /><br /> **Przeglądarkę właściwości** Wyświetla właściwości dla obiektu wybranego w oknie dokumentu lub innego okna narzędzi. Właściwości są prezentowane w widoku siatki hierarchiczne lub złożonych kontrolek podobne okno dialogowe i Zezwalaj użytkownikowi na ustawianie wartości tych właściwości.||

##  <a name="BKMK_ToolWindows"></a> Okna narzędzi

### <a name="overview"></a>Omówienie
 Okna narzędzi obsługują pracę użytkownika, która odbywa się w oknach dokumentów. One może służyć do wyświetlania hierarchii, która reprezentuje obiekt główny podstawowych programu Visual Studio zapewniająca i manipulować.

 Podczas wybierania nowego okna narzędzi w IDE, powinien autorzy:

-   Odpowiednie zadanie istniejących narzędzi systemu windows ale nie tworzenie nowych o podobnych możliwościach. Nowego okna narzędzi powinien zostać utworzony tylko, jeśli oferują one znacznie różnią się "narzędzia" lub funkcje, które nie może zostać zintegrowany do podobnych okna lub przez wyłączenie istniejącego okna do obrotowego koncentratora.

-   Pasek poleceń standardowych, należy użyć, jeśli to konieczne, w górnej części okna narzędzia.

-   Być zgodne ze wzorcami już istnieje w innych oknach narzędzi do kontroli nawigacji prezentacji i klawiatury.

-   Być zgodne z prezentację kontrolki w innymi oknami narzędzi.

-   Okna narzędzi specyficznych dla dokumentu powinny być automatycznie widoczne gdy jest to możliwe, aby były wyświetlane tylko po aktywowaniu dokumentu nadrzędnego.

-   Upewnij się, że ich zawartość okna jest można nawigować przez klawiatury (klawisze strzałek pomocy technicznej).

#### <a name="tool-window-states"></a>Stany okien narzędzi
 Okna narzędzi w usłudze Visual Studio mają różne stany, niektóre z nich, użytkownik aktywował (np. funkcję automatycznego ukrywania). Inne stany, takie jak auto widoczne, Zezwalaj na okna narzędzi, które pojawiają się w odpowiednim kontekście i ukrywania, gdy nie jest potrzebny. Istnieje pięć stanów okna narzędzia w sumie.

- **Zadokowane przypięte** okna narzędzi mogą być dołączane do dowolnego z czterech bokach obszar dokumentu. Ikona pinezki pojawia się na pasku tytułu okna narzędzia. Okno narzędzia może być zadokowane w poziomie lub pionie wzdłuż krawędzi powłoka i innymi oknami narzędzi, a także mogą być łączone przez karty.

- **Automatyczne ukrywane** nieprzypięte są okna narzędzi. Okno można przesunąć psuje, pozostawiając kartę (przy użyciu nazwy okna narzędzi i jego ikonę) na krawędzi obszaru dokumentu. Okno narzędzia wysuwa się, gdy użytkownik zatrzyma na karcie.

- **Automatycznie widoczne** okien narzędzi automatycznie wyświetlane po innej części interfejsu użytkownika, takich jak edytor jest uruchamiana, lub uzyska fokus.

- **Zmiennoprzecinkowe** okna narzędzi, umieść kursor poza IDE. Jest to przydatne w przypadku konfiguracji z wielu monitorów.

- **Dokument z kartami** okien narzędzi może być zadokowane w dokumencie dobrze. Jest to przydatne w przypadku dużych okien, takie jak przeglądarki obiektów, które wymagają więcej miejsca niż pozwala Dokowanie do krawędzi ramki.

  ![Narzędzie Stany okien w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702 01_ToolWindowStates")

  **Stany okien narzędzi w programie Visual Studio**

#### <a name="single-instance-and-multi-instance"></a>Jednym wystąpieniu i obejmujące wiele wystąpień
 Okna narzędzi są jednego wystąpienia lub wielu wystąpień. Niektóre narzędzia w jednym wystąpieniu systemu windows może być skojarzony z oknem aktywnego dokumentu, podczas gdy obejmujące wiele wystąpień narzędzia windows może nie. Obejmujące wiele wystąpień narzędzia windows odpowiadać na polecenia oknie/nowe okno, tworząc nowe wystąpienie klasy okna. Na poniższym obrazie przedstawiono Włączanie polecenie nowe okno, gdy wystąpienie okno jest aktywne okna narzędzi:

 ![Okna narzędzi, włączanie poleceń w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")

 **Okno narzędzia umożliwiające polecenia "Nowe okno", gdy wystąpienie okno jest aktywne**

 Okien narzędzi w jednym wystąpieniu mogą ukryte lub pokazane, gdy wiele wystąpień narzędzia windows może być zamknięte, a także ukryte. Wszystkie okna narzędzi może być zadokowane łączone przez karty, zmiennoprzecinkowego lub Ustaw jako okna podrzędnego interfejsu wielu dokumentów (MDI) (podobnie do okna dokumentu). Wszystkie okna narzędzi powinna odpowiadać na polecenia zarządzania odpowiednie okna w menu Okno:

 ![Okno polecenia zarządzania w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702 03_WindowManagementControls")

 **Polecenia zarządzania okna w menu Okno programu Visual Studio**

#### <a name="document-specific-tool-windows"></a>Okna narzędzi specyficznych dla dokumentu
 Niektóre narzędzia systemu windows są przeznaczone do zmienić w zależności od danego typu dokumentu. Te okna stale aktualizowana w celu odzwierciedlenia funkcje mające zastosowanie do aktywnego okna dokumentu w IDE.

 Przykłady okien narzędzi, których zawartość zmieniać, aby odzwierciedlić wybrane edytora są przybornika i tworzenie konspektu dokumentu. Te okna Pokaż znak wodny, gdy Edytor ma fokus, oferuje kontekstu do okna.

#### <a name="navigable-list-tool-windows"></a>Listy można nawigować okien narzędzi
 Niektóre narzędzia systemu windows, wyświetlanie listy można nawigować elementów, które użytkownik może interakcyjnie przeprowadzić. W tym typie okna zawsze należy opinie dla bieżącego elementu na liście, nawet jeśli okno jest nieaktywny. Lista powinna odpowiadać na **GoToNextLocation** i **GoToPrevLocation** polecenia również zmieniając aktualnie wybranego elementu w oknie

 Przykłady okien narzędzi można nawigować listy Eksploratora rozwiązań i w oknie Znajdź wyniki.

### <a name="tool-window-types"></a>Typy okien narzędzi

#### <a name="common-tool-windows-and-their-functions"></a>Wspólne okna narzędzi i ich funkcje

|Typ|Okna narzędzi|Funkcja|
|----------|-----------------|--------------|
|**Hierarchia**|Eksplorator rozwiązań|Hierarchiczne drzewo, które wyświetla listę dokumenty zawarte w projektach, różne pliki i elementy rozwiązania. Wyświetlanie elementów w obrębie projektów jest definiowany przez pakiet, który jest właścicielem tego typu projektu (na przykład typy na podstawie odwołania, na podstawie katalogu lub trybu mieszanego).|
|**Hierarchia**|Widok klas|Hierarchiczne drzewo, klasy i różne elementy w zestawie roboczym dokumentów, niezależnie od same pliki.|
|**Hierarchia**|Server Explorer|Hierarchiczne drzewo, które wyświetla wszystkie połączenia serwerów i danych w rozwiązaniu.|
|**Hierarchia**|Konspekt dokumentu|Hierarchiczna struktura aktywnego dokumentu.|
|**Siatka**|Właściwości|Siatka, który wyświetla listę właściwości dla wybranego obiektu, wraz z selektorami wartość, aby edytować te właściwości.|
|**Siatka**|Lista zadań|Siatka, który umożliwia użytkownikowi tworzenie/edytowanie/usuwanie zadań i komentarzy.|
|**Zawartość**|Pomoc|Okno które umożliwia użytkownikom dostęp do różnych metod uzyskiwania pomocy z "Jak mogę?" wideo na forach MSDN.|
|**Zawartość**|Dynamiczna pomoc|Okna narzędzi, które wyświetla łącza, które ułatwiają — tematy mające zastosowanie do bieżącego zaznaczenia.|
|**Zawartość**|Przeglądarka obiektów|Zestaw ramek dwie kolumny z listy składników obiekt hierarchiczny, w okienku po lewej stronie i obiektu, właściwości i metod w prawej kolumnie.|
|**Okno dialogowe**|Znajdź, zaawansowane wyszukiwanie|Okno dialogowe, które umożliwia użytkownikom znajdowanie lub Znajdź i Zamień w różnych plików w ramach rozwiązania.|
|**Inne**|Przybornik|Okno narzędzia używane do przechowywania elementów, które zostaną usunięte na powierzchni projektowania, zapewniając spójny źródła przeciągania dla wszystkich projektantów.|
|**Inne**|Strona początkowa|Portal użytkowników w programie Visual Studio, dostęp do źródeł wiadomości dla deweloperów, Pomoc programu Visual Studio i ostatnich projektów. Użytkownicy mogą również tworzyć niestandardowych stron początkowych kopiowania pliku StartPage.xaml z katalogu program files "Common7\IDE\StartPages\" Visual Studio do folderu StartPages w katalogu dokumenty programu Visual Studio, a następnie albo edytując XAML ręcznie lub otwierając go w programie Visual Studio lub innego edytora kodu.|
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Automatyczne||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Natychmiastowe||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Dane wyjściowe|W oknie danych wyjściowych można zawsze wtedy, gdy masz zdarzenia tekstową lub stan, aby zadeklarować.|
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Pamięć||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Punkty przerwania||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Uruchomienie||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Dokumenty||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Stos wywołań||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Zmienne lokalne||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Czujki||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Dezasemblacji||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Rejestruje||
|**Debuger:** grupy specyficzne dla zadania debugowania i monitorowania aktywności systemu Windows|Wątki||

##  <a name="BKMK_DocumentEditorConventions"></a> Konwencje Edytor dokumentów

### <a name="document-interactions"></a>Interakcje z dokumentu
 "Dobrze dokumentu" największą ilość miejsca w środowisku IDE i jest, gdy użytkownik ma skupione ich uwagi w celu wykonania swoich zadań i wspierana przez dodatkowe narzędzia windows. Edytory dokumentu reprezentują podstawowych jednostek pracy, które użytkownik otwiera i zapisuje w programie Visual Studio. Zachowują silne poczucie wybór związany z Eksploratora rozwiązań lub innymi oknami aktywnej hierarchii. Użytkownik powinien móc wskazywały na jeden z tych oknach hierarchii i wiedzieć, gdzie znajduje się dokument i jej zależności do rozwiązania, projektu lub inny obiekt główny dostarczonej przez pakiet Visual Studio.

 Edytowanie dokumentów wymaga spójne środowisko użytkownika. Aby umożliwić użytkownikowi skupić się na wykonywanego zadania zamiast zarządzania systemem Windows i znajdowanie poleceń, wybierz Udokumentowanie strategii widoku, która najlepiej pasuje do zadania użytkownika do edycji tego typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Typowe interakcje dobrze dokumentu

-   Obsługa modelu interakcji spójne we wspólnym **nowy plik** i **Otwórz plik** środowisk.

-   Zaktualizuj pokrewne funkcje w powiązanych systemach windows i menu, po otwarciu okna dokumentu.

-   Polecenia menu są odpowiednio zintegrowane wspólne menu takich jak **Edytuj**, **Format**, i **widoku** menu. Jeśli dostępnych rozległe wyspecjalizowane poleceń, nowe menu mogą być tworzone która jest widoczna tylko wtedy, gdy dokument ma fokus.

-   Osadzonym pasku narzędzi mogą być umieszczane w górnej części edytora. To jest posiadanie oddzielnych narzędzi, który pojawia się poza edytora.

-   Zawsze zachować wybór w Eksploratorze rozwiązań lub podobne aktywne okno hierarchii.

-   Dwukrotne kliknięcie dokumentu w Eksploratorze rozwiązań należy wykonywać ta sama akcja co **Otwórz**.

-   Jeśli więcej niż jeden z nich mogą być używane w danym typie dokumentu, użytkownik powinien móc zastąpić, lub zresetuj domyślne działanie na typ danego dokumentu przy użyciu **Otwórz za pomocą** okno dialogowe, kliknij prawym przyciskiem myszy plik i wybierając **Otwórz Za pomocą** z menu skrótów.

-   Nie twórz dobrze kreatora w dokumencie.

### <a name="user-expectations-for-specific-document-types"></a>Oczekiwania użytkowników dla określonych typów dokumentów
 Istnieje kilka różnych typów podstawowych edytorów dokumentu, a każda ma zestaw interakcji, które są zgodne z innymi osobami z tego samego typu.

- **Edytor tekstowy:** Edytor kodu, plików dziennika

- **Powierzchni projektowej:** WPF formularzy projektanta Windows forms

- **Edytor stylów okna dialogowego:** projektanta manifestu, właściwości projektu

- **Projektant modeli:** projektanta przepływów pracy, takim jak codemap, diagram architektury, postępu

  Istnieje kilka typów innych niż edytora, które również korzystają z dokumentu. Podczas nie edytuje samych dokumentach, muszą one wykonaj standardowych interakcji dla okna dokumentu.

- **Raporty:** IntelliTrace raportu, raport funkcji Hyper-V raportów profilera

- **Pulpit nawigacyjny:** Centrum diagnostyki

#### <a name="text-based-editors"></a>Edytory oparte na tekście

-   Dokument uczestniczy w modelu kartę (wersja zapoznawcza), co umożliwia wyświetlenie podglądu dokumentu bez konieczności otwierania go.

-   Strukturę dokumentu mogą być reprezentowane w ramach pomocnika okna narzędzi, takich jak konspekt dokumentu.

-   Technologia IntelliSense (jeśli jest to konieczne) będzie działać spójnie przy użyciu innych edytorów kodu.

-   Wyskakujące okienka lub pomocniczej interfejsu użytkownika wykonaj podobny — style i wzorców dla istniejących podobnym interfejsem użytkownika, takie jak funkcja CodeLens.

-   Komunikaty dotyczące stanu dokumentu zostanie wyświetlony w kontrolce pasek informacyjny w górnej części dokumentu lub na pasku stanu.

-   Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu **Narzędzia > Opcje** stronie udostępnionej strony czcionek i kolorów lub jeden specyficzne dla edytora.

#### <a name="design-surfaces"></a>Powierzchnia projektu

-   Pusty projektanta powinien mieć znak wodny na powierzchni wskazujący, jak rozpocząć pracę.

-   Przełączanie widoku mechanizmów będą zgodne z istniejących wzorców, takich jak kliknij dwukrotnie, aby otworzyć Edytor kodu lub karty w oknie dokumentu, umożliwiając interakcje z obu okienka.

-   Dodawanie elementów do powierzchni projektowej należy przeprowadzić za pomocą przybornika, chyba że okna narzędzi wysoce jest wymagana.

-   Elementy na powierzchnię będą zgodne z modelu zaznaczenia spójne.

-   Paski narzędzi osadzony zawierają polecenia tylko wtedy, nie Typowe polecenia specyficzne dla dokumentu, takie jak **Zapisz**.

#### <a name="dialog-style-editors"></a>Edytory stylu okna dialogowego

-   Układ formantu należy stosować konwencje układu okna dialogowego normalnego.

-   Karty w edytorze nie powinny odpowiadać wygląd kart dokumentu, powinny one odpowiadać jeden z dwóch stylów dozwolonych kartę posługiwanie się nimi.

-   Użytkownicy muszą mieć możliwość interakcji z kontrolkami, za pomocą klawiatury. albo przez aktywowanie edytora i tabulacji za pomocą kontrolki lub przy użyciu standardowych klawiszy skrótu.

-   Projektant należy używać typowych Zapisz model. Nie Zapisz ogólny lub zatwierdzenia przyciski powinny zostać umieszczone na powierzchni, mimo że inne przyciski mogą być odpowiednie.

#### <a name="model-designers"></a>Model Designer

-   Pusty projektanta powinien mieć znak wodny na powierzchni wskazujący, jak rozpocząć pracę.

-   Dodawanie elementów do powierzchni projektu powinna być wykonywana za pomocą przybornika.

-   Elementy na powierzchnię będą zgodne z modelu zaznaczenia spójne.

-   Paski narzędzi osadzony zawierają polecenia tylko wtedy, nie Typowe polecenia specyficzne dla dokumentu, takie jak **Zapisz**.

-   Legenda może pojawić się na powierzchni indykatywne lub na znak wodny.

-   Użytkownik musi mieć możliwość dostosowania wyglądu czcionki kolorów przy użyciu **Narzędzia > Opcje** stronie udostępnionej strony czcionek i kolorów lub jeden specyficzne dla edytora.

#### <a name="reports"></a>Raporty

-   Raporty są zwykle tylko do informacji i nie są używane w modelu zapisu. Jednak mogą one obejmować interakcji, takie jak łącza do innych istotnych informacji lub sekcje, w których rozwijać i zwijać.

-   Większość poleceń na powierzchni powinien być hiperlinki. Ponadto nie przyciski.

-   Układ należy dołączyć nagłówek i postępuj zgodnie z wytycznymi układ raportu standardowego.

#### <a name="dashboards"></a>Pulpity nawigacyjne

-   Pulpity nawigacyjne nie mają model interakcji samodzielnie, ale służyć jako sposób oferują szeroką gamą innych narzędzi.

-   Nie uczestniczą w modelu zapisu.

-   Użytkownicy muszą być możliwość interakcji z kontrolkami przy użyciu klawiatury, aktywacja w edytorze i tabulacji za pomocą kontrolki lub przy użyciu standardowych klawiszy skrótu.

##  <a name="BKMK_Dialogs"></a> Okna dialogowe

### <a name="introduction"></a>Wprowadzenie
 Okien dialogowych w programie Visual Studio zazwyczaj powinna obsługiwać jedną jednostkę dyskretnych danego użytkownika, a następnie można odrzucić.

 Jeśli już wiesz, że muszą się okno dialogowe, masz trzy opcje, w kolejności priorytetu:

1. Integracja funkcji do jednego z udostępnionego okien dialogowych w programie Visual Studio.

2. Utwórz własne okna dialogowego za pomocą wzorca w istniejących podobne okno dialogowe.

3. Utwórz nowe okno dialogowe, następujące interakcji i wytyczne dotyczące układu.

   W tym temacie opisano, jak wybrać wzorzec poprawne okna dialogowego, w ramach przepływów pracy programu Visual Studio i typowych Konwencji projektu okna dialogowego.

### <a name="themes"></a>Motywy
 Okna dialogowe w programie Visual Studio, wykonaj jedną z dwa podstawowe style:

#### <a name="standard-unthemed"></a>Standard (unthemed)
 Większość okna dialogowe są standardowe narzędzie okien dialogowych i powinny być unthemed. Nie nie szablon re wspólnych formantów ani próba utworzenia stylizowane "nowoczesnych typów" przycisków lub kontrolek. Formanty i wygląd przeglądarki chrome, postępuj zgodnie z [standardowych wytycznych interakcji pulpitu Windows dla okien dialogowych](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx).

#### <a name="themed"></a>Motywów
 Specjalizacja "podpis" w oknach dialogowych, może być motywów. Motywem okien dialogowych mają charakterystyczny wygląd ma również niektóre wzorce interakcji specjalne skojarzonych ze stylem. Motyw okna dialogowego tylko wtedy, gdy spełnia następujące wymagania:

- Okno dialogowe jest wspólne środowisko, który będzie widoczny i używany często ani przez wielu użytkowników (na przykład **nowy projekt** okna dialogowego.

- Okno dialogowe zawiera elementy marki produktu wyraźną (na przykład **ustawienia konta** okna dialogowego).

- Okno dialogowe pojawia się jako integralną częścią większej przepływ, który zawiera inne motywem okien dialogowych (na przykład **Dodaj podłączoną usługę** okna dialogowego).

- Okno dialogowe jest ważną częścią środowiska, które pełnią rolę strategiczną podwyższania poziomu lub rozróżnienie tych wersji produktu.

  Podczas tworzenia tematu okna dialogowego, Użyj kolorów odpowiednie środowisko, a następnie postępuj zgodnie z poprawną układ i wzorce interakcji. (Zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>Okno dialogowe projektu
 Dobrze zaprojektowana okien dialogowych wziąć pod uwagę następujące elementy:

-   Zadanie użytkownika ze wsparcia technicznego

-   Okno dialogowe style tekstu, język i terminologia

-   Konwencje dotyczące interfejsu użytkownika i kontrolki wyboru

-   Układ wizualizacji specyfikacji i kontrola wyrównania

-   Dostęp za pomocą klawiatury

#### <a name="content-organization"></a>Organizowanie zawartości
 Należy wziąć pod uwagę różnice między te podstawowe rodzaje okien dialogowych:

-   [Proste okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) przedstawić kontrolek w jednym modalny. Prezentacja może obejmować zmian wzorców kontrolek złożonych, takimi jak formant pola wyboru lub pasek ikon.

-   [Wielowarstwowe okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) są używane do w pełni wykorzystać powierzchnię ekranu podczas pojedynczy interfejs użytkownika obejmuje wiele grup formantów. Grupowania w oknie dialogowym są "warstwowe" za pomocą kontrolki karty, kontrolki listy lub przycisków, aby użytkownik może wybrać grupowania można wyświetlić w danej chwili.

-   [Kreatorzy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) są przydatne w przypadku kierowania użytkownika w logicznej kolejności kroków do wykonania zadania. Szereg opcji są oferowane w panelach sekwencyjnych, czasami wprowadzenie do różnych przepływów pracy ("gałęzi") zależy od wybranej w poprzednim panelu.

####  <a name="BKMK_SimpleDialogs"></a> Proste okien dialogowych
 Proste okno dialogowe jest prezentację kontrolki w pojedynczej modalny. W tej prezentacji mogą obejmować odmiany wzorców kontrolek złożonych, takie jak formant pola wyboru. W oknach dialogowych prosty postępuj zgodnie z standardowego układu ogólne, a także dowolnego określonego układu wymagane dla grupowań złożonego formantu.

 ![Proste okno dialogowe w programie Visual Studio](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704 01_CreateStrongNameKey")

 **Utwórz klucz silnej nazwy jest przykładem proste okno dialogowe, w programie Visual Studio.**

####  <a name="BKMK_LayeredDialogs"></a> Okna dialogowe warstwowej
 Okna dialogowe warstwowej obejmują karty, pulpity nawigacyjne i osadzone drzewa. Służą one do zmaksymalizowania nieruchomości, gdy istnieje wiele grup formantów oferowana w pojedynczy interfejs użytkownika. Grupowania są warstwowe, tak aby użytkownik może wybrać grupowania można zobaczyć w dowolnym momencie.

 W najprostszym przypadku mechanizmu przełączania między grupowania jest formantem karty. Brak dostępnych kilka rozwiązań alternatywnych. Zobacz Ustawianie priorytetów i warstw dla jak wybrać najbardziej odpowiedni styl.

 **Narzędzia > Opcje** okno dialogowe jest przykładem warstwowej okna dialogowego za pomocą drzewo embedded:

 ![Okno warstwowej w programie Visual Studio](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704 02_ToolsOptions")

 **Narzędzia > Opcje jest przykładem warstwowej okna dialogowego w programie Visual Studio.**

####  <a name="BKMK_Wizards"></a> Kreatorzy
 Kreatorzy są przydatne w przypadku kierowania użytkownika za pomocą Sekwencja logiczna kroków w celu wykonania zadania. Szereg opcji są oferowane w panelach sekwencyjnych, a użytkownik musi nadal za pośrednictwem danego kroku przed przejściem do następnego. Gdy wystarczające domyślne ustawienia są dostępne, **Zakończ** przycisk jest aktywny.

 Modalne kreatory są używane do wykonywania zadań które:

-   Zawiera Podręcznik rozgałęziania, w których różnych ścieżek są oferowane w zależności od wyborów użytkownika

-   Zawierają zależności między krokami, w którym kolejne kroki zależą od dane wejściowe użytkownika z poprzednim czynności

-   Wystarczająco skomplikowane, że interfejs użytkownika powinien być używany do wyjaśnienia z opcji dostępnych i możliwych wartości w każdym kroku

-   Są transakcyjne wymagające zestaw kroków do wykonania w całości przed wszelkie zmiany zostaną zatwierdzone

### <a name="common-conventions"></a>Typowych konwersji
 Aby osiągnąć optymalną i funkcjonalność usługi okna dialogowe, postępuj zgodnie z tych konwencji na rozmiar okna dialogowego, pozycja, standardów, konfiguracji kontroli i wyrównanie, interfejs użytkownika tekstu, paski tytułu, przycisków kontrolnych i klucze dostępu.

 Aby uzyskać wskazówki specyficzne dla układu, zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Rozmiar
 Okna dialogowe powinien się zmieścić w ramach minimalna rozdzielczość ekranu 1024 x 768, a rozmiar okna dialogowego początkowa nie może przekraczać 900 x 700 pikseli. Okna dialogowe może być o zmiennym rozmiarze, ale nie jest wymagane.

 Brak zaleceń dwóch w oknach dialogowych o zmiennych rozmiarach:

1.  Minimalny rozmiar jest zdefiniowany dla okna dialogowego, Optymalizacja pod kątem zestaw formantów bez przycinania, a Dostosuj, aby pomieścić wzrostu uzasadnione lokalizacji.

2.  Czy rozmiar skalowane użytkownika są utrwalane między sesjami. Na przykład jeśli użytkownik skaluje się okno dialogowe 150% kolejnym uruchomieniu okna dialogowego zostaną wyświetlone na 150%.

#### <a name="position"></a>Pozycja
 Okna dialogowe musi znajdować się wyśrodkowany w środowisku IDE przy pierwszym uruchomieniu. W oknach dialogowych nie o zmiennym rozmiarze, nie jest wymagane, trwałość ostatniej pozycji w oknie dialogowym, dlatego pojawi się ono wyśrodkowane na kolejnych uruchomień. W oknach dialogowych o zmiennym rozmiarze rozmiar, powinny zostać utrwalone na kolejnych uruchomień. O zmiennym rozmiarze okien dialogowych, które są modalne pozycji nie być konieczne utrwalone. Wyświetlanie ich wyśrodkowany w IDE zapobiega możliwości okna dialogowego, które pojawiają się w pozycji nieprzewidywalne lub bezużyteczne po zmianie konfiguracji wyświetlania użytkownika. Dla Niemodalne okna dialogowe, które może być przeniesiony pozycji użytkownika należy utrzymywać na kolejne, zostanie uruchomiona, okno dialogowe może często używane w ramach większego przepływu pracy.

 Gdy okien dialogowych musi zduplikować innych oknach dialogowych, najwyższego poziomu okna dialogowego należy zastosować kaskadowo po prawej stronie i w dół od elementu nadrzędnego, tak aby można ją widocznych dla użytkownika, przejście do nowego miejsca.

#### <a name="modality"></a>Modalności
 Trwa modalne oznacza, że wymagane do ukończenia, lub Anuluj okno dialogowe przed kontynuowaniem użytkowników. Ponieważ modalne okna dialogowe Zablokuj użytkownikowi możliwość interakcji z innymi częściami środowiska, przepływ zadań Twojej funkcji powinny być używane jako rzadko, jak to możliwe. Gdy konieczne jest operacją modalne, Visual Studio ma liczbę udostępnionych okien dialogowych, które można zintegrować funkcje do. Jeśli musisz utworzyć nowe okno dialogowe, oparte na wzorcu interakcji istniejącego okna dialogowego o podobnych możliwościach.

 Gdy użytkownicy potrzebują do wykonywania dwóch działań jednocześnie, takich jak **znaleźć** i **Zastąp** podczas zapisywania nowego kodu, okno dialogowe powinna być niemodalne, dzięki czemu użytkownik może łatwo przełączać się między nimi. Visual Studio zazwyczaj używa okien narzędzi dla tego rodzaju Obsługa edytora połączonego zadania.

#### <a name="control-configuration"></a>Konfiguracja kontroli
 Być zgodne z istniejących konfiguracji kontroli, które osiągnąć to samo w programie Visual Studio.

#### <a name="title-bars"></a>Paski tytułu

- Tekst na pasku tytułu muszą odzwierciedlać nazwę polecenia, który go uruchomił.

- Brak ikony, należy używać w paski tytułu okna dialogowego. W przypadkach, w którym system wymaga jednego Użyj logo programu Visual Studio.

- Okna dialogowe nie powinny mieć minimalizowanie lub maksymalizowanie przycisków.

- Przyciski pomocy na pasku tytułu są przestarzałe. Nie należy dodawać ich do nowego okna dialogowe. Jeśli istnieją one powinien być uruchamiany tematu pomocy, koncepcyjnie odpowiednią do zadania.

  ![Tytuł paska specyfikacji dla programu Visual Studio](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704 03_TitleBarSpecs")

  **Specyfikacje wytyczne dotyczące paski tytułu w oknach dialogowych programu Visual Studio.**

#### <a name="control-buttons"></a>Kontrolki przycisków
 Ogólnie rzecz biorąc **OK**/**anulować**/**pomocy** przyciski powinny być ułożone poziomo w prawym dolnym rogu okna dialogowego. Alternatywne pionowy stos jest dozwolone, gdy okno dialogowe ma kilka przycisków w dolnej części okna dialogowego, które przedstawiałoby visual omyłkowe przycisków kontrolnych.

 ![Kontrolowanie konfiguracje przycisku w programie Visual Studio](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704 04_ControlButtonConfig")

 **Dopuszczalne konfiguracje dla przycisków kontrolki w oknach dialogowych programu Visual Studio**

 Okno dialogowe musi zawierać domyślnego formant przycisku. Aby określić najważniejsze polecenie, aby użyć domyślnej, należy wybrać spośród następujących opcji (wymienione w kolejności):

- Wybierz polecenie najbezpieczniejszy i najbardziej bezpieczne jako domyślny. Oznacza to, wybierając polecenie najbardziej prawdopodobne zapobiec utracie danych i uniknąć dostępu do systemu niezamierzone.

- Jeśli utrata danych i zabezpieczenia nie są czynniki, wybierz polecenie domyślne, w oparciu o wygody. Tym najprawdopodobniej polecenie jako domyślny poprawi przepływu pracy użytkownika, gdy okno dialogowe obsługuje częste lub powtarzających się zadań.

  Należy unikać egzaminacyjnym trwale destrukcyjne dla domyślnego polecenia. Jeśli ma takiego polecenia, wybierz polecenie bezpieczniejsze jako domyślny.

#### <a name="access-keys"></a>Klucze dostępu
 Nie używaj klawiszy dostępu dla **OK**/**anulować**/**pomocy** przycisków. Przyciski te są mapowane do klawiszy skrótów domyślnie:

|Nazwa przycisku|Skrót klawiaturowy|
|-----------------|-----------------------|
|OK|Enter|
|Anuluj|Esc|
|Pomoc|F1|

#### <a name="imagery"></a>Obraz
 Rzadko używać obrazów w oknach dialogowych. Nie należy używać dużych ikon w oknach dialogowych jedynie w celu użycia miejsca. Korzystanie z obrazów, tylko wtedy, gdy są ważnym elementem przekazywania wiadomości do użytkownika, np. ikon ostrzeżenie lub stanie animacji.

###  <a name="BKMK_PrioritizingAndLayering"></a> Ustalanie priorytetów i Układanie warstwowo

#### <a name="prioritizing-your-ui"></a>Priorytetyzowanie interfejs użytkownika
 Może być konieczne przenieść niektóre elementy interfejsu użytkownika na czele i umieścić zachowanie bardziej zaawansowane i (w tym polecenia zasłoniętej) opcje w oknach dialogowych. Ożyw najczęściej używane funkcje oprogramowania forefront ilości miejsca dla niego i oznaczania go jako widocznego domyślnie w Interfejsie użytkownika etykietę tekstową, gdy okno dialogowe jest wyświetlane.

#### <a name="layering-your-ui"></a>Układanie warstwowo interfejs użytkownika
 Jeśli już wiesz, że okno dialogowe jest konieczne, ale powiązane funkcje, które mają być widoczne dla użytkownika wykracza poza mogą być wyświetlane w oknie dialogowym prostego, następnie należy warstwy interfejsu użytkownika. Najbardziej typowe metody warstwowe, które korzysta z programu Visual Studio są karty i korytarzach lub pulpitów nawigacyjnych. W niektórych przypadkach może być odpowiednie regiony, które można rozwijać i zwijać. Funkcje adaptacyjnego sterowania interfejsu użytkownika zwykle nie jest zalecane w programie Visual Studio.

 Istnieją zalety i wady różnych metod przez kontrolę nad jak karta Układanie warstwowo interfejsu użytkownika. Przejrzyj listę, aby upewnić się, wybierają technika warstwowe, która jest odpowiednia do swojej sytuacji.

##### <a name="tabbing"></a>TAB

|Mechanizm przełączania|Zalety i właściwego użycia|Wady i nieodpowiednie użycie|
|-------------------------|------------------------------------|-----------------------------------------|
|Kontrolki karty|Logiczne grupowanie stron okien dialogowych w powiązane zestawy<br /><br /> Przydatne w przypadku mniej niż pięć (lub liczba kart, które mieszczą się w jednym wierszu w oknie dialogowym) stron pokrewnych formantów w oknie dialogowym<br /><br /> Karta musi być krótki: jeden lub dwa wyrazy, które można łatwo zidentyfikować zawartości<br /><br /> Typowe style okna dialogowego systemu<br /><br /> Przykład: **folder Eksplorator plików > element właściwości**|Wprowadzanie opisowymi etykietami krótki może okazać się trudne<br /><br /> Na ogół nie skalować ostatnie pięć kart w jednym oknie dialogowym<br /><br /> Nieodpowiedni, jeśli masz zbyt wiele kart dla jednego wiersza; Użyj alternatywnych warstwowe techniki<br /><br /> Nie jest rozszerzalna|
|Nawigacyjny pasek boczny|Proste przełączania urządzenia, które może obsłużyć więcej kategorii niż karty<br /><br /> Niezhierarchizowana lista kategorii (bez hierarchii)<br /><br /> Rozszerzalna<br /><br /> Przykład: **dostosować... > Dodaj — polecenie**|Nie dobrze wykorzystane miejsce w poziomie, jeśli ma mniej niż trzy grup<br /><br /> Zadanie może być lepiej dopasowany do listy rozwijanej|
|Kontrolka drzewa|Umożliwia nieograniczony kategorii<br /><br /> Umożliwia grupowanie i/lub hierarchia kategorii<br /><br /> Rozszerzalna<br /><br /> Przykład: **Narzędzia > Opcje**|Wielokrotnie zagnieżdżone hierarchie mogą powodować nadmierne przewijanie w poziomie<br /><br /> Program Visual Studio zawiera overabundance widoków drzewa|
|Kreator|Pomoc ukończenie zadania przez przeprowadzi opartego na zadaniach, kolejne kroki. Kreator przedstawia zadania wysokiego poziomu, a poszczególne zespoły reprezentują podzadania wymaganych do zrealizowania całego zadania.<br /><br /> Przydatne, gdy zadanie przekracza granice interfejsu użytkownika, jak po użytkownik przeciwnym razie byłoby trzeba użyć wielu edytory i narzędzi systemu windows do ukończenia zadania<br /><br /> Przydatne, gdy zadanie wymaga rozgałęzianie<br /><br /> Przydatne, gdy zadanie zawiera zależności między krokami<br /><br /> Parametr jest przydatne, gdy kilka podobnych zadań z rozwidlenia decyzji co do przedstawienia w jednym okno dialogowe, aby zmniejszyć liczbę różnych podobne okien dialogowych.|Nieodpowiednie dla dowolnego zadania, które nie wymagają sekwencyjnego przepływu pracy<br /><br /> Użytkownicy mogą stać się przeciążeniu i mylić przez kreatora, za pomocą zbyt wiele kroków<br /><br /> Kreatorzy założenia mają ograniczoną powierzchnię ekranu|

##### <a name="hallways-or-dashboards"></a>Korytarzach lub pulpitów nawigacyjnych
 Korytarzach i pulpity nawigacyjne są okien dialogowych lub paneli, które służą jako uruchamianie punktów do innych okien dialogowych i systemu windows. Dobrze zaprojektowana "korytarzowych" prezentuje natychmiast tylko najbardziej typowe opcje, poleceń i ustawień, co pozwala na łatwe wykonywanie typowych zadań. Jak korytarzowych rzeczywistych zapewnia drzwi do dostępu do pomieszczenia za ich, w tym miejscu mniej znane interfejsu użytkownika są zbierane do oddzielnych "pomieszczeń" (często inne okna dialogowe) powiązanych funkcji, które są dostępne z głównym telewizora.

 Alternatywnie interfejs użytkownika, który oferuje wszystkie funkcje dostępne w jednej kolekcji, zamiast refaktoryzacji mniej typowe funkcje w różnych lokalizacjach jest po prostu pulpitu nawigacyjnego.

 ![Pojęcie o tym samym korytarzu w programie Outlook](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704 08_Hallway")

 **Tym samym korytarzu koncepcja udostępnianie dodatkowy interfejs użytkownika w programie Outlook**

##### <a name="adaptive-ui"></a>Funkcje adaptacyjnego sterowania interfejsu użytkownika
 Pokazywanie lub ukrywanie interfejsu użytkownika na podstawie użycia lub przez użytkownika samodzielnie zgłaszane jest innym sposobem przedstawiania niezbędne interfejsu użytkownika innych części są ukryte. Nie jest to zalecane w programie Visual Studio, algorytmy dotyczących decydowania, kiedy pokazać lub ukryć interfejsu użytkownika może być trudne, a zasady zawsze będą nieprawidłowe dla niektórych zestaw przypadków.

##  <a name="BKMK_Projects"></a> Projekty

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
 Projekty zazwyczaj klasyfikowania siebie jako na podstawie odwołania (możliwe do utrwalenia tylko odwołania do elementów projektu w magazynie) na poziomie katalogu (mógł zachować tylko elementy projektu fizycznie przechowywane w hierarchii projektu), lub mieszany (możliwe do utrwalenia odwołania lub elementów fizycznych). Jednocześnie w ramach wszystkich trzech typów projektów obsługuje IDE **Eksploratora rozwiązań**.

 Z punktu widzenia przeciągnij i upuść stosuje następujące właściwości dla każdego typu projektu w ramach **Eksploratora rozwiązań**:

- **Na podstawie odwołań projektu:** kluczowy punkt to, że projekt jest przeciąganie wokół odwołanie do elementu w magazynie. Jeśli odwołanie do projektu działa jako źródło dla operacji przenoszenia, go tylko należy usunąć odwołanie do elementu z projektu. Nie element faktycznie można usunąć z dysku twardego. Jeśli działa na podstawie odwołań projektu jako obiekt docelowy operacji przenoszenia (lub kopiowania), dodawaj odwołania do oryginalnego elementu źródłowego bez wprowadzania prywatną kopię elementu.

- **Oparte na katalog projektu:** projekt z punktu widzenia przeciągania i upuszczania, przeciąga wokół elementu fizycznego, a nie odwołanie. Jeśli projekt na podstawie katalogu działa jako źródło dla operacji przenoszenia, powinny kończyć się się usunięcie elementu fizycznego z dysku twardego, a także usunięcie go z projektu. Jeśli działa na poziomie katalogu projektu jako obiekt docelowy operacji przenoszenia (lub kopiowania), jego Utwórz kopię elementu źródłowego, w lokalizacji docelowej.

- **Projekt docelowy mieszane:** z punktu widzenia przeciągania i upuszczania, zachowanie tego typu projektu zależy od rodzaju elementu przeciąganie (odwołanie do elementu w magazynie) albo sam element. Poprawne zachowanie elementów fizycznych i odwołania do opisanych powyżej.

  Gdyby tylko jeden typ projektu w **Eksploratora rozwiązań**, wyniósłby operacji przeciągania i upuszczania proste. Ponieważ każdy system projektu ma możliwość definiowania zachowanie przeciągnij i upuść, niektóre wytyczne dotyczące (oparte na zachowanie przeciągnij i upuść Eksploratora Windows) powinna znajdować się zapewniają przewidywalne działanie:

- Niezmodyfikowane operacji przeciągania **Eksploratora rozwiązań** (gdy Ctrl ani klawisze Shift nie są przechowywane w dół) powinno dawać wynik operacji przenoszenia.

- Operacja przeciągania SHIFT również powinno spowodować operacji przenoszenia.

- Operacja przeciągania CTRL powinno spowodować operacji kopiowania.

- Systemy projektu odwołania i mieszanych obsługuje pojęcia dodanie link (lub odwołania) do elementu źródłowego. Kiedy te projekty są obiekt docelowy operacji przeciągania i upuszczania (gdy **klawisze Ctrl + Shift** przytrzymanie), powinno zwrócić odwołanie do element dodawany do projektu

  Nie wszystkie operacje przeciągania i upuszczania są za pośrednictwem różnych kombinacji projekty na podstawie odwołania, na podstawie katalogu i mieszanych. W szczególności jest pozwala poudawać umożliwia operacji przenoszenia między projektu na podstawie katalogu źródłowego i docelowego na podstawie odwołań projektu, ponieważ projekt oparty na katalog źródłowy będzie trzeba usunąć elementu źródłowego po ukończeniu przenoszenia. Następnie pojawiłyby docelowy projekt odniesienia z odwołaniem do usuniętego elementu.

  Jest również mylący do poudawać umożliwia operacji kopiowania między tymi typami projektów, ponieważ docelowy projekt odwołanie, nie należy wprowadzać niezależnej kopi elementu źródłowego. Podobnie Ctrl + Shift, przeciągając go do projektu na podstawie katalog docelowy nie powinien być dozwolony ponieważ nie można utrwalić odwołania do katalogu projektu. W przypadkach, gdy operacja przeciągania i upuszczania nie jest obsługiwana IDE powinna nie zezwalaj na liście i pokazania użytkownika nieupuszczalny kursor (pokazane w poniższej tabeli wskaźnika).

  Aby prawidłowo zaimplementować zachowanie przeciągnij i upuść, projekt źródłowy przeciągania musi komunikować się z natury (na przykład, jest ona na podstawie odwołania lub do katalogu?) do projektu docelowego. Informacja ta jest wskazywany przez format Schowka, oferowaną w źródle. Jako źródła przeciągania (lub operacji kopiowania Schowka) projekt powinno oferować się albo **CF_VSREFPROJECTITEM**S lub **CF_VSSTGPROJECTITEMS** odpowiednio w zależności od tego, czy projekt jest oparty na odwołanie lub na podstawie katalogu. Oba te formaty mają taką samą zawartość danych, co jest podobne do Windows **CF_HDROP** formatowania z tą różnicą, że listy ciągów, zamiast nazwy plików, są double -**NULL** zakończony listę  **Projref** ciągów (postaci zwracanej przez **IVsSolution::GetProjrefOfItem** lub **:: GetProjrefOfProject** odpowiednio).

  Jako element docelowy upuszczania (lub operacji wklejania Schowka) projektu należy zaakceptować oba te elementy **CF_VSREFPROJECTITEMS** i **CF_VSSTGPROJECTITEMS**, ale różni się dokładnie obsługi operacji przeciągania i upuszczania w zależności od charakteru projekt docelowy i projektu źródłowego. Projekt źródła deklaruje natury, czy oferuje **CF_VSREFPROJECTITEMS** lub **CF_VSSTGPROJECTITEMS**. Celem listy rozumie swój własny charakter i dlatego ma za mało informacji do podejmowania decyzji, aby, czy przenoszenie, kopiowanie lub łącze powinno być przeprowadzane. Użytkownik modyfikuje również kolejnej operacji przeciągania i upuszczania powinna być wykonywana przez naciśnięcie klawisza Ctrl, Shift, lub zarówno klawisze Ctrl i Shift. Ważne jest, aby element docelowy upuszczania prawidłowo wskazać operację, która odbędzie się wcześniej w jego **DragEnter** i **DragOver** metody. **Eksploratora rozwiązań** automatycznie wykrywa, czy projekt źródłowy i docelowy projekt są tym samym projekcie.

  Przeciąganie elementów projektu w wystąpieniach programu Visual Studio (na przykład z jednego wystąpienia devenv.exe do drugiego) specjalnie nie jest obsługiwane. **Eksploratora rozwiązań** także bezpośrednio powoduje to wyłączenie.

  Użytkownik powinien zawsze można ustalić skutek operacji przeciągania i upuszczania, wybierając element, przeciągając je do lokalizacji docelowej i przestrzegając następujących wskaźników myszy widocznego przed upuszczeniu elementu:

|Wskaźnik myszy|Polecenie|Opis|
|-------------------|-------------|-----------------|
|![Wskaźnik myszy ikonę "nie listy"](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706 01_MouseNoDrop")|Nie listy|Nie można usunąć elementu do określonej lokalizacji.|
|![Ikona "Kopiuj" myszy](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706 02_MouseCopy")|Kopiuj|Element zostanie skopiowany do lokalizacji docelowej.|
|![Ikona myszy "Przenieś"](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706 03_MouseMove")|Przenieś|Element zostanie przeniesiony do lokalizacji docelowej.|
|![Ikona "Dodaj odwołanie" myszy](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706 04_MouseAddRef")|Dodawanie odwołania|Odwołanie do wybranego elementu zostaną dodane do lokalizacji docelowej.|

#### <a name="reference-based-projects"></a>Projekty oparte na odwołanie
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które należy wykonać oparte na rodzaju źródła elementu i modyfikator klawiszy dla projektów docelowych na podstawie odwołania:

|||Element źródłowy: odwołania/łącze|Element źródłowy: element lub plik systemu fizycznego (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Nie modyfikatora|Akcja|Przenieś|Łącze|
|Nie modyfikatora|Docelowy|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Nie modyfikatora|Źródło|Usuwa odwołanie do oryginalnego elementu|Zachowuje oryginalnego elementu|
|Nie modyfikatora|Wynik|**DROPEFFECT_MOVE** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**DROPEFFECT_LINK** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|Shift + przeciągnięcie|Akcja|Przenieś|Nie listy|
|Shift + przeciągnięcie|Docelowy|Dodaje odwołanie do oryginalnego elementu|Nie listy|
|Shift + przeciągnięcie|Źródło|Usuwa odwołanie do oryginalnego elementu|Nie listy|
|Shift + przeciągnięcie|Wynik|**DROPEFFECT_MOVE** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|Nie listy|
|CTRL + przeciągnij|Akcja|Kopiuj|Nie listy|
|CTRL + przeciągnij|Docelowy|Dodaje odwołanie do oryginalnego elementu|Nie listy|
|CTRL + przeciągnij|Źródło|Odwołanie do elementu zachowuje|Nie listy|
|CTRL + przeciągnij|Wynik|**DROPEFFECT_COPY** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|Nie listy|
|Ctrl + Shift + przeciągnięcie|Akcja|Łącze|Łącze|
|Ctrl + Shift + przeciągnięcie|Docelowy|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Ctrl + Shift + przeciągnięcie|Źródło|Odwołanie do elementu zachowuje|Zachowuje oryginalnego elementu|
|Ctrl + Shift + przeciągnięcie|Wynik|**DROPEFFECT_LINK** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**DROPEFFECT_LINK** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|Ctrl + Shift + przeciągnięcie|Uwaga|Taka sama jak zachowanie przeciągnij i upuść skróty w Eksploratorze Windows.||
|Wytnij/Wklej|Akcja|Przenieś|Łącze|
|Wytnij/Wklej|Docelowy|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Wytnij/Wklej|Źródło|Odwołanie do elementu zachowuje|Zachowuje oryginalnego elementu|
|Wytnij/Wklej|Wynik|Element pozostaje w pierwotnej lokalizacji w magazynie|Element pozostaje w pierwotnej lokalizacji w magazynie|
|Kopiowanie/wklejanie|Akcja|Kopiuj|Łącze|
|Kopiowanie/wklejanie|Źródło|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu|
|Kopiowanie/wklejanie|Wynik|Odwołanie do elementu zachowuje|Zachowuje oryginalnego elementu|
|Kopiowanie/wklejanie|Akcja|Element pozostaje w pierwotnej lokalizacji w magazynie|Element pozostaje w pierwotnej lokalizacji w magazynie|

#### <a name="directory-based-projects"></a>Projekty oparte na katalog
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane w oparciu o charakter źródło elementu i modyfikator klawiszy, w przypadku projektów opartych na katalog docelowy:

|||Element źródłowy: odwołania/łącze|Element źródłowy: element lub plik systemu fizycznego (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Nie modyfikatora|Akcja|Przenieś|Przenieś|
|Nie modyfikatora|Docelowy|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Nie modyfikatora|Źródło|Usuwa odwołanie do oryginalnego elementu|Usuwa odwołanie do oryginalnego elementu|
|Nie modyfikatora|Wynik|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|Shift + przeciągnięcie|Akcja|Przenieś|Przenieś|
|Shift + przeciągnięcie|Docelowy|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Shift + przeciągnięcie|Źródło|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Shift + przeciągnięcie|Wynik|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|CTRL + przeciągnij|Akcja|Kopiuj|Kopiuj|
|CTRL + przeciągnij|Docelowy|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|CTRL + przeciągnij|Źródło|Odwołanie do elementu zachowuje|Odwołanie do elementu zachowuje|
|CTRL + przeciągnij|Wynik|**Kopiuj DROPEFFECT_** jest zwracana jako akcji z **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**Kopiuj DROPEFFECT_** jest zwracana jako akcji z **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|Ctrl + Shift + przeciągnięcie||Nie listy|Nie listy|
|Wytnij/Wklej|Akcja|Przenieś|Przenieś|
|Wytnij/Wklej|Docelowy|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Wytnij/Wklej|Źródło|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Wytnij/Wklej|Wynik|Element pozostaje w pierwotnej lokalizacji w magazynie|Element zostanie usunięty z oryginalnej lokalizacji w magazynie|
|Kopiowanie/wklejanie|Akcja|Kopiuj|Kopiuj|
|Kopiowanie/wklejanie|Docelowy|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Kopiowanie/wklejanie|Źródło|Zachowuje oryginalnego elementu|Zachowuje oryginalnego elementu|
|Kopiowanie/wklejanie|Wynik|Element pozostaje w pierwotnej lokalizacji w magazynie|Element pozostaje w oryginalnej lokalizacji dodatki magazynu|

#### <a name="mixed-target-projects"></a>Projektów docelowych mieszane
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także wycinania/kopiowania/wklejania), które powinny być wykonywane w oparciu o charakter naciśnięto dla projektów docelowych mieszane klucze elementów i modyfikator źródła:

|||Element źródłowy: odwołania/łącze|Element źródłowy: element lub plik systemu fizycznego (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Nie modyfikatora|Akcja|Przenieś|Przenieś|
|Nie modyfikatora|Docelowy|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Nie modyfikatora|Źródło|Usuwa odwołanie do oryginalnego elementu|Usuwa odwołanie do oryginalnego elementu|
|Nie modyfikatora|Wynik|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i elementu są usuwane z oryginalnej lokalizacji w magazynie|
|Shift + przeciągnięcie|Akcja|Przenieś|Przenieś|
|Shift + przeciągnięcie|Docelowy|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Shift + przeciągnięcie|Źródło|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Shift + przeciągnięcie|Wynik|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**Przenieś DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i elementu są usuwane z oryginalnej lokalizacji w magazynie|
|CTRL + przeciągnij|Akcja|Kopiuj|Kopiuj|
|CTRL + przeciągnij|Docelowy|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|CTRL + przeciągnij|Źródło|Odwołanie do elementu zachowuje|Zachowuje oryginalnego elementu|
|CTRL + przeciągnij|Wynik|**Kopiuj DROPEFFECT_** jest zwracana jako akcji z **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**Kopiuj DROPEFFECT_** jest zwracana jako akcji z **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|Ctrl + Shift + przeciągnięcie|Akcja|Łącze|Łącze|
|Ctrl + Shift + przeciągnięcie|Docelowy|Dodaje odwołanie do oryginalnego elementu|Dodaje odwołanie do oryginalnego elementu źródłowego|
|Ctrl + Shift + przeciągnięcie|Źródło|Odwołanie do elementu zachowuje|Zachowuje oryginalnego elementu|
|Ctrl + Shift + przeciągnięcie|Wynik|**ŁĄCZE DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|**ŁĄCZE DROPEFFECT_** jest zwracana jako akcji **:: porzucić** i element pozostaje w pierwotnej lokalizacji w magazynie|
|Wytnij/Wklej|Akcja|Przenieś|Przenieś|
|Wytnij/Wklej|Docelowy|Kopiuje element do lokalizacji docelowej|Kopiuje element do lokalizacji docelowej|
|Wytnij/Wklej|Źródło|Usuwa odwołanie do oryginalnego elementu|Usuwa element z oryginalnej lokalizacji|
|Wytnij/Wklej|Wynik|Element pozostaje w pierwotnej lokalizacji w magazynie|Element zostanie usunięty z oryginalnej lokalizacji w magazynie|
|Kopiowanie/wklejanie|Akcja|Kopiuj|Kopiuj|
|Kopiowanie/wklejanie|Docelowy|Dodaje odwołanie do oryginalnego elementu|Kopiuje element do lokalizacji docelowej|
|Kopiowanie/wklejanie|Źródło|Zachowuje oryginalnego elementu|Zachowuje oryginalnego elementu|
|Kopiowanie/wklejanie|Wynik|Element pozostaje w pierwotnej lokalizacji w magazynie|Element pozostaje w pierwotnej lokalizacji w magazynie|

 Te informacje powinny należy brać pod uwagę podczas implementowania przeciąganie w **Eksploratora rozwiązań**:

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

   Dzięki temu użytkownik można zapisać pracę w toku, zanim obiekt docelowy sprawia, że jego kopii. Nowa metoda **IVsHierarchyDropDataSource2::OnBeforeDropNotify** została dodana do włączenia tej obsługi.

   Element docelowy następnie skopiuj stan elementu, ponieważ jest on magazynu (bez uwzględnienia niezapisane zmiany w edytorze, jeśli użytkownik wybrał **nr**). Po zakończeniu docelowej, jej skopiowanie (w **IVsHierarchyDropDataSource::Drop**), źródło jest możliwość wykonania Usuń część operacji przenoszenia (w **IVsHierarchyDropDataSource::O nDropNotify**).

   Wszelkie edytorów z niezapisanymi zmianami należy pozostawić otwarty. W tych dokumentach z niezapisanymi zmianami to oznacza, że odbędzie się kopiowania część operacji przenoszenia, ale część usuwania zostanie przerwane. W przypadku zaznaczenia wielu gdy użytkownik wybierze **nie**, te dokumenty przy użyciu niezapisanych zmian nie powinny zostać zamknięte lub usunięte, ale użytkownicy bez niezapisane zmiany powinny być zamknięte i usunięte.
