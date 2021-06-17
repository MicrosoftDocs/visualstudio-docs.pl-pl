---
title: Ustawienia usługi Git w usłudze Visual Studio
titleSuffix: ''
description: Dowiedz się, Visual Studio zarządzać preferencjami za pomocą plików .gitconfig i ustawień usługi Git
ms.date: 06/08/2021
ms.topic: conceptual
ms.author: prnadago
author: prnadago
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: f8dd9781833706a73b82a71236d42cc71c9fb9ec
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126683"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Ustawienia i preferencje usługi Git w Visual Studio

W Visual Studio można konfigurować i wyświetlać typowe ustawienia i preferencje usługi Git, takie jak nazwa i adres e-mail, preferowane narzędzia do porównywania i scalania i nie tylko. Te ustawienia i preferencje można wyświetlać  i konfigurować w oknie dialogowym Opcje na stronie Ustawienia globalne usługi **Git** (dotyczy wszystkich repozytoriów) lub na stronie Ustawienia repozytorium **Git** (dotyczy bieżącego repozytorium).

Można skonfigurować dwa typy ustawień:

- [Ustawienia usługi Git](#git-settings) — ustawienia w tej sekcji odpowiadają ustawieniam usługi Git zapisanym w plikach konfiguracji usługi Git. Te ustawienia można wyświetlać i modyfikować w usłudze Visual Studio, ale są zarządzane przez pliki konfiguracji usługi Git.
- [Visual Studio — ustawienia w](#visual-studio-settings) tej sekcji konfigurują ustawienia i preferencje związane z usługą Git, które są zarządzane przez usługę Visual Studio.

## <a name="how-to-configure-settings"></a>Jak skonfigurować ustawienia

1. Aby skonfigurować ustawienia usługi Git w Visual Studio, wybierz **pozycję Ustawienia** z menu najwyższego poziomu Usługi Git.

   :::image type="content" source="media/git-menu-settings.png" alt-text="Menu Usługi Git z objaśnieniami do polecenia Ustawienia.":::

2. Wybierz **pozycję Ustawienia globalne usługi Git** lub Ustawienia **repozytorium Git,** aby wyświetlić i skonfigurować ustawienia na poziomie globalnym lub na poziomie repozytorium.

   :::image type="content" source="media/source-control-settings.png" alt-text="Okienko nawigacji w oknie dialogowym Opcje z objaśnieniami do ustawień usługi Git.":::

3. Można skonfigurować kilka typowych ustawień usługi Git, zgodnie z opisem w poniższych sekcjach tego artykułu. Po skonfigurowaniu żądanych ustawień wybierz przycisk **OK,** aby zapisać zaktualizowane ustawienia.

   :::image type="content" source="media/ok-button.png" alt-text="Obszar wyświetlania okna dialogowego Opcje z objaśnieniami do przycisku OK.":::

## <a name="git-settings"></a>Ustawienia usługi Git

Możesz również skonfigurować i sprawdzić niektóre z najbardziej typowych ustawień konfiguracji usługi Git. Możesz wyświetlać i modyfikować następujące ustawienia w usłudze Visual Studio, mimo że są one zarządzane przez pliki konfiguracji usługi Git.

- [Nazwa i adres e-mail](#name-and-email)
- [Rozgałęzienia zdalne podczas pobierania](#prune-remote-branches-during-fetch)
- [Ponowne bazowanie gałęzi lokalnej podczas ściągania](#rebase-local-branch-when-pulling)
- [Dostawca sieci kryptograficznych](#cryptographic-network-provider)
- [Pomocnik poświadczeń](#credential-helper)
- [Narzędzia & scalania różnic](#diff--merge-tools)
- [Pliki Git](#git-files)
- [Piloty](#remotes)
- [Inne ustawienia](#other-settings)

>[!NOTE]
>Ustawienia usługi Git skonfigurowane w ustawieniach globalnych usługi Visual Studio odpowiadają ustawieniam w pliku konfiguracji  specyficznym dla użytkownika usługi Git, a ustawienia w ustawieniach repozytorium odpowiadają ustawieniam w pliku konfiguracji specyficznym dla repozytorium.  Aby uzyskać więcej informacji na temat konfiguracji usługi Git, zobacz rozdział Pro Git poświęcony dostosowywaniu usługi [Git,](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)dokumentację [git-config](https://git-scm.com/docs/git-config)i dokumentację [usługi Pro Git dotyczącą plików konfiguracji](https://git-scm.com/docs/git-config#FILES). Aby skonfigurować ustawienia usługi Git, które nie są Visual Studio w usłudze , użyj polecenia , aby zapisać wartość `git config` w plikach konfiguracji: `git config [--local|--global|--system] section.key value` .

### <a name="name-and-email"></a>Nazwa i adres e-mail

Podany adres e-mail i nazwa będą używane jako informacje o zatwierdzeniu dla każdego zatwierdzenia. To ustawienie jest dostępne zarówno w zakresie globalnym, jak i w zakresie repozytorium i odpowiada user.name `git config` [](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) i [user.email](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail) repozytorium.

1. Z menu Git przejdź do pozycji **Ustawienia**. Aby ustawić nazwę użytkownika i adres e-mail na poziomie globalnym, przejdź do **tematu Ustawienia globalne usługi Git.** Aby ustawić nazwę użytkownika i adres e-mail na poziomie repozytorium, przejdź do **tematu Git Repository Settings (Ustawienia repozytorium Git).**

2. Podaj nazwę użytkownika i adres e-mail, a następnie wybierz przycisk **OK,** aby zapisać. 

   :::image type="content" source="media/user-email-setting.png" alt-text="Okienko Ustawień globalnych usługi Git w oknie dialogowym Opcje z objaśnieniami do nazwy użytkownika w wiadomości e-mail.":::

### <a name="prune-remote-branches-during-fetch"></a>Rozgałęzienia zdalne podczas pobierania

Oczyszczanie usuwa gałęzie zdalnego śledzenia, które nie istnieją już na zdalnym i pomaga zachować listy gałęzi czyste i aktualne. To ustawienie jest dostępne zarówno w zakresie globalnym, jak i w zakresie repozytorium i odpowiada ustawieniu `git config` [fetch.prune.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune)

Zalecamy ustawienie tej opcji na **wartość True** na poziomie globalnym. Prawidłowe ustawienia są następujące:

- True (zalecane)
- Fałsz
- Nieustawienia (ustawienie domyślne)

1. Z menu Git przejdź do pozycji **Ustawienia**. Przejdź do **ustawień globalnych usługi Git,** aby skonfigurować tę opcję na poziomie globalnym. Przejdź do **ustawień repozytorium Git,** aby skonfigurować tę opcję na poziomie repozytorium.

2. Dla **ustawienia Gałęzie zdalne usługi Prune podczas pobierania ustaw** wartość **True** (zalecane). Wybierz **przycisk OK,** aby zapisać.

:::image type="content" source="media/prune-setting.png" alt-text="Zrzut ekranu przedstawiający wyróżnioną opcję &quot;Prune remote branches during fetch&quot; (Czy rozgałęzienia zdalne podczas pobierania) z wybraną wartością &quot;True&quot; (Prawda) z listy rozwijanej.":::    

### <a name="rebase-local-branch-when-pulling"></a>Ponowne bazowanie gałęzi lokalnej podczas ściągania

Zmianabasing ustawia zmiany wprowadzone przez zatwierdzenia w bieżącej gałęzi, które nie znajdują się w gałęzi nadrzędnej, resetuje bieżącą gałąź do gałęzi nadrzędnej, a następnie stosuje zmiany, które zostały przeznaczone. To ustawienie jest dostępne zarówno w zakresie globalnym, jak i w zakresie repozytorium i odpowiada ustawieniu `git config` [pull.rebase.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) Prawidłowe ustawienia są następujące:

- True: Po pobraniu należy ponownie bazy danych current branch na początku gałęzi nadrzędnej.
- False: scal bieżącą gałąź z gałęzią upstream.
- Nieustawienia (wartość domyślna): chyba że określono w innych plikach konfiguracji, scal bieżącą gałąź z gałęzią nadrzędnej.
- Interakcyjne: ponowne bazy danych w trybie interaktywnym.
- Zachowaj: przeksztuj bazę bez spłaszczania lokalnie utworzonych zatwierdzeń scalania.

1. Z menu Git przejdź do pozycji **Ustawienia**. Przejdź do **ustawień globalnych usługi Git,** aby skonfigurować tę opcję na poziomie globalnym. Przejdź do **ustawień repozytorium Git,** aby skonfigurować tę opcję na poziomie repozytorium.

2. Ustaw **pozycję Przeszukaj ponownie gałąź** lokalną podczas ściągania do żądanego ustawienia, a następnie wybierz przycisk **OK,** aby zapisać.

    :::image type="content" source="media/rebase-setting.png" alt-text="Zrzut ekranu przedstawiający wyróżniony element &quot;Ponownie bazyj gałąź lokalną podczas ściągania&quot; i wybraną z listy rozwijanej wartość &quot;True&quot;.":::

Nie można skonfigurować ustawienia Interakcyjne `pull.rebase` **w** Visual Studio. Visual Studio nie ma interaktywnej obsługi ponownej bazy.
Aby skonfigurować `pull.rebase` do korzystania z trybu interaktywnego, użyj wiersza polecenia.

### <a name="cryptographic-network-provider"></a>Dostawca sieci kryptograficznych

Dostawca sieci kryptograficznych to ustawienie konfiguracji usługi Git w zakresie globalnym, które konfiguruje, które zaplecza protokołu TLS/SSL mają być dostępne w czasie wykonywania i odpowiada ustawieniu `git config` [http.sslBackend.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) Te wartości są następujące:

- OpenSSL: użyj [protokołu OpenSSL dla](https://www.openssl.org/) protokołów TLS i SSL.
- Bezpieczny kanał: użyj [protokołu Secure Channel (schannel) dla](/windows/win32/secauthn/secure-channel) protokołów TLS i SSL. Schannel to natywne rozwiązanie systemu Windows, które uzyskuje dostęp do Credential Store Windows, umożliwiając w ten sposób zarządzanie certyfikatami w całym przedsiębiorstwie.
- Nieustawienia (wartość domyślna): jeśli to ustawienie jest nieuprawniane, wartość domyślna to OpenSSL.

1. Z menu Git przejdź do pozycji **Ustawienia**. Przejdź do **ustawień globalnych usługi Git,** aby skonfigurować to ustawienie.

2. Ustaw **żądaną wartość Dostawca** sieci kryptograficznych, a następnie wybierz przycisk **OK,** aby zapisać.

   :::image type="content" source="media/network-provider-setting.png" alt-text="Zrzut ekranu przedstawiający element &quot;Dostawca sieci kryptograficznych&quot; wyróżniony z listą rozwijaną &quot;OpenSSL&quot;.":::

### <a name="credential-helper"></a>Pomocnik poświadczeń

Gdy Visual Studio zdalną operację Git, zdalny punkt końcowy może odrzucić żądanie, ponieważ wymaga ono poświadczeń dostarczonych z żądaniem. W tym czasie usługa Git wywołuje pomocnika poświadczeń, który zwróci poświadczenia wymagane do wykonania operacji, a następnie spróbuje ponownie wykonać żądanie. Użyty pomocnik poświadczeń odpowiada ustawieniu `git config` [credential.helper.](https://git-scm.com/docs/gitcredentials) Jest ona dostępna w zakresie globalnym z następującymi wartościami:

- USŁUGA GCM dla systemu Windows: użyj [Menedżer poświadczeń Git dla systemu Windows](https://github.com/microsoft/Git-Credential-Manager-for-Windows) jako pomocnika.
- GCM Core: użyj [narzędzia Git Menedżer poświadczeń Core](https://github.com/microsoft/Git-Credential-Manager-Core) jako pomocnika.
- Nie ustawiono (wartość domyślna): jeśli to ustawienie nie zostanie ustawione, zostanie użyty pomocnik poświadczeń ustawiony w konfiguracji systemu. W systemie Git dla systemu Windows 2.29 domyślnym pomocnikiem poświadczeń jest GCM Core.

1. Z menu Git przejdź do pozycji **Ustawienia**. Przejdź do **ustawień globalnych usługi Git,** aby skonfigurować to ustawienie.

2. Ustaw **pomocnika poświadczeń** na żądaną wartość, a następnie wybierz przycisk **OK,** aby zapisać.

:::image type="content" source="media/credential-helper-setting.png" alt-text="Zrzut ekranu przedstawiający ustawienie pomocnika poświadczeń w oknie dialogowym Opcje.":::

### <a name="diff--merge-tools"></a>Narzędzia & scalania różnic

Usługa Git pokaże różnice i konflikty scalania w preferowanych narzędziach. Ustawienia w tej sekcji odpowiadają `git config` [ustawieniam diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) i [merge.tool.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) Usługę Git można skonfigurować do używania Visual Studio jako narzędzia scalania lub porównywania w ustawieniach globalnych usługi **Git** i ustawieniach repozytorium **Git,** wybierając pozycję **Użyj Visual Studio**. Aby skonfigurować inne narzędzia do porównywania i scalania, użyj narzędzia `git config` [z przełącznikiem diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) [lub merge.tool.](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool)

:::image type="content" source="media/tools-setting.png" alt-text="Zrzut ekranu przedstawiający sekcję do ustawienia domyślnego narzędzia różnicowego i narzędzia scalania w oknie dialogowym Opcje.":::

### <a name="git-files"></a>Pliki Git

Sekcja Pliki **Git** w zakresie Ustawienia repozytorium **Git** umożliwia wyświetlanie i edytowanie plików [gitignore](https://git-scm.com/docs/gitignore) i [gitattributes](https://git-scm.com/docs/gitattributes) dla repozytorium.

:::image type="content" source="media/git-files-setting.png" alt-text="Zrzut ekranu przedstawiający sekcję do wyświetlania i edytowania plików Ignore i attributes w repozytorium.":::

### <a name="remotes"></a>Piloty

Możesz użyć okienka **Remotes (Repozytoria** zdalne) w obszarze Git Repository Settings (Ustawienia **repozytorium Git),** aby skonfigurować repozytorium zdalne. To ustawienie odpowiada [zdalnemu poleceniu git](https://git-scm.com/docs/git-remote) i umożliwia dodawanie, edytowanie lub usuwanie zdalnych plików.

:::image type="content" source="media/remotes-settings.png" alt-text="Zrzut ekranu przedstawiający okienko Repozytoria zdalne Usługi Git w oknie dialogowym Opcje.":::

### <a name="other-settings"></a>Inne ustawienia

Aby wyświetlić wszystkie inne ustawienia konfiguracji usługi Git, możesz otworzyć i wyświetlić pliki konfiguracji samodzielnie lub uruchomić program , aby `git config --list` wyświetlić ustawienia.

## <a name="visual-studio-settings"></a>Visual Studio ustawień

Poniższe ustawienia zarządzają preferencjami związanymi z usługą Git w usłudze Visual Studio i są zarządzane Visual Studio a nie plikami konfiguracji usługi Git. Wszystkie ustawienia w tej sekcji są konfigurowane na stronie **Ustawienia globalne usługi Git.**

- [Lokalizacja domyślna](#default-location)
- [Zamykanie otwartych rozwiązań, które nie są w obszarze usługi Git, podczas otwierania repozytorium](#close-open-solutions-not-under-git-when-opening-a-repository)
- [Włączanie pobierania obrazów author ze źródeł innych firm](#enable-download-of-author-images-from-third-party-sources)
- [Domyślne zatwierdzanie zmian po scaleniu](#commit-changes-after-merge-by-default)
- [Włączanie wypychania — wymuszanie](#enable-push---force-with-lease)
- [Otwieranie folderu w Eksplorator rozwiązań podczas otwierania repozytorium Git](#open-folder-in-solution-explorer-when-opening-a-git-repository)
- [Automatyczne ładowanie rozwiązania podczas otwierania repozytorium Git](#automatically-load-the-solution-when-opening-a-git-repository)
- [Automatyczne wyewidencjanie gałęzi za pomocą dwukrotnego kliknięcia lub klawisza Enter](#automatically-check-out-branches-with-double-click-or-the-enter-key)

### <a name="default-location"></a>Lokalizacja domyślna

**Lokalizacja domyślna** umożliwia skonfigurowanie domyślnego folderu, w którym są klonowane repozytoria.

:::image type="content" source="media/default-location-setting.png" alt-text="Zrzut ekranu przedstawiający domyślne pole lokalizacji w oknie dialogowym Opcje.":::

### <a name="close-open-solutions-not-under-git-when-opening-a-repository"></a>Zamykanie otwartych rozwiązań, które nie są w obszarze usługi Git, podczas otwierania repozytorium

Domyślnie program Visual Studio wszystkie otwarte rozwiązania lub foldery po przełączeniu do innego repozytorium. W tym przypadku rozwiązanie lub folder nowego repozytorium może zostać załadowane w zależności od tego, czy podczas otwierania repozytorium Git wybierzesz opcję Otwórz folder w usłudze [Eksplorator rozwiązań i](#open-folder-in-solution-explorer-when-opening-a-git-repository) automatycznie załaduj rozwiązanie podczas otwierania repozytorium [Git.](#automatically-load-the-solution-when-opening-a-git-repository) Zapewnia to spójność między otwartym kodem i otwartym repozytorium. Jeśli jednak rozwiązanie nie znajduje się w tym samym folderze głównym co repozytorium, możesz zachować to rozwiązanie otwarte po przełączeniu się do jego repozytorium. Można to zrobić za pomocą tego ustawienia. Te wartości są następujące:

- Tak: po otwarciu repozytorium obecnie otwarte rozwiązanie jest zawsze zamykane
- Nie: Po otwarciu repozytorium Visual Studio sprawdza, czy bieżące rozwiązanie znajduje się w obszarze Git. Jeśli tak nie jest, rozwiązanie pozostaje otwarte.
- Zawsze pytaj (ustawienie domyślne): jeśli to ustawienie jest ustawione, możesz dokonać wyboru za pomocą okna dialogowego dla każdego otwartego repozytorium, niezależnie od tego, czy chcesz, aby bieżące rozwiązanie było otwarte, czy zamknięte.

:::image type="content" source="media/close-sln-setting.png" alt-text="Zrzut ekranu przedstawiający ustawienie zamykania rozwiązania w oknie dialogowym Opcje.":::


### <a name="enable-download-of-author-images-from-third-party-sources"></a>Włączanie pobierania obrazów author ze źródeł innych firm

Włączanie pobierania obrazów author ze źródeł innych firm jest ustawieniem specyficznym Visual Studio w zakresie globalnym. Gdy ta opcja jest zaznaczona, obrazy autora są pobierane z usługi [obrazów gravatar](https://en.gravatar.com/), jeśli są dostępne, i wyświetlane w widokach zatwierdzania i historii.

:::image type="content" source="media/download-image-setting.png" alt-text="Zrzut ekranu przedstawiający pole wyboru umożliwiające pobieranie obrazów author ze źródła innej firmy w oknie dialogowym Opcje. ":::

>[!IMPORTANT]
>Aby udostępnić obrazy autora w widokach Zatwierdzanie i Historia, narzędzie tworzy skrót MD5 dla adresów e-mail autora przechowywanych w aktywnym repozytorium. Ten skrót jest następnie wysyłany do gravatar w celu znalezienia pasującej wartości skrótu dla użytkowników, którzy wcześniej założyli usługę. Jeśli dopasowanie zostanie znalezione, obraz użytkownika zostanie pobrany z usługi i wyświetlony w Visual Studio. Użytkownicy, którzy nie skonfigurowali usługi, będą zwracać losowo wygenerowany obraz. Pamiętaj, że adresy e-mail nie są rejestrowane przez Visual Studio ani nie są kiedykolwiek udostępniane gravatarowi ani żadnej innej stronie.

### <a name="commit-changes-after-merge-by-default"></a>Domyślne zatwierdzanie zmian po scaleniu

Po **domyślnym włączeniu opcji Zatwierdzanie** zmian po scaleniu usługa Git automatycznie tworzy nowe zatwierdzenie, gdy gałąź zostanie scalona z gałęzią bieżącą.

:::image type="content" source="media/merge-commit-setting.png" alt-text="Zrzut ekranu przedstawiający pole wyboru służące do zatwierdzania zmian po scaleniu domyślnie w oknie dialogowym Opcje.":::

- Gdy to pole `git merge` jest zaznaczone, polecenia Visual Studio są uruchamiane z `--commit` opcją .
- Gdy pole wyboru nie jest zaznaczone, `git merge` polecenia Visual Studio są uruchamiane z `--no-commit --no-ff` opcjami .

Aby uzyskać więcej informacji na temat tych opcji, zobacz [--commit i --no-commit](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) i [--no-ff](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff).

### <a name="enable-push---force-with-lease"></a>Włączanie wypychania --force-with-lease

Gdy to ustawienie jest włączone, można to zrobić `push --force-with-lease` z poziomu Visual Studio. Domyślnie opcja **Włącz wypychanie --force-with-lease** jest wyłączona.

:::image type="content" source="media/push-force-setting.png" alt-text="Zrzut ekranu przedstawiający pole wyboru umożliwiające włączenie wymuszania wypychania z dzierżawą w oknie dialogowym Opcje.":::

Aby uzyskać więcej informacji, zobacz [push --force-with-lease](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease).

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>Otwieranie folderu w Eksplorator rozwiązań podczas otwierania repozytorium Git
<!-- todo: write section -->
Gdy używasz narzędzia Visual Studio do otwierania lub przełączania się do repozytorium Git, program Visual Studio ładuje zawartość Git, aby można było wyświetlać zmiany, zatwierdzenia, gałęzie i zarządzać repozytorium z poziomu środowiska IDE. Ponadto Visual Studio również załadować kod repozytorium w Eksplorator rozwiązań. Visual Studio przeskanuje folder repozytorium w poszukiwaniu rozwiązań, CMakeLists.txt lub innych rozpoznanych plików widoku i wyświetli je jako listę w Eksplorator rozwiązań. W tym miejscu możesz wybrać rozwiązanie do załadowania lub folder, aby wyświetlić zawartość katalogu. Jeśli to pole wyboru zostanie wyłączone, Visual Studio folder repozytorium nie zostanie otwarty w Eksplorator rozwiązań. Pozwoli to zasadniczo otwierać pliki Visual Studio tylko jako menedżer repozytorium Git. To ustawienie jest domyślnie włączone.

:::image type="content" source="media/open-folder-setting.png" alt-text="Zrzut ekranu przedstawiający pole wyboru służące do otwierania folderu podczas otwierania repozytorium Git w oknie dialogowym Opcje.":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>Automatyczne ładowanie rozwiązania podczas otwierania repozytorium Git

To ustawienie ma zastosowanie tylko wtedy, gdy ustawienie [Otwórz folder w Eksplorator rozwiązań podczas](#open-folder-in-solution-explorer-when-opening-a-git-repository) otwierania repozytorium Git jest włączone. Po otwarciu repozytorium Git w usłudze Visual Studio, gdy kolejne skanowanie folderów wykryje, że w repozytorium znajduje się tylko jedno rozwiązanie, Visual Studio automatycznie ładuje to rozwiązanie. Jeśli wyłączysz to ustawienie, Eksplorator rozwiązań wyświetli jedno rozwiązanie obecne w repozytorium na liście widoków. Ale rozwiązanie nie zostanie załadowane. Domyślnie to ustawienie jest wyłączone.

:::image type="content" source="media/load-solution-setting.png" alt-text="Zrzut ekranu przedstawiający pole wyboru służące do automatycznego ładowania rozwiązania podczas otwierania repozytorium Git w oknie dialogowym Opcje.":::

### <a name="automatically-check-out-branches-with-double-click-or-the-enter-key"></a>Automatyczne wyewidencjanie gałęzi za pomocą dwukrotnego kliknięcia lub klawisza Enter

Okno Repozytorium Git zawiera listę gałęzi wyświetlanych w strukturze drzewa. Wybranie jednej gałęzi spowoduje przełączenie okienka historii zatwierdzeń w celu wyświetlenia zatwierdzeń dla wybranej gałęzi. Aby wyewidencjonować gałąź, możesz kliknąć prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybrać polecenie **Wyewidencjonowanie**. Jeśli włączysz to ustawienie, dwukrotne kliknięcie lub naciśnięcie klawisza Enter spowoduje wyewidencjenie gałęzi i wyświetlenie jej zatwierdzeń. 
  
:::image type="content" source="media/checkout-branch-setting.png" alt-text="Zrzut ekranu przedstawiający pole wyboru służące do wyewidencjiowania gałęzi za pomocą dwukrotnego kliknięcia lub klawisza Enter w oknie dialogowym Opcje.":::


## <a name="see-also"></a>Zobacz też

> [!IMPORTANT]
> Jeśli masz dla nas sugestię, daj nam znać! Doceniamy możliwość kontaktowania się z Tobem w sprawie decyzji projektowych za [**pośrednictwem Developer Community**](https://aka.ms/vsgitsuggestions) portal.

- [Rozpocznij z narzędziami Git i gitHub](/learn/modules/visual-studio-github-push/) w Visual Studio samouczku Microsoft Learn
- [Wprowadzenie do usługi Git w Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) wideo w serwisie YouTube
- [Poprawiona produktywność dzięki narzędziu Git Visual Studio](https://devblogs.microsoft.com/visualstudio/enhanced-productivity-with-git-in-visual-studio/) wpis w blogu
- [Opcje — Okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md)
