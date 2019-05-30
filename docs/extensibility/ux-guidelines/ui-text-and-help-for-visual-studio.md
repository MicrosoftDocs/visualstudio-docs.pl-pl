---
title: Tekst interfejsu użytkownika i pomoc dotyczącą programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7917bdd3b7a94af605b2626016c9a9a725fa2b29
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310796"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Tekst interfejsu użytkownika i pomoc dotyczącą programu Visual Studio
## <a name="BKMK_UITextAndTerminology"></a> Tekst interfejsu użytkownika i terminologia
 Tekst zrozumiałymi ma podstawowe znaczenie dla skutecznego interfejsu użytkownika. Użytkownicy oprogramowania mają tendencję do odczytu etykiet, a mianowicie te najistotniejsze Kończenie wykonywanego zadania. Tekst statyczny jest do odczytu z mniejszą częstotliwością. Zaplanuj użytkownikom na uruchamianie ich sesji pracy za pomocą szybkiego skanowania całego okna, następuje odczytywanie interfejsu użytkownika w tej kolejności przybliżony:

1. Kontrolki interaktywne na środku

2. Zatwierdź przycisków

3. Znalezionych w innym miejscu interaktywnych formantów

4. Głównej instrukcji

5. Dodatkowe objaśnienia

6. Tytuł okna

7. Inny tekst statyczny w treści głównego

### <a name="usage-patterns-for-ui-text"></a>Wzorce użycia dla tekst interfejsu użytkownika

#### <a name="title-bar-text"></a>Tekst paska tytułu
 Tekst paska tytułu musi odpowiadać polecenie, które zduplikowany interfejsu użytkownika.

#### <a name="instructional-text-helper-text"></a>Tekst (pomocnika tekst)
 W niektórych oknach dialogowych warto zapewnić wyraźną głównej instrukcji, aby wyjaśnić, co należy zrobić w oknie lub na stronie. To jest czasami określane jako "tekst pomocy".

##### <a name="writing-style-rules-for-helper-text"></a>Zapisywanie reguł stylu tekstu pomocy

- Nie objaśniono oczywiste. O ile nie jest bezwzględnie konieczne, nie zawierają tekst.

- Tekst jest zawsze umieszczane w górnej części okna dialogowego i powinni zapoznać się z zadanie wykonywane.

- Dokładnie Wyjaśnij użytkownikom, których potrzebują do wykonania. Unikaj nadmiernego komunikacji i nadmiarowość.

- Przejrzyj każde okno i wyeliminować zduplikowane wyrazy i instrukcji.

- Należy zachować krótki tekst. Jeśli takie informacje są niezbędne dla niektórych użytkowników lub scenariuszy, następnie podaj link do szczegółowych tematu pojęciowego online.

- Wpisz tekst, tak aby każdy wyraz przechowuje wagi i jest konieczne.

- Postępuj zgodnie z istniejących wskazówki firmy Microsoft dotyczące [tekst interfejsu użytkownika](/windows/desktop/uxguide/text-ui) i [styl i ton](/windows/desktop/uxguide/text-style-tone).

