---
title: Powiadomienia i postęp dla Visual Studio | Microsoft Docs
description: Dowiedz się więcej o kilku sposobach informowania użytkowników o tym, co dzieje się Visual Studio o ich zadaniach związanych z tworzeniem oprogramowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 994a315d04b06d1998a8c8e0c4291b6a4c54cb61
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902244"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Powiadomienia i postęp dla programu Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Systemy powiadomień

### <a name="overview"></a>Omówienie
 Istnieje kilka sposobów informowania użytkownika o tym, co dzieje się Visual Studio o zadaniach związanych z tworzeniem oprogramowania.

 Podczas implementowania dowolnego rodzaju powiadomienia:

- **Zachowaj minimalną liczbę efektywnych** powiadomień. Komunikaty powiadomień powinny dotyczyć większości Visual Studio użytkowników lub użytkowników określonej funkcji/obszaru funkcji. Nadmierne użycie powiadomień może powodować śledzenie użytkownika lub zmniejszać postrzeganą łatwość korzystania z systemu.

- **Upewnij się, że prezentujesz jasne komunikaty z** możliwością działania, których użytkownik może użyć do wywoływania odpowiedniego kontekstu w celu podejmowania bardziej złożonych wyborów i podejmowania dalszych działań.

- **Odpowiednio prezentuj komunikaty synchroniczne i asynchroniczne.** Powiadomienia synchroniczne wskazują, że coś wymaga natychmiastowej uwagi, na przykład w przypadku awarii usługi internetowej lub zgłoszenia wyjątku kodu. Użytkownik powinien być od razu poinformowany o takich sytuacjach w sposób, który wymaga danych wejściowych, na przykład w modalnych oknach dialogowych. Powiadomienia asynchroniczne to powiadomienia, o których użytkownik powinien wiedzieć, ale których nie trzeba wymagać natychmiastowego działania, na przykład po zakończeniu operacji kompilacji lub zakończeniu wdrażania witryny internetowej. Te komunikaty powinny być bardziej otoczenia i nie przerywać przepływu zadań użytkownika.

- **Modalnych okien dialogowych należy używać** tylko wtedy, gdy jest to konieczne, aby uniemożliwić użytkownikowi podejmowanie dalszych działań przed potwierdzeniem komunikatu lub podjęciem decyzji przedstawionej w oknie dialogowym.

- **Usuń powiadomienia otoczenia, gdy nie są już prawidłowe.** Nie wymagaj od użytkownika odrzucania powiadomienia, jeśli podjął już działania w celu rozwiązania problemu, o który został powiadomiony.

- **Należy pamiętać, że powiadomienia mogą prowadzić do fałszywych korelacji.** Użytkownicy mogą uważać, że co najmniej jedna akcja wyzwoliła powiadomienie, gdy w rzeczywistości nie ma relacji przyczynowej. W komunikacie powiadomienia należy wyraźnie znaleźć informacje o kontekście, wyzwalaczu i źródle powiadomienia.

### <a name="choosing-the-right-method"></a>Wybieranie właściwej metody
 Skorzystaj z tej tabeli, aby pomóc w wyborze właściwej metody powiadamiania użytkownika o wiadomości.

