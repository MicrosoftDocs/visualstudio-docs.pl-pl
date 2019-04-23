---
title: Powiadomienia i postęp dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc5ddb4561c2c353271babe590a9e5b2b3c2e510
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044293"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Powiadomienia i postęp dla programu Visual Studio
## <a name="BKMK_NotificationSystems"></a> Systemy powiadomień

### <a name="overview"></a>Omówienie
 Istnieje kilka sposobów, aby poinformować użytkownika, co dzieje się w programie Visual Studio dotyczące ich zadań rozwoju oprogramowania.

 Podczas implementowania dowolnego rodzaju powiadomienia:

- **Zachowaj liczbę zgłoszeń do minimum** numer skuteczne. Komunikaty powiadomień powinny być stosowane dla większości użytkowników programu Visual Studio lub dla użytkowników obszaru określonych funkcji. Nadmiernego wykorzystania powiadomienia mogą być sidetrack użytkownika lub obniżyć postrzegany łatwość użycia systemu.

- **Upewnij się, jest wyświetlana jasny, możliwością wykonywania akcji wiadomości** czy użytkownik może użyć do wywołania odpowiedniego kontekstu zapewnianiu bardziej złożonych i podjęcie dalszych akcji.

- **Przedstawia komunikaty synchroniczne i asynchroniczne odpowiednio.** Synchroniczne powiadomienia wskazać, że jakieś elementy wymagają natychmiastowej uwagi, takie jak kiedy ulega awarii usługi sieci web lub kod wyjątku. Użytkownik, powinna być powiadamiana o sytuacji razu w taki sposób, który wymaga danych wejściowych, takich jak w modalne okno dialogowe. Asynchroniczne powiadomienia są te, które użytkownik powinien wiedzieć o, ale nie wymaga się działać od razu, np. po zakończeniu operacji tworzenia lub na zakończeniu wdrożenia witryny sieci web. Te komunikaty powinien być bardziej otoczenia i przerywają pracy przepływ zadań użytkownika.

- **Użyj modalne okna dialogowe tylko wtedy, gdy jest to niezbędne uniemożliwić użytkownikowi korzystanie z podjęciem dalszych działań** przed potwierdzając wiadomości lub podejmowania decyzji, znajdujące się w oknie dialogowym.

- **Usuń otoczenia powiadomienia, gdy nie są już prawidłowe.** Wymaga od użytkownika odrzucić powiadomienie, jeśli już jakieś działania, aby rozwiązać ten problem, który one zostali powiadomieni o.

- **Należy pamiętać, że powiadomienia może prowadzić do korelacji wartość false.** Użytkownicy mogą uważa, że co najmniej jeden z nich działania ma wyzwalane powiadomienie, gdy w rzeczywistości nie było żadnych przyczynowego. Być jasno komunikatu powiadomienia o kontekście, wyzwalacz i źródła powiadomienia.

### <a name="choosing-the-right-method"></a>Wybór odpowiedniej metody
 Pomocne w wyborze odpowiedniej metody w celu powiadomienia użytkownika wiadomości przy użyciu tej tabeli.

