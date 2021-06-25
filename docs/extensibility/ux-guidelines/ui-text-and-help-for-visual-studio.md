---
title: Tekst interfejsu użytkownika i pomoc Visual Studio | Microsoft Docs
description: Dowiedz się więcej o tekście interfejsu użytkownika i terminologii używanej w informacjach pomocy dla Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b128c5e95c70457d92843e620b4aa072c409ba
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899436"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Tekst interfejsu użytkownika i pomoc dla programu Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Tekst interfejsu użytkownika i terminologia
 Zrozumiały tekst ma kluczowe znaczenie dla efektywnego interfejsu użytkownika. Użytkownicy oprogramowania zwykle najpierw odczytują etykiety, czyli te, które są najbardziej istotne do wykonania danego zadania. Tekst statyczny jest odczytywany z mniejszą częstotliwością. Zaplanuj, aby użytkownicy rozpoczynali sesje służbowe od szybkiego skanowania całego okna, a następnie odczytania interfejsu użytkownika w tej przybliżonej kolejności:

1. Kontrolki interaktywne w środku

2. Przyciski zatwierdzania

3. Kontrolki interaktywne znalezione w innym miejscu

4. Instrukcje główne

5. Dodatkowe wyjaśnienia

6. Tytuł okna

7. Inny tekst statyczny w głównej treści

### <a name="usage-patterns-for-ui-text"></a>Wzorce użycia tekstu interfejsu użytkownika

#### <a name="title-bar-text"></a>Tekst paska tytułu
 Tekst paska tytułu musi odpowiadać poleceniu, które zduplikowało interfejs użytkownika.

#### <a name="instructional-text-helper-text"></a>Tekst instruktażowy (tekst pomocnika)
 W niektórych oknach dialogowych warto podać najważniejsze instrukcje główne, aby wyjaśnić, co należy zrobić w oknie lub na stronie. Jest to czasami określane jako "tekst pomocnika".

##### <a name="writing-style-rules-for-helper-text"></a>Pisanie reguł stylu dla tekstu pomocnika

- Nie wyjaśniaj oczywistych. Jeśli nie jest to absolutnie konieczne, nie należy dołączać tekstu instruktażowego.

- Tekst instruktażowy jest zawsze umieszczany w górnej części okna dialogowego i powinien odwoływać się do wykonywanego zadania.

- Dokładnie wyjaśnij użytkownikom, co muszą zrobić. Unikaj nadmiernej komunikacji i nadmiarowości.

- Przejrzyj każde okno i wyeliminuj zduplikowane słowa i instrukcje.

- Zachowaj krótki tekst instruktażowy. Jeśli w przypadku niektórych użytkowników lub scenariuszy jest potrzebnych więcej informacji, podaj link do szczegółowego koncepcyjnego tematu online.

- Napisz tekst tak, aby każde słowo zawierało wagę i było konieczne.

- Postępuj zgodnie z istniejącymi wskazówkami firmy Microsoft [Interfejs użytkownika tekst i](/windows/desktop/uxguide/text-ui) styl oraz [ton.](/windows/desktop/uxguide/text-style-tone)

