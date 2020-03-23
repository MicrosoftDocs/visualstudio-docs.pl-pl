---
title: Tekst interfejsu użytkownika i pomoc dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303128"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Tekst interfejsu użytkownika i pomoc dla programu Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Tekst interfejsu użytkownika i terminologia
 Zrozumiały tekst ma kluczowe znaczenie dla skutecznego interfejsu użytkownika. Użytkownicy oprogramowania mają tendencję do czytania etykiet po raz pierwszy, a mianowicie te najbardziej istotne dla wykonania zadania pod ręką. Tekst statyczny jest odczytywany z mniejszą częstotliwością. Zaplanuj użytkownikom rozpoczęcie sesji roboczych za pomocą szybkiego skanowania całego okna, a następnie odczytu interfejsu użytkownika w tej przybliżonej kolejności:

1. Interaktywne elementy sterujące w centrum

2. Przyciski zatwierdzania

3. Interaktywne formanty znalezione w innym miejscu

4. Główne instrukcje

5. Dodatkowe wyjaśnienia

6. Tytuł okna

7. Inny tekst statyczny w treści głównej

### <a name="usage-patterns-for-ui-text"></a>Wzorce użycia tekstu interfejsu użytkownika

#### <a name="title-bar-text"></a>Tekst paska tytułu
 Tekst paska tytułu musi być zgodny z poleceniem, które zrodziło interfejs użytkownika.

#### <a name="instructional-text-helper-text"></a>Tekst instruktażowy (tekst pomocniczy)
 W niektórych oknach dialogowych warto podać ważne główne instrukcje, aby wyjaśnić, co należy zrobić w oknie lub na stronie. Jest to czasami określane jako "tekst pomocniczy".

##### <a name="writing-style-rules-for-helper-text"></a>Reguły stylu pisania dla tekstu pomocniczego

- Nie wyjaśniaj tego, co oczywiste. Jeśli nie jest to absolutnie potrzebne, nie zawierają tekstu instruktażowego.

- Tekst instruktażowy jest zawsze umieszczany w górnej części okna dialogowego i powinien odnosić się do wykonywanego zadania.

- Dokładnie wyjaśnij użytkownikom, co muszą zrobić. Unikaj nadmiernej komunikacji i nadmiarowości.

- Przejrzyj każde okno i wyeliminuj zduplikowane słowa i instrukcje.

- Tekst instruktażowy należy zachować krótko. Jeśli więcej informacji jest niezbędne dla niektórych użytkowników lub scenariuszy, następnie podaj łącze do szczegółowego tematu koncepcyjnego online.

- Napisz tekst tak, aby każde słowo miało wagę i było konieczne.

- Postępuj zgodnie z istniejącymi wskazówkami firmy Microsoft dotyczącymi tekstu interfejsu [użytkownika](/windows/desktop/uxguide/text-ui) oraz stylu [i tonu](/windows/desktop/uxguide/text-style-tone).

