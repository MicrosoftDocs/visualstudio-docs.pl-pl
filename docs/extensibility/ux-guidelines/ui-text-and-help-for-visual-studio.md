---
title: Tekst interfejsu użytkownika i pomoc dla programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3247aeaa702b59722471c7d28e98957f04f3e07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698297"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Tekst interfejsu użytkownika i pomoc dla programu Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Tekst i terminologia interfejsu użytkownika
 Zrozumiały tekst jest decydujący dla efektywnego interfejsu użytkownika. Użytkownicy oprogramowania mają najpierw odczytywać etykiety, a mianowicie te, które są najbardziej istotne do ukończenia zadania. Tekst statyczny jest odczytywany z mniejszą częstotliwością. Zaplanuj użytkownikom możliwość uruchamiania ich sesji pracy przy użyciu szybkiego skanowania całego okna, a następnie odczytu interfejsu użytkownika w tej przybliżonej kolejności:

1. Formanty interaktywne w środku

2. Przyciski zatwierdzania

3. Formanty interaktywne znalazły się w innym miejscu

4. Główne instrukcje

5. Wyjaśnienia uzupełniające

6. Tytuł okna

7. Inny tekst statyczny w treści głównej

### <a name="usage-patterns-for-ui-text"></a>Wzorce użycia dla tekstu interfejsu użytkownika

#### <a name="title-bar-text"></a>Tekst paska tytułu
 Tekst paska tytułu musi być zgodny z poleceniem, które zostało zduplikowane w interfejsie użytkownika.

#### <a name="instructional-text-helper-text"></a>Tekst instruktażowy (tekst pomocnika)
 W niektórych oknach dialogowych warto przedstawić widoczne główne instrukcje wyjaśniające, co należy zrobić w oknie lub na stronie. Jest to czasami określane jako "tekst pomocnika".

##### <a name="writing-style-rules-for-helper-text"></a>Pisanie reguł stylu dla tekstu pomocnika

- Nie Wyjaśnij oczywiste. O ile nie jest to absolutnie konieczne, nie należy uwzględniać tekstu instruktażowego.

- Tekst instruktażowy jest zawsze umieszczony u góry okna dialogowego i powinien odnosić się do wykonywanego zadania.

- Dokładnie Wyjaśnij użytkownikom, czego potrzebują. Unikaj nadmiernej komunikacji i nadmiarowości.

- Przejrzyj wszystkie okna i eliminowanie zduplikowanych słów i instrukcji.

- Przechowuj tekst instruktażowy jako krótki. Jeśli niektóre użytkownicy lub scenariusze są niezbędne do uzyskania dodatkowych informacji, podaj link do szczegółowego tematu w trybie online.

- Napisz tekst tak, aby każdy wyraz miał wagę i jest wymagany.

- Postępuj zgodnie z istniejącymi wskazówkami firmy Microsoft dotyczącymi tekstu i [stylu i dźwięku](/windows/desktop/uxguide/text-style-tone) [interfejsu użytkownika](/windows/desktop/uxguide/text-ui) .