|Metoda|Zastosowanie|Nie używaj|
|------------|---------|----------------|
|[Modalne błąd komunikatu w oknach dialogowych](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Opcja używana podczas odpowiedź użytkownika jest wymagana przed kontynuowaniem.|Należy używać, gdy nie ma potrzeby zablokować użytkownika, a także przerwań ich przepływu. Należy unikać używania modalne okna dialogowe, jeśli jest to możliwe wyświetlić komunikat w sposób inny, ta opcja jest mniej pożądana.|
|[Pasek stanu IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Użycie po otoczenia tekstową informacji dotyczących stanu procesu.|Nie używaj samodzielnie. Najlepiej używać w połączeniu z innego mechanizmu opinii.|
|[Osadzony pasek informacyjny](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|W oknie narzędzia lub okno dokumentu używany do powiadamiania postępu, stan błędu, wyniki i/lub informacji.|Należy używać, jeśli informacje nie są odpowiednie do lokalizacji, w którym znajduje się pasek informacyjny.<br /><br /> Nie należy używać poza oknem dokumentu/narzędzia.|
|[Zmiany kursora myszy](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Może służyć do powiadomienia, że proces się dzieje. Umożliwia również powiadomi, że istnieje zmiana stanu mysz, takie jak podczas przeciągania i upuszczania jest w toku lub kursor myszy znajduje się w niektórych trybach, takie jak tryb rysowania.|Nie używaj w przypadku zmiany krótki postępu lub fluttering z kursora jest prawdopodobne, (na przykład, gdy powiązany z części dłużej procesu uruchomionego zamiast całego procesu).|
|[Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Użycie, w przypadku konieczności raportować postęp (określony lub nieokreślony). Istnieją różne typy wskaźników postępu i użycie określone dla każdego. Zobacz [wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Visual Studio powiadomienia okna](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno powiadomień nie jest rozszerzalna publicznie. Służy do komunikowania się z szeregu komunikaty dotyczące programu Visual Studio, w tym krytycznych problemów z licencji i informacyjny powiadomienia o aktualizacji do programu Visual Studio lub pakietów.|Nie należy używać dla innych typów powiadomień.|
|[Lista błędów](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Gdy problem odnosi się bezpośrednio do aktualnie otwartego rozwiązania użytkownika wystąpił problem (/ ostrzeżenia/informacje o błędzie), ich może być konieczne podejmowanie akcji na kod.<br /><br /> To dotyczy, na przykład:<br /><br /> — Komunikaty kompilatora (/ ostrzeżenia/informacje o błędzie)<br /><br /> -Code diagnostycznych analizatora komunikatów o kodzie<br /><br /> — Tworzenie wiadomości<br /><br /> Może być odpowiednie dla zagadnienia odnoszące się do plików projektu lub rozwiązania, ale najpierw należy wziąć pod uwagę wskazanie Eksploratora rozwiązań.|Nie należy używać dla elementów, które nie mają żadnych relacji kodowi otwartego rozwiązania użytkownika.|
|Edytor powiadomienia: Żarówka|Użycie, gdy poprawka jest dostępna rozwiązać problem, który istnieje w otwartego pliku.<br /><br /> Należy zauważyć, że ikona żarówki powinien być używany do hostowania szybkie akcje, które pochodzą od użytkownika kodu na żądanie, takie jak refaktoryzacji, ale w takiej sytuacji nie będą widoczne "style powiadomień".|Nie należy używać dla elementów, które nie mają żadnych relacji do otwartego pliku.|
|Edytor powiadomienia: Faliste linie|Użyj, aby ostrzec użytkownika wystąpił problem z określonego zakresu swój kod open (na przykład czerwona fala błędów).|Nie należy używać dla elementów, które nie odnoszą się do określonego zakresu swój kod open.|
|[Paski stanu osadzonego](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Służy do udostępniania informacji o stanie związane z zawartością lub proces w kontekście określonego narzędzia okna, okno dokumentu lub okna dialogowego.|Nie należy używać produktu ogólne powiadomienia, procesy lub elementy, które nie mają żadnych relacji z zawartością w określonym oknie.|
|[Windows na pasku powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Służy do powierzchni powiadomienia dla procesów procesem lub towarzyszące aplikacje.|Nie należy używać powiadomień, które mają zastosowanie w środowisku IDE.|
|[Bąbelki powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Użyj, aby powiadomić zdalnego procesu lub zmienić **poza** środowiska IDE.|Nie należy używać jako środek do powiadamiania użytkownika procesów **w ramach** IDE.|

### <a name="notification-methods"></a>Metody powiadamiania

#### <a name="BKMK_ModalErrorMessageDialogs"></a> Modalne błąd komunikatu w oknach dialogowych
 Błąd modalne okno dialogowe wiadomości jest używany do wyświetlania komunikat o błędzie, który wymaga potwierdzenia lub akcji użytkownika.

 ![Komunikat o błędzie modalne](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")

 **Okno dialogowe komunikat błędu modalne alerty użytkownika nieprawidłowe parametry połączenia z bazą danych**

#### <a name="BKMK_IDEStatusBar"></a> Pasek stanu IDE
 Jest prawdopodobieństwo, że użytkownicy zauważyć tekst paska stanu komputera wszechstronną środowiska i określonych doświadczenie z platformą Windows. Bazy klientów programu Visual Studio jest zwykle doświadczenie w obu obszarach, chociaż nawet wiedzą użytkownikom Windows pominąć zmian w pasku stanu. W związku z tym na pasku stanu najlepiej nadaje się do celów informacyjnych lub jako nadmiarowy wskaźnik dla informacje przedstawione w innym miejscu. W oknie dialogowym lub w oknie narzędzia powiadomienia, należy podać dowolny rodzaj krytyczne informacje, które użytkownik musi niezwłocznie rozwiązać.

 Na pasku stanu w programie Visual Studio umożliwia dla różnych typów informacji mają być wyświetlane. Jest ona podzielony na regiony dla opinii, projektanta, pasek postępu, animacji i klienta.

 Region opinii i projektanta region są zawsze widoczne. Pasek postępu i animacji regiony są zawsze dynamiczne i oparte na kontekście użytkownika. Projektanta regionu ma szerokość statyczne, określa długość ciągu, który jest pobierany z zasobem towarzyszący wiadomości tekstowych. Umożliwia to lokalizacja zmienić rozmiar szerokość bez konieczności zmiany kodu. Dla języka angielskiego szerokość ten ciąg jest około 220 pikseli. Projektanta region będzie działać prawidłowo, i regionu opinie będą absorbować ilość wolnego miejsca.

 Na pasku stanu jest także pokolorowane pozwala dodać wizualny i wartość funkcjonalności, komunikując się różne zmiany stanu IDE, np. gdy IDE jest w trybie debugowania.

 ![Pasek koloru zmiany stanu IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")

 **Kolory paska stanu IDE**

#### <a name="BKMK_EmbeddedInfobar"></a> Osadzony pasek informacyjny
 Pasek informacyjny może służyć w górnej części okna dokumentu lub okna narzędzi w celu poinformowania użytkownika o stanu lub warunku. On również oferować polecenia, dzięki czemu użytkownik może łatwo podjąć działania w sposób. Pasek informacyjny jest formantem standardowa powłoki. Unikaj tworzenia własnych, który będzie działać i występować niespójne z innymi osobami w środowisku IDE. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) szczegółów implementacji i wskazówki dotyczące użycia.

 ![Osadzone informacyjnym](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")

 **Pasek informacyjny osadzony w oknie dokumentu alerty użytkownika, który jest w trybie debugowania historycznego IDE i edytor nie będzie odpowiadać w taki sam sposób jak w trybie standardowym debugowania.**

#### <a name="BKMK_MouseCursorChanges"></a> Zmiany kursora myszy
 Po zmianie kursora myszy, należy użyć kolorów, które są powiązane z usługą VSColor i są już skojarzone z kursorem. Kursor zmiany mogą służyć do wskazywania trwającą operację, a także trafień strefy, gdy użytkownik po umieszczeniu wskaźnika nad obiektu docelowego, który można przeciągnąć, upuszczone na lub używany do wybierania obiektu.

 Kursor myszy zajęty oczekiwania należy używać tylko wtedy, gdy cały dostępny czas procesora CPU musi być zarezerwowana dla operacji, uniemożliwiając wyrażanie wszelkich dalszych danych wejściowych użytkownika. W większości przypadków z dobrze napisane aplikacje za pomocą wielowątkowości razy, gdy użytkownicy mają zablokowaną możliwość wykonywania innych operacji powinna być rzadkie.

 Należy pamiętać o tym, kursor zmiany są przydatne, nadmiarowe wskazówki informacje przedstawione w innym miejscu. Nie należy polegać na zmianę kursora jako jedyny sposób komunikowania się z użytkownikiem, szczególnie w przypadku próby przekazania coś, który ma kluczowe znaczenie, czy użytkownik muszą spełnić.

#### <a name="BKMK_NotSysProgressIndicators"></a> Wskaźniki postępu
 Wskaźniki postępu są ważne w przypadku wyrażanie opinii użytkownika w procesach, które przyjmują więcej niż kilka sekund. Wskaźniki postępu, które mogą być wyświetlane w miejscu (w pobliżu punkt uruchamiania działania w toku), na pasku stanu osadzony, modalne okno dialogowe lub na pasku stanu w programie Visual Studio. Postępuj zgodnie ze wskazówkami w [wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) dotyczące ich stosowanie i wdrożenie.

#### <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio powiadomienia okna
 W oknie Powiadomienia usługi Visual Studio powiadamia deweloperów o tym licencjonowania, środowiska (Visual Studio), rozszerzenia i aktualizacje. Użytkownicy mogą odrzucić indywidualne powiadomienia lub zignorować określonych typów powiadomień. Listę ignorowanych powiadomień jest zarządzany w **Narzędzia > Opcje** strony.

 Okno powiadomień nie jest obecnie rozszerzonego.

 ![Visual Studio powiadomienia okna](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")

 **Okno narzędzia w usłudze Visual Studio powiadomienia**

#### <a name="BKMK_ErrorList"></a> Lista błędów
 Powiadomienie w liście błędów wskazują błędy i ostrzeżenia, które wystąpiły podczas kompilacji i procesu kompilacji i umożliwia użytkownikowi nawigację w kodzie do tego określonego kodu błędu.

 ![Lista błędów](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")

 **Lista błędów w programie Visual Studio**

#### <a name="BKMK_EmbeddedStatusBars"></a> Paski stanu osadzonego
 Ponieważ pasek stanu IDE jest dynamiczny, za pomocą jego kontekst regionu klienta Ustaw aktywne okno dokumentu i informacje o aktualizacji w kontekście użytkownika i/lub odpowiedzi systemu, jest trudne do utrzymania ciągłego wyświetlania informacji lub Prześlij stanu na długoterminowe Proces asynchroniczny. Na przykład na pasku stanu IDE nie jest właściwe dla powiadomień wyników przebiegu testu dla wielu uruchomień i/lub od razu wiarygodne wybrane opcje. Należy zachować takie informacje o stanie w kontekście okna dokumentu lub narzędzia, gdzie użytkownika powoduje, że zaznaczenie lub rozpoczyna się proces.

 ![Pasek stanu osadzone](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")

 **Pasek stanu osadzonego w programie Visual Studio**

#### <a name="BKMK_WindowsTray"></a> Windows na pasku powiadomień
 Windows, w obszarze powiadomień jest obok system zegara na pasku zadań Windows. Wiele narzędzi i składników oprogramowania zapewniają ikon, w tym obszarze, dzięki czemu użytkownik może uzyskać menu kontekstowe dla zadania systemowe, takie jak zmiana rozdzielczości ekranu lub uzyskiwanie aktualizacji oprogramowania.

 Powiadomienia na poziomie środowiska powinien udostępniane w Centrum powiadomień usługi Visual Studio, a nie Windows obszaru powiadomień.

#### <a name="BKMK_NotificationBubbles"></a> Bąbelki powiadomień
 Bąbelki powiadomienia mogą być wyświetlane, informacyjny w edytorze/projektanta lub w ramach obszaru powiadomień Windows. Użytkownik uświadamia sobie, te bąbelki jako problemy, które można rozwiązać później, który jest to korzyść dla powiadomienia niekrytyczne. Bąbelków nie mają zastosowania do kluczowych informacji, które użytkownik musi następnie od razu rozwiązania. Jeśli używasz bąbelki powiadomień w programie Visual Studio, postępuj zgodnie z [pulpitu Windows wskazówki dotyczące powiadomień bąbelki](/windows/desktop/uxguide/mess-notif).

 ![Powiadomienie w dymku](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")

 **Bąbelkowy powiadomień w obszarze powiadomień Windows używane dla programu Visual Studio**

## <a name="BKMK_ProgressIndicators"></a> Wskaźniki postępu

### <a name="overview"></a>Omówienie
 Wskaźniki postępu są ważnym elementem systemu powiadomień, do udzielania opinii użytkowników. Informują one użytkownika, gdy zostanie ukończone procesów i operacji. Typy wskaźników znanych obejmują paski postępu, kursory rotowania i ikony animowany. Typ i położenia wskaźnika postępu zależy od kontekstu, w tym, co jest raportowane i jak długo proces lub operacja spowoduje przejście do ukończenia.

#### <a name="factors"></a>Czynniki
 Aby ustalić, jakiego typu wskaźnika jest odpowiednia, należy określić następujące czynniki.

1. **Przedział czasowy:** czas operacji potrwa

2. **Modalności:** tego, czy operacja jest modalnego dla środowiska (blokady interfejsu użytkownika do czasu ukończenia procesu)

3. **Trwały/przejściowy:** tego, czy wynik końcowy postępu musi być zgłaszane i/lub możliwy do wyświetlenia w późniejszym czasie

4. **Określony/nieokreślone:** tego, czy można obliczyć postępu i godzina zakończenia działania

5. **Grafika/Textual lokalizacji:** czy postępu lub procesu jest przechwycone w tekście, w treści wiadomości lub określonej kontrolki, na przykład kontrolki drzewa

6. **Zbliżeniowe:** czy postępu powinien znajdować się w bliskim sąsiedztwie w interfejsie użytkownika, który jest powiązany. (Na przykład może ona znajdować się w pasku stanu, które mogą być daleko, lub czy ma znajdować się w pobliżu przycisku, który uruchomił proces?)

#### <a name="determinate-progress"></a>Określony postępu

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (określania)|Oczekiwany czas trwania > 5 sekund.<br /><br /> Może zawierać opis tekstowy szczegóły procesu.|**Nie** osadzania tekstu w animacji.|
|Pasek informacyjny|Do obsługi komunikatów skojarzony z kontekstowych interfejsu użytkownika. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Może zawierać opis tekstowy szczegóły procesu.|**Nie** używać wielu infobars, gdy należy wskazać wiele procesów. Zamiast tego użyj paski postępu skumulowanego.|
|Okno wyniku|Powiadomienie przejściowy: procesu na poziomie aplikacji danego użytkownika mają być **Przejrzyj** szczegóły po zakończeniu.|**Nie** używać, jeśli użytkownik musi odwoływać się do danych później.|
|Plik dziennika|Sparowane intransient powiadomienie w przypadku, gdy ważne jest, aby **Zapisz** szczegóły po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowy: procesu na poziomie aplikacji danego użytkownika zostanie **nie jest konieczne** szczegóły po zakończeniu.<br /><br /> Zawiera pasek postępu osadzonych.<br /><br /> Może zawierać opis tekstowy szczegóły procesu.||

#### <a name="indeterminate-progress"></a>Nieokreślonego postępu

|Typ postępu|Kiedy i jak używać|Uwagi|
|-------------------|-------------------------|-----------|
|Pasek postępu (nieokreślone)|Oczekiwany czas trwania > 5 sekund.<br /><br /> Może zawierać opis tekstowy szczegóły procesu.|**Nie** osadzania tekstu w animacji.|
|Mrówki (animowany punktów w poziomie)|Obiegu do serwera.<br /><br /> Na górze kontenera nadrzędnego, należy umieścić punktu near kontekstu.|**Nie** używać, jeśli nie elementem nadrzędnym, przez cały kontener.|
|Pokrętła (pierścień postępu)|Proces związany z kontekstowych interfejsu użytkownika lub miejsce w przypadku jest brany pod uwagę.<br /><br /> Może zawierać opis tekstowy szczegóły procesu.||
|Pasek informacyjny|Do obsługi komunikatów skojarzony z kontekstowych interfejsu użytkownika. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nie** używać wielu infobars, gdy należy wskazać wiele procesów. Zamiast tego użyj paski postępu skumulowanego.|
|Okno wyniku|Powiadomienie przejściowy: procesu na poziomie aplikacji użytkownik będzie chciał **Przejrzyj** szczegóły po zakończeniu.|**Nie** informacji, który ma zostać zachowany między sesjami.|
|Plik dziennika|Sparowane intransient powiadomienie w przypadku, gdy ważne jest, aby **Zapisz** szczegóły po zakończeniu.||
|Pasek stanu|Powiadomienie przejściowy: procesu na poziomie aplikacji danego użytkownika zostanie **nie jest konieczne** szczegóły po zakończeniu.<br /><br /> Zawiera pasek postępu osadzonych.<br /><br /> Może zawierać opis tekstowy szczegóły procesu.||

### <a name="progress-indicator-types"></a>Typy wskaźnika postępu

#### <a name="progress-bars"></a>Paski postępu

##### <a name="indeterminate"></a>Nieokreślony
 ![Pasek postępu indeterminate](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")

 **Pasek postępu nieokreślony**

 "Nieokreślone" oznacza, że całkowity postęp operacji lub proces nie może być określony. Użyj pasków nieokreślonego postępu dla operacji, które wymagają niezwiązana ilość czasu, lub które mają dostęp do nieznanych liczbę obiektów. Opis tekstowy umożliwia towarzyszyć, co się dzieje. Limity czasu umożliwia oferowanie granic na podstawie czasu operacji. Paski postępu nieokreślony Użyj animacji, aby pokazać postęp odbywa się, że nie udostępniają żadnych innych informacji. Nie należy wybierać pasek postępu indeterminate oparte tylko na możliwego braku dokładność samodzielnie.

##### <a name="determinate"></a>Określony
 ![Pasek postępu określania](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")

 **Pasek postępu określania**

 "Określony" oznacza, że operacji lub proces wymaga ograniczoną ilość czasu, nawet wtedy, gdy nie można dokładnie przewidzieć tego przedziału czasu. Jasno wskazywać ukończenia. Nie przegap pasek postępu, przejdź do 100 procent, chyba, że operacja zostanie ukończona. Animacja pasek postępu określania Przenosi od lewej do prawej z zakresu od 0 do 100%.

 Nigdy nie jest przenoszony do tyłu podczas operacji wskaźnik postępu. Pasek należy do przodu intensywność po rozpoczęciu operacji i dotrzeć do 100%, po jego zakończeniu. Punkt paska postępu jest przyznać użytkownikowi oszacowanie, cała operacja czas, niezależnie od tego, jak wiele kroków są zaangażowane.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Współbieżne raportowania (paski postępu skumulowane)
 Jeśli operacja potrwa długo - prawdopodobnie kilku minut — następnie paski postępu dwóch mogą być używane, która pokazuje ogólny postęp operacji i inny wpis dla postęp bieżącego etapu. Na przykład jeśli program instalacyjny jest kopiowanie wielu plików, następnie co pasek postępu może służyć do wskazania, jak długo cały proces trwa sekundy można wskazać, jaki procent bieżącego pliku lub katalogu są kopiowane. Nie zgłaszaj więcej niż 5 współbieżnych operacji lub za pomocą paski postępu skumulowanego. Jeśli masz więcej niż 5 współbieżnych operacji lub procesów do raportu, za pomocą modalne okno dialogowe przycisk Anuluj i raport szczegóły postępu w oknie danych wyjściowych.

##### <a name="textual-descriptions"></a>Opisy tekstowe
 Użyj opis tekstowy, która ma towarzyszyć, co się dzieje i szacowany czas do ukończenia. Jeśli nie jest możliwe ustalenie, jak długo potrwa operacją, lepszym wyborem wyrażanie opinii może być animowaną ikonę zamiast pasek postępu.

 Visual Studio zawiera pasek postępu standard na pasku stanu, który mogą być używane przez dowolny produkt zintegrowane w programie Visual Studio. Opisy tekstowe co się dzieje, gdy jest animowany pasek postępu tekst na pasku stanu może być aktualizowana.

#### <a name="other-progress-indicators"></a>Inne wskaźniki postępu

##### <a name="ants-animated-horizontal-dots"></a>Mrówki (animowany punktów w poziomie)
 ![Postęp Mrówki](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")

 "Mrówki," animowany punktów w poziomie, stanowią wizualny materiał referencyjny dla procesu nieokreślony obustronne serwera.

##### <a name="spinner-progress-ring"></a>Pokrętła (pierścień postępu)
 ![Postęp pokrętła](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")

 Pokrętła (znany także jako "pierścień postępu") jest wskaźnikiem nieokreślonego postępu używane głównie w odniesieniu do kontekstowe interfejsu użytkownika. Okrągły wskaźnik przetwarzania są wyświetlane w bliskim sąsiedztwie do jego zawartości pokrewne, takie jak nagłówek tekstową kategorii, obsługi komunikatów lub kontroli.

##### <a name="cursor-feedback"></a>Kursor opinii
 Operacje, które zająć od 2 do 7 sekundach kursor opinii. Zazwyczaj oznacza to, za pomocą kursor oczekiwania, dostarczone przez system operacyjny. Aby uzyskać wskazówki, zobacz artykuł w witrynie MSDN [właściwość Cursors.Wait](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Lokalizacje wskaźnik postępu

##### <a name="status-bar"></a>Pasek stanu
 Na pasku stanu zapewnia aplikacji miejsce do wyświetlenia wiadomości i przydatnych informacji do użytkownika bez przerywania pracy użytkownika. Zazwyczaj są wyświetlane w dolnej części okna, stan, postęp będzie okienko Porada narzędzi, który zawiera komunikat o miernikiem postępu w połączeniu ze wskaźnikiem pasek postępu.

 ![Pasek stanu ze pasek postępu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")

 **Pasek stanu ze pasek postępu**

 ![Pasek stanu z obsługą komunikatów](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")

 **Pasek stanu ze opis tekstowy**

##### <a name="infobar"></a>Pasek informacyjny
 Podobnie jak pasek stanu, pasek informacyjny zawiera kontekstowe powiadomienia i komunikaty, które również mogą być parowane ze wskaźnikami nieokreślonego postępu, takich jak pasek postępu lub pokrętła. Paska informacyjnego nie zawiera szczegółowego poziomu postępu lub oznaczenie określania postępu. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Pasek informacyjny przy użyciu paska postępu i messaging](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")

 **Pasek informacyjny pasek postępu i opis tekstowy**

 ![Pasek informacyjny w oknie](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")

##### <a name="inline"></a>wbudowane
 Wskazuje postęp wbudowane może być reprezentowany przez dowolnego typu modułu ładującego postępu. Zazwyczaj wskaźnik postępu jest sparowana z obsługą komunikatów, ale nie jest wymagane.

 ![Wbudowane postępu pokrętła](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")

 **W połączeniu z opis tekstowy pokrętła**

 ![Wbudowane skumulowany paski postępu](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")

 **Paski postępu skumulowany określania**

 ![Wiadomości postępu wbudowane](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")

 **Tekst wbudowany Eksploratora serwera: Trwa odświeżanie...**

##### <a name="tool-windows"></a>Okna narzędzi
 Wskazuje postęp globalnego jest reprezentowany przez pasek postępu indeterminate umieszczony bezpośrednio poniżej paska narzędzi.

 ![Pasek postępu nieokreślony globalnego](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")

 **Team Explorer globalnego nieokreślony ProgressBar**

##### <a name="dialogs"></a>Okna dialogowe
 Okna dialogowe mogą zawierać żadnego z typów modułu ładującego postępu. Wskaźniki postępu może być sparowane z obsługą komunikatów także w połączeniu z oznaczaniem postępu reprezentują szczegółową i procesy podrzędne na wielu poziomach.

 ![Okno dialogowe z wieloma typami wskaźnika postępu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")

 **Visual Studio okna dialogowego przy użyciu procesów współbieżnych i wiele typów wskaźnika postępu**

 ![Okno dialogowe z modułu ładującego postępu i komunikatów](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")

 **Visual Studio okna dialogowego za pomocą modułu ładującego postępu i funkcji komunikatów w wierszu polecenia**

##### <a name="document-well"></a>Dobrze dokumentu
 Dokument również można wyświetlić wiele typów modułu ładującego postęp w połączeniu z formantami.

 ![Postęp oraz obsługi komunikatów w dokumencie](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")

 **Pasek postępu indeterminate poniżej paska narzędzi**

##### <a name="output-window"></a>Okno wyniku
 W oknie danych wyjściowych jest odpowiednia do obsługi procesu postępu i stanu aktualnych za pośrednictwem wiadomości tekstowej wbudowanego. Należy użyć na pasku stanu oraz wszelkie dane wyjściowe okna postępu raportowania.

 ![Postęp komunikaty w oknie danych wyjściowych](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")

 **Okno danych wyjściowych ze stanem ciągły proces i zaczekaj, obsługi komunikatów**

## <a name="BKMK_Infobars"></a> Infobars

### <a name="overview"></a>Omówienie
 Infobars przyznać użytkownikowi wskaźnik blisko ich punktu uwagi i za pomocą kontroli udostępnionego informacyjnym zapewnia spójność wyglądu i interakcji.

 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Infobars w programie Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Zastosowań odpowiednie pasek informacyjny

- Aby przyznać użytkownikowi wiadomość bez blokowania, ale ważne istotne dla bieżącego kontekstu

- Aby wskazać, że interfejs użytkownika określonego stanu lub warunek, który niesie ze sobą skutki niektórych interakcji, takich jak debugowanie historyczne

- Powiadomienie użytkownika, że system wykrył problemy, takie jak kiedy rozszerzenie jest przyczyną problemów z wydajnością

- Aby umożliwić użytkownikowi łatwo podjęcia działania, np. gdy Edytor wykryje, że plik zawiera różne znaki tabulacji i spacje

##### <a name="do"></a>Należy wykonać:

- Tekst komunikatu informacyjnym należy zachować krótki i na.

- Zachowaj tekst na łącza i przyciski zwięzły.

- Upewnij się, że opcje "action", które zapewniają użytkownikom są minimalne, pokazujący tylko wymagane akcje.

##### <a name="dont"></a>Nie:

- Użyj pasek informacyjny, aby oferować standardowych poleceń, które powinny zostać umieszczone na pasku narzędzi.

- Użyj paska informacyjnego zamiast modalne okno dialogowe.

- Utwórz wiadomość zmiennoprzecinkowych poza oknem.

- Użyj wielu infobars w kilku lokalizacjach, w tym samym oknie.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Czy wiele infobars można wyświetlić w tym samym czasie?
 Tak, wiele infobars można pokazać, w tym samym czasie. Pojawi się one w kto, obsługiwane w pierwszej kolejności za pomocą pierwszego przedstawiający na górze, a dodatkowe infobars przedstawiający poniżej paska informacyjnego.

 Użytkownik będzie widział maksymalnie trzech infobars w czasie, po, dostępnych więcej infobars region informacyjnym staną się przewijany.

### <a name="creating-an-infobar"></a>Tworzenie pasek informacyjny
 Pasek informacyjny zawiera cztery sekcje, od lewej do prawej:

- **Ikona:** Jest to, gdzie należy dodać wszystkie ikony chcesz wyświetlić na pasku informacyjnym, takie jak ikona ostrzeżenia.

- **Tekst:** Można dodać tekst opisujący użytkownika scenariusz/sytuacji trwa wraz z linkami do tekstu, jeśli jest to wymagane. Pamiętaj, aby tekst zwięzły.

- **Akcje:** W tej sekcji może zawierać łącza i przyciski dla akcji, które użytkownik może robić na Twoje informacyjnym.

- **Przycisk zamknięcia:** Ostatnia sekcja po prawej stronie może mieć przycisk Zamknij.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Tworzenie standardowego paska informacyjnego w kodzie zarządzanym
 Klasa InfoBarModel może służyć do tworzenia źródła danych dla paska informacyjnego. Użyj jednej z tych czterech konstruktorów:

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

 Oto przykład tworzenia InfoBarModel z tekstem hiperlinku, przycisk akcji i ikony.

 ![Pasek informacyjny z hiperlinkiem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")

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
 Implementuj interfejs IVsInfoBar w celu zapewnienia pasek informacyjny z kodu natywnego.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Pobieranie pasek informacyjny UIElement z pasek informacyjny
 Implementacja InfoBarModel lub IVsInfoBar są modeli danych, które musi być włączony w element interfejsu użytkownika, aby można było wyświetlane w interfejsie użytkownika. Element interfejsu użytkownika mogą być pobierane przy użyciu usługi elementu SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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
 Infobars mogą być wyświetlane w co najmniej jeden z następujących lokalizacji:

- Okna narzędzi

- W ramach karty dokumentu

> [!IMPORTANT]
>  Istnieje możliwość pozycji pasek informacyjny zapewnienie komunikat o kontekście globalnym. Ten pojawi się pomiędzy paskami narzędzi i dobrze dokumentu. Nie jest to zalecane, ponieważ powoduje problemy z "szybkiego dostępu i jerk" środowiska IDE i należy ich unikać, chyba że absolutnie konieczne i właściwe.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umieszczenie pasek informacyjny w obiektu ToolWindowPane
 Metoda ToolWindowPane.AddInfoBar(IVsInfoBar) może służyć do dodawania pasek informacyjny do okna narzędzi. Ten interfejs API albo dodać IVsInfoBar, (które InfoBarModel jest domyślna implementacja) lub elementu IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Umieszczenie pasek informacyjny w dokumencie lub innych obiektu ToolWindowPane
 Umieszcza pasek informacyjny w dowolnym IVsWindowFrame, należy użyć właściwości elementu vsfpropid_infobarhost zakończyło można uzyskać IVsInfoBarHost ramki, a następnie dodaj pasek informacyjny element interfejsu użytkownika.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Umieszczenie pasek informacyjny w oknie głównym
 Aby umieścić pasek informacyjny w głównym oknie, użyj VSSPROPID_MainWindowInfoBarHost usługi elementu IVsShell, aby pobrać IVsInfoBarHost okno główne, a następnie dodać pasek informacyjny UIElement do niego.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Mam wiedzieć, gdy użytkownik wykona akcję na Moje informacyjnym?
 Tak, możemy zwróci każdej akcji zdarzeń do autora paska informacyjnego. Następnie jest autorem informacyjnym, aby podjąć działania w środowisku IDE, w oparciu o wybór użytkownika na pasku informacyjnym. Infobars zostaną automatycznie usunięte z hosta, którego Zamknij przycisk został kliknięty, ale dodatkowa praca będzie polegała, jeśli inne potrzeby infobars ma zostać usunięta po zamknięciu. Dane telemetryczne trzeba będzie również rejestrowany niezależnie przez każdego paska informacyjnego.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Odbieranie zdarzeń pasek informacyjny w obiektu ToolWindowPane
 Elementu ToolWindowPane ma dwa zdarzenia dla infobars. Zdarzenie InfoBarClosed jest wywoływane, gdy pasek informacyjny w obiektu ToolWindowPane jest zamknięty. InfoBarActionItemClicked zdarzenie jest wywoływane po kliknięciu hiperlinku lub przycisk wewnątrz paska informacyjnego.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Odbieranie zdarzeń o przerwaniu pracy bezpośrednio z element interfejsu użytkownika
 IVsInfoBarUIElement.Advise może służyć do subskrybowania zdarzenia bezpośrednio z poziomu paska informacyjnego element interfejsu użytkownika. Implementowanie IVsInfoBarUIEvents umożliwi tworzenie otrzymywać Zamknij, a następnie kliknij przycisk zdarzenia.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="BKMK_ErrorValidation"></a> Błąd weryfikacji
 Gdy użytkownik wprowadzi informacje, które nie są dopuszczalne, np. gdy to pole wymagane jest pomijana, lub podczas wprowadzania danych w niepoprawnym formacie, zaleca się użycie kontroli weryfikacji lub opinie, obok kontrolki zamiast blokowania okna dialogowego błędu okna podręcznego.

### <a name="field-validation"></a>Sprawdzanie poprawności pól
 Weryfikacja formularza i pola składa się z trzech składników: kontrolki, ikonę i etykietkę narzędzia. Chociaż kilka typów formantów, użyć tej funkcji, pola tekstowego będzie służyć jako przykład.

 ![Weryfikacja pola &#40;puste&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")

 Jeśli pole jest wymagane, powinien istnieć limitu, podając tekstu  **\<wymagane >** i tło pola powinny być światła żółty (VSColor: `Environment.ControlEditRequiredBackground`), a kolor pierwszego planu będzie szary (VSColor: `Environment.ControlEditRequiredHintText`):

 ![Weryfikacja z etykietą "Required" pola](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")

 Program można określić, czy kontrolka jest w stanie *Nieprawidłowa zawartość wprowadzono* gdy fokus jest przenoszony do innej kontrolki lub gdy użytkownik kliknie przycisk Zatwierdź [OK] lub po użytkownik zapisze dokument lub formularz.

 Gdy zostanie uznane za nieprawidłowy stan zawartości, pojawi się ikona wewnątrz formantu lub po prostu obok niej. Etykietka narzędzia zawierająca opis błędu powinna zostać wyświetlona po najechaniu wskaźnikiem ikony lub formant. Ponadto 1-pikselowe obramowanie powinna pojawić się wokół formantu, który tworzy nieprawidłowy stan.

 ![Pola specyfikacji układ weryfikacji](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")

 **Specyfikacje układu dla sprawdzanie poprawności pól**

#### <a name="acceptable-variations-for-icon-location"></a>Odmian dopuszczalne dla lokalizacji ikony
 Dostępne są niezliczone unikatowych przypadków, w których użytkownicy muszą być poinformowany o błędach weryfikacji. Biorąc pod uwagę — typ formantu i Konfiguracja interfejsu użytkownika wybierz odpowiednie do danej sytuacji położenie ikony.

 ![Dopuszczalne lokalizacje dla lokalizacji ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")

 **Dopuszczalne odmiany dla lokalizacji ikony sprawdzanie poprawności pól**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Weryfikacja wymaga rund do serwera lub połączenia sieciowego
 W niektórych przypadkach komunikacji dwustronnej z serwerem jest wymagane, aby sprawdzić zawartość, a istotne pokazać postęp zweryfikowana i stany błędu. Poniższy rysunek przedstawia przykład takim i zalecane interfejsu użytkownika.

 ![Weryfikacja obejmująca komunikacji dwustronnej z serwerem](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")

 **Weryfikacja obejmująca komunikacji dwustronnej z serwerem**

 Pamiętaj, że odpowiednie dostępnego miejsca z prawej strony formantu musi być podana w celu uwzględnienia tekst "Weryfikowanie..." i "Spróbuj ponownie".

#### <a name="in-place-warning-text"></a>Tekst ostrzeżenia w miejscu
 Gdy ma miejsce dostępne do umieszczenia komunikat o błędzie blisko kontrolki w stanie błędu, zalecane jest przy użyciu samodzielnie etykietki narzędzia.

 ![W&#45;umieść ostrzeżenie](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")

 **Tekst ostrzeżenia w miejscu**

#### <a name="watermarks"></a>Znaki wodne
 Czasami całego kontroli lub okna jest w stanie błędu. W takiej sytuacji należy użyć znaku wodnego, aby wskazać błąd.

 ![Znak wodny](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 07_Watermark")

 **Sprawdzanie poprawności pól znaku wodnego**