#### <a name="supplemental-instructions"></a>Instrukcje uzupełniające
 Instrukcje uzupełniające zawierają dodatkowe informacje, które pomagają użytkownikowi zrozumieć kontrolki lub grupowania kontrolek. Może to również zawierać tekst wskazówki niezbędny do zrozumienia, jakiego formatu oczekuje kontrolka wejściowa. Instrukcje uzupełniające należy stosować oszczędnie. Rezerwuj je na przypadki, w których prawdopodobnie użytkownik nie będzie w pełni rozumieć konsekwencji wybranego wyboru.

 ![Zrzut ekranu przedstawiający Internet Explorer Opcje z tekstem uzupełniającym poniżej, który opisuje wpływ zmiany ustawień opcji.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Tekst uzupełniający w Visual Studio**

 ![Zrzut ekranu przedstawiający okno dialogowe Wybieranie kontroli źródła w Visual Studio tekst uzupełniający opisujący poszczególne opcje systemu kontroli źródła.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Tekst uzupełniający w Visual Studio**

#### <a name="infotips"></a>Etykietki informacyjne
 Często tekst instruktażowy może być zbyt długi, aby umieścić go w miejscu w interfejsie użytkownika, lub może być przydatny tylko dla nowych użytkowników, czując się jak zaśmiecony dla doświadczonych użytkowników. W takim przypadku tekst instruktażowy/informacyjny należy umieścić jako etykietkę narzędzia w obszarze Etykietka informacyjna.

 Etykietki informacyjne powinny być umieszczone w pobliżu kontrolek, z którymi są powiązane, i powinny używać określonej ikony Etykietki informacji, która jest dyskretna, ale zauważalna.

 ![Etykietka informacyjna w Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Przykład etykietki informacyjnej w Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Pisanie reguł stylu dla etykietek informacji

- Pisz etykietki informacyjne jako pełne zdania. Wymagają one określonych czasowników, liter zdań i końcowej interpunkcji.

- Użyj etykietek informacyjnych, aby uzupełnić instrukcje główne lub informacje. Jeśli używasz tylko różnych wyrazów do przekierowynia głównego pomysłu, nie potrzebujesz etykietki informacyjnej.

- Zachowaj krótką i krótką etykietkę informacyjną. Używaj małych słów i zwykłego, codziennego języka, który obsługuje i zachęca użytkownika.

- Postępuj zgodnie z istniejącymi wskazówkami firmy Microsoft [Interfejs użytkownika tekst i](/windows/desktop/uxguide/text-ui) styl oraz [ton.](/windows/desktop/uxguide/text-style-tone)

#### <a name="control-labels"></a>Etykiety kontrolek
 Etykiety kontrolek powinny być krótkie, zwięzłe i zgodne ze wskazówkami programu [Windows Desktop dla kontrolek](/windows/desktop/uxguide/controls).

 Aby uzyskać więcej informacji na temat formatowania i umieszczania etykiet kontrolek w interfejsie użytkownika, zapoznaj się z tematem [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Linki pomocy
 Linki pomocy można umieścić w tekście instruktażowym lub w treści interfejsu użytkownika. Mogą to być linki do pomocy lub uruchamiania wewnętrznych okien dialogowych.

##### <a name="visual-style-rules-for-help-links"></a>Reguły stylu wizualizacji dla linków Pomocy

- Użyj odpowiednich kolorów środowiska dla hiperlinków. Hiperlink o prawidłowym stylu nie będzie krótko pulsował na czerwono po kliknięciu. Jeśli to widzisz, oznacza to, że kolory środowiska nie są używane.

- Podkreśleń należy używać tylko po umieszczeniu wskaźnika myszy lub po osadzona linku w akapicie.

- Aby uzyskać bardziej szczegółowe informacje na temat stylów wizualizacji i interakcji dla hiperlinków, zobacz Przyciski i hiperlinki.

##### <a name="writing-style-rules-for-help-links"></a>Pisanie reguł stylu dla linków pomocy

- Podczas uruchamiania okien dialogowych należy zachować standardy wielokropka: brak wielokropka na potrzeby nawigacji, wielokropek, jeśli zadanie wymaga dodatkowego interfejsu użytkownika.

     ![Link Pomocy w Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Wielokropek (...) w linku Pomoc wskazuje, że zadanie będzie wymagało dodatkowego interfejsu użytkownika.**

- Linki nie powinny zaczynać się od "Learn", ponieważ nie jest to intencja użytkownika. Użytkownik chce odpowiedzieć na konkretne pytanie, a nie uzyskać ogólną edukację.

- Linki pomocy dotyczącej fraz, aby zadać pytanie, na które będzie odpowiadać temat.

     Niepoprawne: "Dowiedz się więcej o cenach usługi Windows Azure Mobile Services"

     Odpowiedź prawidłowa: "Jakie opcje cenowe są dostępne dla usługi Windows Azure Mobile Services?"

- Nigdy nie *używaj funkcji Click...* w tekście linku.

- Nigdy nie łącz tylko słowa "tutaj". Jest to problematyczne w przypadku niektórych czytników zawartości ekranu, które będą głosić tylko słowo z hiperlinkiem.

     Niepoprawne: "Znajdź informacje o platformie Windows Azure Mobile Services **tutaj**"

     Odpowiedź prawidłowa: "Jakie opcje cenowe są dostępne dla usługi Windows Azure Mobile Services?"

- Aby uzyskać więcej informacji na temat poprawnego stylu pisania linków pomocy, zobacz Wskazówki dotyczące programu [Windows Desktop dla pomocy](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Tekst wskazówki
 Tekst wskazówki jest wyświetlany jako znak wodny w obrębie kontrolki lub poniżej kontrolki. Poprawne formatowanie zostanie zastosowane przy użyciu odpowiedniego tokenu VSColors, `Environment.GrayText` .

 Może występować w wielu formularzach.

- W miejsce etykiety kontrolki:

     ![Zrzut ekranu przedstawiający kontrolkę listy rozwijanej z tekstem wskazówki w miejscu etykiety kontrolki z tekstem "Wyszukaj Eksplorator rozwiązań (Ctrl+;)".](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Za pomocą czasownika, który daje instrukcje:

     ![Zrzut ekranu przedstawiający pole tekstowe z tekstem wskazówki w kontrolce z tekstem "Wprowadź swoje imię".](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Z tekstem wskazującym wymagany wpis:

     ![Zrzut ekranu przedstawiający pole tekstowe z tekstem wskazówki w kontrolce z tekstem \< \> "Wymagane".](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Tekst limitu
 Na pustej powierzchni projektowej tekst powinien wskazywać, co należy zrobić, a także udostępnić linki do otwierania innych powiązanych okien, jeśli jest to konieczne:

 ![Tekst znaku wodnego w Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Przykładowy tekst limitu w Visual Studio**

### <a name="common-terminology"></a>Wspólna terminologia

|Okres|Wyjaśnienie|Komentarz|
|----------|-----------------|-------------|
|Logowanie/wyloguj się|Czasowniki używane w sposób synonimicznie z siecią Web do reprezentowania uwierzytelniania we właściwości sieci Web. W obrębie klientów używamy tego raz jako informacji najwyższego poziomu do logowania się i wyczyniania połączenia użytkownika środowiska IDE, która reprezentuje tożsamość najwyższego poziomu, która zapewnia możliwości wyższego poziomu, takie jak roaming i licencjonowanie, które nie są dostępne dla wszystkich innych połączeń.|Użytkownik IDE jest jedyną funkcją, która powinna reprezentować czasownik logowania/wylogowania, ponieważ reprezentuje użytkownika ide najwyższego poziomu.|
|Łączenie/rozłączanie|Należy używać w miejscach, w których funkcja utrzymuje jedno połączenie z usługą online.|Eksplorator serwera, w którym można mieć tylko jedno aktywne połączenie platformy Azure na raz, jest to przykład połączenia/rozłączenia.|
|Dodawanie/usuwanie|Nieniszczący. Użyj podczas dodawania lub usuwania elementów z listy.|Przykładem dodawania/usuwania jest okno dialogowe listy serwerów Menedżer połączeń TFS.|
|Usuń|Destrukcyjne. Należy używać tylko wtedy, gdy usuwany element zostanie trwale odrzucony lub usunięty z dysku.|"Usuń" zwykle wymaga monitu, jeśli wynik jest usuwanie pliku z dysku.|

## <a name="error-messages"></a>Komunikaty o błędach

### <a name="overview"></a>Omówienie
 Występują błędy. Ustawianie ograniczeń dotyczących czynności, które użytkownik może wykonać, jest rozsądnym pierwszym krokiem w zapobieganiu komunikatom o błędach, których można uniknąć. Jednak w przypadku wystąpienia błędu dobrze napisany komunikat o błędzie może pójść daleko w kierunku rozwiązania problemu. Komunikaty o błędach są prawdopodobnie jednym z najważniejszych typów powiadomień wyświetlanych przez użytkownika, ponieważ są one synchroniczne i wskazują problem, który należy rozwiązać. Źle napisane komunikaty o błędach pozostawiają użytkowników samodzielnie, aby decydować o ich przyczynach i wszelkich możliwych rozwiązaniach.

 Użytkownicy mogą przestać zwracać uwagę na zbytnie lub mylące komunikaty o błędach, więc piszą tylko niezbędne komunikaty, które dodają wartość do obsługi użytkownika. Jeśli komunikat jest po prostu powiadomieniem, użyj prezentacji alternatywnej.

### <a name="rules-for-creating-an-error-message"></a>Reguły tworzenia komunikatu o błędzie

- Podczas tworzenia komunikatów o błędach wybierz odpowiedni poziom błędu dla odbiorców. Staraj się uzyskać proste podsumowania, które zapewniają akcję, które użytkownik może podjąć, jeśli ma to zastosowanie. Nie oznaczaj niczego, czego użytkownik nie musi wiedzieć.

- Zapewnianie pomocy konstruktywnej. Łatwiej jest odczytać komunikat o błędzie zawierający instrukcję i działać na nim.

- Nie używaj podwójnych wartości ujemnych.

- Wykonaj automatyczne i ręczne sprawdzanie gramatyki i pisowni dla każdego pisanych komunikatów o błędzie.

- W przypadku złożonych komunikatów o błędach unikaj komunikacji sekwencyjnej. Nigdy nie używaj podłączania klawisza F1 dla komunikatu o błędzie. Sam komunikat powinien być wystarczający.

- Użyj poprawnej ikony.

- Ułatwiaj zrozumienie pytań i używaj przycisków, które mają czytelne opcje, takie jak "Usuń" i "Anuluj".

- W przypadku ostrzeżeń należy wyraźnie wyjaśnić, jakie będą konsekwencje tego postępowania. Przyciski powinny wskazywać konsekwencje.

- W przypadku błędów opisz, co użytkownik może zrobić, aby rozwiązać problem. Przyciski powinny być akcjami lub powiedz "Zamknij". Nie używaj przycisku "OK" dla komunikatu o błędzie.

- Niektóre pytania, które należy zadać sobie podczas konstruowania komunikatu o błędzie:

  - Czy użytkownik może samodzielnie ustalić, jak rozwiązać problem z tym błędem?

  - Czy użytkownik używa tego samego słownictwa co ten błąd?

  - Czy ten błąd jest nieuprawniany, czy współużytkował go w wielu sytuacjach? Jeśli tak, jak kierować użytkowników do rozwiązania, które są im potrzebne?

#### <a name="build-errors"></a>Błędy kompilacji
 Ponieważ Visual Studio to narzędzie do tworzenia oprogramowania, wiele jego składników ma krok kompilacji, konwersji lub kodowania w celu przekonwertowania pracy dewelopera na postać binarną. Te konwersje mogą powodować błędy, gdy kompilator nie może przetworzyć nieprawidłowo tworzyć plików lub gdy opcje kompilatora nie zostały prawidłowo ustawione.

 Visual Studio użytkownicy mogą poświęcać ogromną liczbę godzin programistów na rozwiązywanie błędów kompilacji. Ten czas rozwiązania wydłuża się, gdy błędy mają zależności lub gdy komunikaty o błędach są źle napisane, co może utrudnić odkrycie źródła błędu.

 Najlepsze błędy kompilacji to te, które nie występują w pierwszej kolejności, dlatego usługa Visual Studio udostępnia zygieł funkcji Autouzupełnianie i IntelliSense. Narzędzia do sprawdzania poprawności schematów i podobne narzędzia zapewniają ten sam rodzaj opinii. Te mechanizmy proaktywnie przekierują użytkownika do konstruowania dobrze utworzonego kodu, co zwiększa prawdopodobieństwo błędów kompilacji.

 Visual Studio udostępnia okno narzędzi, w którym użytkownicy mogą odczytywać błędy, które wystąpiły w oknach dokumentów, i przechodzić przez nie. Dostępne są skróty klawiaturowe, dzięki którym użytkownik może szybko nawigować po dużych ilościach kodu i przechodzić bezpośrednio do lokalizacji problemu. Visual Studio każdy błąd kompilacji może być powiązany z konkretnym identyfikatorem słowa kluczowego/kontekstu pomocy, dzięki czemu użytkownik może przejść bezpośrednio do tematu pomocy, który zawiera bardziej szczegółowe informacje o błędzie.

 Pisz czytelne, zwięzłe błędy kompilacji:

- **Użyj zwykłego języka,** który wyjaśnia problem przy użyciu niewielkiego lub żadnego żargonu kompilatora. Tekst błędu kompilacji nie powinien być zbyt techniczny.

- **Konspektuj możliwe przyczyny.** Na przykład "Brak dwukropka między właściwością i wartością w deklaracji '(property) : (value)".

- Podaj szczegółowe informacje o potencjalnych poprawkach. Jeśli nie ma wystarczającej ilości miejsca, dodatkowe szczegóły można umieścić w odpowiednim temacie pomocy.

### <a name="components-of-a-well-written-error-message"></a>Składniki dobrze napisanego komunikatu o błędzie

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Użyj usługi okna dialogowego powłoki dla komunikatów o błędach.
 Usługa okna dialogowego powłoki umożliwia kontrolowanie wyglądu komunikatu, w szczególności czcionek, bez istotnych zmian poszczególnych elementów. Użyj mechanizmów **IErrorInfo** i zgłoś je przy użyciu interfejsu **IVsUIShell::SetErrorInfo/ReportErrorInfo.**

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wybierz skuteczną i odpowiednią prezentację powiadomień.
 Użyj modalnego okna dialogowego z ostrzeżeniem krytycznym, jeśli jest wymagane natychmiastowe działanie w celu uniknięcia utraty danych (powiadomienie synchroniczne). Ikony krytyczne są zarezerwowane w sytuacjach, w których zamknięcie komunikatu bez jego odczytania może prowadzić do negatywnych konsekwencji. Utrata danych jest krytyczną sytuacją, która wymaga reakcji na poziomie alarmu. Overuse of the critical icon desensizes users to its importance. Jeśli komunikat o błędzie ma charakter informacyjny, rozważ alternatywę dla modalnego okna dialogowego (powiadomienie asynchroniczne).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Podaj czyste, zwięzłe wyjaśnienie przyczyny problemu, a nie wyjaśnienie techniczne.
 Przeciążenie użytkowników ze szczegółami technicznymi w objaśnieniu sprawi, że będą bardziej skłonni do ignorowania komunikatów o błędach. Przykłady dobrych wiadomości:

- "Nie można otworzyć żądanego pliku".

- "Nie można nawiązać połączenia z Internetem".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Podaj informacje na temat sposobu rozwiązania problemu.
 Zaoferuj użytkownikom sugestie dotyczące sposobu rozwiązania problemu. Jeśli nie ma sugestii, należy być uczciwym wobec użytkownika. Udostępnij bezpośrednie linki do alternatywnych źródeł online, takich jak pomoc techniczna lub pomoc społecznościowa. Spróbuj wskazać użytkownikom konkretne informacje online dotyczące problemu. W przypadku identyfikatora błędu rozważ połączenie użytkowników z wątkiem dyskusji na temat tego konkretnego błędu. Przykłady dobrych wiadomości:

- "Upewnij się, że masz połączenie z Internetem i spróbuj ponownie wykonać tę operację".

- "Upewnij się, że plik istnieje i że masz uprawnienia do jego otwarcia".

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Napisz wiadomość, która jest krótka i do punktu.
 Komunikat o błędzie może powiadamiać, wyjaśniać i oferować rozwiązanie, ale nadal można je zignorować, jeśli jest ono zbyt wyrazowe. Jednym z rozwiązań jest użycie stopniowego ujawnienia z przyciskiem szczegółów. Na przykład podaj krótki opis/rozwiązanie, a następnie umieść więcej szczegółów pod przyciskiem szczegółów. Jeśli użytkownik zdecyduje się przeczytać więcej informacji na temat błędu, może to zrobić.

 Język w komunikacie powinien być:

- **Odpowiednie dla domeny.** Użyj języka, który będzie zrozumiały dla użytkownika. Mimo że nasi klienci są deweloperami, często nie mają używanego kontekstu i terminologii.

- **Określonych.** Unikaj niejasnych słów i nadawaj konkretne nazwy i lokalizacje obiektów, których dotyczy ten konflikt. Na przykład komunikat o błędzie, taki jak "znak jest nieprawidłowy", nie jest przydatny. Który znak? "Nie znaleziono pliku". Który plik?

- **Uprzejmy.** Nie należy obwiniać użytkownika ani sprawić, aby czuli się od siebie odimówieni. Unikaj wulgarnego lub obraźliwego języka (kill, execute, terminate, fatal, illegal). Unikaj wielkich liter, który jest często postrzegany jako przechyłanie i nie jest tak czytelny. Nie używaj ich do tego celu.

- **Poprawne.** Używaj poprawnej pisowni i gramatyki (nawet w alfasach). Literówki są nieprofesjonalne i kłopotliwe.

- **Odpowiednie kontekstowo.** Użyj odpowiedniego tekstu przycisku. Unikaj przycisku "OK", a zamiast tego użyj opcji "Kontynuuj" lub "Tak/Nie".

### <a name="error-message-examples"></a>Przykłady komunikatów o błędach

|Dobrze|Zła|
|----------|---------|
|"Wybrany numer nie jest już w usłudze. Sprawdź numer i wybierz ponownie lub wybierz 0 dla operatora".|- "Błąd (449): Liczba niedozwolona"<br />- "Ten nieobsługiwany błąd wyjątku wskazuje, że operacja została zakończona pomyślnie".<br /><br /> ![Zły komunikat o błędzie w Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Uzyskiwanie dostępu do pomocy

### <a name="overview"></a>Omówienie
 Oprócz dokumentacji w witrynie MSDN użytkownik Visual Studio kilka punktów dostępu, które pomagają użytkownikowi w interfejsie użytkownika. Aby zapewnić stałą dostęp do tych punktów dostępu, zespoły ds. funkcji muszą korzystać z systemu pomocy oferowanego przez środowisko. Te punkty dostępu to:

- **Tekst instruktażowy i uzupełniający w oknach dialogowych.** Tekst statyczny, który podaje kierunek lub wyjaśnienie, na powierzchni interfejsu użytkownika lub dostępny po najechaniu kursorem na ikonę InfoTip.

- **Pomoc F1** (tylko edytor). W edytorze Visual Studio użytkownik może mieć zaufanie, że w dowolnym momencie naciśnięcie klawisza F1 spowoduje, że pojawi się temat Pomocy specyficzny dla bieżącego zaznaczenia. Upewnij się, że tematy skojarzone z F1 są odpowiednie i informacyjne.

- **Hiperlinki do tematów Pomocy.** Hiperlink w oknie dialogowym, oknie narzędzi lub powierzchni projektowej, który uruchamia temat, aby pomóc użytkownikowi dowiedzieć się więcej na temat technologii, możliwości lub informacji na temat sposobu wykonania zadania.

- **Mechanizmy interfejsu użytkownika pomocnika, takie jak tagi inteligentne i okna dialogowe tworzenia.** Te mechanizmy pomagają użytkownikowi w zrozumieniu elementu interfejsu użytkownika lub ułatwiają zadanie, takie jak inteligentne tagi lub okna dialogowe konstruktora.

- **Przyciski pomocy interfejsu użytkownika** (przestarzałe). Widoczny wskaźnik na pasku tytułu, który zapewnia dostęp do powiązanego tematu pomocy F1.

### <a name="text"></a>Tekst

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Tekst instruktażowy i uzupełniający w oknach dialogowych
 W oknach dialogowych, które obsługują złożone zadania, może być konieczne nadaj tekst instruktażowy w interfejsie użytkownika, często w górnej części okna dialogowego lub w pobliżu złożonych kontrolek. Zobacz [tekst interfejsu użytkownika i terminologię,](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) aby uzyskać szczegółowe informacje na temat stylu pisania.

#### <a name="infotips"></a>Etykietki informacji
 Często tekst instruktażowy może być zbyt długi, aby można go było umieścić w interfejsie użytkownika, lub może być przydatny tylko dla nowych użytkowników, poczuw się jak zaśmiecony dla doświadczonych użytkowników. W takim przypadku tekst instruktażowy/informacyjny należy umieścić jako etykietkę narzędzia w obszarze Etykietka informacyjna.

 Etykietki informacyjne powinny być umieszczone w pobliżu kontrolek, z którymi są powiązane, i powinny używać określonej ikony Etykietki informacji, która jest dyskretna, ale zauważalna.

 ![Etykietka informacyjna w Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Przykład etykietki informacyjnej w Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mechanizmy interaktywnej pomocy

#### <a name="f1-help"></a>Pomoc F1
 Pomoc F1 jest wymagana w obrębie edytora lub powierzchni projektowej, ale nie w innym Visual Studio środowisku.

#### <a name="hyperlinks-to-help-topics"></a>Hiperlinki do tematów Pomocy
 Hiperlinki mogą służyć do wykonywania akcji, nawigowania w obrębie środowiska IDE lub uruchamiania Pomocy w przeglądarce. Zobacz [tekst interfejsu użytkownika](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) i terminologię, aby uzyskać szczegółowe informacje na temat języka oraz przyciski i hiperlinki 07.10.01, aby uzyskać wskazówki dotyczące wizualizacji i układu.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Przyciski Pomocy [?] na paskach tytułu okna dialogowego (przestarzałe)
 W większości przypadków przyciski Pomoc [?] na pasku tytułu okien dialogowych są przestarzałe. Tematy interfejsu użytkownika nie są już częścią naszego modelu dokumentacji i w związku z tym może nie być odpowiednim tematem, z który należy utworzyć link. Zasadniczo przycisk paska tytułu był taki sam jak przycisk Pomoc F1 i nie jest już wymagany w oknach dialogowych. W niektórych przypadkach nadal można tego użyć jako wskaźnika, że dostępnych jest więcej informacji koncepcyjnych lub proceduralnych, chociaż hiperlinki są częściej używane w nowszej wersji interfejsu użytkownika.

##### <a name="dialogs-created-through-the-environment"></a>Okna dialogowe utworzone za pośrednictwem środowiska
 Wiele okien dialogowych powłoki jest tworzona za pomocą **funkcji VBDialogBoxParam.** Ta funkcja udostępniona została zaktualizowana, aby ułatwić przenoszenie **przycisku Pomoc** z okna dialogowego do **?** z zachowaniem architektury zgodnej z poprzednimi wersjami i rozszerzalnej.

 W szczególności funkcja **VBDialogBoxParam** wyszukuje w szablonie okna dialogowego przycisk o identyfikatorze **IDHELP** (9) lub etykietę Help **or**&Help ( **Pomoc).** Jeśli przycisk Pomoc zostanie znaleziony, zostanie ukryty, a styl WS_EX_CONTEXTHELP **zostanie** dodany do okna dialogowego, w którym znajduje się **?** na pasku tytułu okna dialogowego.

 Po utworzeniu okna dialogowego wypycha ono okno dialogowe do stosu i wywołuje okno dialogowe z przetwarzaniem wstępnym o nazwie **DialogPreProc**. Kiedy **?** kliknięcie przycisku powoduje wysłanie **WM_SYSCOMMAND** **SC_CONTEXTHELP** do okna dialogowego. **DialogPreProc** przechwytuje to polecenie  i zmienia je na komunikat WM_HELP, który jest przekazywany do oryginalnego proc okna dialogowego.

 Większość okien dialogowych utworzonych w środowisku ma przycisk Pomoc w oknie dialogowym. Gdy zostanie wyświetlone okno dialogowe, przycisk Pomoc zostanie automatycznie ukryty i będzie widoczny tylko **przycisk ?** Przycisk działa. Jeśli **?** przycisk jest kiedykolwiek usuwany lub zmieniany w systemie Windows. Dzięki temu rozwiązaniu można szybko wrócić do oryginalnych przycisków Pomoc.

 To rozwiązanie wprowadza cztery założenia, które mogą powodować błędy:

- Przycisk pomocy w oknie dialogowym to **IDHELP** (9).

- Okno dialogowe wygląda poprawnie, gdy przycisk Pomoc jest ukryty.

- Okno dialogowe nie zastępuje jego winproc.

- Okno dialogowe nie jest osadzone wewnątrz innego okna dialogowego.

  Jeśli okno dialogowe znajduje się w programie msenv i nie używa narzędzia **VBDialogBoxParam,** przed zaimplementowaniem własnej procedury obsługi zbadaj użycie właściwości **VBDialogBoxParam.**

##### <a name="dialogs-created-through-other-packages"></a>Okna dialogowe utworzone za pomocą innych pakietów
 Możesz zaimplementować własne rozwiązanie dla okien dialogowych, które znajdują się poza msenv. W przypadku klasy udostępnionego okna dialogowego w pakietach VSPackage rozważ przeniesienie przycisku na pasek tytułu lub zaimplementowanie procedury obsługi w każdym oknie dialogowym. Poniższy kod jest szkieletem implementacji, który pomoże Ci rozpocząć pracę:

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
 Zastępowanie domyślnego zachowania przycisku Pomoc na pasku tytułu okna jest łatwe w kodzie zarządzanym. Poniżej znajduje się kompletna aplikacja demonstracyjna, która demonstruje to zachowanie. W zasadzie należy zastąpić metodę **WndProc** formularza, **a** następnie wyłączyć żądania pomocy F1 po przechwyceniu komunikatu SC_CONTEXTHELP formularza.

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