#### <a name="supplemental-instructions"></a>Instrukcje uzupełniające
 Instrukcje uzupełniające zawierają dodatkowe informacje, które ułatwiają użytkownikowi zrozumienie formantów lub grup kontroli. Może to również obejmować tekst wskazówki, który jest niezbędny do zrozumienia formatu, który jest oczekiwany przez kontrolkę wejściową. Korzystaj z dodatkowych instrukcji. Zarezerwuj je w przypadkach, gdy użytkownik jest w stanie w pełni zrozumieć konsekwencje wyboru przez nie.

 ![Tekst uzupełniający w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 — b_SupplementalText1")

 **Tekst uzupełniający w programie Visual Studio**

 ![Tekst uzupełniający w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 — c_SupplementalText2")

 **Tekst uzupełniający w programie Visual Studio**

#### <a name="infotips"></a>InfoTips
 Często tekst instrukcji może być zbyt długi, aby można było pomieścić miejsce w interfejsie użytkownika lub może być przydatny tylko dla nowych użytkowników, mało więcej, tak jak bałagane dla doświadczonych użytkowników. W takim przypadku tekst instruktażowy/informacyjny powinien zostać umieszczony jako etykietka narzędzia w obszarze porady.

 InfoTips powinny być umieszczone blisko formantów, z którymi są one powiązane, i powinny korzystać z określonej ikony porady, która nie jest jeszcze zauważalna.

 ![Porada w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 — d_InfoTip")

 **Przykład porady w programie Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Pisanie reguł stylu dla InfoTips

- Napisz InfoTips jako kompletne zdania. Wymagają one określonych czasowników, przypadku zdania i końcowej interpunkcji.

- Użyj InfoTips, aby uzupełnić główną instrukcję lub informacje. Jeśli tylko używasz innych słów do przestanania głównego pomysłu, nie potrzebujesz porady.

- Zachowaj InfoTips krótkie i słodkie. Używaj małych słów i zwykłych, codziennych języków, które obsługują i zachęca użytkownika.

- Postępuj zgodnie z istniejącymi wskazówkami firmy Microsoft dotyczącymi tekstu i [stylu i dźwięku](/windows/desktop/uxguide/text-style-tone) [interfejsu użytkownika](/windows/desktop/uxguide/text-ui) .

#### <a name="control-labels"></a>Etykiety kontrolki
 Etykiety kontrolki powinny być krótkie, zwięzłe i zgodne ze [wskazówkami dotyczącymi pulpitu systemu Windows](/windows/desktop/uxguide/controls).

 Aby uzyskać więcej informacji na temat formatowania i położenia etykiet kontrolek w interfejsie użytkownika, zobacz [układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Linki pomocy
 Linki pomocy można umieścić w tekście instrukcji lub w treści interfejsu użytkownika. Mogą to być linki do pomocy lub uruchamiania wewnętrznych okien dialogowych.

##### <a name="visual-style-rules-for-help-links"></a>Reguły stylu wizualnego dla linków pomocy

- Użyj poprawnych kolorów środowiska dla hiperłączy. W przypadku kliknięcia prawidłowo oznaczonego stylem hiperłącze nie będzie miało na chwilę lampę błyskową. Jeśli widzisz to, oznacza to, że kolory środowiska nie są używane.

- Podkreślenia powinny być używane tylko po aktywowaniu lub po osadzeniu łącza w akapicie.

- Aby uzyskać bardziej szczegółowe informacje na temat stylów wizualizacji i interakcji dla hiperłączy, zobacz przyciski i hiperlinki.

##### <a name="writing-style-rules-for-help-links"></a>Pisanie reguł stylu dla linków pomocy

- W przypadku uruchamiania okien dialogowych należy zachować standardy dla wielokropka: brak wielokropek dla nawigacji, elipsy, jeśli zadanie wymaga dodatkowego interfejsu użytkownika.

     ![Link pomocy w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 — e_HelpLink")

     **Wielokropek (...) w linku pomocy wskazuje, że zadanie będzie wymagało dodatkowego interfejsu użytkownika.**

- Linki nie powinny rozpoczynać się od "uczenia się", ponieważ nie jest to intencja użytkownika. Użytkownik chce odpowiedzieć na określone pytanie, nie otrzymuje ogólnego wykształcenia.

- Linki pomocy frazy, dzięki czemu zwracają pytania dotyczące odpowiedzi w temacie.

     Nieprawidłowe: "Dowiedz się więcej na temat cennika usługi Windows Azure Mobile Services"

     Poprawne: "Jakie opcje cenowe są dostępne dla systemu Windows Azure Mobile Services?".

- Nigdy nie używaj *przycisku...* do tekstu łącza.

- Nigdy nie łącz tylko tego słowa "tutaj". Jest to problematyczne w przypadku niektórych czytników ekranu, które będą głosować tylko w przypadku wyrazów z hiperłączem.

     Nieprawidłowe: "Znajdź informacje o platformie Microsoft Azure Mobile Services **tutaj**"

     Poprawne: "Jakie opcje cenowe są dostępne dla systemu Windows Azure Mobile Services?".

- Aby uzyskać więcej informacji na temat poprawnego stylu pisania dla linków pomocy, zobacz [wskazówki dotyczące pulpitu systemu Windows](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Tekst wskazówki
 Tekst wskazówki pojawia się jako znak wodny wewnątrz kontrolki lub pod kontrolką. Poprawne formatowanie zostanie zastosowane przy użyciu odpowiedniego tokenu VSColors `Environment.GrayText` .

 Może być wyświetlana w kilku formularzach.

- Zamiast etykiety kontrolki:

     ![Tekst wskazówki w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 — f_HintText1")

- Z czasownikiem, podając instrukcje:

     ![Tekst wskazówki w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 — g_HintText2")

- Z tekstem wskazującym wymagany wpis:

     ![Tekst wskazówki w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 — h_HintText3")

#### <a name="watermark-text"></a>Tekst znaku wodnego
 Na pustej powierzchni projektowej tekst powinien wskazywać, co należy zrobić, a także udostępniać linki do otwierania innych powiązanych okien, jeśli jest to konieczne:

 ![Tekst znaku wodnego w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 — i_WatermarkText")

 **Przykład tekstu wodnego w programie Visual Studio**

### <a name="common-terminology"></a>Powszechna terminologia

|Okres|Wyjaśnienie|Komentarz|
|----------|-----------------|-------------|
|Logowanie/wylogowywanie|Czasowniki użyły synonimu w sieci Web do reprezentowania uwierzytelniania we właściwości sieci Web. W ramach klientów używamy tego raz jako koncepcji najwyższego poziomu do logowania się i z połączenia użytkownika IDE, które reprezentuje tożsamość najwyższego poziomu, która zapewnia funkcje wyższego poziomu, takie jak roaming i Licencjonowanie, które nie są dostępne ze wszystkimi innymi połączeniami.|Użytkownik IDE jest jedyną funkcją, która powinna reprezentować czasownik logowania/wylogowywania, ponieważ reprezentuje użytkownika IDE najwyższego poziomu.|
|Połącz/Rozłącz|Użyj w miejscach, w których funkcja utrzymuje pojedyncze połączenie z usługą online.|Eksplorator serwera, w którym można mieć tylko jedno aktywne połączenie platformy Azure, to przykład połączenia/rozłączenia.|
|Dodaj/Usuń|Nieniszczące. Używany podczas dodawania lub usuwania elementu z listy.|W oknie dialogowym Lista serwerów Menedżera połączeń TFS jest przykładem dodawania/usuwania.|
|Usuń|Destrukcyj. Używane tylko wtedy, gdy usuwany element zostanie trwale odrzucony lub usunięty z dysku.|"Usuń" zwykle wymaga monitu, jeśli wynikiem jest usunięcie pliku z dysku.|

## <a name="error-messages"></a>Komunikaty o błędach

### <a name="overview"></a>Omówienie
 Występują błędy. Ustawienie ograniczeń dotyczących tego, co użytkownik może zrobić, to rozsądny pierwszy krok w zapobieganiu unikaniu komunikatów o błędach. Jednak w przypadku wystąpienia błędu dobrze zapisany komunikat o błędzie może być długi w kierunku zmniejszenia problemu. Komunikaty o błędach są raczej jednym z najważniejszych typów powiadomień, które widzi użytkownik, ponieważ są synchroniczne i wskazują problem, który należy rozwiązać. Komunikaty o błędach zostały zapisywane przez użytkowników w celu określenia przyczyn błędów i ewentualnych rozwiązań.

 Użytkownicy mogą zrezygnować z uwagi na nadużywane lub mylące komunikaty o błędach, dlatego należy zapisywać tylko niezbędne komunikaty, które dodają wartość do środowiska użytkownika. Jeśli komunikat jest po prostu powiadomieniem, użyj alternatywnej prezentacji.

### <a name="rules-for-creating-an-error-message"></a>Reguły tworzenia komunikatu o błędzie

- Podczas konstruowania komunikatów o błędach wybierz odpowiedni poziom błędów dla odbiorców. Zapoznaj się z prostymi podsumowaniami, które zapewniają akcję, którą użytkownik może podjąć, jeśli ma to zastosowanie. Nie należy wprowadzać żadnych informacji o tym, że użytkownik nie musi wiedzieć.

- Zapewnij konstruktywną pomoc. Jest to łatwiejsze do odczytania i działania na komunikat o błędzie zawierający instrukcje.

- Nie używaj podwójnych wartości ujemnych.

- Wykonaj zarówno automatyczne, jak i ręczne sprawdzanie pisowni podczas pisania.

- W przypadku złożonych komunikatów o błędach należy unikać komunikacji sekwencyjnej. Nie należy nigdy używać podłączenie F1 dla komunikatu o błędzie. Wiadomość powinna być wystarczająca.

- Użyj poprawnej ikony.

- Zapoznaj się z prostymi pytaniami i korzystaj z przycisków, które mają jasne opcje, takie jak "Usuń" i "Anuluj".

- W przypadku ostrzeżeń należy wyczyścić informacje o tym, co będzie miało skutek. Przyciski powinny wskazywać na sekwencję.

- W przypadku błędów opisz, co użytkownik może zrobić, aby rozwiązać ten problem. Przyciski powinny być akcjami lub powiedzieć "Close" (Zamknij). Nie używaj przycisku "OK", aby uzyskać komunikat o błędzie.

- Niektóre pytania, które należy zadać sobie podczas konstruowania komunikatu o błędzie:

  - Czy użytkownik może ustalić, jak rozwiązać problem z tym błędem?

  - Czy użytkownik używa tego samego słownika co ten błąd?

  - Czy ten błąd ambigious czy jest udostępniany w wielu sytuacjach? Jeśli tak, jak poprowadzisz użytkowników do rozwiązania, których potrzebują?

#### <a name="build-errors"></a>Błędy kompilacji
 Ponieważ program Visual Studio jest narzędziem do tworzenia oprogramowania, wiele z jego składników zawiera kompilację, konwertowanie lub krok kodowania w celu przekonwertowania pracy dewelopera na postać binarną. Te konwersje mogą spowodować błędy, gdy kompilator nie może przetwarzać nieprawidłowo utworzonych plików lub gdy opcje kompilatora nie zostały prawidłowo ustawione.

 Użytkownicy programu Visual Studio mogą poświęcać olbrzymią liczbę godzin deweloperskich, rozwiązując błędy kompilacji. Ten czas rozpoznawania zwiększa się, gdy błędy mają zależności lub gdy komunikaty o błędach są źle zapisywane, co może utrudnić odzyskanie źródła błędu.

 Najlepsze błędy kompilacji to te, które nie występują w pierwszym miejscu, co oznacza, że program Visual Studio udostępnia Autouzupełnianie i funkcję IntelliSense. Moduły sprawdzania poprawności schematu i podobne narzędzia zapewniają ten sam rodzaj informacji zwrotnych. Te mechanizmy aktywnie przeprowadzą użytkownika do skonstruowania dobrze uformowanego kodu, co zmniejsza prawdopodobieństwo wystąpienia błędów kompilacji.

 Program Visual Studio udostępnia okno narzędzi, w którym użytkownicy mogą odczytywać błędy, które wystąpiły w swoich oknach dokumentów i poruszać się z nimi. Skróty klawiaturowe są dostępne, aby użytkownik mógł szybko nawigować do dużych ilości kodu i przejść bezpośrednio do lokalizacji problemu. Program Visual Studio umożliwia również każdemu błędowi kompilacji powiązana z określonym słowem kluczowym pomocy/IDENTYFIKATORem kontekstu, aby użytkownik mógł przejść bezpośrednio do tematu pomocy, który zawiera bardziej szczegółowe informacje o błędzie.

 Napisz jasne, zwięzłe błędy kompilacji:

- **Używaj zwykłego języka** , który wyjaśnia problem niewielkim lub bez żargon kompilatora. Tekst błędu kompilacji nie powinien być poza technicznym.

- **Konspekt możliwych przyczyn.** Na przykład "Brak dwukropka między właściwością i wartością w deklaracji" (Właściwość): (wartość) ".

- Podaj szczegółowe informacje o potencjalnych poprawkach. Jeśli nie ma wystarczającej ilości miejsca, dodatkowe szczegóły mogą zostać wprowadzone do odpowiedniego tematu pomocy.

### <a name="components-of-a-well-written-error-message"></a>Składniki dobrze zarejestrowanego komunikatu o błędzie

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Użyj usługi okna dialogowego powłoki dla komunikatów o błędach.
 Za pomocą usługi okna dialogowego powłoki można kontrolować wygląd wiadomości, w szczególności czcionki, bez konieczności wprowadzania istotnych zmian do poszczególnych elementów. Użyj mechanizmów **IErrorInfo** i zgłoś je za pomocą **IVsUIShell:: SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Wybierz skuteczną i odpowiednią prezentację powiadomienia.
 Użyj modalnego okna dialogowego z ostrzeżeniem krytycznym, jeśli wymagana jest natychmiastowa akcja, aby uniknąć utraty danych (powiadomienia synchronicznego). Ikony krytyczne są zarezerwowane dla sytuacji, w których zamknięcie komunikatu bez odczytywania może prowadzić do negatywnego wpływu. Utrata danych jest krytyczną sytuacją, która wymaga reakcji na poziomie alarmu. Zbyt duże użycie ikony krytycznej desensitizes użytkownikom. Jeśli komunikat o błędzie ma charakter informacyjny, należy rozważyć alternatywy dla modalnego okna dialogowego (powiadomienie asynchroniczne).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Podaj czyste, zwięzłe wyjaśnienie przyczyny wystąpienia problemu, a nie wyjaśnień technicznych.
 Przeciążanie użytkowników ze szczegółami technicznymi w wyjaśnieniu spowoduje, że będą one lepiej ignorować komunikaty o błędach. Przykłady dobrego przesyłania komunikatów:

- "Nie można otworzyć żądanego pliku".

- "Nie można nawiązać połączenia z Internetem".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Podaj informacje o sposobach rozwiązania problemu.
 Zaproponuj użytkownikowi sugestie dotyczące sposobu rozwiązania problemu. Jeśli nie ma żadnych sugestii, być uczciwym użytkownikom. Udostępniaj bezpośrednie linki do alternatywnych źródeł online, takich jak pomoc techniczna lub społeczność techniczna. Spróbuj wskazać użytkownikom konkretne informacje online dotyczące problemu. Aby uzyskać identyfikator błędu, należy rozważyć Łączenie użytkowników z wątkiem dyskusji o tym konkretnym błędzie. Przykłady dobrego przesyłania komunikatów:

- "Upewnij się, że nawiązano połączenie z Internetem, a następnie spróbuj ponownie wykonać tę operację".

- "Upewnij się, że plik istnieje i że masz uprawnienia do jego otwierania".

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Napisz komunikat, który jest krótki i do punktu.
 Komunikat o błędzie może powiadomić, wyjaśnić i zaoferować rozwiązanie, ale nadal będzie ignorowany, jeśli jest zbyt Word. Jednym z rozwiązań jest używanie ujawniania progresywnego za pomocą przycisku Szczegóły. Na przykład Podaj krótki opis/rozwiązanie, a następnie wprowadź więcej szczegółów w obszarze przycisku Szczegóły. Jeśli użytkownik zdecyduje się uzyskać więcej informacji o błędzie, może to zrobić.

 Język w komunikacie powinien:

- **Odpowiednie dla domeny.** Użyj języka, który użytkownik będzie zrozumieć. Mimo że nasi klienci to deweloperzy, często nie mają kontekstu i terminologii.

- **Specjalne.** Unikaj niejasnych wyrazów i podaj określone nazwy i lokalizacje obiektów. Na przykład komunikat o błędzie, taki jak "znak jest nieprawidłowy", nie jest użyteczny. Który znak? "Nie znaleziono pliku". Który plik?

- **Courteous.** Nie polecenia Blame użytkownika ani nie należy ich Stupid. Unikaj nieszkodliwości lub wulgarnego języka (Kill, wykonaj, Przerwij, krytyczne, niedozwolone). Unikaj wielkich liter, które często są postrzegane jako Shouting i nie są odczytywane. Nie używaj humor.

- **Odpowiedź prawidłowa.** Używaj poprawnej pisowni i gramatyki (nawet w przypadku alfa). Literówki są nieprofesjonalne i gorzej.

- **Odpowiednio odpowiednie.** Użyj odpowiedniego tekstu przycisku. Należy unikać przycisku "OK" i zamiast tego użyć "Continue" lub "yes/no".

### <a name="error-message-examples"></a>Przykłady komunikatów o błędach

|Dobrze|Zła|
|----------|---------|
|"Numer wybrany przez Ciebie nie jest już w trakcie obsługi. Sprawdź numer i ponownie nawiąż połączenie lub wybierz 0 dla operatora.|-"Błąd (449): niedozwolony numer"<br />-"Ten nieobsługiwany błąd wyjątku wskazuje, że operacja została ukończona pomyślnie".<br /><br /> ![Zły komunikat o błędzie w programie Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 — a_ErrorDialog")|

## <a name="accessing-help"></a>Uzyskiwanie dostępu do pomocy

### <a name="overview"></a>Omówienie
 Oprócz dokumentacji w witrynie MSDN użytkownik programu Visual Studio ma kilka punktów dostępu, które ułatwiają użytkownikowi pomoc w INTERFEJSie użytkownika. Aby zapewnić, że te punkty dostępu są stale dostępne, zespoły funkcji muszą korzystać z systemu pomocy oferowanego przez środowisko. Te punkty dostępu są następujące:

- **Instruktażowe i uzupełniające tekst w oknach dialogowych.** Tekst statyczny, który daje kierunek lub wyjaśnienie, na powierzchni interfejsu użytkownika lub dostępne na umieszczeniu wskaźnika myszy nad ikoną porady.

- **F1 — Pomoc** (tylko Edytor). W edytorze programu Visual Studio użytkownik może ufać, że w dowolnym momencie naciśnięcie klawisza F1 spowoduje wyświetlenie tematu pomocy specyficznego dla bieżącego zaznaczenia. Upewnij się, że tematy skojarzone z klawiszem F1 są odpowiednie i informacyjne.

- **Hiperłącza do tematów pomocy.** Hiperłącze w oknie dialogowym, oknie narzędzi lub na powierzchni projektowej, w którym jest uruchamiany temat, aby pomóc użytkownikowi w nauce dodatkowych informacji na temat technologii, możliwości lub informacji o sposobach wykonywania zadania.

- **Mechanizmy interfejsu użytkownika pomocnika, takie jak Tagi inteligentne i okna dialogowe tworzenia.** Te mechanizmy ułatwiają użytkownikowi zrozumienie elementu interfejsu użytkownika lub ułatwiają wykonywanie zadań, takich jak Tagi inteligentne lub okna dialogowe konstruktorów.

- **Przyciski pomocy interfejsu użytkownika** (przestarzałe). Widoczny wskaźnik na pasku tytułu, który zapewnia dostęp do powiązanego tematu pomocy F1.

### <a name="text"></a>Tekst

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Instruktażowe i uzupełniające tekst w oknach dialogowych
 W oknach dialogowych, które obsługują złożone zadania, może być konieczne wydawanie tekstu instruktażowego w interfejsie użytkownika, często w górnej części okna dialogowego lub blisko złożonych kontrolek. Aby uzyskać szczegółowe informacje na temat stylu pisania [, zobacz tekst i terminologia interfejsu użytkownika](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>InfoTips
 Często tekst instrukcji może być zbyt długi, aby można było pomieścić w interfejsie użytkownika lub może być przydatny tylko dla nowych użytkowników, mało więcej, jak bałagany dla doświadczonych użytkowników. W takim przypadku tekst instruktażowy/informacyjny powinien zostać umieszczony jako etykietka narzędzia w obszarze porady.

 InfoTips powinny być umieszczone blisko formantów, z którymi są one powiązane, i powinny korzystać z określonej ikony porady, która nie jest jeszcze zauważalna.

 ![Porada w programie Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 — d_InfoTip")

 **Przykład porady w programie Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktywne mechanizmy pomocy

#### <a name="f1-help"></a>Pomoc F1
 Pomoc F1 jest wymagana w edytorze lub na powierzchni projektowej, ale nie w innym miejscu w środowisku programu Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hiperlinki do tematów pomocy
 Hiperłącza mogą służyć do wykonywania akcji, nawigowania w środowisku IDE lub uruchamiania pomocy w przeglądarce. Aby uzyskać szczegółowe informacje na temat języka i przycisków 07.10.01 oraz hiperlinków dla wytycznych dotyczących wizualizacji i układu, zobacz [tekst i terminologia interfejsu użytkownika](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Przyciski pomocy [?] w paskach tytułu okna dialogowego (przestarzałe)
 W większości, przyciski pomocy [?] na pasku tytułu okien dialogowych są przestarzałe. Tematy interfejsu użytkownika nie są już częścią naszego modelu doc i dlatego mogą nie być odpowiednim tematem do powiązania. Zasadniczo przycisk paska tytułu był taki sam jak Pomoc F1 i nie jest już wymagany w oknach dialogowych. W niektórych przypadkach może być nadal używany jako wskaźnik informujący o tym, że dostępne są więcej informacji koncepcyjnych lub proceduralnych, chociaż hiperłącza są najczęściej używane w nowszych interfejsie użytkownika.

##### <a name="dialogs-created-through-the-environment"></a>Okna dialogowe utworzone za pomocą środowiska
 Wiele okien dialogowych powłoki jest tworzonych za pomocą funkcji **VBDialogBoxParam** . Ta funkcja udostępniona została zaktualizowana, aby pomóc w przenoszeniu przycisku **pomocy** z okna dialogowego do **?** przycisk przy zachowaniu architektury zgodnej z poprzednimi wersjami i rozszerzalnością.

 W odniesieniu do **VBDialogBoxParam** funkcja przegląda szablon okna dialogowego dla przycisku, którego identyfikator jest **IDHELP** (9) lub etykieta jest **pomocna** lub **&**. Jeśli zostanie znaleziony przycisk pomocy, jest on ukryty, a **WS_EX_CONTEXTHELP** stylu zostanie dodany do okna dialogowego, które umieszcza **?** na pasku tytułu okna dialogowego.

 Po utworzeniu okna dialogowego wypycha proces okna dialogowego do stosu i wywołuje okno dialogowe z procesem okna dialogowego przetwarzania wstępnego o nazwie **DialogPreProc**. Kiedy **?** kliknięto przycisk powoduje wysłanie **WM_SYSCOMMAND** **SC_CONTEXTHELP** do okna dialogowego. **DialogPreProc** przechwytuje to polecenie i zmienia go na komunikat **WM_HELP** , który jest przesyłany do oryginalnego procesu dialogu.

 Większość okien dialogowych utworzonych w środowisku ma przycisk Pomoc w oknie dialogowym. Po wyświetleniu okna dialogowego przycisk Pomoc jest ukryty i tylko **?** przycisk działa. Jeśli **?** przycisk jest kiedykolwiek usunięty lub zmieniony w systemie Windows, to rozwiązanie umożliwia szybkie przejście do oryginalnych przycisków pomocy.

 To rozwiązanie udostępnia cztery założenia, które mogą spowodować błędy:

- Przycisk Pomoc okna dialogowego to **IDHELP** (9).

- Okno dialogowe jest wyświetlane prawidłowo, gdy przycisk Pomoc jest ukryty.

- Okno dialogowe nie zastępuje jego winproc.

- Okno dialogowe nie jest osadzone w innym oknie dialogowym.

  Jeśli Twoje okno dialogowe znajduje się w msenv i nie korzysta z **VBDialogBoxParam**, zbadaj użycie **VBDialogBoxParam** przed wdrożeniem własnego programu obsługi.

##### <a name="dialogs-created-through-other-packages"></a>Okna dialogowe utworzone za poorednictwem innych pakietów
 Własne rozwiązanie można zaimplementować dla okien dialogowych, które znajdują się poza msenv. W przypadku udostępnionej klasy okna dialogowego w pakietu VSPackage Rozważ przeniesienie przycisku do paska tytułu lub wdrożenie procedury obsługi w każdym oknie dialogowym. Poniższy kod stanowi szkielet implementacji, aby ułatwić rozpoczęcie pracy:

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
 Zastępowanie domyślnego zachowania przycisku pomoc paska tytułu jest łatwe w kodzie zarządzanym. Poniżej znajduje się kompletna aplikacja demonstracyjna, która demonstruje to zachowanie. W zasadzie należy przesłonić metodę **WndProc** formularza, a następnie wyłączyć żądania pomocy F1 w przypadku przechwycenia komunikatu **SC_CONTEXTHELP** .

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