|Metoda|Zastosowanie|Nie używaj|
|------------|---------|----------------|
|[Modalne okna dialogowe komunikatów o błędach](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Użyj, gdy odpowiedź użytkownika jest wymagana przed podjęciem działania.|Nie należy używać, gdy nie ma potrzeby blokowania użytkownika i przerywania jego przepływu. Unikaj korzystania z modalnych okien dialogowych, jeśli jest możliwe pokazanie komunikatu w inny, mniej uciążliwy sposób.|
|[Pasek stanu środowiska IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Użyj, gdy istnieją informacje tekstowe otoczenia dotyczące stanu procesu.|Nie używaj go samodzielnie. Najlepiej używać w połączeniu z innym mechanizmem opinii.|
|[Osadzony pasek informacyjny](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|W oknie narzędzia lub oknie dokumentu użyj polecenia , aby powiadomić o postępie, stanie błędu, wynikach i/lub informacjach z akcjami.|Nie należy używać, jeśli informacje nie są istotne dla lokalizacji, w której znajduje się pasek informacyjny.<br /><br /> Nie należy używać poza oknem dokumentu/narzędzia.|
|[Zmiany kursora myszy](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Może służyć do powiadamiania o tym, że proces się dzieje. Służy również do powiadamiania o zmianie stanu myszy, na przykład gdy przeciąganie/upuszczanie jest w toku lub że kursor myszy jest w określonym trybie, takim jak tryb rysowania.|Nie używaj funkcji w przypadku krótkich zmian postępu lub jeśli chybienie kursora jest prawdopodobne (na przykład gdy jest powiązane z częściami dłużej działającego procesu, a nie z całym procesem).|
|[Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Użyj, gdy musisz zgłosić postęp (determinować lub nieokreślony). Istnieją różne typy wskaźników postępu i określone użycie dla każdego z nich. Zobacz [Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Visual Studio powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno Powiadomienia nie jest publicznie rozszerzalne. Jest on jednak używany do przekazywania różnych komunikatów dotyczących Visual Studio, w tym krytycznych problemów z licencją i powiadomień informacyjnych o aktualizacjach Visual Studio lub pakietach.|Nie należy używać w przypadku innych typów powiadomień.|
|[Lista błędów](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Jeśli problem dotyczy bezpośrednio otwartego rozwiązania użytkownika, w którym występuje problem (błąd/ostrzeżenie/informacje), może być konieczne podjęcia działania na kodzie.<br /><br /> Może to obejmować na przykład:<br /><br /> - Komunikaty kompilatora (błąd/ostrzeżenie/informacje)<br /><br /> - Analizator kodu/komunikaty diagnostyczne dotyczące kodu<br /><br /> - Kompilacja komunikatów<br /><br /> Może być odpowiednie w przypadku problemów związanych z plikami projektu lub rozwiązania, ale należy najpierw rozważyć Eksplorator rozwiązań wskazanie.|Nie należy używać w przypadku elementów, które nie mają żadnej relacji z otwartym kodem rozwiązania użytkownika.|
|Powiadomienia edytora: Żarówka|Użyj , jeśli masz dostępną poprawkę, aby rozwiązać problem, który istnieje w otwartym pliku.<br /><br /> Należy pamiętać, że żarówka powinna być również używana do hostowania szybkich akcji, które są podejmowane na żądanie przez kod użytkownika, takich jak refaktoryzowanie, ale w takim przypadku nie będzie wyświetlany "styl powiadomień".|Nie należy używać w przypadku elementów, które nie mają żadnej relacji z otwartym plikiem.|
|Powiadomienia edytora: Zygmki|Użyj , aby zaalarmować użytkownika o problemie z określonym zakresem otwartego kodu (na przykład czerwoną zygmki błędów).|Nie należy używać w przypadku elementów, które nie odnoszą się do określonego zakresu ich otwartego kodu.|
|[Osadzone paski stanu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Służy do zapewnienia stanu związanego z zawartością lub procesem w kontekście określonego okna narzędzia, okna dokumentu lub okna dialogowego.|Nie należy używać w przypadku ogólnych powiadomień o produktach, procesów ani elementów, które nie mają żadnego związku z zawartością w określonym oknie.|
|[Powiadomienia na pasku zadań systemu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Użyj, aby rozsyłać powiadomienia dla procesów poza procą lub aplikacji towarzyszących.|Nie należy używać w przypadku powiadomień, które są istotne dla środowiska IDE.|
|[Bąbelki powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Umożliwia powiadamianie o zdalnym procesie lub zmianie **poza** ideą IDE.|Nie należy używać go jako środka do powiadamiania użytkownika o procesach **w ramach** środowiska IDE.|

### <a name="notification-methods"></a>Metody powiadomień

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Modalne okna dialogowe komunikatów o błędach
 Modalne okno dialogowe komunikatu o błędzie służy do wyświetlania komunikatu o błędzie, który wymaga potwierdzenia lub akcji użytkownika.

 ![Modalny komunikat o błędzie](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Modalne okno dialogowe komunikatu o błędzie z alertem dla użytkownika o nieprawidłowych parametrów połączenia z bazą danych**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Pasek stanu środowiska IDE
 Prawdopodobieństwo, że użytkownicy zauważą tekst paska stanu, jest skorelowane z całym doświadczeniem komputera i konkretnym doświadczeniem z platformą Windows. Zespół Visual Studio klientów ma tendencję do doświadczenia w obu obszarach, chociaż nawet doświadczeni użytkownicy systemu Windows mogą pominąć zmiany na pasku stanu. Dlatego pasek stanu najlepiej jest używać do celów informacyjnych lub jako nadmiarowy wskaźnik informacji przedstawionych w innym miejscu. Wszelkie informacje krytyczne, które użytkownik musi natychmiast rozwiązać, należy podać w oknie dialogowym lub w oknie narzędzia Powiadomienia.

 Pasek Visual Studio jest przeznaczony do zezwalania na kilka typów informacji, które mają być wyświetlane. Jest ona podzielona na regiony na opinie, projektanta, pasek postępu, animację i klienta.

 Region opinii i region projektanta są zawsze widoczne. Obszary paska postępu i animacji są zawsze dynamiczne i oparte na kontekście użytkownika. Region projektanta ma statyczną szerokość określaną na podstawie długości ciągu, który jest ściągany z towarzyszącego zasobu dla wiadomości TEKSTOWEJ. Dzięki temu lokalizacja może zmieniać rozmiar szerokości bez konieczności zmiany kodu. W przypadku języka angielskiego szerokość tego ciągu wynosi około 220 pikseli. Region projektanta będzie zachowywać się normalnie, a region opinii będzie zasyłać pozostałe miejsce.

 Pasek stanu jest również pokolorowany, aby dodać wizualne zainteresowanie i wartość funkcjonalną, komunikując różne zmiany stanu środowiska IDE, na przykład gdy ide jest w trybie debugowania.

 ![Zmiany koloru paska stanu środowiska IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Kolory paska stanu środowiska IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Osadzony pasek informacyjny
 W górnej części okna dokumentu lub okna narzędzi można użyć paska informacyjnego, aby poinformować użytkownika o stanie lub warunku. Może również oferować polecenia, dzięki czemu użytkownik może mieć możliwość łatwego podjęcia akcji. Pasek informacyjny to standardowa kontrolka powłoki. Unikaj tworzenia własnych, które będą działać i wydawać się niespójne z innymi w idee IDE. Aby [uzyskać szczegółowe informacje o implementacji](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) i wskazówki dotyczące użycia, zobacz Pasek informacyjny.

 ![Osadzony pasek informacyjny](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Pasek informacyjny osadzony w oknie dokumentu z alertem dla użytkownika, że ide jest w trybie debugowania historycznego, a edytor nie będzie odpowiadać w taki sam sposób, jak w standardowym trybie debugowania.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Zmiany kursora myszy
 Podczas zmiany kursora myszy użyj kolorów, które są powiązane z usługą VSColor i są już skojarzone z kursorem. Zmiany kursora mogą służyć do wskazywania trwającej operacji, a także stref trafień, w których użytkownik umieszcza wskaźnik myszy na obiekcie docelowym, który można przeciągać, upuszczać na nie lub używać do wybierania obiektu.

 Kursora myszy zajętego/oczekiwania należy używać tylko wtedy, gdy cały dostępny czas procesora CPU musi być zarezerwowany dla operacji, co uniemożliwia użytkownikowi wyrażanie dalszych danych wejściowych. W większości przypadków w przypadku dobrze napisanych aplikacji korzystających z wielowątkości czasy, w których użytkownicy nie mogą wykonywania innych operacji, powinny być rzadkie.

 Należy pamiętać, że zmiany kursora są przydatne jako nadmiarowa wskazówka dla informacji przedstawionych w innym miejscu. Nie należy polegać na zmianie kursora jako jedynego sposobu komunikowania się z użytkownikiem, szczególnie w przypadku próby przekazania czegoś, co ma kluczowe znaczenie dla użytkownika.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Wskaźniki postępu
 Wskaźniki postępu są ważne w przypadku dawania opinii użytkownika podczas procesów, których ukończenie trwa dłużej niż kilka sekund. Wskaźniki postępu mogą być wyświetlane w miejscu (w pobliżu punktu uruchomienia akcji w toku), na osadzonym pasku stanu, w modalnych oknach dialogowych lub w Visual Studio pasku stanu. Postępuj zgodnie ze wskazówkami [we wskaźnikach postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) dotyczącymi ich użycia i implementacji.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio powiadomień
 Okno powiadomień Visual Studio powiadamia deweloperów o licencjonowaniu, środowisku (Visual Studio), rozszerzeniach i aktualizacjach. Użytkownicy mogą odrzucać poszczególne powiadomienia lub zdecydować się na zignorowanie niektórych typów powiadomień. Lista zignorowanych powiadomień jest zarządzana na **stronie Narzędzia > opcje.**

 Okno Powiadomienia nie jest obecnie rozszerzalne.

 ![Visual Studio powiadomień](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio narzędzi powiadomienia**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Lista błędów
 Powiadomienie na liście błędów wskazuje błędy i ostrzeżenia, które wystąpiły podczas kompilacji lub procesu kompilacji, i umożliwia użytkownikowi przejście w kodzie do tego konkretnego błędu kodu.

 ![Lista błędów](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Lista błędów w Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Osadzone paski stanu
 Ponieważ pasek stanu środowiska IDE jest dynamiczny, z kontekstem regionu klienta ustawionym na aktywne okno dokumentu i aktualizowaniem informacji w kontekście użytkownika i/lub odpowiedziach systemowych, trudno jest zachować ciągłe wyświetlanie informacji lub nadać stan długoterminowym procesom asynchronicznym. Na przykład pasek stanu środowiska IDE nie jest odpowiedni dla powiadomień o wynikach uruchomienia testu dla wielu przebiegów i/lub opcji elementów z akcjami natychmiast. Ważne jest, aby zachować takie informacje o stanie w kontekście dokumentu lub okna narzędzi, w którym użytkownik dokonuje wyboru lub uruchamia proces.

 ![Osadzony pasek stanu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Osadzony pasek stanu w Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Powiadomienia na pasku zadań systemu Windows
 Obszar powiadomień systemu Windows znajduje się obok zegara systemowego na pasku zadań systemu Windows. Wiele narzędzi i składników oprogramowania zapewnia ikony w tym obszarze, dzięki czemu użytkownik może uzyskać menu kontekstowe dla zadań całego systemu, takich jak zmienianie rozdzielczości ekranu lub uzyskiwanie aktualizacji oprogramowania.

 Powiadomienia na poziomie środowiska powinny być wyświetlane w centrum powiadomień Visual Studio, a nie w obszarze powiadomień systemu Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bąbelki powiadomień
 Bąbelki powiadomień mogą być wyświetlane jako informacyjne w edytorze/projektancie lub w obszarze Powiadomień systemu Windows. Użytkownik postrzega te bąbelki jako problemy, które można później rozwiązać, co jest korzystne w przypadku powiadomień niekrytycznych. Bąbelki są nieodpowiednie dla kluczowych informacji, które użytkownik musi od razu rozwiązać. Jeśli korzystasz z bąbelków powiadomień w Visual Studio, postępuj zgodnie ze wskazówkami programu Windows Desktop dla [bąbelków powiadomień.](/windows/desktop/uxguide/mess-notif)

 ![Bąbelek powiadomień](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bąbelek powiadomień w obszarze Powiadomień systemu Windows używany na Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Wskaźniki postępu

### <a name="overview"></a>Omówienie
 Wskaźniki postępu są ważną częścią systemu powiadomień w przypadku zgłaszania opinii użytkowników. Informują użytkownika o zakończeniu procesów i operacji. Znane typy wskaźników obejmują paski postępu, obracające się kursory i animowane ikony. Typ i położenie wskaźnika postępu zależy od kontekstu, w tym zgłaszanego stanu i czasu ukończenia procesu lub operacji.

#### <a name="factors"></a>Czynników
 Aby określić, który typ wskaźnika jest odpowiedni, należy określić następujące czynniki.

1. **Chronometraż:** czas trwania operacji

2. **Opcjonalnie:** czy operacja jest modalna dla środowiska (blokuje interfejs użytkownika do czasu ukończenia procesu)

3. **Trwałe/przejściowe:** czy końcowy wynik postępu musi zostać zgłoszony i/lub można go wyświetlić w późniejszym czasie

4. **Determinate/Indeterminate: określa,** czy można obliczyć czas zakończenia i postęp operacji

5. **Lokalizacja grafiki/tekstu:** określa, czy postęp lub proces jest przechwytywany w tekście, w treści komunikatu, czy w określonej kontrolce, takiej jak kontrolka Drzewo

6. **Bliskość:** czy postęp powinien być blisko interfejsu użytkownika, z który jest powiązany. (Czy na przykład może on być na pasku stanu, który może być daleko, czy musi być blisko przycisku, który uruchomił proces?)

#### <a name="determinate-progress"></a>Determinate progress (Determinate progress)

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (determinate)|Oczekiwany czas trwania >5 sekund.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.|**NIE OSADZAJ** tekstu w animacji.|
|Pasek informacji|Obsługa komunikatów skojarzonych z kontekstowym interfejsem użytkownika. Zobacz [Infobars (Pasek informacji).](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)<br /><br /> Może zawierać tekstowy opis szczegółów procesu.|**NIE UŻYWAJ wielu** paskach informacyjnych, gdy musisz wskazać wiele procesów. Zamiast tego użyj skumulowanych pasków postępu.|
|Okno wyniku|Powiadomienie przejściowe: proces na poziomie aplikacji, dla którego użytkownik chce **przejrzeć** szczegóły po zakończeniu.|**NIE UŻYWAJ,** jeśli użytkownik będzie musiał później odwoływać się do danych.|
|Plik dziennika|Sparowane z nieprzejednoznanym powiadomieniem w przypadkach, gdy ważne jest **zapisanie szczegółów** po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowe: proces na poziomie aplikacji, dla których użytkownik nie **potrzebuje** szczegółowych informacji po zakończeniu.<br /><br /> Zawiera osadzony pasek postępu.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.||

#### <a name="indeterminate-progress"></a>Nieokreślony postęp

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (nieokreślony)|Oczekiwany czas trwania >5 sekund.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.|**NIE OSADZAJ** tekstu w animacji.|
|Ants (animowane poziome kropki)|Runda do serwera.<br /><br /> Umieszczony w pobliżu punktu kontekstu w górnej części kontenera nadrzędnego.|**NIE używaj elementu** , jeśli element nie jest nadrzędny przez cały kontener.|
|Pokrętło (pierścień postępu)|Proces skojarzony z kontekstowym interfejsem użytkownika lub miejsce, w którym należy wziąć pod uwagę miejsce.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.||
|Pasek informacji|Obsługa komunikatów skojarzonych z kontekstowym interfejsem użytkownika. Zobacz [Infobars (Pasek informacji).](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)|**NIE UŻYWAJ wielu** paskach informacyjnych, gdy musisz wskazać wiele procesów. Zamiast tego użyj skumulowanych pasków postępu.|
|Okno wyniku|Powiadomienie przejściowe: proces na poziomie aplikacji, dla którego użytkownik chce **przejrzeć** szczegóły po zakończeniu.|**NIE należy używać** w przypadku informacji, które muszą być utrwalane między sesjami.|
|Plik dziennika|Sparowane z nieprzejednoznanym powiadomieniem w przypadkach, gdy ważne jest **zapisanie szczegółów** po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowe: proces na poziomie aplikacji, dla których użytkownik nie **potrzebuje** szczegółowych informacji po zakończeniu.<br /><br /> Zawiera osadzony pasek postępu.<br /><br /> Może zawierać tekstowy opis szczegółów procesu.||

### <a name="progress-indicator-types"></a>Typy wskaźników postępu

#### <a name="progress-bars"></a>Paski postępu

##### <a name="indeterminate"></a>Nieokreślony
 ![Nieokreślony pasek postępu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Nieokreślony pasek postępu**

 "Nieokreślony" oznacza, że nie można określić ogólnego postępu operacji lub procesu. Użyj nieokreślonych pasków postępu dla operacji, które wymagają niepowiązanego czasu lub mają dostęp do nieznanej liczby obiektów. Użyj opisu tekstowego, aby towarzyszyć temu, co się dzieje. Użyj limitów czasu, aby dawać granice operacji opartych na czasie. Nieokreślone paski postępu używają animacji, aby pokazać postęp, ale nie zawierają żadnych innych informacji. Nie wybieraj nieokreślony pasek postępu tylko na podstawie możliwego braku dokładności.

##### <a name="determinate"></a>Zdeterminowany
 ![Pasek postępu determinacji](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Pasek postępu determinacji**

 "Determinate" oznacza, że operacja lub proces wymaga ograniczonego czasu, nawet jeśli nie można dokładnie przewidzieć tego czasu. Wyraźnie wskaż ukończenie. Nie pozwól, aby pasek postępu był na poziomie 100%, chyba że operacja została zakończona. Ustalanie animacji paska postępu powoduje przesunięcie od lewej do prawej z 0 do 100%.

 Nigdy nie przesuwaj wskaźnika postępu do tyłu podczas operacji. Pasek powinien przechodzić do przodu, gdy operacja rozpoczyna się i osiąga 100% po zakończeniu. Punktem na pasku postępu jest danie użytkownikowi informacji o tym, jak długo trwa cała operacja, niezależnie od tego, ile kroków jest zaangażowanych.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Współbieżne raportowanie (skumulowane paski postępu)
 Jeśli operacja będzie trwać długo — być może kilka minut — można użyć dwóch pasków postępu, jednego, który pokazuje ogólny postęp operacji, a drugiego dla postępu bieżącego kroku. Jeśli na przykład program instalacyjny kopiuje wiele plików, można użyć jednego paska postępu, aby wskazać, jak długo trwa cały proces, a drugi może wskazać procent kopiowania bieżącego pliku lub katalogu. Nie raportuj więcej niż pięciu współbieżnych operacji lub procesów przy użyciu skumulowanych pasków postępu. Jeśli raport obejmuje więcej niż pięć współbieżnych operacji lub procesów, użyj modalnego okna dialogowego z przyciskiem Anuluj i zgłoś szczegóły postępu Okno Dane wyjściowe.

##### <a name="textual-descriptions"></a>Opisy tekstowe
 Użyj opisu tekstowego, aby towarzyszyć temu, co się dzieje, i szacowanego czasu do ukończenia. Jeśli nie można określić, jak długo będzie trwać operacja, lepszym wyborem do dawania opinii może być animowana ikona, a nie pasek postępu.

 Visual Studio standardowy pasek postępu na pasku stanu, który może być używany przez dowolny produkt zintegrowany z Visual Studio. Tekstowe opisy tego, co się dzieje, gdy pasek postępu jest animowany, można zaktualizować tekst na pasku stanu.

#### <a name="other-progress-indicators"></a>Inne wskaźniki postępu

##### <a name="ants-animated-horizontal-dots"></a>Ants (animowane poziome kropki)
 ![Progress ants (Postępy)](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 Animowane poziome kropki "Ants" stanowią wizualne odwołanie do nieokreślonych rundy procesu serwera.

##### <a name="spinner-progress-ring"></a>Pokrętło (pierścień postępu)
 ![Pokrętło postępu](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Pokrętło (nazywane również "pierścieniem postępu") jest nieokreślonym wskaźnikiem postępu używanym głównie w odniesieniu do kontekstowego interfejsu użytkownika. Wyświetla pokrętło w pobliżu powiązanej zawartości, takiej jak tekstowy nagłówek kategorii, komunikaty lub kontrolka.

##### <a name="cursor-feedback"></a>Opinie dotyczące kursora
 W przypadku operacji, które potrwają od 2 do 7 sekund, podaj opinię kursora. Zazwyczaj oznacza to użycie kursora oczekiwania dostarczonego przez system operacyjny. Aby uzyskać wskazówki, zobacz artykuł w witrynie MSDN [Cursors.Wait Property (Właściwość Cursors.Wait).](/dotnet/api/system.windows.input.cursors.wait)

#### <a name="progress-indicator-locations"></a>Lokalizacje wskaźników postępu

##### <a name="status-bar"></a>Pasek stanu
 Pasek stanu zapewnia aplikacji miejsce do wyświetlania komunikatów i przydatnych informacji użytkownikowi bez zakłócania pracy użytkownika. Zwykle wyświetlany w dolnej części okna stan postępu będzie okienkiem etykietki narzędzia, które zawiera komunikat o mierze postępu w połączeniu ze wskaźnikiem paska postępu.

 ![Pasek stanu z pasekem postępu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Pasek stanu z pasekem postępu**

 ![Pasek stanu z komunikatami](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Pasek stanu z opisem tekstowym**

##### <a name="infobar"></a>Pasek informacji
 Podobnie jak na pasku stanu, pasek informacji zawiera kontekstowe powiadomienia i komunikaty, które mogą być również sparowane z nieokreślonymi wskaźnikami postępu, takimi jak pasek postępu lub pokrętło. Pasek informacji nie powinien zapewniać szczegółowego postępu na poziomie ani wskazywać postępu. Zobacz [Infobars (Pasek informacji).](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)

 ![Pasek informacji z paskami postępu i komunikatami](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Pasek informacyjny z pasekem postępu i opisem tekstowym**

 ![Pasek informacji w oknie](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Śródwierszowo
 Wbudowane wskazanie postępu może być reprezentowane przez dowolny typ modułu ładującego postępu. Zazwyczaj wskaźnik postępu jest sparowany z komunikatami, ale nie jest to wymagane.

 ![Pokrętło postępu wbudowanego](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Pokrętło połączone z opisem tekstowym**

 ![Wbudowane skumulowane paski postępu](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Determinuj skumulowane paski postępu**

 ![Komunikaty o postępie w tekście](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Eksplorator serwera tekst w tekście: Odświeżanie...**

##### <a name="tool-windows"></a>Okna narzędzi
 Globalne wskazanie postępu jest reprezentowane przez nieokreślony pasek postępu umieszczony bezpośrednio pod pasek narzędzi.

 ![Globalny, nieokreślony pasek postępu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer globalny, nieokreślony pasek postępu**

##### <a name="dialogs"></a>Okna dialogowe
 Okna dialogowe mogą zawierać dowolny typ modułu ładującego postępu. Wskaźniki postępu mogą być sparowane z komunikatami, a także połączone z wieloma poziomami oznaczania postępu w celu reprezentowania szczegółowych i podrzędnych procesów.

 ![Okno dialogowe z wieloma typami wskaźników postępu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Visual Studio dialogowe z współbieżnych procesów i wieloma typami wskaźników postępu**

 ![Okno dialogowe z modułu ładującego postępu i komunikatów](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Visual Studio dialogowe z modułu ładującego postępu i komunikatów wbudowanego polecenia**

##### <a name="document-well"></a>Dobrze udokumentuj
 W dokumencie można wyświetlać wiele typów modułu ładującego postępu w połączeniu z kontrolkami.

 ![Wysyłanie komunikatów o postępie w dokumencie](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Nieokreślony pasek postępu poniżej paska narzędzi**

##### <a name="output-window"></a>Okno wyniku
 Okno Dane wyjściowe jest odpowiednie do obsługi postępu procesu i bieżącego stanu postępu za pośrednictwem wbudowanej wiadomości tekstowej. Należy użyć paska Stanu wraz z dowolnym raportowaniem postępu okna danych wyjściowych.

 ![Komunikaty o postępie w Okno Dane wyjściowe](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Okno Dane wyjściowe z bieżącym stanem procesu i komunikatami oczekiwania**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Pasek informacji

### <a name="overview"></a>Omówienie
 Pasek informacji zapewnia użytkownikowi wskaźnik blisko punktu uwagi, a użycie udostępnionej kontrolki paska informacji zapewnia spójność wizualnego wyglądu i interakcji.

 ![Pasek informacji](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Pasek informacji w Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Odpowiednie zastosowania paska informacyjnego

- Aby przekazać użytkownikowi nieblokujący, ale ważny komunikat odpowiedni dla bieżącego kontekstu

- Aby wskazać, że interfejs użytkownika jest w określonym stanie lub stanie, który wiąże się z pewnymi implikacjami interakcji, takimi jak debugowanie historyczne

- Aby powiadomić użytkownika, że system wykrył problemy, na przykład gdy rozszerzenie powoduje problemy z wydajnością

- Aby zapewnić użytkownikowi sposób łatwego podjęcia akcji, na przykład gdy edytor wykryje, że plik zawiera mieszane karty i spacje

##### <a name="do"></a>Zrobić:

- Tekst komunikatu na pasku informacyjnym nie może być krótki i do punktu.

- Zachowaj zwięzły tekst w linkach i przyciskach.

- Upewnij się, że opcje "akcji" zapewniane użytkownikom są minimalne i zawierają tylko wymagane akcje.

##### <a name="dont"></a>Nie:

- Użyj paska informacyjnego, aby zaoferować standardowe polecenia, które powinny być umieszczone na pasku narzędzi.

- Użyj paska informacyjnego w miejsce modalnego okna dialogowego.

- Utwórz komunikat przestawny poza oknem.

- Użyj wielu paskach informacyjnych w kilku lokalizacjach w tym samym oknie.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Czy w tym samym czasie może być pokazywanych wiele paska informacji?
 Tak, wiele paseków informacyjnych może być jednocześnie pokazywanych. Będą one wyświetlane w zamówieniu "pierwszy, pierwszy" z wyświetlonym pierwszym pasek informacyjnym oraz dodatkowymi paskami informacyjnymi widocznymi poniżej.

 Użytkownik zobaczy maksymalnie trzy paski informacyjne na raz, po czym, jeśli będzie dostępnych więcej pasków informacyjnych, region paska informacji stanie się przewijany.

### <a name="creating-an-infobar"></a>Tworzenie paska informacyjnego
 Pasek informacyjny ma cztery sekcje od lewej do prawej:

- **Ikona:** W tym miejscu należy dodać dowolną ikonę, która ma być wyświetlana dla paska informacji, na przykład ikonę ostrzeżenia.

- **Tekst:** Możesz dodać tekst opisujący scenariusz/sytuację, w której znajduje się użytkownik, wraz z linkami w tekście, jeśli jest to wymagane. Pamiętaj, aby zachować zwięzłość tekstu.

- **Akcje:** Ta sekcja powinna zawierać linki i przyciski dla akcji, które użytkownik może podjąć na pasku informacji.

- **Przycisk Zamknij:** Ostatnia sekcja po prawej stronie może mieć przycisk zamykania.

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

 Oto przykład tworzenia modelu InfoBarModel z tekstem z hiperlinkiem, przyciskiem akcji i ikoną.

 ![Pasek informacji z hiperlinkiem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Tworzenie standardowego paska informacji w kodzie natywnym
 Zaim implementuj interfejs IVsInfoBar w celu zapewnienia paska informacyjnego z kodu natywnego.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Pobieranie elementu interfejsu użytkownika paska informacji z paska informacji
 Implementacja InfoBarModel lub IVsInfoBar to modele danych, które muszą zostać przekształcone w element UIElement, aby można je było wyświetlać w interfejsie użytkownika. Element UIElement można pobrać za pomocą usługi SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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
 Pasek informacji można wyświetlać w co najmniej jednej z następujących lokalizacji:

- Okna narzędzi

- Na karcie dokumentu

> [!IMPORTANT]
> Pasek informacyjny można umieścić w celu przesłania komunikatu o kontekście globalnym. Pojawi się on między paskami narzędzi a sukami dokumentu. Nie jest to zalecane, ponieważ powoduje problemy z "skokowym i przeskokowym" ideą i należy tego unikać, chyba że jest to absolutnie konieczne i odpowiednie.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umieszczanie paska informacyjnego w narzędziu ToolWindowPane
 Metoda ToolWindowPane.AddInfoBar(IVsInfoBar) może służyć do dodawania paska informacyjnego do okna narzędzi. Ten interfejs API może dodawać element IVsInfoBar (z którego element InfoBarModel jest implementacją domyślną) lub element IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Umieszczanie paska informacyjnego w dokumencie lub innym niż ToolWindowPane
 Aby umieścić pasek informacyjny w dowolnym obiekcie IVsWindowFrame, użyj właściwości VSFPROPID_InfoBarHost, aby pobrać element IVsInfoBarHost dla ramki, a następnie dodaj element interfejsu użytkownika paska informacji.

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
 Aby umieścić pasek informacyjny w oknie głównym, użyj polecenia VSSPROPID_MainWindowInfoBarHost usługi IVsShell, aby pobrać element IVsInfoBarHost w oknie głównym, a następnie dodaj do niego element interfejsu użytkownika paska informacji.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Czy na pasku informacji będzie wiadomo, kiedy użytkownik podejmuje działania?
 Tak, każda akcja zdarzenia zostanie zwrócona autorowi paska informacji. Następnie autor paska informacji musi podjąć działania w ide na podstawie wyboru użytkownika na pasku informacyjnym. Pasek informacji zostanie automatycznie usunięty z hosta, którego przycisk Zamknij został klikony, ale dodatkowa praca jest wymagana, jeśli inne paseky informacyjne muszą zostać usunięte po zamknięciu. Dane telemetryczne muszą być rejestrowane niezależnie przez każdy pasek informacyjny.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Odbieranie zdarzeń paska informacyjnego w narzędziu ToolWindowPane
 ToolWindowPane ma dwa zdarzenia dla paska informacji. Zdarzenie InfoBarClosed jest wywoływane po zamknięciu paska informacyjnego w narzędziu ToolWindowPane. Zdarzenie InfoBarActionItemClicked jest wywoływane po kliknięciu hiperlinku lub przycisku na pasku informacyjnym.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Odbieranie zdarzeń paska informacyjnego bezpośrednio z elementu UIElement
 IVsInfoBarUIElement.Advise może służyć do subskrybowania zdarzeń bezpośrednio z elementu UIElement paska informacji. Zaimplementowanie zdarzenia IVsInfoBarUIEvents umożliwi autorowi odbieranie zdarzeń zamknięcia i kliknięcia.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Walidacja błędu
 Gdy użytkownik wprowadza informacje, które są niedopuszczalne, na przykład gdy wymagane pole zostanie pominięte lub gdy dane są wprowadzone w nieprawidłowym formacie, lepiej jest użyć weryfikacji kontrolki lub opinii w pobliżu kontrolki zamiast blokowania okna dialogowego błędu wyskakującego.

### <a name="field-validation"></a>Sprawdzanie poprawności pól
 Walidacja formularzy i pól składa się z trzech składników: kontrolki, ikony i etykietki narzędzia. Chociaż można użyć kilku typów kontrolek, jako przykładu zostanie użyte pole tekstowe.

 ![Pole weryfikacji &#40;puste&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Jeśli pole jest wymagane, powinien być w tym miejscu tekst limitu, a tło pola powinno być jasnożółte (VSColor: ), a pierwszy plan powinien **\<Required>** `Environment.ControlEditRequiredBackground` być szary (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Walidacja pola z etykietą "Required"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program może ustalić, że kontrolka  jest w stanie nieprawidłowej zawartości wprowadzonej, gdy fokus zostanie przeniesiony do innej kontrolki lub gdy użytkownik kliknie przycisk zatwierdzenia [OK] lub gdy użytkownik zapisze dokument lub formularz.

 Gdy zostanie określony nieprawidłowy stan zawartości, wewnątrz kontrolki lub po prostu obok niej zostanie wyświetlona ikona. Etykietka narzędzia opisująca błąd powinna pojawić się po umieszczeniu wskaźnika myszy na ikonie lub kontrolce. Ponadto wokół kontrolki, która tworzy nieprawidłowy stan, powinno pojawić się obramowanie 1 piksela.

 ![Specyfikacje układu walidacji pola](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Specyfikacje układu na stronie Walidacja pola**

#### <a name="acceptable-variations-for-icon-location"></a>Dopuszczalne odmiany lokalizacji ikony
 Istnieje niezliczona liczba unikatowych przypadków, w których użytkownicy muszą być poinformowani o błędach walidacji. Biorąc pod uwagę typ kontrolki i konfigurację interfejsu użytkownika, wybierz położenie ikony odpowiednie dla Twojej sytuacji.

 ![Dopuszczalne lokalizacje dla lokalizacji ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Dopuszczalne odmiany lokalizacji ikon weryfikacji pola**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Walidacja wymagająca rundy z serwerem lub połączeniem sieciowym
 W niektórych przypadkach w celu zweryfikowania zawartości wymagana jest runda na serwerze. Ważne jest, aby pokazać postęp, weryfikację i stany błędów użytkownika. Na poniższej ilustracji przedstawiono przykład tego przypadku i zalecany interfejs użytkownika.

 ![Walidacja obejmująca rundę do serwera](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Walidacja obejmująca rundę do serwera**

 Należy pamiętać, że po prawej stronie kontrolki należy podać odpowiednią ilość dostępnego miejsca w celu uwzględnienia informacji "Weryfikowanie..." i tekst "Ponów próbę".

#### <a name="in-place-warning-text"></a>Tekst ostrzeżenia w miejscu
 Jeśli jest dostępne miejsce na zamknięcie komunikatu o błędzie w pobliżu kontrolki w stanie błędu, preferowane jest użycie samej etykietki narzędzia.

 ![W&#45;umieść](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Tekst ostrzeżenia w miejscu**

#### <a name="watermarks"></a>Znaki wodne
 Czasami cała kontrolka lub okno jest w stanie błędu. W takiej sytuacji użyj znaku wodnego, aby wskazać błąd.

 ![Znak wodny](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Walidacja pola limitu**
