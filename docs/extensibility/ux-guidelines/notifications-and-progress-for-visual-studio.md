---
title: Powiadomienia i postępy programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699882"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Powiadomienia i postęp dla programu Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Systemy powiadomień

### <a name="overview"></a>Omówienie
 Istnieje kilka sposobów informowania użytkownika, co dzieje się w programie Visual Studio dotyczące ich zadań programistycznych.

 Podczas wdrażania wszelkiego rodzaju powiadomień:

- **Zachowaj liczbę powiadomień do minimalnej** liczby efektywnej. Komunikaty powiadomień powinny dotyczyć większości użytkowników programu Visual Studio lub użytkowników określonego obszaru funkcji/funkcji. Nadmierne korzystanie z powiadomień może sidetrack użytkownika lub zmniejszyć postrzeganą łatwość korzystania z systemu.

- **Upewnij się, że są prezentujące jasne, zasłynialne wiadomości,** które użytkownik może użyć do wywołania odpowiedniego kontekstu do dokonywania bardziej złożonych wyborów i podejmowania dalszych działań.

- **Odpowiednio prezentuj komunikaty synchroniczne i asynchroniczne.** Powiadomienia synchroniczne wskazują, że coś wymaga natychmiastowej uwagi, na przykład gdy usługa sieci web ulegnie awarii lub zostanie zgłoszony wyjątek kodu. Użytkownik powinien być informowany o tych sytuacjach od razu w sposób, który wymaga ich danych wejściowych, takich jak w oknie dialogowym modalnego. Powiadomienia asynchroniczne to powiadomienia, o których użytkownik powinien wiedzieć, ale nie muszą działać natychmiast, na przykład po zakończeniu operacji kompilacji lub zakończeniu wdrażania witryny sieci Web. Te komunikaty powinny być bardziej otoczenia i nie przerywać przepływu zadań użytkownika.

- **Modalne okna dialogowe należy używać tylko wtedy, gdy jest to konieczne, aby uniemożliwić użytkownikowi podjęcie dalszych działań** przed potwierdzeniem wiadomości lub podjęciem decyzji przedstawionej w oknie dialogowym.

- **Usuń powiadomienia otoczenia, gdy nie są już prawidłowe.** Nie wymagaj od użytkownika, aby odrzucić powiadomienie, jeśli już podjął działania w celu rozwiązania problemu, o którym został powiadomiony.

- **Należy pamiętać, że powiadomienia mogą prowadzić do fałszywych korelacji.** Użytkownicy mogą uwierzyć, że co najmniej jedno z ich działań wyzwoliło powiadomienie, gdy w rzeczywistości nie było związku przyczynowego. Być jasne w komunikacie powiadomienia o kontekście, wyzwalacza i źródła powiadomienia.

### <a name="choosing-the-right-method"></a>Wybór właściwej metody
 Ta tabela ułatwia wybór odpowiedniej metody powiadamiania użytkownika o wiadomości.

