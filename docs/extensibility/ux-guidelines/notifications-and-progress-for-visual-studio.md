---
title: Powiadomienia i postęp dla programu Visual Studio | Microsoft Docs
description: Poznaj kilka sposobów, aby poinformować użytkowników, co dzieje się w programie Visual Studio, w odniesieniu do zadań związanych z programowaniem oprogramowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bac47ee29029bdcccb5c248bc8e366376b5aed0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931659"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Powiadomienia i postęp dla programu Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Systemy powiadomień

### <a name="overview"></a>Omówienie
 Istnieje kilka sposobów, aby poinformować użytkownika o tym, co dzieje się w programie Visual Studio, w odniesieniu do zadań programistycznych oprogramowania.

 Podczas implementowania dowolnego rodzaju powiadomienia:

- **Zachowaj liczbę powiadomień do minimalnej** liczby efektywnej. Komunikaty powiadomień powinny dotyczyć większości użytkowników programu Visual Studio lub użytkowników określonego obszaru funkcji/funkcji. Nadmierne wykorzystanie powiadomień może sidetrack użytkownika lub ograniczyć wygodę korzystania z systemu.

- **Upewnij się, że przedstawiasz elementy,** które użytkownik może użyć do wywołania odpowiedniego kontekstu w celu utworzenia bardziej złożonych opcji i podjęcia dalszych działań.

- **Zaprezentowanie odpowiednio synchronicznych i asynchronicznych komunikatów.** Powiadomienia synchroniczne wskazują, że coś wymaga natychmiastowej uwagi, na przykład w przypadku awarii usługi sieci Web lub zgłoszenia wyjątku kodu. Użytkownik powinien zostać powiadomiony o tych sytuacjach od razu w sposób, który wymaga ich danych wejściowych, takich jak modalne okno dialogowe. Powiadomienia asynchroniczne są tymi, które użytkownik powinien wiedzieć, ale nie muszą być wymagane natychmiastowego działania, na przykład po zakończeniu operacji kompilacji lub zakończeniu wdrożenia witryny sieci Web. Komunikaty te powinny być bardziej otoczenia i nie przerywają przepływu zadań użytkownika.

- **Użyj modalnych okien dialogowych tylko wtedy, gdy jest to konieczne, aby uniemożliwić użytkownikowi podejmowanie dalszych działań** przed potwierdzeniem komunikatu lub podjęciem decyzji przedstawionej w oknie dialogowym.

- **Usuń powiadomienia otoczenia, gdy nie są już prawidłowe.** Nie należy wymagać, aby użytkownik odrzucić powiadomienie, jeśli podjął już akcję dotyczącą problemu, o którym powiadomiono.

- **Należy pamiętać, że powiadomienia mogą prowadzić do fałszywych korelacji.** Użytkownicy mogą podejrzewać, że co najmniej jedna z akcji wywołała powiadomienie, gdy w rzeczywistości nie istniała żadna związek przyczynowy. Należy wyczyścić komunikat powiadomienia o kontekście, wyzwalaczu i źródle powiadomienia.

### <a name="choosing-the-right-method"></a>Wybieranie właściwej metody
 Skorzystaj z tej tabeli, aby pomóc w wyborze odpowiedniej metody powiadamiania użytkownika o wiadomości.