#### <a name="supplemental-instructions"></a>Dodatkowe instrukcje
 Dodatkowe instrukcje zawierają dodatkowe informacje, który pomaga użytkownikom zrozumieć kontrolek i kontrolować grupowania. Może to również obejmować niezbędne do zrozumienia jakiego formatu oczekuje kontrolki wprowadzania tekstu wskazówki. Dodatkowe instrukcje należy używać oszczędnie. Zarezerwować je dla przypadków, kiedy istnieje prawdopodobieństwo, że użytkownik nie będzie w pełni zrozumieć zagadnienia, wyboru, które wykorzystują one.

 ![Uzupełniające tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")

 **Uzupełniające tekstu w programie Visual Studio**

 ![Uzupełniające tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")

 **Uzupełniające tekstu w programie Visual Studio**

#### <a name="infotips"></a>InfoTips
 Często instruktażowy tekst może być zbyt obszerne, aby umieścić w miejscu w interfejsie użytkownika lub mogą być przydatne tylko dla nowych użytkowników, czujesz, takich jak zaśmiecania doświadczonym użytkownikom. W tym przypadku tekst instruktażowy/informacyjny powinna zostać umieszczona jako etykietka narzędzia w ramach poradę.

 InfoTips powinna zostać umieszczona obok kontrolki są powiązane i należy używać określonych ikonę poradę, która jest dyskretny kod jeszcze widoczne.

 ![Porada w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")

 **Przykład porady w programie Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Zapisywanie reguły stylu InfoTips

- Pisanie InfoTips jako postaci kompletnych zdań. Wymagają one określonych zleceń, jak w zdaniu i kończące znaki interpunkcyjne.

- Użyj InfoTips uzupełnienie swojej głównej instrukcji lub informacji. Jeśli są po prostu użyć innych wyrazów, aby potwierdzić główne zagadnienie, nie potrzebujesz porady.

- Zachowaj InfoTips krótki słodkie. Użyj małe słówka i zwykłym tekstem, potocznym językiem, który obsługuje i zachęca do użytkownika.

- Postępuj zgodnie z istniejących wskazówki firmy Microsoft dotyczące [tekst interfejsu użytkownika](/windows/desktop/uxguide/text-ui) i [styl i ton](/windows/desktop/uxguide/text-style-tone).

#### <a name="control-labels"></a>Kontrolka etykiety
 Kontrolka etykiety powinny być krótkie i zwięzłe i postępuj zgodnie z [pulpitu Windows wskazówki dotyczące formantów](/windows/desktop/uxguide/controls).

 Aby uzyskać więcej informacji na temat format etykiety kontroli i umieszczanie w Interfejsie dotyczą [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Linki pomocy
 Linki pomocy albo można umieścić w ramach tekst lub w treści interfejsu użytkownika. Można je łącza do tematów pomocy lub uruchamianie wewnętrznego okien dialogowych.

##### <a name="visual-style-rules-for-help-links"></a>Reguły stylu wizualnego łącza pomocy

- Użyj kolorów odpowiednie środowisko dla hiperlinków. Poprawnie ze stylem hiperłącze nie zostaną krótko flash czerwony po kliknięciu. Jeśli tak się dzieje, to wskazanie, że kolory środowiska nie jest używane.

- Podkreślenia powinna służyć wyłącznie po wskazaniu wskaźnikiem lub gdy łącze jest osadzony w akapicie.

- Aby uzyskać bardziej szczegółowe informacje o style wizualizacji i interakcji dla hiperlinków Zobacz przycisków i hiperłączy.

##### <a name="writing-style-rules-for-help-links"></a>Zapisywanie reguły stylów dla łącza pomocy

- Podczas uruchamiania okien dialogowych, obsługa standardów wielokropek: nie wielokropka dla nawigacji, a wielokropek, jeśli zadanie wymaga dodatkowego interfejsu użytkownika.

     ![Link pomoc w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")

     **Wielokropek (...) w linku pomocy wskazuje, że zadanie będzie wymagać dodatkowego interfejsu użytkownika.**

- Linki nie może rozpoczynać "Dowiedz się więcej", ponieważ nie jest celem użytkownika. Użytkownik chce, aby uzyskać odpowiedzi na określone pytanie, odbiera edukacji ogólne.

- Pomoc frazy łączy tak, aby ich zadać sobie pytanie odpowiedzą tematu.

     Niepoprawne:    "Dowiedz się więcej na temat cen usług Windows Azure Mobile Services"

     Popraw:    "Jakie opcje cenowe są dostępne dla systemu Windows Azure Mobile Services?"

- Nigdy nie używaj *kliknij...*  w tekście linku.

- Link nigdy nie tylko słowo "tutaj". Jest to problemy w przypadku czytniki ekranu, które będzie głosu hiperłącza słowo.

     Niepoprawne:    "Informacje dotyczące systemu Windows Azure Mobile Services **tutaj**"

     Popraw:    "Jakie opcje cenowe są dostępne dla systemu Windows Azure Mobile Services?"

- Aby uzyskać więcej informacji na styl pisania poprawne linki pomocy zobacz [wskazówki Windows Desktop, aby uzyskać Pomoc](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Tekst wskazówki
 Wskazówka tekst jest wyświetlany jako znak wodny w formancie lub pod formantem. Prawidłowe formatowanie, zostaną zastosowane przy użyciu odpowiedniego tokenu VSColors `Environment.GrayText`.

 Może się pojawić w wielu formach.

- Zamiast etykieta kontrolki:

     ![Podpowiedzi tekstowe w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")

- Z czasownikiem ze wskazówkami:

     ![Podpowiedzi tekstowe w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")

- Tekst zawierający wymaganego wpisu:

     ![Podpowiedzi tekstowe w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")

#### <a name="watermark-text"></a>Tekst znaku wodnego
 Na powierzchni projektowej pusty tekst powinny wskazywać, co należy zrobić, a także zapewniają linki, aby otworzyć inne powiązane okna, jeśli jest to odpowiednie:

 ![Znak wodny tekstu w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")

 **Przykład tekstu znaku wodnego w programie Visual Studio**

### <a name="common-terminology"></a>Wspólna terminologia

|Termin|Wyjaśnienie|Komentarz|
|----------|-----------------|-------------|
|Zaloguj się / zaloguj|Czasowniki do reprezentowania uwierzytelniania do właściwości sieci web, a następnie używać synonimów z sieci web. W ramach klientów ten jeden raz jako używamy pojęcie najwyższego poziomu do podpisywania i połączenie użytkownika IDE, które reprezentuje najwyższego poziomu tożsamości, która zapewnia możliwości wyższego poziomu, takie jak roaming i licencjonowania, które nie są dostępne w innych połączeń.|Użytkownika IDE jest jedyną funkcją powinny reprezentować logowania / Wyloguj zlecenie, ponieważ reprezentuje on użytkownika najwyższego poziomu środowiska IDE.|
|Łączenie / rozłączanie|Użyj w miejscach, w którym funkcja zajmuje pojedynczego połączenia usługi online.|Eksplorator serwera, gdzie może mieć tylko jedno aktywne połączenie platformy Azure w danym momencie, jest przykładem łączenia/rozłączania.|
|Dodawanie lub usuwanie|Bez operacji. Opcja używana podczas dodawania lub usuwania elementu z listy.|Okno dialogowe listy serwera TFS Menedżera połączeń jest przykładem Dodaj/Usuń.|
|Usuwanie|Destrukcyjne. Użyj tylko wtedy, gdy element usuwany, zostaną trwale odrzucone lub usunięte z dysku.|Ogólnie "Delete" wymaga monitu, jeśli wynik jest usunięcie pliku z dysku.|

## <a name="error-messages"></a>Komunikaty o błędach

### <a name="overview"></a>Omówienie
 Błędy występować. Ustawianie ograniczeń co użytkownik może zrobić to rozsądne, pierwszym krokiem w celu zapobiegania komunikaty o błędach zapobiegających. Jednak po wystąpieniu błędu, komunikat o błędzie dobrze napisane przejść długą drogę w łagodzenia problem. Komunikaty o błędach są prawdopodobnie jednym z najważniejszych typów powiadomień, widziany przez użytkownika, ponieważ są synchroniczne i wskazują na problem, który ma zostać rozwiązany. Komunikaty o błędach źle sprawić, że użytkownicy na ich do określania przyczyny błędów i wszelkie możliwe rozwiązania.

 Użytkownicy mogą przestać, zwracając uwagę nadmiernie obciążany lub mylące komunikaty o błędach, więc wystąpić zapisu wiadomości tylko niezbędne dodające wartość do użytkownika. Jeśli komunikat jest po prostu powiadomienie, użyj alternatywny sposób prezentacji.

### <a name="rules-for-creating-an-error-message"></a>Zasady tworzenia komunikat o błędzie

- Podczas tworzenia komunikatów o błędach, należy wybrać poziom odpowiedni komunikat o błędzie dla odbiorców. Staraj się dla prostego podsumowań, które zapewniają akcję, którą użytkownik może robić, jeśli ma to zastosowanie. Wszystko, co użytkownik nie musi wiedzieć, nie stanu.

- Zapewnianie pomocy konstruktywnych informacji. Jest łatwiej odczytywać i zajmującym się komunikat o błędzie, który zawiera instrukcję.

- Nie używaj negatywów podwójnej precyzji.

- Wykonywać zarówno zautomatyzowane i ręczne gramatykę i pisownię sprawdzić wszelkie komunikaty o błędach, które piszesz.

- Komunikaty o błędach złożonych należy unikać sekwencyjne komunikacji. Nigdy nie używaj zaczep F1 komunikatu o błędzie. Samej wiadomości powinny być wystarczające.

- Użyj ikony jest poprawna.

- Ułatw pytania do zrozumienia i użycia przycisków, które są wyczyść opcje, takie jak "Delete" i "Anuluj".

- W przypadku ostrzeżenia być jasno konsekwencją postępowania, jaka będzie. Przyciski powinny wskazywać jego konsekwencję.

- Błędy Opisz, co użytkownik może zrobić, aby rozwiązać ten problem. Przyciski powinny być akcji lub powiedzieć "Zamknij". Nie używaj przycisku "OK", komunikat o błędzie.

- Kilka pytań, które Zadaj sobie pytanie, podczas tworzenia komunikatu o błędzie:

    - Jak rozwiązać problem z tym błędem samodzielnie określić użytkownika?

    - Użytkownik używa tego samego słownictwa jako błąd?

    - Jest to błąd ambigious lub udostępnione w wielu sytuacjach? Jeśli tak, jak możesz prowadzą użytkowników do rozwiązania, które są im potrzebne?

#### <a name="build-errors"></a>Błędy kompilacji
 Ponieważ program Visual Studio jest narzędziem do projektowania oprogramowania, wiele z jego składników ma kompilacji, konwertowania lub kodowanie krok, aby przekonwertować pracy dewelopera do postaci binarnej. Takiej konwersji może powodować błędy, gdy kompilator nie może przetworzyć nieprawidłowo utworzone pliki lub opcje kompilatora nie zostały prawidłowo ustawione.

 Visual Studio użytkownicy mogą poświęcać olbrzymią liczbę godzin rozwoju Rozwiązywanie błędów kompilacji. Ten czas rozpoznawania nazw zwiększa się po błędy mają zależności lub gdy komunikaty o błędach zostały źle napisane, które mogą utrudnić odkryć przyczynę błędu.

 Najważniejsze błędy kompilacji są te, które nie występują w pierwszym miejscu, co jest dlaczego Visual Studio zapewnia automatycznego uzupełniania, a zygzaki funkcji IntelliSense. Moduły weryfikacji schematu i podobne narzędzia udostępniają ten sam rodzaj opinii. Te mechanizmy aktywnie prowadzą użytkownika do konstruowania sformułowany kod, zmniejszenie ryzyko wystąpienia błędów kompilacji.

 Program Visual Studio udostępnia okna narzędzi, gdzie użytkownicy może odczytywać i nawigowanie po błędów, które wystąpiły podczas ich okna dokumentu. Skróty klawiaturowe są udostępniane, aby użytkownik może szybko przejść duże ilości kodu i przejdź bezpośrednio do lokalizacji problemu. Program Visual Studio umożliwia również każdy błąd kompilacji ograniczeni do określonego Identyfikatora — słowo kluczowe/kontekstu pomocy, aby użytkownik może przejść bezpośrednio do tematu pomocy, który zapewnia bardziej szczegółowe informacje o błędzie.

 Błędy kompilacji jest to zrozumiałe i zwięzłe zapisu:

- **Użyj prostego języka** tłumaczy to problem z niewielkiego lub żadnego żargonu kompilatora. Tekst błędu kompilacji nie może być nadmiernie Technical Preview.

- **Opisano możliwe przyczyny.** Na przykład "Brak dwukropka pomiędzy właściwością, a wartość" (właściwość): (wartość) "deklaracji."

- Zawierają szczegółowe informacje o potencjalne rozwiązania. Jeśli nie jest wystarczająco dużo miejsca, dodatkowe informacje mogą być wprowadzane do odpowiedniego tematu Pomocy.

### <a name="components-of-a-well-written-error-message"></a>Składniki dobrze napisane komunikat

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Usługa powłoki okna dialogowego komunikaty o błędach.
 Za pomocą usługi powłoki okno dialogowe pozwala sterować wyglądem komunikatu czcionek, w szczególności bez poważne zmiany w poszczególnych elementów. Użyj **IErrorInfo** mechanizmów i zgłosi je przy użyciu **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wybierz z prezentacji skuteczne i odpowiednie powiadomienie.
 Za pomocą modalne okno dialogowe krytyczne ostrzeżenie razie natychmiastowych akcji w celu uniknięcia utraty danych (synchronicznego powiadomienia). Krytyczne ikony są zarezerwowane dla sytuacji, w których zamykanie wiadomość bez odczytu może prowadzić do negatywne skutki. Utrata danych jest krytyczna sytuację, która wymaga odpowiedzi poziom alarmu. Ikona stanu krytycznego nadmiernemu zużyciu desensitizes użytkownikom na ich znaczenie. Jeśli komunikat o błędzie jest charakter informacyjny, należy wziąć pod uwagę alternatywy dla modalnego okna dialogowego (asynchronicznego powiadomienia).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Dostarcza zawsze przejrzyste i zwięzłą wyjaśnienie przyczynę wystąpienia problemu zamiast wyjaśnienia techniczne.
 Nadmiernego obciążania użytkowników za pomocą szczegóły techniczne w wyjaśnienie spowoduje, że ich bardziej prawdopodobne zignorować komunikaty o błędach. Przykłady dobre wiadomości:

- "Nie można otworzyć żądanego pliku."

- "Nie można połączyć się z Internetem."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Podaj informacje o tym, jak rozwiązać problem.
 Oferuj sugestii użytkowników, jak rozwiązać ten problem. Przyznaj się z użytkownikiem w przypadku brak sugestii. Zawierają bezpośrednie linki do innych źródeł online, takich jak pomoc techniczna i pomoc techniczna w społeczności. Spróbuj umożliwienie do określonych informacji online dotyczących problemu. Identyfikator błędu należy wziąć pod uwagę oznaczając użytkowników do wątków dyskusji dotyczących tego błędu. Przykłady dobre wiadomości:

- "Upewnij się, że połączenie z Internetem, a następnie spróbuj wykonać tę operację ponownie."

- "Upewnij się, że plik istnieje i czy masz uprawnienia, aby go otworzyć."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Wpisz komunikat, który jest krótki, a także punkt.
 Komunikat o błędzie może generować powiadomienia, wyjaśnić i oferuje rozwiązanie ale nadal można zignorować, jeśli jest zbyt oddechu. Jednym rozwiązaniem jest stopniowego ujawniania za pomocą przycisku Szczegóły. Na przykład podać krótki opis/rozwiązania, a następnie umieść szczegółowe informacje w obszarze przycisk Szczegóły. Jeśli użytkownik wybierze uzyskać więcej informacji na temat błędu, mogą to zrobić.

 Język wiadomości powinny być następujące:

- **Odpowiedniej domeny.** Użyj języka, w którym będzie zrozumiałe dla użytkownika. Mimo, że deweloperzy znajdują się w naszych klientów, często nie muszą oni kontekstu i terminologię, z którą mamy.

- **Określone.** Należy unikać niejasne Treść oraz podać konkretne nazwy i lokalizacje obiektów, które są zaangażowani. Na przykład komunikat o błędzie, takie jak "jest nieprawidłowy znak" nie jest przydatne. Znak, który? "Nie znaleziono pliku." Plik, który?

- **Uprzejmy.** Nie blame użytkownika lub stały się, że stupid. Należy unikać szkodliwy lub obraźliwy język (kill, wykonywanie, przerwać krytyczny, nielegalnych). Należy unikać wielkie tekst, który jest często postrzegana jako shouting, a nie jako do odczytu. Nie używaj humor.

- **Popraw.** Użyj błędu pisowni i gramatyki (nawet w przypadku parametrami wymaganymi). Błędy pisowni to nieprofesjonalnie i Zakłopotanie.

- **Kontekstowe właściwe.** Użyj przycisku odpowiedni tekst. Należy unikać przycisk "OK" — zamiast tego użyj "Kontynuuj" lub "Yes/No."

### <a name="error-message-examples"></a>Przykłady komunikat o błędzie

|dobre|Zły|
|----------|---------|
|"Numer wybrany użytkownik nie jest już w usłudze. Sprawdź numer i spróbuj ponownie lub wybierz numer 0 dla operatora."|-"Błąd (449): Niedozwolona liczba"<br />-"Ten błąd nieobsługiwanego wyjątku wskazuje, że operacja została ukończona pomyślnie."<br /><br /> ![Komunikat o błędzie zły w programie Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|

## <a name="accessing-help"></a>Uzyskiwanie dostępu do pomocy

### <a name="overview"></a>Omówienie
 Oprócz dokumentacji w witrynie MSDN użytkownikiem programu Visual Studio ma kilka punktów dostępu do pomocy użytkownika znajduje się w interfejsie użytkownika. Aby upewnić się, że stale dostępne są te punkty dostępu, zespoły funkcji muszą korzystać z zalet systemu pomocy oferowane przez środowisko. Te punkty dostępu są:

- **Instruktażowe i uzupełniające tekst w oknach dialogowych.** Statyczny tekst, który zapewnia kierunku lub wyjaśnienie, albo w interfejsie użytkownika, powierzchni lub będą dostępne po przesunięciu myszy na ikonie porada.

- **F1 Pomoc** (tylko w edytorze). W edytorze programu Visual Studio użytkownika mogą ufać, że w dowolnym momencie, naciskając klawisz F1 zostanie wyświetlone okno tematu pomocy, specyficzne dla bieżącego zaznaczenia. Upewnij się, że zagadnień związanych z F1 są właściwe i zawierającego wiele użytecznych informacji.

- **Hiperlinki do tematów Pomocy.** Hiperłącze w obrębie okna dialogowego, okno narzędzia lub powierzchni projektu, który uruchamia tematu, aby ułatwić użytkownikowi więcej informacji na temat technologii, funkcji lub informacji o sposobie wykonania zadania.

- **Mechanizmy interfejsu użytkownika pomocnika, takich jak tagi inteligentne i tworzenie okien dialogowych.** Te mechanizmy pomóc użytkownikowi zrozumieć elementu interfejsu użytkownika lub ułatwienia zadania, takie jak tagi inteligentne lub konstruktora w oknach dialogowych.

- **Przyciski pomocy interfejsu użytkownika** (przestarzałe). Widoczny wskaźnik na pasku tytułu, który zapewnia dostęp do powiązanych tematów pomocy F1.

### <a name="text"></a>Tekst

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Instruktażowe i uzupełniające tekst w oknach dialogowych
 W oknach dialogowych, które obsługują złożonych zadań może być, aby nadać tekst w interfejsie użytkownika, często w górnej części okna dialogowego lub w pobliżu złożonych kontrolek. Zobacz [interfejsu użytkownika tekstu i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) szczegółowe informacje dotyczące stylu pisania.

#### <a name="infotips"></a>InfoTips
 Często tekst może być zbyt obszerne, aby umieścić w miejscu w interfejsie użytkownika lub mogą być przydatne tylko dla nowych użytkowników, czujesz, takich jak zaśmiecania doświadczonym użytkownikom. W tym przypadku tekst instruktażowy/informacyjny powinna zostać umieszczona jako etykietka narzędzia w ramach poradę.

 InfoTips powinna zostać umieszczona obok kontrolki są powiązane i należy używać określonych ikonę poradę, która jest dyskretny kod jeszcze widoczne.

 ![Porada w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")

 **Przykład porady w programie Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktywne mechanizmów pomocy

#### <a name="f1-help"></a>Pomoc F1
 Wymagana jest pomocy F1 w edytorze lub powierzchni projektowej, ale nie w innych miejscach w środowisku Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hiperlinki do tematów pomocy
 Hiperlinki może służyć do wykonywania akcji, nawigowanie w IDE lub uruchom Pomoc w przeglądarce. Zobacz [interfejsu użytkownika tekstu i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) szczegółowe informacje na temat języka i 07.10.01 przycisków i hiperłączy w wizualizacji i układów.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pomoc [?] przycisków w paski tytułu okna dialogowego (przestarzałe)
 W większości przypadków przyciski pomocy [?], na pasku tytułu okna dialogowe są przestarzałe. Tematy interfejsu użytkownika nie są już częścią modelu naszej dokumentacji, a w związku z tym nie może być odpowiedni temat się połączyć. Zasadniczo przycisk paska tytułu został tak samo jak F1 Pomoc i który nie jest już wymagany w oknach dialogowych. W niektórych przypadkach to nadal można jako wskaźnika dostępne jest więcej informacji o pojęciach i procedurach Chociaż hiperłącza częściej są używane w nowszej interfejsu użytkownika.

##### <a name="dialogs-created-through-the-environment"></a>Okna dialogowe utworzonymi za pomocą środowiska
 Wiele okien dialogowych powłoki są tworzone za pomocą **VBDialogBoxParam** funkcji. Ta funkcja udostępniony został zaktualizowany ułatwiają przenoszenie **pomocy** przycisk z poziomu okna dialogowego, aby **?** przycisk przy zachowaniu architektury, która jest ze starszymi wersjami zgodne i rozszerzalny.

 W szczególności **VBDialogBoxParam** funkcja analizuje szablonu okna dialogowego dla przycisku, którego identyfikator **IDHELP** (9) lub etykieta **pomocy** lub **& Pomoc**. Jeśli przycisk pomocy zostanie znaleziona, jest on ukryty i **WS_EX_CONTEXTHELP** stylu jest dodawany do okna dialogowego, który umieszcza **?** przycisk na pasku tytułu okna dialogowego.

 Podczas tworzenia okna dialogowego wypycha proc okna dialogowego na stosie i wywołuje okno dialogowe z przetwarzania wstępnego proc okna dialogowego o nazwie **DialogPreProc**. Gdy **?** kliknięto przycisk wysyła **WM_SYSCOMMAND** z **SC_CONTEXTHELP** do okna dialogowego. **DialogPreProc** przechwytuje tego polecenia i zmienia ją do **WM_HELP** komunikat, który jest przekazywany do oryginalnego pola dialogowe proc.

 Większość okien dialogowych, które są tworzone w środowisku mają przycisk Pomoc w oknie dialogowym. Po wyświetleniu okna dialogowego przycisk Pomoc jest automatyczne ukrywane pod **?** przycisk działa. Jeśli **?** przycisk nigdy nie jest usunięte lub zmienione w Windows, dzięki temu rozwiązaniu można szybko przenieść z powrotem do oryginalnego przyciski pomocy.

 To rozwiązanie zapewnia cztery założenia, które mogłyby spowodować usterki:

- Przycisk Pomoc w oknie dialogowym jest **IDHELP** (9).

- Okno dialogowe wydaje się prawidłowe, gdy przycisk Pomoc jest ukryty.

- Okno dialogowe nie zastąpić jej winproc.

- Okno dialogowe nie jest osadzone wewnątrz innego okna dialogowego.

  Jeśli znajduje się w obrębie msenv okna dialogowego, a nie korzysta z **VBDialogBoxParam**, Zbadaj, wykorzystując **VBDialogBoxParam** przed wdrożeniem własnego programu obsługi.

##### <a name="dialogs-created-through-other-packages"></a>Okna dialogowe utworzonych za pomocą innych pakietów
 Można zaimplementować rozwiązania w oknach dialogowych, które znajdują się poza msenv. Klasy okien dialogowych udostępnione w Twojej pakietu VSPackage rozważ Przenoszenie przycisku paska tytułu lub wykonawcze programu obsługi dla każdego okna dialogowego. Następujący kod to szkielet tego wdrożenia, aby pomóc Ci rozpocząć pracę:

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

##### <a name="help-buttons-in-managed-code"></a>Przyciski pomocy w kodzie zarządzanym
 Zastępowanie zachowania domyślnego przycisk pomocy pasek tytułu okna jest łatwa w kodzie zarządzanym. Poniżej przedstawiono aplikację pełną wersję demonstracyjną, która przedstawia tego zachowania. W zasadzie musisz przesłonić formularza **WndProc** metody i następnie fire wyłączanie pomocy F1 żądań, kiedy **SC_CONTEXTHELP** wiadomość zostanie przechwycona.

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