|Metoda|Użycie|Nie używać|
|------------|---------|----------------|
|[Okna dialogowe komunikatu o błędzie modalnego](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Użyj, gdy odpowiedź użytkownika jest wymagana przed kontynuowaniem.|Nie należy używać, gdy nie ma potrzeby blokowania użytkownika i przerywania jego przepływu. Unikaj używania modalnych okien dialogowych, jeśli jest możliwe wyświetlenie wiadomości w inny, mniej inwazyjny sposób.|
|[Pasek stanu IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Użyj, gdy istnieją otaczające informacje tekstowe dotyczące stanu procesu.|Nie stosować samodzielnie. Najlepiej stosować w połączeniu z innym mechanizmem sprzężenia zwrotnego.|
|[Osadzony pasek informacyjny](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|W oknie narzędzia lub oknie dokumentu służy do powiadamiania o postępie, stanie błędu, wynikach i/lub informacjach zasysanych.|Nie należy używać, jeśli informacje nie są istotne dla lokalizacji, w której znajduje się pasek informacyjny.<br /><br /> Nie należy używać poza oknem dokumentu/narzędzia.|
|[Zmiany kursora myszy](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Może służyć do powiadamiania, że proces się dzieje. Używany również do powiadamiania, że w myszy występuje zmiana stanu, na przykład gdy trwa przeciąganie/upuszczanie lub kursor myszy w określonym trybie, takim jak tryb rysowania.|Nie należy używać do krótkich zmian postępu lub jeśli trzepotanie kursora jest prawdopodobne (na przykład, gdy jest powiązany z częściami dłużej działającego procesu, a nie do całego procesu).|
|[Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Użyj, gdy trzeba zgłosić postęp (określony lub nieokreślony). Istnieje wiele typów wskaźników postępu i określonego użycia dla każdego. Zobacz [Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Okno Powiadomienia programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno Powiadomienia nie jest publicznie rozszerzalne. Jednak jest on używany do komunikowania zakresu komunikatów dotyczących programu Visual Studio, w tym krytycznych problemów z licencją i informacyjnych powiadomień o aktualizacjach programu Visual Studio lub do pakietów.|Nie używaj do innych typów powiadomień.|
|[Lista błędów](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Gdy problem dotyczy bezpośrednio aktualnie otwartego rozwiązania użytkownika, które ma problem (błąd/ostrzeżenie/informacje), może być konieczne podjęcie działań w sprawie kodu.<br /><br /> Obejmowałoby to na przykład:<br /><br /> - Komunikaty kompilatora (błąd / ostrzeżenie / informacje)<br /><br /> - Analizator kodu/ Komunikaty diagnostyczne dotyczące kodu<br /><br /> - Tworzenie wiadomości<br /><br /> Może być odpowiednie dla problemów związanych z plikami projektu lub rozwiązania, ale należy najpierw rozważyć wskazanie Eksploratora rozwiązań.|Nie należy używać dla elementów, które nie mają żadnego związku z kodem otwartego rozwiązania użytkownika.|
|Powiadomienia edytora: Żarówka|Użyj, gdy masz dostępne poprawki, aby rozwiązać problem, który istnieje w otwartym pliku.<br /><br /> Należy zauważyć, że żarówka powinna być również używana do hostowania szybkich akcji, które są podejmowane na kodzie użytkownika na żądanie, takich jak refaktoryzacja, ale w takim przypadku nie pojawi się "styl powiadomień".|Nie należy używać dla elementów, które nie mają żadnego związku z otwartym plikiem.|
|Powiadomienia edytora: Squiggles|Służy do ostrzegania użytkownika o problemie z określonym zakresem ich otwartego kodu (na przykład czerwona falista dla błędów).|Nie należy używać dla towarów, które nie odnoszą się do określonego zakresu ich otwartego kodu.|
|[Osadzone paski stanu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Służy do dostarczania stanu związanego z zawartością lub procesem w kontekście określonego okna narzędzia, okna dokumentu lub okna dialogowego.|Nie należy używać do ogólnych powiadomień o produktach, procesów ani elementów, które nie mają żadnego związku z zawartością w określonym oknie.|
|[Powiadomienia z zasobnika systemu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Służy do wysyłek powiadomień dla procesów poza proc lub aplikacji towarzyszących.|Nie należy używać dla powiadomień, które są istotne dla IDE.|
|[Dymki powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Służy do powiadamiania o zdalnym procesie lub zmianie **poza** IDE.|Nie należy używać jako środek powiadamiania użytkownika o procesach **w ramach** IDE.|

### <a name="notification-methods"></a>Metody powiadamiania

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Okna dialogowe komunikatu o błędzie modalnego
 Okno dialogowe komunikatu o błędzie modalnego służy do wyświetlania komunikatu o błędzie, który wymaga potwierdzenia lub akcji użytkownika.

 ![Komunikat o błędzie modalnego](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Okno dialogowe komunikatu o błędzie modalnego informujące użytkownika o nieprawidłowym ciągu połączenia z bazą danych**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Pasek stanu IDE
 Prawdopodobieństwo, że użytkownicy zauważą tekst paska stanu, koreluje z ich wszechstronnym doświadczeniem komputera i określonym doświadczeniem z platformą Windows. Baza klientów programu Visual Studio ma tendencję do doświadczenia w obu obszarach, chociaż nawet doświadczeni użytkownicy systemu Windows mogą przegapić zmiany w pasku stanu. W związku z tym pasek stanu jest najlepiej używany do celów informacyjnych lub jako nadmiarowy sygnał dla informacji prezentowanych w innym miejscu. Wszelkiego rodzaju krytyczne informacje, które użytkownik musi natychmiast rozwiązać powinny być dostarczone w oknie dialogowym lub w oknie narzędzia powiadomienia.

 Pasek stanu programu Visual Studio ma na celu umożliwienie wyświetlania kilku typów informacji. Jest podzielony na regiony dla opinii, projektanta, paska postępu, animacji i klienta.

 Region opinii i region projektanta są zawsze widoczne. Pasek postępu i regiony animacji są zawsze dynamiczne i oparte na kontekście użytkownika. Region projektanta ma szerokość statyczną określoną przez długość ciągu, który jest pobierany z towarzyszącego zasobu dla wiadomości tekstowej. Dzięki temu lokalizacja, aby zmienić rozmiar szerokości bez konieczności zmiany kodu. W języku angielskim szerokość tego ciągu wynosi około 220 pikseli. Region projektanta będzie zachowywać się normalnie, a obszar sprzężenia zwrotnego pochłonie pozostałą przestrzeń.

 Pasek stanu jest również pokolorowany, aby dodać zainteresowanie wizualne i wartość funkcjonalną, komunikując różne zmiany stanu IDE, takie jak gdy IDE jest w trybie debugowania.

 ![Zmiany koloru paska stanu IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Kolory paska stanu IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Osadzony pasek informacyjny
 W górnej części okna dokumentu lub okna narzędzia można użyć paska informacyjnego informującego użytkownika o stanie lub stanie. Może również oferować polecenia, dzięki czemu użytkownik może mieć sposób na łatwe podjęcie działań. Pasek informacyjny jest standardową kontrolką powłoki. Należy unikać tworzenia własnych, które będą działać i pojawiają się niezgodne z innymi w IDE. Szczegółowe informacje na temat implementacji i wskazówki dotyczące użycia można znaleźć na [paskach informacyjnych.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)

 ![Osadzony pasek informacyjny](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Pasek informacji osadzony w oknie dokumentu, ostrzegający użytkownika, że IDE jest w trybie debugowania historycznego i edytor nie będzie reagować w taki sam sposób, jak w trybie standardowego debugowania.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Zmiany kursora myszy
 Podczas zmiany kursora myszy należy użyć kolorów, które są powiązane z usługą VSColor i są już skojarzone z kursorem. Zmiany kursora mogą służyć do wskazywania trwającej operacji, a także stref trafień, w których użytkownik najeżdża kursor nad obiektem docelowym, który może zostać przeciągnięty, upuszczony lub użyty do zaznaczenia obiektu.

 Użyj kursora myszy zajęty/czekać tylko wtedy, gdy cały dostępny czas procesora CPU musi być zarezerwowany dla operacji, uniemożliwiając użytkownikowi wyrażenie dalszych danych wejściowych. W większości przypadków z dobrze napisanych aplikacji przy użyciu wielowątkowych, czasy, gdy użytkownicy nie mogą wykonywać innych operacji powinny być rzadkie.

 Należy pamiętać, że zmiany kursora są przydatne jako nadmiarowy sygnał dla informacji prezentowanych w innym miejscu. Nie należy polegać na zmianie kursora jako jedyny sposób komunikowania się z użytkownikiem, zwłaszcza podczas próby przekazania coś, co jest krytyczne, że użytkownik musi adres.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Wskaźniki postępu
 Wskaźniki postępu są ważne dla przekazywania opinii użytkownika podczas procesów, które trwają dłużej niż kilka sekund. Wskaźniki postępu mogą być wyświetlane w miejscu (w pobliżu punktu rozpoczęcia akcji w toku), na osadzonym pasku stanu, w oknie dialogowym modalnym lub na pasku stanu programu Visual Studio. Postępuj zgodnie ze [wskaźnikami postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) dotyczącymi ich stosowania i wdrażania.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Okno Powiadomienia programu Visual Studio
 Okno Powiadomienia programu Visual Studio powiadamia deweloperów o licencjonowaniu, środowisku (Visual Studio), rozszerzeniach i aktualizacjach. Użytkownicy mogą odrzucać poszczególne powiadomienia lub ignorować określone typy powiadomień. Lista ignorowanych powiadomień jest zarządzana na stronie **Opcje > narzędzia.**

 Okno Powiadomienia nie jest obecnie rozszerzalne.

 ![Okno Powiadomienia programu Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Okno narzędzia Powiadomienia programu Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Lista błędów
 Powiadomienie na liście błędów wskazuje błędy i ostrzeżenia, które wystąpiły podczas kompilacji i lub procesu kompilacji i umożliwia użytkownikowi przejście w kodzie do tego błędu określonego kodu.

 ![Lista błędów](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Lista błędów w programie Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Osadzone paski stanu
 Ponieważ pasek stanu IDE jest dynamiczny, a jego kontekst regionu klienta jest ustawiony na aktywne okno dokumentu i aktualizowanie informacji o kontekście użytkownika i/lub odpowiedziach systemowych, trudno jest zachować ciągłe wyświetlanie informacji lub podać stan długoterminowych procesów asynchronicznych. Na przykład pasek stanu IDE nie jest odpowiedni dla powiadomień o wynikach przebiegu testu dla wielu przebiegów i/lub natychmiast zasuwających przyborów elementów. Ważne jest, aby zachować takie informacje o stanie w kontekście okna dokumentu lub narzędzia, w którym użytkownik dokonuje wyboru lub rozpoczyna proces.

 ![Wbudowany pasek stanu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Osadzony pasek stanu w programie Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Powiadomienia z zasobnika systemu Windows
 Obszar powiadomień systemu Windows znajduje się obok zegara systemowego na pasku zadań systemu Windows. Wiele narzędzi i składników oprogramowania udostępnia ikony w tym obszarze, dzięki czemu użytkownik może uzyskać menu kontekstowe dla zadań ogólnosystemowych, takich jak zmiana rozdzielczości ekranu lub uzyskanie aktualizacji oprogramowania.

 Powiadomienia na poziomie środowiska powinny być wyświetlane w centrum powiadomień programu Visual Studio, a nie w obszarze powiadomień systemu Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Dymki powiadomień
 Dymki powiadomień mogą być wyświetlane jako informacje w edytorze/projektancie lub jako część obszaru powiadomienia systemu Windows. Użytkownik postrzega te pęcherzyki jako problemy, które można rozwiązać później, co jest korzystne dla powiadomień niekrytycznych. Pęcherzyki są nieodpowiednie dla krytycznych informacji, które użytkownik musi rozwiązać od razu. Jeśli używasz dymków powiadomień w programie Visual Studio, postępuj zgodnie [ze wskazówkami pulpitu systemu Windows dotyczącymi dymków powiadomień](/windows/desktop/uxguide/mess-notif).

 ![Dymek powiadomień](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Dymek powiadomień w obszarze powiadomień systemu Windows używanym w programie Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Wskaźniki postępu

### <a name="overview"></a>Omówienie
 Wskaźniki postępu są ważną częścią systemu powiadomień do przekazywania opinii użytkowników. Informują użytkownika, kiedy procesy i operacje zostaną zakończone. Znane typy wskaźników obejmują paski postępu, obracające się kursory i animowane ikony. Typ i rozmieszczenie wskaźnika postępu zależy od kontekstu, w tym od tego, co jest zgłaszane i jak długo potrwa proces lub operacja.

#### <a name="factors"></a>Czynników
 Aby określić, który typ wskaźnika jest odpowiedni, należy określić następujące czynniki.

1. **Czas:** czas trwania operacji

2. **Modalność:** czy operacja jest modal do środowiska (blokuje interfejsu użytkownika, dopóki proces zostanie zakończony)

3. **Trwałe/przejściowe:** czy ostateczny wynik postępu musi być zgłoszony i/lub widoczny w późniejszym czasie

4. **Określenie/nieokreślony:** czy można obliczyć czas zakończenia operacji i postęp

5. **Lokalizacja graficzna/tekstowa:** niezależnie od tego, czy postęp lub proces jest przechwytywany w tekście wiadomości, czy też w określonym formancie, takim jak formant Drzewo

6. **Bliskość:** czy postęp powinien znajdować się w pobliżu interfejsu użytkownika, z który jest powiązany. (Na przykład, może to być w pasku stanu, który może być daleko, czy musi być w pobliżu przycisku, który uruchomił proces?)

#### <a name="determinate-progress"></a>Określanie postępu

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (określony)|Przewidywany czas trwania >5 sekund.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.|**NIE** osadzaj tekstu w animacji.|
|Pasek informacyjny|Wiadomości skojarzone z kontekstowego interfejsu użytkownika. Zobacz [Paski informacyjne](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Może zawierać tekstowy opis szczegółów procesu.|**NIE używaj** wielu pasków informacyjnych, gdy trzeba wskazać wiele procesów. Zamiast tego należy użyć skumulowanych pasków postępu.|
|Okno wyniku|Powiadomienie przejściowe: proces na poziomie aplikacji, który użytkownik chce **przejrzeć** szczegóły po zakończeniu.|**NIE używaj,** jeśli użytkownik będzie musiał odwołać się do danych później.|
|Plik dziennika|W połączeniu z powiadomieniem nieprzejezdnym w przypadkach, gdy ważne **jest,** aby zapisać szczegóły po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowe: proces na poziomie aplikacji, którego użytkownik nie będzie **potrzebował** szczegółów po zakończeniu.<br /><br /> Zawiera osadzony pasek postępu.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.||

#### <a name="indeterminate-progress"></a>Nieokreślony postęp

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (nieokreślony)|Przewidywany czas trwania >5 sekund.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.|**NIE** osadzaj tekstu w animacji.|
|Mrówki (animowane kropki poziome)|Podróż w obie strony na serwer.<br /><br /> Umieszczony w pobliżu punktu kontekstu w górnej części kontenera nadrzędnego.|**NIE używaj,** jeśli nie jest nadrzędny przez cały kontener.|
|Pokrętło (pierścień postępu)|Proces skojarzony z kontekstowym interfejsem użytkownika lub gdzie przestrzeń jest brana pod uwagę.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.||
|Pasek informacyjny|Wiadomości skojarzone z kontekstowego interfejsu użytkownika. Zobacz [Paski informacyjne](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**NIE używaj** wielu pasków informacyjnych, gdy trzeba wskazać wiele procesów. Zamiast tego należy użyć skumulowanych pasków postępu.|
|Okno wyniku|Powiadomienie przejściowe: proces na poziomie aplikacji, który użytkownik będzie chciał **przejrzeć** szczegóły po zakończeniu.|**NIE używaj** informacji, które muszą być zachowywane w sesjach.|
|Plik dziennika|W połączeniu z powiadomieniem nieprzejezdnym w przypadkach, gdy ważne **jest,** aby zapisać szczegóły po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowe: proces na poziomie aplikacji, którego użytkownik nie będzie **potrzebował** szczegółów po zakończeniu.<br /><br /> Zawiera osadzony pasek postępu.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.||

### <a name="progress-indicator-types"></a>Typy wskaźników postępu

#### <a name="progress-bars"></a>Paski postępu

##### <a name="indeterminate"></a>Nieokreślony
 ![Nieokreślony pasek postępu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Nieokreślony pasek postępu**

 "Nieokreślony" oznacza, że nie można określić ogólnego postępu operacji lub procesu. Nieokreślone paski postępu należy używać dla operacji, które wymagają nieograniczonej ilości czasu lub które uzyskują dostęp do nieznanej liczby obiektów. Użyj opisu tekstowego, aby dołączyć do tego, co się dzieje. Użyj limitów czasu, aby nadać granice operacjom opartym na czasie. Nieokreślone paski postępu używają animacji, aby pokazać, że postęp jest dokonywany, ale nie zawierają żadnych innych informacji. Nie wybieraj nieokreślonego paska postępu tylko na podstawie ewentualnego braku samej dokładności.

##### <a name="determinate"></a>Zdeterminowany
 ![Określony pasek postępu](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Określony pasek postępu**

 "Determinate" oznacza, że operacja lub proces wymaga ograniczonej ilości czasu, nawet jeśli nie można dokładnie przewidzieć tej ilości czasu. Wyraźnie wskazać zakończenie. Nie pozwól, aby pasek postępu przejść do 100 procent, chyba że operacja została zakończona. Określanie animacji paska postępu przesuwa się od lewej do prawej od 0 do 100%.

 Nigdy nie przesuwaj wskaźnika postępu do tyłu podczas operacji. Pasek powinien poruszać się do przodu stale po rozpoczęciu operacji i osiągnąć 100% po jej zakończeniu. Punkt paska postępu jest dać użytkownikowi wyobrażenie, jak długo trwa cała operacja, niezależnie od tego, ile kroków są zaangażowane.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Raportowanie współbieżne (skumulowane paski postępu)
 Jeśli operacja zajmie dużo czasu - być może kilka minut - następnie można użyć dwóch pasków postępu, jeden, który pokazuje ogólny postęp dla operacji, a drugi dla postępu bieżącego kroku. Na przykład, jeśli program instalacyjny kopiuje wiele plików, jeden pasek postępu może służyć do wskazania, jak długo trwa cały proces, podczas gdy drugi może wskazać, jaki procent bieżącego pliku lub katalogu jest kopiowany. Nie należy zgłaszać więcej niż pięć równoczesnych operacji lub procesów przy użyciu skumulowanych pasków postępu. Jeśli masz więcej niż pięć równoczesnych operacji lub procesów do raportowania, użyj modalnego okna dialogowego z przyciskiem Anuluj i zgłoś szczegóły postępu do okna wyjściowego.

##### <a name="textual-descriptions"></a>Opisy tekstowe
 Użyj opisu tekstowego, aby dołączyć do tego, co się dzieje i szacowanego czasu do zakończenia. Jeśli niemożliwe jest określenie, jak długo potrwa operacja, lepszym wyborem do przekazywania opinii może być animowana ikona, a nie pasek postępu.

 Visual Studio udostępnia standardowy pasek postępu na pasku stanu, który może być używany przez dowolny produkt zintegrowany z programem Visual Studio. W przypadku tekstowych opisów tego, co dzieje się podczas animowanego paska postępu, można zaktualizować tekst paska stanu.

#### <a name="other-progress-indicators"></a>Inne wskaźniki postępu

##### <a name="ants-animated-horizontal-dots"></a>Mrówki (animowane kropki poziome)
 ![Mrówki postępu](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Mrówki", animowane poziome kropki, stanowią wizualne odniesienie do nieokreślonego procesu serwera w obie strony.

##### <a name="spinner-progress-ring"></a>Pokrętło (pierścień postępu)
 ![Pokrętło postępu](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Pokrętło (znane również jako "pierścień postępu") jest nieokreślonym wskaźnikiem postępu używanym głównie w odniesieniu do kontekstowego interfejsu użytkownika. Wyświetlanie pokrętła w pobliżu powiązanej zawartości, takiej jak nagłówek kategorii tekstowej, wiadomości lub formant.

##### <a name="cursor-feedback"></a>Informacja zwrotna kursora
 W przypadku operacji, które trwa od 2 do 7 sekund, podaj informacje zwrotne kursora. Zazwyczaj oznacza to użycie kursora oczekiwania dostarczonego przez system operacyjny. Aby uzyskać wskazówki, zobacz artykuł MSDN [Cursors.Wait Właściwość](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Lokalizacje wskaźników postępu

##### <a name="status-bar"></a>Pasek stanu
 Pasek stanu daje aplikacji miejsce do wyświetlania wiadomości i przydatnych informacji dla użytkownika bez przerywania pracy użytkownika. Zazwyczaj wyświetlany w dolnej części okna stan postępu będzie okienkiem porad narzędzi, które zawiera komunikat o miarie postępu w połączeniu ze wskaźnikiem paska postępu.

 ![Pasek stanu z paskiem postępu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Pasek stanu z paskiem postępu**

 ![Pasek stanu z wiadomościami](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Pasek stanu z opisem tekstowym**

##### <a name="infobar"></a>Pasek informacyjny
 Podobnie jak pasek stanu, pasek informacji zapewnia kontekstowe powiadomienia i wiadomości, które można również sparować z nieokreślonymi wskaźnikami postępu, takimi jak pasek postępu lub pokrętło. Pasek informacji nie powinien zapewniać szczegółowego postępu poziomu ani określania wskaźnika postępu. Zobacz [Paski informacyjne](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Pasek informacyjny z paskiem postępu i wiadomościami](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Pasek informacyjny z paskiem postępu i opisem tekstowym**

 ![Pasek informacyjny wewnątrz okna](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Śródwierszowo
 Wbudowane wskazanie postępu może być reprezentowane przez dowolny typ modułu ładującego postępu. Zazwyczaj wskaźnik postępu jest sparowany z wiadomością, ale nie jest to wymagane.

 ![Pokrętło postępu wbudowanego](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner w połączeniu z opisem tekstowym**

 ![Paski postępu skumulowane w linii](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Określanie skumulowanych pasków postępu**

 ![Komunikaty o postępie wbudowanym](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Tekst w tekście Eksploratora serwera: Odświeżanie...**

##### <a name="tool-windows"></a>Okna narzędzi
 Globalne wskazanie postępu jest reprezentowane przez nieokreślony pasek postępu umieszczony bezpośrednio pod paskiem narzędzi.

 ![Globalny nieokreślony pasek postępu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Pasek postępu nieokreślonego globalnego programu Team Explorer**

##### <a name="dialogs"></a>Okna dialogowe
 Okna dialogowe mogą zawierać dowolny typ modułu ładującego postępu. Wskaźniki postępu można sparować z wiadomością, a także w połączeniu z wieloma poziomami wskazywała postęp, aby reprezentować szczegółowe i podprocesy.

 ![Okno dialogowe z wieloma typami wskaźników postępu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Okno dialogowe programu Visual Studio z równoczesnymi procesami i wieloma typami wskaźników postępu**

 ![Okno dialogowe z modułem ładujący postępu i wiadomością](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Okno dialogowe programu Visual Studio z programem ładującym postęp i wbudowanym poleceniem obsługi wiadomości**

##### <a name="document-well"></a>Dobrze dokumentuj
 Dokument dobrze można wyświetlić wiele typów modułu ładującego postępu w połączeniu z formantami.

 ![Komunikaty o postępach w dokumencie](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Nieokreślony pasek postępu poniżej paska narzędzi**

##### <a name="output-window"></a>Okno wyniku
 Okno Dane wyjściowe jest odpowiednie do obsługi postępu procesu i bieżącego stanu postępu za pośrednictwem wbudowanej wiadomości tekstowej. Należy użyć paska stanu wraz z dowolnym raportowaniem postępu okna danych wyjściowych.

 ![Komunikaty o postępie w oknie wyjściowym](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Okno wyjściowe z bieżącym stanem procesu i wiadomościami oczekiwania**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Paski informacyjne

### <a name="overview"></a>Omówienie
 Paski informacyjne dają użytkownikowi wskaźnik zbliżony do punktu uwagi, a użycie udostępnionego formantu paska informacyjnego zapewnia spójność wyglądu i interakcji.

 ![Pasek informacyjny](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Paski informacyjne w programie Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Odpowiednie zastosowania paska informacyjnego

- Aby nadać użytkownikowi nieblokujące, ale ważne wiadomości istotne dla bieżącego kontekstu

- Aby wskazać, że interfejs użytkownika jest w określonym stanie lub stanie, który niesie ze sobą pewne implikacje interakcji, takie jak debugowanie historyczne

- Aby powiadomić użytkownika, że system wykrył problemy, takie jak gdy rozszerzenie powoduje problemy z wydajnością

- Aby zapewnić użytkownikowi sposób łatwego podejmowania działań, na przykład gdy edytor wykryje, że plik ma mieszane karty i spacje

##### <a name="do"></a>Zrobić:

- Tekst wiadomości na pasku informacyjnym jest krótki i do tego stopnia.

- Zachowaj tekst na łączach i przyciskach zwięzłe.

- Upewnij się, że opcje "akcji", które udostępniasz użytkownikom, są minimalne, pokazując tylko wymagane akcje.

##### <a name="dont"></a>Nie:

- Użyj paska informacyjnego, aby oferować standardowe polecenia, które powinny być umieszczone na pasku narzędzi.

- Zamiast modalnego okna dialogowego należy użyć paska informacyjnego.

- Utwórz wiadomość przestawną poza oknem.

- Użyj wielu pasków informacyjnych w kilku lokalizacjach w tym samym oknie.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Czy wiele pasków informacyjnych może być wyświetlane w tym samym czasie?
 Tak, wiele pasków informacyjnych może być wyświetlane w tym samym czasie. Będą one wyświetlane w kolejności "kto pierwszy, ten lepszy" z pierwszym paskiem informacyjnym wyświetlanym na górze i dodatkowymi paskami informacyjnymi wyświetlanymi poniżej.

 Użytkownik zobaczy maksymalnie trzy paski informacyjne naraz, po czym, jeśli dostępnych jest więcej pasków informacyjnych, obszar paska informacyjnego stanie się przewijany.

### <a name="creating-an-infobar"></a>Tworzenie paska informacyjnego
 Pasek informacyjny ma cztery sekcje, od lewej do prawej:

- **Ikona:** W tym miejscu należy dodać dowolną ikonę, którą chcesz wyświetlić dla paska informacyjnego, taką jak ikona ostrzeżenia.

- **Tekst:** Można dodać tekst, aby opisać scenariusz/sytuację użytkownika jest w, wraz z łączami w tekście, jeśli jest to wymagane. Pamiętaj, aby tekst był zwięzły.

- **Działania:** Ta sekcja powinna zawierać łącza i przyciski dla działań, które użytkownik może podjąć na pasku informacyjnym.

- **Przycisk Zamknij:** Ostatnia sekcja po prawej stronie może mieć przycisk zamknięcia.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Tworzenie standardowego paska informacyjnego w kodzie zarządzanym
 Klasa InfoBarModel może służyć do tworzenia źródła danych dla paska informacyjnego. Użyj jednego z tych czterech konstruktorów:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Oto przykład, który tworzy Program InfoBarModel z tekstem z hiperłączem, przyciskiem akcji i ikoną.

 ![Pasek informacyjny z hiperłączem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Tworzenie standardowego paska informacyjnego w kodzie macierzystym
 Implementuj interfejs IVsInfoBar w celu zapewnienia paska informacyjnego z kodu macierzystego.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Uzyskiwanie uielement paska informacyjnego z paska informacyjnego
 Implementacja Programu InfoBarModel lub IVsInfoBar to modele danych, które muszą zostać przekształcone w UIElement, aby były wyświetlane w interfejsie użytkownika. UIElement można pobrać za pomocą usługi SVsInfoBarUIFactory/IVsInfoBarUIFactory.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Umieszczanie
 Paski informacyjne mogą być wyświetlane w co najmniej jednej z następujących lokalizacji:

- Okna narzędzi

- W obrębie karty dokumentu

> [!IMPORTANT]
> Możliwe jest umieszczenie paska informacyjnego, aby przekazać komunikat o kontekście globalnym. To pojawi się między paskami narzędzi a dokumentem dobrze. Nie jest to zalecane, ponieważ powoduje problemy z "skok i szarpnięcie" IDE i należy unikać, chyba że jest to absolutnie konieczne i właściwe.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umieszczanie paska informacyjnego w pokładzie narzędzia ToolWindowPane
 Metoda ToolWindowPane.AddInfoBar(IVsInfoBar) może służyć do dodawania paska informacyjnego do okna narzędzia. Ten interfejs API można dodać IVsInfoBar (z których InfoBarModel jest domyślną implementacją) lub IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Umieszczanie paska informacyjnego w dokumencie lub w poprzek okna nienarzędziewadowego
 Aby umieścić pasek informacyjny w dowolnym IVsWindowFrame, użyj właściwości VSFPROPID_InfoBarHost, aby uzyskać IVsInfoBarHost dla ramki, a następnie dodaj pasek informacyjny UIElement.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Umieszczanie paska informacyjnego w oknie głównym
 Aby umieścić pasek informacji w oknie głównym, użyj VSSPROPID_MainWindowInfoBarHost usługi IVsShell, aby uzyskać IVsInfoBarHost w oknie głównym, a następnie dodaj do niego uielement paska informacyjnego.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Czy wiem, kiedy użytkownik podejmie działania na pasku informacyjnym?
 Tak, każdą akcję wydarzenia zwrócimy autorowi paska informacyjnego. Następnie do autora paska informacyjnego do podjęcia działań w IDE na podstawie wyboru użytkownika na pasku informacyjnym. Paski informacyjne zostaną automatycznie usunięte z hosta, którego przycisk Zamknij został kliknięty, ale dodatkowa praca jest wymagana, jeśli inne paski informacyjne muszą zostać usunięte po zamknięciu. Telemetria również musi być rejestrowane niezależnie przez każdy pasek informacyjny.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Odbieranie zdarzeń na pasku informacyjnym w posyłce ToolWindowPane
 ToolWindowPane ma dwa zdarzenia dla pasków informacyjnych. Zdarzenie InfoBarClosed jest wywoływane po zamknięciu paska informacyjnego w platformie ToolWindowPane. Zdarzenie InfoBarActionItemClicked jest wywoływane po kliknięciu hiperłącza lub przycisku wewnątrz paska informacyjnego.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Odbieranie zdarzeń na pasku informacyjnym bezpośrednio z UIElement
 IVsInfoBarUIElement.Advise może służyć do subskrybowania zdarzeń bezpośrednio z uielement paska informacyjnego. Implementacja IVsInfoBarUIEvents pozwoli autorowi odbierać zdarzenia zamknięcia i kliknięcia.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Sprawdzanie poprawności błędów
 Gdy użytkownik wprowadza informacje, które nie są akceptowane, takie jak gdy wymagane pole jest pomijane lub gdy dane są wprowadzane w niepoprawnym formacie, lepiej jest użyć sprawdzania poprawności formantu lub opinii w pobliżu formantu zamiast używać okna dialogowego błędu wyskakujących okienek blokowania.

### <a name="field-validation"></a>Sprawdzanie poprawności pól
 Sprawdzanie poprawności formularza i pola składa się z trzech składników: formantu, ikony i etykietki narzędzia. Podczas gdy kilka typów formantów można użyć tego, pole tekstowe będzie używany jako przykład.

 ![Sprawdzanie poprawności pola &#40;puste&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Jeśli pole jest wymagane, powinien być tekst znaku wodnego z ** \<napisem Wymagane>** a tło pola `Environment.ControlEditRequiredBackground`powinno być jasnożółte (VSColor: ), a pierwszy plan powinien być szary (VSColor): `Environment.ControlEditRequiredHintText`

 ![Sprawdzanie poprawności pola z etykietą "Wymagane"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program może ustalić, że formant jest w stanie *nieprawidłowej zawartości wprowadzonej* podczas przenoszenia fokusu do innego formantu lub gdy użytkownik kliknie przycisk zatwierdzania [OK] lub gdy użytkownik zapisze dokument lub formularz.

 Po określeniu nieprawidłowego stanu zawartości ikona pojawia się wewnątrz formantu lub tuż obok niego. Etykietka narzędzia opisująca błąd powinna pojawić się po najechaniu kursorem myszy na ikonę lub formant. Ponadto obramowanie 1 piksela powinno pojawić się wokół formantu, który tworzy nieprawidłowy stan.

 ![Specyfikacje układu sprawdzania poprawności pola](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Specyfikacje układu sprawdzania poprawności pola**

#### <a name="acceptable-variations-for-icon-location"></a>Dopuszczalne odmiany lokalizacji ikon
 Istnieje wiele unikatowych przypadków, w których użytkownicy muszą być informowani o błędach sprawdzania poprawności. Biorąc pod uwagę typ formantu i konfigurację interfejsu użytkownika, wybierz położenie ikony odpowiednie dla twojej sytuacji.

 ![Dopuszczalne lokalizacje dla lokalizacji ikon](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Dopuszczalne różnice dla lokalizacji ikon sprawdzania poprawności pola**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Sprawdzanie poprawności wymagające połączenia z serwerem lub siecią w obie strony
 W niektórych przypadkach do weryfikacji zawartości wymagana jest podróż w obie strony do serwera i ważne byłoby wyświetlenie stanu postępu użytkownika, weryfikacji i błędów. Poniższy rysunek przedstawia przykład tego przypadku i zalecany interfejs użytkownika.

 ![Sprawdzanie poprawności obejmujące podróż w obie strony do serwera](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Sprawdzanie poprawności obejmujące podróż w obie strony do serwera**

 Należy pamiętać, że aby uwzględnić "Weryfikację..." i "Ponów próbę".

#### <a name="in-place-warning-text"></a>Tekst ostrzeżenia w miejscu
 Gdy jest dostępna przestrzeń, aby umieścić komunikat o błędzie w pobliżu formantu w stanie błędu, jest to korzystne dla korzystania z etykietki narzędzia sam.

 ![W&#45;miejscu ostrzeżenie](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Tekst ostrzeżenia w miejscu**

#### <a name="watermarks"></a>Znaki wodne
 Czasami cały formant lub okno jest w stanie błędu. W tej sytuacji użyj znaku wodnego, aby wskazać błąd.

 ![Znak wodny](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Sprawdzanie poprawności pola znaku wodnego**