|Metoda|Zastosowanie|Nie używaj|
|------------|---------|----------------|
|[Modalne okna dialogowe komunikatu o błędzie](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Użyj, gdy odpowiedź użytkownika jest wymagana przed kontynuowaniem.|Nie należy używać, gdy nie ma potrzeby blokowania użytkownika i przerywania ich przepływu. Należy unikać używania modalnych okien dialogowych, jeśli jest możliwe wyświetlenie komunikatu w innej, mniej niepożądanej sposób.|
|[Pasek stanu IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Użyj w przypadku otoczenia informacji tekstowych dotyczących stanu procesu.|Nie używaj samego siebie. Najlepiej używać w połączeniu z innym mechanizmem przesyłania opinii.|
|[Osadzony pasek informacyjny](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|W oknie narzędzi lub oknie dokumentu Użyj do powiadomienia o postępie, stanie błędu, wynikach i/lub informacjach z możliwością działania.|Nie używaj, jeśli informacje nie są istotne dla lokalizacji, w której znajduje się pasek informacji.<br /><br /> Nie używaj poza oknem dokumentu/narzędzia.|
|[Zmiany kursora myszy](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Może służyć do powiadamiania o przejściu procesu. Służy również do powiadamiania o zmianie stanu na myszy, na przykład gdy trwa przeciąganie/upuszczanie lub kursor myszy znajduje się w określonym trybie, takim jak tryb rysowania.|Nie należy używać na potrzeby zmian krótkich postępów lub jeśli Fluttering kursora jest najprawdopodobniej (na przykład w przypadku części większego uruchomionego procesu, a nie całego procesu).|
|[Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Użyj, gdy chcesz raportować postęp (Przerwij lub nieokreślone). Istnieją różne typy wskaźników postępu i konkretne użycie dla każdego z nich. Zobacz [wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Okno powiadomień programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno powiadomienia nie jest publicznie rozszerzalne. Jest on jednak używany do komunikowania się z zakresem komunikatów o programie Visual Studio, w tym w przypadku problemów krytycznych dotyczących licencji i powiadomień informacyjnych dotyczących aktualizacji programu Visual Studio lub pakietów.|Nie należy używać w przypadku innych typów powiadomień.|
|[Lista błędów](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Gdy problem odnosi się bezpośrednio do aktualnie otwartego rozwiązania użytkownika o problemie (błąd/ostrzeżenie/informacje), może być konieczne wykonanie akcji na kodzie.<br /><br /> Może to obejmować na przykład:<br /><br /> -Komunikaty kompilatora (Error/Warning/info)<br /><br /> -Analizator kodu/komunikaty diagnostyczne dotyczące kodu<br /><br /> -Build messages<br /><br /> Mogą być odpowiednie w przypadku problemów związanych z plikami projektu lub rozwiązania, ale najpierw należy rozważyć wskazanie Eksplorator rozwiązań.|Nie należy używać dla elementów, które nie mają żadnych relacji z otwartym kodem rozwiązania użytkownika.|
|Powiadomienia edytora: żarówka|Użyj, gdy jest dostępna poprawka do rozwiązania problemu, który istnieje w otwartym pliku.<br /><br /> Należy zauważyć, że żarówka powinna również służyć do hostowania szybkich akcji podejmowanych na żądanie użytkownika, takich jak refaktoryzacje, ale w takim przypadku nie będą wyświetlane "styl powiadomienia".|Nie należy używać dla elementów, które nie mają żadnych relacji z otwartym plikiem.|
|Powiadomienia edytora: zygzaki|Użyj, aby ostrzec użytkownika o problemie z konkretnym zakresem ich otwartego kodu (na przykład czerwony zygzak dla błędów).|Nie należy używać w przypadku elementów, które nie są powiązane z konkretnym zakresem otwartych kodów.|
|[Osadzone paski stanu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Użyj, aby podać stan związany z zawartością lub procesem w kontekście określonego okna narzędzi, okna dokumentu lub okna dialogowego.|Nie należy używać w przypadku ogólnych powiadomień, procesów ani elementów, które nie mają żadnych relacji z zawartością w określonym oknie.|
|[Powiadomienia na pasku zadań systemu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Służy do otrzymywania powiadomień na temat procesów niezwiązanych z procesem lub aplikacji pomocniczych.|Nie należy używać do powiadomień, które są istotne dla środowiska IDE.|
|[Dymki powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Służy do powiadamiania procesu zdalnego lub zmiany **poza** IDE.|Nie należy używać jako metody powiadamiania użytkownika o procesach **w środowisku** IDE.|

### <a name="notification-methods"></a>Metody powiadamiania

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Modalne okna dialogowe komunikatu o błędzie
 Modalne okno dialogowe komunikatu o błędzie służy do wyświetlania komunikatu o błędzie, który wymaga potwierdzenia użytkownika lub jego akcji.

 ![Modalny komunikat o błędzie](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 — 01_ModalErrorMessage")

 **Modalne okno dialogowe komunikatu o błędzie ostrzega użytkownika o nieprawidłowych parametrach połączenia z bazą danych**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Pasek stanu IDE
 Prawdopodobieństwo, że użytkownicy mogą zauważyć, że tekst paska stanu jest skorelowany ze wszystkimi środowiskami komputera i określonym doświadczeniem z platformą Windows. Podstawa klienta programu Visual Studio jest zaświadczona w obu obszarach, mimo że użytkownicy systemu Windows z informacją o wiedzy mogą pominąć zmiany na pasku stanu. Z tego względu pasek stanu najlepiej służy do celów informacyjnych lub jako nadmiarowy wskaźnik dla informacji prezentowanych w innym miejscu. Wszelkie krytyczne informacje, które użytkownik musi rozwiązać natychmiast, powinny być podane w oknie dialogowym lub w oknie narzędzia powiadomienia.

 Pasek stanu programu Visual Studio został zaprojektowany tak, aby umożliwić wyświetlanie kilku typów informacji. Jest podzielony na regiony w celu uzyskania opinii, projektanta, paska postępu, animacji i klienta.

 Region opinii i region projektanta są zawsze widoczne. Pasek postępu i regiony animacji są zawsze dynamiczne i oparte na kontekście użytkownika. Region projektanta ma szerokość statyczną określoną przez długość ciągu, który jest pobierany z towarzyszącego zasobu dla wiadomości tekstowej. Pozwala to lokalizacji na zmianę rozmiaru szerokości bez konieczności zmiany kodu. W przypadku języka angielskiego Szerokość tego ciągu jest około 220 pikseli. Region projektanta będzie działać normalnie, a region opinii będzie wchłonąć pozostałe miejsce.

 Kolor paska stanu jest również określany w celu dodania interesujących elementów wizualnych i wartości funkcjonalnych przez komunikowanie się różnych zmian stanu IDE, takich jak gdy IDE jest w trybie debugowania.

 ![Zmiany koloru paska stanu środowiska IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 — 02_IDEStatusBar")

 **Kolory paska stanu IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Osadzony pasek informacyjny
 Pasek informacyjny może być używany w górnej części okna dokumentu lub okna narzędzi, aby poinformować użytkownika o stanie lub warunku. Może również oferować polecenia, aby użytkownik mógł w łatwy sposób podjąć odpowiednie działania. Pasek informacyjny jest standardową kontrolkę powłoki. Unikaj tworzenia własnych elementów, które będą działać i będą niespójne z innymi w środowisku IDE. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) , aby uzyskać szczegółowe informacje dotyczące implementacji i wskazówki dotyczące użycia.

 ![Osadzony pasek informacyjny](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 — 03_EmbeddedInfobar")

 **Pasek informacyjny osadzony w oknie dokumentu, informujący użytkownika, że IDE jest w trybie debugowania historycznego, a Edytor nie odpowie w taki sam sposób, jak w trybie debugowania standardowego.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Zmiany kursora myszy
 Podczas zmiany kursora myszy Użyj kolorów powiązanych z usługą VSColor i są one już skojarzone z kursorem. Zmiany kursora mogą być używane do wskazywania trwającej operacji, a także stref trafień, w których użytkownik jest aktywowany na miejscu docelowym, który można przeciągnąć, porzucić lub użyć do wybrania obiektu.

 Za pomocą kursora myszy zajętego/zaczekaj tylko wtedy, gdy wszystkie dostępne czas procesora CPU muszą być zarezerwowane dla operacji, uniemożliwiając użytkownikowi wyrażenie dalszych danych wejściowych. W większości przypadków z dobrze wypisanymi aplikacjami przy użyciu wielowątkowości, czasy, w których użytkownicy nie mogą wykonać innych operacji, powinny być rzadkie.

 Pamiętaj, że zmiany kursora są przydatne jako nadmiarowe wskazówki dla informacji prezentowanych w innym miejscu. Nie należy polegać na zmianie kursora jako jedynego sposobu komunikowania się z użytkownikiem, szczególnie podczas próby przekazania czegoś o znaczeniu krytycznym dla użytkownika.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Wskaźniki postępu
 Wskaźniki postępu są ważne do przekazywania opinii użytkowników w trakcie procesów, które trwają więcej niż kilka sekund. Wskaźniki postępu mogą być wyświetlane w miejscu (blisko punktu uruchomienia akcji w toku), na osadzonym pasku stanu, w oknie dialogowym modalnym lub na pasku stanu programu Visual Studio. Postępuj zgodnie ze wskazówkami w [wskaźnikach postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) dotyczących ich użycia i implementacji.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Okno powiadomień programu Visual Studio
 Okno powiadomienia programu Visual Studio powiadamia deweloperów o licencjonowaniu, środowisku (Visual Studio), rozszerzeniach i aktualizacjach. Użytkownicy mogą odrzucać pojedyncze powiadomienia lub ignorować niektóre typy powiadomień. Lista ignorowanych powiadomień jest zarządzana na stronie **narzędzia > opcje** .

 Okno powiadomienia nie jest obecnie rozszerzalne.

 ![Okno powiadomień programu Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 — 06_VSNotificationsWindow")

 **Okno narzędzia powiadomień programu Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Lista błędów
 Powiadomienie na liście błędów wskazuje błędy i ostrzeżenia, które wystąpiły podczas kompilacji lub procesu kompilacji, i umożliwia użytkownikowi nawigowanie w kodzie do tego błędu kodu.

 ![Lista błędów](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 — 08_ErrorList")

 **Lista błędów w programie Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Osadzone paski stanu
 Ponieważ pasek stanu IDE jest dynamiczny, z kontekstem regionu klienta ustawionym na okno aktywnego dokumentu i aktualizacjami informacji na temat kontekstu i/lub odpowiedzi użytkownika, trudno jest zachować ciągły sposób wyświetlania informacji lub nadawać status długoterminowych procesów asynchronicznych. Na przykład pasek stanu IDE nie jest odpowiedni do powiadomień o wynikach przebiegu testu dla wielu operacji i/lub natychmiastowego wyboru elementu. Ważne jest, aby zachować takie informacje o stanie w kontekście dokumentu lub okna narzędzi, w którym użytkownik dokonuje wyboru lub uruchamia proces.

 ![Osadzony pasek stanu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 — 09_EmbeddedStatusBar")

 **Osadzony pasek stanu w programie Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Powiadomienia na pasku zadań systemu Windows
 Obszar powiadomień systemu Windows jest obok zegara systemowego na pasku zadań systemu Windows. Wiele narzędzi i składników oprogramowania zawiera ikony w tym obszarze, dzięki czemu użytkownik może uzyskać menu kontekstowe dla zadań dla całego systemu, takich jak zmiana rozdzielczości ekranu lub uzyskanie aktualizacji oprogramowania.

 Powiadomienia na poziomie środowiska powinny być wyświetlane w centrum powiadomień programu Visual Studio, a nie w obszarze powiadomień systemu Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Dymki powiadomień
 Bąbelki powiadomień mogą występować jako informacje w edytorze/projektancie lub w obszarze powiadomień systemu Windows. Użytkownik postrzega te bąbelki jako problemy, które mogą zostać później rozwiązane, co stanowi korzyść dla niekrytycznych powiadomień. Bąbelki są nieodpowiednie w przypadku krytycznych informacji, które użytkownik musi natychmiast rozwiązać. Jeśli używasz bąbelków powiadomień w programie Visual Studio, postępuj zgodnie ze [wskazówkami na pulpicie systemu Windows dotyczącymi bąbelków powiadomień](/windows/desktop/uxguide/mess-notif).

 ![Dymek powiadomień](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 — 07_NotificationBubbles")

 **Dymek powiadomień w obszarze powiadomień systemu Windows używanym dla programu Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Wskaźniki postępu

### <a name="overview"></a>Omówienie
 Wskaźniki postępu są ważną częścią systemu powiadomień w celu przekazywania opinii użytkownika. Poinformują użytkownika, kiedy procesy i operacje zostaną ukończone. Znane typy wskaźników obejmują paski postępu, obracające się kursory i ikony animowane. Typ i rozmieszczenie wskaźnika postępu zależy od kontekstu, w tym informacje o raportowaniu i czas ukończenia procesu lub operacji.

#### <a name="factors"></a>Elementy
 Aby określić, który typ wskaźnika jest odpowiedni, należy określić poniższe czynniki.

1. **Chronometraż:** czas trwania operacji

2. **Modalne:** czy operacja jest modalna dla środowiska (blokuje interfejs użytkownika do momentu zakończenia procesu)

3. **Trwały/przejściowy:** określa, czy końcowy wynik postępu musi być raportowany i/lub widoczny w późniejszym czasie

4. **Odkończ/nieokreślone:** określa, czy można obliczyć czas zakończenia operacji i postęp

5. **Lokalizacja graficzna/tekstowa:** czy postęp lub proces są przechwytywane wewnętrznie, w treści komunikatu lub w określonej kontrolce, takiej jak kontrolka drzewa

6. **Bliskość:** czy postęp powinien znajdować się w pobliżu interfejsu użytkownika, z którym jest powiązany. (Na przykład może znajdować się na pasku stanu, który może być daleko lub czy musi znajdować się blisko przycisku, który uruchomił proces?)

#### <a name="determinate-progress"></a>Postęp dekończenia

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (rozkończ)|Oczekiwany czas trwania wynoszący >5 sekund.<br /><br /> Może zawierać tekstowy opis szczegółowych informacji o procesie.|**Nie** osadzaj tekstu w animacji.|
|Powiadomienie|Obsługa komunikatów skojarzonych z kontekstowym interfejsem użytkownika. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Może zawierać tekstowy opis szczegółowych informacji o procesie.|**Nie** używaj wielu infobars, gdy musisz wskazać wiele procesów. Zamiast tego użyj pasków postępu skumulowanych.|
|Okno wyniku|Powiadomienie przejściowe: proces na poziomie aplikacji, którego użytkownik chce **przejrzeć** szczegóły po zakończeniu.|**Nie** Używaj, jeśli użytkownik będzie musiał później odwołać się do danych.|
|Plik dziennika|Sparowane z powiadomieniem nieprzejściowym w przypadkach, gdy ważne jest **zapisanie** szczegółów po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowe: proces na poziomie aplikacji, którego użytkownik **nie będzie potrzebował** szczegółów po zakończeniu.<br /><br /> Zawiera osadzony pasek postępu.<br /><br /> Może zawierać tekstowy opis szczegółowych informacji o procesie.||

#### <a name="indeterminate-progress"></a>Nieokreślony postęp

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (nieokreślony)|Oczekiwany czas trwania wynoszący >5 sekund.<br /><br /> Może zawierać tekstowy opis szczegółowych informacji o procesie.|**Nie** osadzaj tekstu w animacji.|
|ANTS (animowane kropki w poziomie)|Rundy z serwerem.<br /><br /> Umieszczony blisko punktu kontekstu w stosunku do kontenera nadrzędnego.|**Nie** należy używać go, jeśli nie jest elementem nadrzędnym przez cały kontener.|
|Pokrętło (pierścień postępu)|Proces skojarzony z kontekstowym interfejsem użytkownika lub miejscem, gdzie jest brany pod uwagę.<br /><br /> Może zawierać tekstowy opis szczegółowych informacji o procesie.||
|Powiadomienie|Obsługa komunikatów skojarzonych z kontekstowym interfejsem użytkownika. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nie** używaj wielu infobars, gdy musisz wskazać wiele procesów. Zamiast tego użyj pasków postępu skumulowanych.|
|Okno wyniku|Powiadomienie przejściowe: proces na poziomie aplikacji, który użytkownik będzie chciał **przejrzeć** szczegóły po zakończeniu.|**Nie** należy używać w celu uzyskania informacji, które muszą być utrwalane między sesjami.|
|Plik dziennika|Sparowane z powiadomieniem nieprzejściowym w przypadkach, gdy ważne jest **zapisanie** szczegółów po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowe: proces na poziomie aplikacji, którego użytkownik **nie będzie potrzebował** szczegółów po zakończeniu.<br /><br /> Zawiera osadzony pasek postępu.<br /><br /> Może zawierać tekstowy opis szczegółowych informacji o procesie.||

### <a name="progress-indicator-types"></a>Typy wskaźników postępu

#### <a name="progress-bars"></a>Paski postępu

##### <a name="indeterminate"></a>Określona
 ![Nieokreślony pasek postępu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 — 04_Indeterminate")

 **Nieokreślony pasek postępu**

 "Nieokreślone" oznacza ogólny postęp operacji lub procesu nie może zostać określony. Użyj nieokreślonych pasków postępu dla operacji wymagających nieograniczonego czasu lub uzyskania dostępu do nieznanej liczby obiektów. Użyj opisu tekstowego, aby dołączać się do tego, co się dzieje. Użyj limitów czasu, aby zapewnić zakres operacji opartych na czasie. Nieokreślone paski postępu używają animacji, aby pokazać ten postęp, ale nie podawać innych informacji. Nie wybieraj nieokreślonego paska postępu w oparciu tylko o możliwy brak dokładności.

##### <a name="determinate"></a>Przerwij
 ![Pasek postępu dekończenia](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 — 05_Determinate")

 **Pasek postępu dekończenia**

 "Odkończ" oznacza, że operacja lub proces wymaga ograniczonego czasu, nawet jeśli nie można dokładnie przewidzieć tego czasu. Jasno wskazuje uzupełnianie. Nie pozwól, aby pasek postępu przeszedł do 100%, chyba że operacja została ukończona. Odkończ animację paska postępu od 0 do 100%.

 Nie przenoś wskaźnika postępu z tyłu w trakcie operacji. Pasek powinien zostać przesunięty w dół, gdy rozpoczyna się operacja i osiągnie 100% czasu. Punkt na pasku postępu ma dać użytkownikowi pomysł na to, jak długo trwa cała operacja, niezależnie od tego, ile kroków jest związanych.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Współbieżne Raportowanie (skumulowane paski postępu)
 Jeśli operacja będzie długotrwała, może trwać kilka minut, a następnie można użyć dwóch pasków postępu, jednego, który pokazuje ogólny postęp operacji i drugi dla postępu bieżącego kroku. Na przykład jeśli program instalacyjny kopiuje wiele plików, można użyć jednego paska postępu, aby wskazać, jak długo cały proces trwa, a druga może wskazywać, jaki procent bieżącego pliku lub katalogu jest kopiowany. Nie zgłaszaj więcej niż pięciu współbieżnych operacji lub procesów przy użyciu skumulowanych słupków postępu. Jeśli masz więcej niż pięć współbieżnych operacji lub procesów do raportowania, użyj modalnego okna dialogowego z przyciskiem Anuluj i Zgłoś szczegóły postępu w Okno Dane wyjściowe.

##### <a name="textual-descriptions"></a>Opisy tekstowe
 Użyj opisu tekstowego, aby dołączyć się do tego, co się dzieje, i szacowany czas do ukończenia. Jeśli nie można ustalić czasu trwania operacji, lepszym wyborem do przekazywania opinii może być animowana ikona, a nie pasek postępu.

 Program Visual Studio udostępnia standardowy pasek postępu na pasku stanu, który może być używany przez dowolny produkt zintegrowany z Visual Studio. Aby uzyskać tekstowe opisy dotyczące tego, co dzieje się, gdy pasek postępu jest animowany, tekst paska stanu można zaktualizować.

#### <a name="other-progress-indicators"></a>Inne wskaźniki postępu

##### <a name="ants-animated-horizontal-dots"></a>ANTS (animowane kropki w poziomie)
 ![ANTS postępu](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 — 01_Ants")

 "ANTS", "animowane kropki poziome", podaj odwołanie wizualizacji dla nieokreślonego procesu serwera w postaci okrężnej.

##### <a name="spinner-progress-ring"></a>Pokrętło (pierścień postępu)
 ![Pokrętło postępu](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 — 02_Spinner")

 Pokrętło (znany również jako "pierścień postępu") to nieokreślony wskaźnik postępu używany głównie w odniesieniu do kontekstowego interfejsu użytkownika. Wyświetl pokrętło w pobliżu swojej powiązanej zawartości, takiej jak nagłówek kategorii tekstu, obsługa komunikatów lub kontrola.

##### <a name="cursor-feedback"></a>Opinia dotycząca kursora
 W przypadku operacji, które trwają od 2-7 sekund, należy podać informacje zwrotne kursora. Zazwyczaj oznacza to użycie kursora oczekiwania dostarczonego przez system operacyjny. Aby uzyskać wskazówki, zobacz Właściwość * Cursors [. wait](/dotnet/api/system.windows.input.cursors.wait)artykułu MSDN.

#### <a name="progress-indicator-locations"></a>Lokalizacje wskaźnika postępu

##### <a name="status-bar"></a>Pasek stanu
 Pasek stanu zapewnia aplikacji miejsce do wyświetlania komunikatów i przydatnych informacji dla użytkownika bez zakłócania pracy użytkownika. Zwykle wyświetlany u dołu okna, stan postępu będzie okienkiem etykietki narzędzia, która zawiera komunikat o mierze postępu w połączeniu ze wskaźnikiem paska postępu.

 ![Pasek stanu z paskiem postępu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 — 03_StatusBarProgressBar")

 **Pasek stanu z paskiem postępu**

 ![Pasek stanu z obsługą wiadomości](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 — 04_StatusBarMessage")

 **Pasek stanu z opisem tekstowym**

##### <a name="infobar"></a>Powiadomienie
 Podobnie jak w przypadku paska stanu, pasek informacji zawiera kontekstowe powiadomienia i komunikaty, które mogą być również sparowane z nieokreślonymi wskaźnikami postępu, takimi jak pasek postępu lub pokrętło. Pasek informacji nie powinien zapewniać postępu szczegółowości ani informacji o postępie dekończenia. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Pasek informacyjny z paskiem postępu i obsługą komunikatów](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 — 05_InfoBar")

 **Pasek informacyjny z paskiem postępu i opisem tekstowym**

 ![Pasek informacyjny w oknie](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 — 06_InfoBarInWindow")

##### <a name="inline"></a>Śródwierszowo
 Wbudowane wskazanie postępu może być reprezentowane przez dowolny z typów modułu ładującego postęp. Zazwyczaj wskaźnik postępu jest sparowany z obsługą komunikatów, ale nie jest to wymagane.

 ![Pokrętło postępu wbudowanego](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 — 07_InlineSpinner")

 **Pokrętło połączone z opisem tekstowym**

 ![Wbudowane paski postępu skumulowanego](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 — 08_InlineStackedProgress")

 **Rozkończ skumulowane paski postępu**

 ![Komunikaty o postępach wbudowanych](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 — 09_InlineText")

 **Eksplorator serwera tekst wbudowany: odświeżanie...**

##### <a name="tool-windows"></a>Okna narzędzi
 Globalny wskaźnik postępu jest reprezentowany przez nieokreślony pasek postępu umieszczony bezpośrednio pod paskiem narzędzi.

 ![Globalny pasek postępu nieokreślony](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 — 23_GlobalIndeterminate")

 **Team Explorer globalny nieokreślony pasek postępu**

##### <a name="dialogs"></a>Okna dialogowe
 Okna dialogowe mogą zawierać dowolne typy modułu ładującego postęp. Wskaźniki postępu można łączyć z wiadomościami, a także z wieloma poziomami wskazywania postępu, aby reprezentować szczegółowe i podrzędne procesy.

 ![Okno dialogowe z wieloma typami wskaźników postępu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 — 11_Dialog")

 **Okno dialogowe programu Visual Studio z współbieżnymi procesami i wieloma typami wskaźników postępu**

 ![Okno dialogowe z programem ładującym postęp i obsługą komunikatów](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 — 12_Dialog2")

 **Okno dialogowe programu Visual Studio z poleceniami ładującymi postęp i obsługą komunikatów wbudowanych**

##### <a name="document-well"></a>Źródło dokumentu
 Źródło dokumentu może wyświetlać wiele typów modułu ładującego postęp w połączeniu z kontrolkami.

 ![Komunikaty o postępie w źródle dokumentu](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 — 13_DocumentWell")

 **Nieokreślony pasek postępu poniżej paska narzędzi**

##### <a name="output-window"></a>Okno wyniku
 Okno dane wyjściowe jest odpowiednie do obsługi postępu procesu i stanu ciągłego postępu za pośrednictwem wbudowanej wiadomości tekstowej. Pasek stanu powinien być używany wraz z dowolnym raportem o postępie okna danych wyjściowych.

 ![Komunikaty postępu w Okno Dane wyjściowe](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 — 14_OutputWindow")

 **Okno Dane wyjściowe z trwającym stanem procesu i zaczekaj na komunikaty**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Infobars

### <a name="overview"></a>Omówienie
 Infobars nadaje użytkownikowi wskaźnik blisko punktu uwagi i użycie udostępnionej kontrolki paska na pasku informacji zapewnia spójność wyglądu i interakcji w wizualizacji.

 ![Powiadomienie](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904 — 01_Infobar")

 **Infobars w programie Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Odpowiednie zastosowania na pasku informacyjnym

- Aby dać użytkownikowi nieblokującego, ale ważny komunikat istotny dla bieżącego kontekstu

- Aby wskazać, że interfejs użytkownika znajduje się w określonym stanie lub warunku, który spełnia pewne implikacje interakcji, takich jak debugowanie historyczne

- Powiadomienie użytkownika, że system wykrył problemy, takie jak, gdy rozszerzenie powoduje problemy z wydajnością

- Aby zapewnić użytkownikowi możliwość łatwego podejmowania akcji, na przykład gdy Edytor wykryje, że plik zawiera mieszane karty i spacje

##### <a name="do"></a>Nie

- Pozostaw tekst komunikatu na pasku informacji jako krótki i do punktu.

- Pamiętaj, aby tekst na linkach i przyciskach był zwięzły.

- Upewnij się, że opcje "Akcja", które zapewniasz użytkownikom, są minimalne, pokazując tylko wymagane akcje.

##### <a name="dont"></a>Nie:

- Pasek informacyjny umożliwia oferowanie standardowych poleceń, które powinny być umieszczone na pasku narzędzi.

- Użyj paska informacyjnego zamiast modalnego okna dialogowego.

- Utwórz komunikat przestawny poza oknem.

- Użyj wielu infobars w kilku lokalizacjach w tym samym oknie.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Czy można wyświetlić wiele infobars w tym samym czasie?
 Tak, wiele infobars może być pokazywanych w tym samym czasie. Zostaną one wyświetlone w pierwszej kolejności, w której pierwsze jest obsługiwane, z pierwszym paskiem informacyjnym widocznym na górze i dodatkowym infobars pokazanym poniżej.

 Użytkownik zobaczy maksymalnie trzy infobars w danym momencie, a następnie, jeśli będą dostępne więcej infobars, region paska przeglądania stanie się przewijany.

### <a name="creating-an-infobar"></a>Tworzenie paska informacji
 Pasek informacyjny ma cztery sekcje, od lewej do prawej:

- **Ikona:** W tym miejscu możesz dodać dowolną ikonę, która ma być wyświetlana na pasku informacyjnym, na przykład ikonę ostrzeżenia.

- **Tekst:** W razie potrzeby można dodać tekst opisujący scenariusz/sytuację, w której znajduje się użytkownik. Pamiętaj, aby zachować tekst zwięzły.

- **Akcje:** Ta sekcja powinna zawierać linki i przyciski dotyczące akcji, które użytkownik może wykonać na pasku informacji.

- **Przycisk zamykania:** Ostatnia sekcja po prawej stronie może mieć przycisk Zamknij.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Tworzenie standardowego paska informacyjnego w kodzie zarządzanym
 Klasa InfoBarModel może służyć do tworzenia źródła danych dla paska informacyjnego. Użyj jednego z czterech następujących konstruktorów:

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

 Oto przykład, który tworzy InfoBarModel z tekstem z hiperłączem, przyciskiem akcji i ikoną.

 ![Pasek informacyjny z hiperłączem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 — 02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Tworzenie standardowego paska informacyjnego w kodzie natywnym
 Zaimplementuj interfejs IVsInfoBar, aby udostępnić pasek informacyjny z kodu natywnego.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Pobieranie elementu UIElement na pasku informacyjnym z paska informacji
 Implementacja InfoBarModel lub IVsInfoBar to modele danych, które muszą być włączone, aby były wyświetlane w interfejsie użytkownika. Element UIElement można pobrać przy użyciu usługi elementu svsinfobaruifactory/IVsInfoBarUIFactory.

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
 Infobars można wyświetlić w co najmniej jednej z następujących lokalizacji:

- Okna narzędzi

- Na karcie dokumentu

> [!IMPORTANT]
> Można umieścić pasek informacyjny, aby otrzymać komunikat dotyczący kontekstu globalnego. Ta wartość będzie wyświetlana między paskami narzędzi i obszarem dokumentu. Nie jest to zalecane, ponieważ powoduje problemy dotyczące "skoku i jerk" IDE i należy je unikać, chyba że jest to absolutnie konieczne i odpowiednie.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umieszczanie paska informacji w elementu toolwindowpane
 Za pomocą metody elementu toolwindowpane. AddInfoBar (IVsInfoBar) można dodać pasek narzędzi do okna narzędzia. Ten interfejs API może dodać IVsInfoBar (z którym InfoBarModel jest implementacją domyślną) lub IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Umieszczanie paska informacji w dokumencie lub innym niż elementu toolwindowpane
 Aby umieścić pasek informacyjny w dowolnym działanie funkcji IVsWindowFrame, użyj właściwości VSFPROPID_InfoBarHost, aby uzyskać IVsInfoBarHost dla ramki, a następnie Dodaj element UIElement na pasku informacyjnym.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Umieszczanie paska informacji w oknie głównym
 Aby umieścić pasek informacyjny w oknie głównym, użyj VSSPROPID_MainWindowInfoBarHost usługi IVsShell, aby uzyskać IVsInfoBarHost głównego okna, a następnie Dodaj do niego UIElement.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Wiemy, kiedy użytkownik wykonuje akcję na moim pasku informacji?
 Tak. zwrócimy każdą akcję zdarzenia do autora paska informacji. Następnie do autora paska informacji na pasku narzędzi zostanie podjęta akcja w środowisku IDE w oparciu o wybór użytkownika na pasku informacyjnym. Infobars zostanie automatycznie usunięta z hosta, którego przycisk zamknięcia został kliknięty, ale dodatkowe czynności są wymagane, jeśli inne Infobars należy usunąć po zamknięciu. Dane telemetryczne muszą być również rejestrowane niezależnie od poszczególnych pasków informacyjnych.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Otrzymywanie zdarzeń paska informacji w elementu toolwindowpane
 Elementu toolwindowpane ma dwa zdarzenia dla infobars. Zdarzenie InfoBarClosed jest wywoływane, gdy zostanie zamknięty pasek informacyjny w elementu toolwindowpane. Zdarzenie InfoBarActionItemClicked jest wywoływane, gdy kliknięto hiperłącze lub przycisk wewnątrz paska informacji.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Otrzymywanie zdarzeń paska informacji bezpośrednio z UIElement
 IVsInfoBarUIElement. Advise może służyć do subskrybowania zdarzeń bezpośrednio z elementu UIElement na pasku informacji. Wdrożenie IVsInfoBarUIEvents umożliwi autorowi otrzymywanie zdarzeń zamknięcia i kliknięcia.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Sprawdzanie poprawności błędów
 Gdy użytkownik wprowadza informacje, które nie są akceptowalne, na przykład wtedy, gdy wymagane pole jest pominięte lub gdy dane są wprowadzane w nieprawidłowym formacie, lepiej jest używać walidacji kontroli lub informacji zwrotnych blisko kontrolki zamiast korzystać z okna dialogowego błędów blokowania okienka wyskakującego.

### <a name="field-validation"></a>Sprawdzanie poprawności pól
 Walidacja formularzy i pól składa się z trzech składników: kontrolki, ikony i etykietki narzędzia. Chociaż kilka typów formantów może korzystać z tego, jako przykładu zostanie użyte pole tekstowe.

 ![Sprawdzanie poprawności pola &#40;puste&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 — 01_FieldValidation")

 Jeśli pole jest wymagane, powinien zawierać tekst znaku wodnego, **\<Required>** a tło pola powinno być żółte (VSColor: `Environment.ControlEditRequiredBackground` ), a pierwszy plan powinien być szary (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Sprawdzanie poprawności pola z etykietą "wymagane"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 — 02_FieldValidationRequired")

 Program może określić, że formant jest w stanie *nieprawidłowej zawartości* , gdy fokus jest przenoszony do innej kontrolki lub gdy użytkownik kliknie przycisk Zatwierdź [OK] lub gdy użytkownik zapisze dokument lub formularz.

 Po ustaleniu nieprawidłowego stanu zawartości ikona pojawia się wewnątrz kontrolki lub tuż obok niej. Etykietka narzędzia opisująca błąd powinna być wyświetlana po umieszczeniu ikony lub kontrolki. Ponadto wokół kontrolki, która tworzy nieprawidłowy stan, powinna zostać wyświetlona krawędź 1-pikseli.

 ![Specyfikacje układu sprawdzania poprawności pól](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 — 03_LayoutSpecs")

 **Specyfikacje układu dla weryfikacji pola**

#### <a name="acceptable-variations-for-icon-location"></a>Akceptowalne Wariacje dla lokalizacji ikon
 Istnieją niezliczone unikatowe przypadki, w których użytkownicy muszą być informowani o błędach walidacji. Biorąc pod uwagę typ formantu i konfigurację interfejsu użytkownika, wybierz ikonę umieszczania odpowiednią do danej sytuacji.

 ![Akceptowalne lokalizacje dla lokalizacji ikon](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 — 04_IconLocation")

 **Akceptowalne Wariacje dla lokalizacji ikon walidacji pól**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Walidacja wymagająca rundy do serwera lub połączenia sieciowego
 W niektórych przypadkach w celu zweryfikowania zawartości wymagane jest przekazanie do serwera, a ważne jest, aby pokazać postęp, zweryfikowane i Stany błędów użytkownika. Poniższy rysunek przedstawia przykład tego przypadku oraz zalecany interfejs użytkownika.

 ![Weryfikacja obejmująca rundę do serwera](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 — 05_RoundTrip")

 **Weryfikacja obejmująca rundę do serwera**

 Należy zauważyć, że odpowiednie dostępne miejsce z prawej strony kontrolki musi zostać podane w celu uwzględnienia "weryfikacji..." i "ponów" tekst.

#### <a name="in-place-warning-text"></a>Tekst ostrzeżenia w miejscu
 Gdy istnieje wolne miejsce, aby komunikat o błędzie był blisko formantu w stanie błędu, preferowane jest użycie samej etykietki narzędzia.

 ![Ostrzeżenie o miejscu&#45;](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 — 06_InPlaceWarning")

 **Tekst ostrzeżenia w miejscu**

#### <a name="watermarks"></a>Znaki wodne
 Czasami cały formant lub okno jest w stanie błędu. W tej sytuacji użyj znaku wodnego, aby wskazać błąd.

 ![-](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 — 07_Watermark")

 **Weryfikacja pola znaku wodnego**