#### <a name="supplemental-instructions"></a>Dodatkowe instrukcje
 Dodatkowe instrukcje zawierają dodatkowe informacje, które pomagają użytkownikowi zrozumieć formanty lub grupowania kontroli. Może to również zawierać tekst podpowiedzi niezbędne do zrozumienia, jaki format oczekuje formantu wejściowego. Używaj dodatkowych instrukcji oszczędnie. Zarezerwuj je w przypadkach, w których jest prawdopodobne, że użytkownik nie będzie w pełni zrozumieć konsekwencje wyboru, którego dokonują.

 ![Tekst uzupełniający w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Tekst uzupełniający w programie Visual Studio**

 ![Tekst uzupełniający w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Tekst uzupełniający w programie Visual Studio**

#### <a name="infotips"></a>Porady informacyjne
 Często tekst instruktażowy może być zbyt długi, aby umieścić w miejscu w interfejsie użytkownika lub może być przydatne tylko dla nowych użytkowników, czując się bałagan u doświadczonych użytkowników. W takim przypadku tekst instruktażowy/informacyjny powinien być umieszczony jako etykietka narzędzia w obszarze Etykieta informacyjna.

 Porady informacyjne powinny być umieszczane w pobliżu formantów, które są związane z i należy użyć określonej ikony Porady, która jest dyskretny, ale zauważalne.

 ![Porada informacyjna w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Przykład porady w programie Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Reguły stylu pisania dla etykietek informacyjnych

- Zapisz porady informacyjne jako kompletne zdania. Wymagają one określonych czasowników, sprawy zdania i kończącej interpunkcji.

- Skorzystaj z porad informacyjnych, aby uzupełnić główną instrukcję lub informacje. Jeśli po prostu używasz różnych słów, aby przekształcić główną ideę, nie potrzebujesz porady informacyjnej.

- Utrzymuj krótkie i słodkie porady. Używaj małych słów i zwykłego, codziennego języka, który wspiera i zachęca użytkownika.

- Postępuj zgodnie z istniejącymi wskazówkami firmy Microsoft dotyczącymi tekstu interfejsu [użytkownika](/windows/desktop/uxguide/text-ui) oraz stylu [i tonu](/windows/desktop/uxguide/text-style-tone).

#### <a name="control-labels"></a>Etykiety sterujące
 Etykiety kontrolne powinny być krótkie, zwięzłe i postępować zgodnie [ze wskazówkami pulpitu systemu Windows dotyczącymi kontrolek](/windows/desktop/uxguide/controls).

 Aby uzyskać więcej informacji na temat formatu etykiety formantu i umieszczania w interfejsie użytkownika, zobacz [Układ dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Łącza pomocy
 Łącza pomocy można umieszczać w tekście instruktażowym lub w treści interfejsu użytkownika. Mogą to być łącza do Pomocy lub uruchamiania wewnętrznych okien dialogowych.

##### <a name="visual-style-rules-for-help-links"></a>Reguły stylu wizualnego dla łączy Pomocy

- Użyj odpowiednich kolorów środowiska dla hiperłączy. Prawidłowo wystylizowany hiperłącze nie będzie krótko migać na czerwono po kliknięciu. Jeśli to widzisz, to jest wskazanie, że kolory środowiska nie są używane.

- Podkreślenia powinny być używane tylko podczas najechaniu kursorem lub po umieszczeniu łącza w akapicie.

- Aby uzyskać bardziej szczegółowe informacje na temat stylów wizualnych i interakcji hiperłączy, zobacz Przyciski i hiperłącza.

##### <a name="writing-style-rules-for-help-links"></a>Reguły stylu pisania dla łączy Pomocy

- Podczas uruchamiania okien dialogowych, należy zachować standardy dla elips: nie wielokropek do nawigacji, elipsy, jeśli zadanie wymaga dodatkowego interfejsu użytkownika.

     ![Łącze Pomocy w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Wielokropek (...) w łączu Pomoc wskazuje, że zadanie będzie wymagało dodatkowego interfejsu użytkownika.**

- Łącza nie powinny zaczynać się od "Dowiedz się", ponieważ nie jest to intencją użytkownika. Użytkownik chce odpowiedzieć na konkretne pytanie, a nie otrzymać wykształcenie ogólne.

- Fraza pomoc linki tak, że zadają pytanie, że temat odpowie.

     Niepoprawne: "Dowiedz się więcej o cenach usług Windows Azure Mobile Services"

     Poprawna: "Jakie opcje cenowe są dostępne dla usług Windows Azure Mobile Services?"

- Nigdy nie *używaj kliknij...* do tekstu łącza.

- Nigdy nie łącz tylko słowa "tutaj". Jest to problematyczne dla niektórych czytników ekranu, które będą wyrażać tylko słowo hiperłącza.

     Niepoprawne: "Znajdź informacje o usługach Windows Azure Mobile **Tutaj"**

     Poprawna: "Jakie opcje cenowe są dostępne dla usług Windows Azure Mobile Services?"

- Aby uzyskać więcej informacji na temat prawidłowego stylu pisania łączy Pomocy, zobacz [Wskazówki dotyczące pulpitu systemu Windows dla Pomocy](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Tekst podpowiedzi
 Tekst wskazówki jest wyświetlany jako znak wodny w formancie lub pod formantem. Prawidłowe formatowanie zostanie zastosowane przy użyciu odpowiedniego `Environment.GrayText`tokenu VSColors, .

 Może pojawić się w wielu formach.

- Zamiast etykiety kontrolnej:

     ![Tekst podpowiedzi w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Z czasownikiem, dając instrukcje:

     ![Tekst podpowiedzi w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Z tekstem wskazującym wymagany wpis:

     ![Tekst podpowiedzi w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Tekst znaku wodnego
 Na pustej powierzchni projektowej tekst powinien wskazywać, co należy zrobić, a także podać łącza do otwierania innych powiązanych okien, jeśli to konieczne:

 ![Tekst znaku wodnego w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Przykład tekstu znaku wodnego w programie Visual Studio**

### <a name="common-terminology"></a>Wspólna terminologia

|Termin|Wyjaśnienie|Komentarz|
|----------|-----------------|-------------|
|Zaloguj się / Wyloguj się|Zlecenia używane synonimie z siecią Web do reprezentowania uwierzytelniania w właściwości sieci web. W ramach klientów używamy tego raz jako pojęcia najwyższego poziomu do logowania się i z połączenia użytkownika IDE, który reprezentuje tożsamość najwyższego poziomu, która zapewnia funkcje wyższego poziomu, takie jak roaming i licencjonowanie, które nie są dostępne dla wszystkich innych połączeń.|Użytkownik IDE jest jedyną funkcją, która powinna reprezentować zlecenie logowania/wylogowywania, ponieważ reprezentuje użytkownika IDE najwyższego poziomu.|
|Podłączanie / rozłączanie|Używaj w miejscach, w których funkcja utrzymuje jedno połączenie z usługą online.|Eksplorator serwera, w którym można mieć tylko jedno aktywne połączenie platformy Azure naraz, jest przykładem Connect/Disconnect.|
|Dodaj / Usuń|Niedestrukcyjne. Użyj podczas dodawania lub usuwania czegoś z listy.|Okno dialogowe serwera Menedżera połączeń TFS jest przykładem Dodaj/Usuń.|
|Usuń|Destrukcyjne. Używaj tylko wtedy, gdy usunięty element zostanie trwale odrzucony lub usunięty z dysku.|"Usuń" zazwyczaj wymaga monitu, jeśli wynik jest usunięcie pliku z dysku.|

## <a name="error-messages"></a>Komunikaty o błędach

### <a name="overview"></a>Omówienie
 Zdarzają się błędy. Ustawienie ograniczeń co użytkownik może zrobić jest rozsądnym pierwszym krokiem w zapobieganiu komunikatów o błędach, których można uniknąć. Jednak gdy wystąpi błąd, dobrze napisany komunikat o błędzie może przejść długą drogę w kierunku złagodzenia problemu. Komunikaty o błędach są prawdopodobnie jednym z najważniejszych typów powiadomień, które użytkownik widzi, ponieważ są one synchroniczne i wskazują problem, który należy rozwiązać. Źle napisane komunikaty o błędach pozostawiają użytkownikom na własną rękę, aby zdecydować przyczynę błędów i ewentualnych rozwiązań.

 Użytkownicy mogą przestać zwracać uwagę na nadużywane lub mylące komunikaty o błędach, więc pisz tylko niezbędne komunikaty, które dodają wartość do środowiska użytkownika. Jeśli wiadomość jest po prostu powiadomieniem, użyj alternatywnej prezentacji.

### <a name="rules-for-creating-an-error-message"></a>Reguły tworzenia komunikatu o błędzie

- Podczas konstruowania komunikatów o błędach wybierz odpowiedni poziom błędu dla odbiorców. Dążyć do prostych podsumowań, które zapewniają działania, które użytkownik może podjąć, jeśli ma to zastosowanie. Nie podawaj niczego, czego użytkownik nie musi wiedzieć.

- Zapewnij konstruktywną pomoc. Łatwiej jest odczytać i działać na komunikat o błędzie, który zawiera instrukcje.

- Nie używaj podwójnych negatywów.

- Wykonaj automatyczne i ręczne sprawdzanie gramatyki i pisowni na każdym komunikacie o błędzie, który piszesz.

- W przypadku złożonych komunikatów o błędach należy unikać komunikacji sekwencyjnej. Nigdy nie używaj podpięcia F1 dla komunikatu o błędzie. Sama wiadomość powinna być wystarczająca.

- Użyj poprawnej ikony.

- Ułatwianie zrozumienia pytań i używania przycisków, które mają wyraźne opcje, takie jak "Usuń" i "Anuluj".

- W przypadku ostrzeżeń, należy jasno powiedzieć, jakie będą konsekwencje postępowania. Przyciski powinny wskazywać konsekwencję.

- W przypadku błędów opisz, co użytkownik może zrobić, aby rozwiązać problem. Przyciski powinny być akcje lub powiedzieć "Zamknij". Nie używaj przycisku "OK" dla komunikatu o błędzie.

- Kilka pytań, które należy zadać sobie podczas konstruowania komunikatu o błędzie:

  - Czy użytkownik może dowiedzieć się, jak rozwiązać problem z tym błędem sam?

  - Czy użytkownik używa tego samego słownictwa co ten błąd?

  - Czy ten błąd jest niejednoznaczny lub współużytkuje się w wielu sytuacjach? Jeśli tak, w jaki sposób poprowadzisz użytkowników do rozwiązania, którego potrzebują?

#### <a name="build-errors"></a>Błędy kompilacji
 Ponieważ visual studio jest narzędziem do tworzenia oprogramowania, wiele z jego składników mają kompilacji, konwersji lub kodowania kroku do konwersji pracy dewelopera do postaci binarnej. Te konwersje mogą powodować błędy, gdy kompilator nie może przetwarzać nieprawidłowo utworzonych plików lub gdy opcje kompilatora nie zostały poprawnie ustawione.

 Użytkownicy programu Visual Studio mogą spędzić ogromną liczbę godzin rozwoju rozwiązywania błędów kompilacji. Ten czas rozwiązania zwiększa się, gdy błędy mają zależności lub gdy komunikaty o błędach są źle napisane, co może utrudnić wykrycie źródła błędu.

 Błędy najlepszej kompilacji to te, które nie występują w pierwszej kolejności, dlatego visual studio udostępnia autouzupełnianie i intellisense squiggles. Moduły sprawdzania poprawności schematu i podobne narzędzia zapewniają ten sam rodzaj opinii. Mechanizmy te proaktywnie prowadzą użytkownika do tworzenia dobrze sformułowanego kodu, zmniejszając ryzyko błędów kompilacji.

 Visual Studio udostępnia okno narzędzia, w którym użytkownicy mogą odczytywać i poruszać się po błędach, które wystąpiły w oknach dokumentów. Skróty klawiaturowe są dostarczane, dzięki czemu użytkownik może szybko poruszać się po dużych ilościach kodu i przejść bezpośrednio do lokalizacji problemu. Visual Studio umożliwia również każdy błąd kompilacji, które mają być powiązane z określonego słowa kluczowego/kontekstu Pomocy identyfikator, dzięki czemu użytkownik może przejść bezpośrednio do tematu Pomocy, który daje bardziej szczegółowe informacje o błędzie.

 Zapisz jasne, zwięzłe błędy kompilacji:

- **Użyj prostego języka,** który wyjaśnia problem z małym lub żadnym żargonem kompilatora. Tekst błędu kompilacji nie powinien być zbyt techniczny.

- **Zarys możliwych przyczyn.** Na przykład "Brak dwukropka między właściwością a wartością w deklaracji '(właściwość) : (value)'".

- Podaj szczegółowe informacje na temat potencjalnych poprawek. Jeśli nie ma wystarczającej ilości miejsca, dodatkowe szczegóły mogą zostać umieszczone w odpowiednim temacie Pomocy.

### <a name="components-of-a-well-written-error-message"></a>Składniki dobrze napisanego komunikatu o błędzie

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Użyj usługi okna dialogowego powłoki dla komunikatów o błędach.
 Korzystanie z usługi okna dialogowego powłoki pozwala kontrolować wygląd wiadomości, czcionki w szczególności, bez większych zmian w poszczególnych elementów. Użyj mechanizmów **IErrorInfo** i zgłoś je za pomocą **funkcji IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wybierz skuteczną i odpowiednią prezentację powiadomień.
 Użyj modalnego okna dialogowego z krytycznym ostrzeżeniem, jeśli wymagane jest natychmiastowe działanie, aby uniknąć utraty danych (powiadomienie synchroniczne). Krytyczne ikony są zarezerwowane dla sytuacji, w których zamknięcie wiadomości bez jej odczytania może prowadzić do negatywnych konsekwencji. Utrata danych jest krytyczną sytuacją, która wymaga reakcji na poziomie alarmu. Nadużywanie ikony krytycznej odczławia użytkowników do jego znaczenia. Jeśli komunikat o błędzie ma charakter informacyjny, należy wziąć pod uwagę alternatywy dla modalnego okna dialogowego (powiadomienie asynchroniczne).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Podaj czyste, zwięzłe wyjaśnienie, dlaczego wystąpił problem, a nie wyjaśnienie techniczne.
 Nadmierne obciążanie użytkowników szczegółami technicznymi w wyjaśnieniu sprawi, że będą bardziej skłonni do ignorowania komunikatów o błędach. Przykłady dobrych wiadomości:

- "Nie można otworzyć żądanego pliku."

- "Nie można połączyć się z Internetem."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Podaj informacje dotyczące sposobu rozwiązania problemu.
 Zaoferuj użytkownikom sugestie dotyczące rozwiązywania problemu. Bądź szczery z użytkownikiem, jeśli nie ma żadnych sugestii. Podaj bezpośrednie linki do alternatywnych źródeł online, takich jak pomoc techniczna lub wsparcie społeczności. Spróbuj wskazać użytkownikom konkretne informacje online związane z tym problemem. W przypadku identyfikatora błędu należy rozważyć powiązanie użytkowników z wątkiem dyskusji na temat tego określonego błędu. Przykłady dobrych wiadomości:

- "Upewnij się, że masz połączenie z Internetem i spróbuj ponownie wykonać tę operację."

- "Upewnij się, że plik istnieje i że masz uprawnienia do jego otwarcia."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Napisz wiadomość, która jest krótka i do rzeczy.
 Komunikat o błędzie może powiadamiać, wyjaśniać i oferować rozwiązanie, ale nadal jest ignorowany, jeśli jest zbyt rozsłowiony. Jednym z rozwiązań jest użycie stopniowego ujawniania za pomocą przycisku szczegółów. Na przykład podaj krótki opis/rozwiązanie, a następnie umieść więcej szczegółów pod przyciskiem szczegółów. Jeśli użytkownicy zdecydują się przeczytać więcej informacji na temat błędu, mogą to zrobić.

 Językiem w wiadomości powinien być:

- **Właściwa dla domeny.** Użyj języka, który użytkownik zrozumie. Mimo że nasi klienci są deweloperami, często nie mają kontekstu i terminologii, którą mamy.

- **Określonych.** Unikaj niejasnych sformułowań i podawaj konkretne nazwy i lokalizacje zaangażowanych obiektów. Na przykład komunikat o błędzie, taki jak "znak jest nieprawidłowy" nie jest przydatny. Która postać? "Nie znaleziono pliku". Który plik?

- **Uprzejmy.** Nie obwiniaj użytkownika lub sprawiają, że czują się głupi. Unikaj wrogiego lub obraźliwego języka (zabijaj, zabijaj, kończyj, kończyj, śmiertelnie, nielegalnie). Unikaj tekstu zawuszczki, który jest często postrzegany jako krzyczący i nie jest tak czytelny. Nie używaj humoru.

- **Poprawne.** Użyj poprawnej pisowni i gramatyki (nawet w alfa). Literówki są nieprofesjonalne i żenujące.

- **Kontekstowo odpowiednie.** Użyj odpowiedniego tekstu przycisku. Unikaj przycisku "OK" i zamiast tego użyj "Kontynuuj" lub "Tak/Nie".

### <a name="error-message-examples"></a>Przykłady komunikatów o błędach

|Dobrze|Zła|
|----------|---------|
|"Wybrany numer nie jest już w służbie. Sprawdź numer i wybierz ponownie numer 0 dla operatora."|- "Błąd (449): Numer nielegalny"<br />- "Ten nieobsługiowany błąd wyjątku wskazuje, że operacja została pomyślnie zakończona."<br /><br /> ![Nieprawidłowy komunikat o błędzie w programie Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Uzyskiwanie dostępu do Pomocy

### <a name="overview"></a>Omówienie
 Oprócz dokumentacji w msdn, użytkownik programu Visual Studio ma kilka punktów dostępu, aby pomóc użytkownikowi, podczas gdy w interfejsie użytkownika. Aby zapewnić, że te punkty dostępu są stale dostępne, zespoły funkcji muszą korzystać z systemu Pomocy oferowanego przez środowisko. Te punkty dostępu są:

- **Tekst instruktażowy i uzupełniający w oknach dialogowych.** Tekst statyczny, który podaje kierunek lub wyjaśnienie na powierzchni interfejsu użytkownika lub jest dostępny po umieszczeniu wskaźnika myszy nad ikoną Etykietki informacyjnej.

- **Pomoc F1** (tylko edytor). W edytorze Visual Studio użytkownik może ufać, że w dowolnym momencie naciśnięcie klawisza F1 spowoduje przywołanie tematu Pomocy specyficznego dla bieżącego zaznaczenia. Upewnij się, że tematy związane z F1 są odpowiednie i pouczające.

- **Hiperłącza do tematów Pomocy.** Hiperłącze w oknie dialogowym, oknie narzędzi lub powierzchni projektowej, które uruchamia temat, aby pomóc użytkownikowi w dowiedzieć się więcej o technologii, możliwości lub informacji o tym, jak wykonać zadanie.

- **Mechanizmy interfejsu użytkownika pomocnika, takie jak tagi inteligentne i okna dialogowe tworzenia.** Mechanizmy te pomagają użytkownikowi w zrozumieniu elementu interfejsu użytkownika lub ułatwiają zadanie, takie jak tagi inteligentne lub okna dialogowe konstruktora.

- **Przyciski pomocy interfejsu użytkownika** (przestarzałe). Widoczny wskaźnik na pasku tytułu, który daje dostęp do tematu Pomocy F1.

### <a name="text"></a>Tekst

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Tekst instruktażowy i uzupełniający w oknach dialogowych
 W oknach dialogowych, które obsługują złożone zadania, może istnieć potrzeba podania tekstu instruktażowego w interfejsie użytkownika, często w górnej części okna dialogowego lub w pobliżu złożonych formantów. Zobacz [tekst interfejsu użytkownika i terminologii,](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) aby uzyskać szczegółowe informacje na temat stylu pisania.

#### <a name="infotips"></a>Porady informacyjne
 Często tekst instruktażowy może być zbyt długi, aby umieścić je w interfejsie użytkownika lub może być przydatny tylko dla nowych użytkowników, czując się bałaganem dla doświadczonych użytkowników. W takim przypadku tekst instruktażowy/informacyjny powinien być umieszczony jako etykietka narzędzia w obszarze Etykieta informacyjna.

 Porady informacyjne powinny być umieszczane w pobliżu formantów, które są związane z i należy użyć określonej ikony Porady, która jest dyskretny, ale zauważalne.

 ![Porada informacyjna w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Przykład porady w programie Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktywne mechanizmy pomocy

#### <a name="f1-help"></a>Pomoc F1
 Pomoc F1 jest wymagana w edytorze lub powierzchni projektowej, ale nie w innym miejscu w środowisku programu Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hiperłącza do tematów Pomocy
 Hiperłącza mogą służyć do wykonywania akcji, nawigacji w środowisku IDE lub uruchamiania Pomocy w przeglądarce. Zobacz [tekst interfejsu użytkownika i terminologii,](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) aby uzyskać szczegółowe informacje na temat języka i 07.10.01 Przyciski i hiperłącza dla wizualnych i układu wskazówki.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Przyciski Pomocy [?] na paskach tytułów dialogowych (przestarzałe)
 W przeważającej części przyciski Pomocy [?] na pasku tytułu okien dialogowych są przestarzałe. Tematy interfejsu użytkownika nie są już częścią naszego modelu doc i dlatego może nie być odpowiedni temat do linku. Zasadniczo przycisk paska tytułu był tym samym, co Pomoc F1 i nie jest już wymagany w oknach dialogowych. W niektórych przypadkach może to być nadal używane jako wskaźnik, że jest więcej informacji koncepcyjnych lub proceduralnych dostępnych, chociaż hiperłącza są częściej używane w nowszym interfejsie użytkownika.

##### <a name="dialogs-created-through-the-environment"></a>Okna dialogowe utworzone w środowisku
 Wiele okien dialogowych powłoki są tworzone za pomocą funkcji **VBDialogBoxParam.** Ta funkcja współużytkowana została zaktualizowana, aby pomóc w przeniesieniu przycisku **Pomoc** z okna dialogowego do **?** przy zachowaniu architektury, która jest wstecznie kompatybilna i rozszerzalna.

 W szczególności funkcja **VBDialogBoxParam** analizuje szablon okna dialogowego dla przycisku, którego identyfikatorem jest **IDHELP** (9) lub etykietą jest **Pomoc** lub **&Pomoc**. Jeśli przycisk Pomoc zostanie znaleziony, zostanie on ukryty, a styl **WS_EX_CONTEXTHELP** zostanie dodany do okna dialogowego, które umieszcza **?** na pasku tytułu okna dialogowego.

 Po utworzeniu okna dialogowego wypycha proszkę dialogową na stos i wywołuje okno dialogowe z przepustem dialogowym o nazwie **DialogPreProc**. Kiedy **?** jest klikany, wysyła **WM_SYSCOMMAND** **SC_CONTEXTHELP** do okna dialogowego. **DialogPreProc** przechwytuje to polecenie i zmienia go na **komunikat WM_HELP,** który jest przekazywany do oryginalnego proc okna dialogowego.

 Większość okien dialogowych utworzonych przez środowisko ma przycisk Pomocy w oknie dialogowym. Po wyświetleniu okna dialogowego przycisk Pomoc jest automatycznie ukryty i tylko **?** działa przycisk. Jeśli **?** jest zawsze usuwany lub zmieniany w systemie Windows, to rozwiązanie pozwala szybko wrócić do oryginalnych przycisków Pomocy.

 To rozwiązanie zawiera cztery założenia, które mogą powodować błędy:

- Przycisk pomocy okna dialogowego to **IDHELP** (9).

- Okno dialogowe wygląda poprawnie, gdy przycisk Pomoc jest ukryty.

- Okno dialogowe nie zastępuje jego winproc.

- Okno dialogowe nie jest osadzone wewnątrz innego okna dialogowego.

  Jeśli okno dialogowe znajduje się w msenv i nie używa **VBDialogBoxParam,** należy zbadać wykorzystanie **VBDialogBoxParam** przed zaimplementowaniem własnego programu obsługi.

##### <a name="dialogs-created-through-other-packages"></a>Okna dialogowe utworzone za pośrednictwem innych pakietów
 Można zaimplementować własne rozwiązanie dla okien dialogowych, które znajdują się poza msenv. Dla klasy udostępnionego okna dialogowego w programie VSPackage należy rozważyć przeniesienie przycisku na pasek tytułu lub zaimplementowanie programu obsługi w każdym oknie dialogowym. Poniższy kod jest szkielet implementacji, aby ułatwić rozpoczęcie pracy:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Przyciski Pomocy w kodzie zarządzanym
 Zastępowanie domyślnego zachowania przycisku Pomocy na pasku tytułu okna jest łatwe w kodzie zarządzanym. Poniżej znajduje się pełna aplikacja demo, która demonstruje to zachowanie. W istocie należy zastąpić formularz **WndProc** metody, a następnie odpalić F1 żądania pomocy, gdy **wiadomość SC_CONTEXTHELP** zostanie przechwycona.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Zobacz też
- [Czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Układ dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Powiadomienia i postęp dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
