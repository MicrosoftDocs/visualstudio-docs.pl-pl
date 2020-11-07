---
title: Rozwiązywanie problemów z błędami (wdrożenia ClickOnce)
description: W tym artykule opisano typowe błędy, które mogą wystąpić podczas wdrażania aplikacji ClickOnce i przedstawiono kroki umożliwiające rozwiązanie każdego problemu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af462178cf18d57afa6b51aedaba0004615ebb6f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349269"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce
W tym artykule wymieniono następujące typowe błędy, które mogą wystąpić podczas wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, i przedstawiono kroki umożliwiające rozwiązanie każdego problemu.

## <a name="general-errors"></a>Błędy ogólne

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Gdy próbujesz zlokalizować plik aplikacji, nic się nie dzieje lub renderuje XML w programie Internet Explorer lub otrzymujesz okno dialogowe Uruchom lub Zapisz jako
 Ten błąd jest prawdopodobnie spowodowany przez typy zawartości (znane także jako typy MIME), które nie są poprawnie rejestrowane na serwerze lub kliencie.

 Najpierw upewnij się, że serwer jest skonfigurowany do kojarzenia rozszerzenia *. Application* z typem zawartości "application/x-MS-Application".

 Jeśli serwer jest skonfigurowany prawidłowo, sprawdź, czy na komputerze jest zainstalowany .NET Framework 2,0. Jeśli zainstalowano .NET Framework 2,0 i nadal widzisz ten problem, spróbuj odinstalować i ponownie zainstalować .NET Framework 2,0 w celu ponownego zarejestrowania typu zawartości na kliencie.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Zostanie wyświetlony komunikat o błędzie "nie można pobrać aplikacji. Brak plików w wdrożeniu lub "Pobieranie aplikacji zostało przerwane, sprawdź, czy występują błędy sieci i spróbuj ponownie później"
 Ten komunikat oznacza, że nie można pobrać co najmniej jednego pliku, do którego odwołuje się [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty. Najprostszym sposobem debugowania tego błędu jest próba pobrania adresu URL, który wskazuje, że [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie można go pobrać. Poniżej przedstawiono niektóre możliwe przyczyny:

- Jeśli plik dziennika mówi "(403) zabronione" lub "(404) nie został znaleziony", sprawdź, czy serwer sieci Web został skonfigurowany tak, aby nie blokował pobierania tego pliku. Aby uzyskać więcej informacji, zobacz [problemy z konfiguracją serwera i klienta we wdrożeniach ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Jeśli plik *. config* jest blokowany przez serwer, zapoznaj się z sekcją "błąd pobierania podczas próby zainstalowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zawierającej plik. config" w dalszej części tego artykułu.

- Ustal, czy ten błąd wystąpił, ponieważ `deploymentProvider` adres URL w manifeście wdrożenia wskazuje inną lokalizację niż adres URL używany na potrzeby aktywacji.

- Upewnij się, że wszystkie pliki są obecne na serwerze; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dziennik powinien poinformować o tym, który plik nie został znaleziony.

- Sprawdź, czy występują problemy z łącznością sieciową; Możesz otrzymać ten komunikat, jeśli komputer kliencki przeszedł w tryb offline podczas pobierania.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Błąd pobierania podczas próby zainstalowania aplikacji ClickOnce, która ma plik. config
 Domyślnie aplikacja oparta na systemie Windows Visual Basic zawiera plik App.config. Wystąpi problem, gdy użytkownik spróbuje zainstalować program z serwera sieci Web, który używa systemu Windows Server 2003, ponieważ ten system operacyjny zablokuje instalację plików *. config* ze względów bezpieczeństwa. Aby włączyć instalację pliku *. config* , kliknij przycisk **Użyj rozszerzenia pliku ". deploy"** w oknie dialogowym **Opcje publikowania** .

 Należy również ustawić typy zawartości (znane także jako typy MIME) odpowiednio dla plików. Application,. manifest i. deploy. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją serwera sieci Web.

 Aby uzyskać więcej informacji, zobacz "Windows Server 2003: zablokowane typy zawartości" w temacie [problemy z konfiguracją serwera i klienta we wdrożeniach ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Komunikat o błędzie: "aplikacja jest nieprawidłowo sformatowana;" Plik dziennika zawiera "podpis XML jest nieprawidłowy"
 Upewnij się, że plik manifestu został zaktualizowany i podpisany ponownie. Opublikuj ponownie aplikację przy użyciu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub użyj narzędzia Mage do ponownego podpisania aplikacji.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Aplikacja została zaktualizowana na serwerze, ale klient nie pobiera aktualizacji
 Ten problem można rozwiązać, wykonując jedną z następujących czynności:

- Zapoznaj się z `deploymentProvider` adresem URL w manifeście wdrożenia. Upewnij się, że aktualizujesz bity w tej samej lokalizacji, która `deploymentProvider` wskazuje na.

- Sprawdź interwał aktualizacji w manifeście wdrożenia. Jeśli dla tego interwału określono okresowe interwały, na przykład co sześć godzin, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] program nie będzie skanować w poszukiwaniu aktualizacji, dopóki ten interwał nie zostanie zakończony. Można zmienić manifest, aby przeprowadzić skanowanie w poszukiwaniu aktualizacji za każdym razem, gdy aplikacja zostanie uruchomiona. Zmiana interwału aktualizacji jest wygodną opcją w czasie projektowania w celu sprawdzenia, czy aktualizacje są instalowane, ale spowalniają aktywację aplikacji.

- Spróbuj ponownie uruchomić aplikację w menu Start. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Program mógł wykryć aktualizację w tle, ale wyświetli monit o zainstalowanie usługi BITS przy następnej aktywacji.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Podczas aktualizacji zostanie wyświetlony komunikat o błędzie o następującym wpisie dziennika: "odwołanie w tym wdrożeniu nie jest zgodne z tożsamością zdefiniowaną w manifeście aplikacji"
 Ten błąd może wystąpić, ponieważ zostały ręcznie edytowane manifesty wdrożenia i aplikacji oraz spowodowały, że opis tożsamości zestawu w jednym manifeście stanie się niezsynchronizowany z drugim. Tożsamość zestawu składa się z jego nazwy, wersji, kultury i tokenu klucza publicznego. Sprawdź opisy tożsamości w manifestach i popraw różnice.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Po raz pierwszy Aktywacja z dysku lokalnego lub dysku CD-ROM powiedzie się, ale kolejna Aktywacja z menu Start nie powiedzie się
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przy użyciu adresu URL dostawcy wdrożenia otrzymuje aktualizacje aplikacji. Sprawdź, czy lokalizacja wskazywana przez adres URL jest poprawna.

#### <a name="error-cannot-start-the-application"></a>Błąd: "nie można uruchomić aplikacji"
 Ten komunikat o błędzie zazwyczaj wskazuje, że występuje problem z instalowaniem tej aplikacji w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sklepie. Wystąpił błąd aplikacji albo magazyn jest uszkodzony. Plik dziennika może poinformować o miejscu wystąpienia błędu.

 Należy wykonać następujące czynności:

- Sprawdź, czy tożsamość manifestu wdrożenia, tożsamość manifestu aplikacji i tożsamość głównego pliku WYKONYWALNego aplikacji są unikatowe.

- Sprawdź, czy ścieżki plików nie przekraczają 100 znaków. Jeśli aplikacja zawiera ścieżki plików, które są zbyt długie, można przekroczyć ograniczenia dotyczące maksymalnej ścieżki, którą można przechowywać. Spróbuj skrócić ścieżki i ponownie zainstalować program.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Ustawienia PrivatePath w pliku konfiguracji aplikacji nie są honorowane
 Aby można było używać PrivatePath (łączenie ścieżek Bing), aplikacja musi zażądać pełnego uprawnienia zaufania. Spróbuj zmienić manifest aplikacji, aby zażądać pełnego zaufania, a następnie spróbuj ponownie.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Podczas dezinstalacji pojawia się komunikat "nie można odinstalować aplikacji"
 Ten komunikat zazwyczaj wskazuje, że aplikacja została już usunięta lub że magazyn jest uszkodzony. Po kliknięciu przycisku **OK** zostanie usunięty wpis **Dodaj/Usuń program** .

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Podczas instalacji pojawia się komunikat z informacją, że zależności platformy nie są zainstalowane
 Brak wymagań wstępnych w pamięci podręcznej GAC (Global Assembly Cache) wymaganej przez aplikację w celu jej uruchomienia.

## <a name="publishing-with-visual-studio"></a>Publikowanie za pomocą programu Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>Publikowanie w programie Visual Studio kończy się niepowodzeniem
 Upewnij się, że masz prawo do publikowania na serwerze docelowym. Na przykład jeśli użytkownik jest zalogowany na komputerze serwera terminali jako zwykły użytkownik, a nie jako administrator, prawdopodobnie nie będziesz mieć uprawnień wymaganych do opublikowania na lokalnym serwerze sieci Web.

 Jeśli publikujesz przy użyciu adresu URL, upewnij się, że na komputerze docelowym włączono rozszerzenia FrontPage Server Extensions włączony.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Komunikat o błędzie: nie można utworzyć witryny sieci Web ' \<site> '. Składniki do komunikacji z rozszerzenia FrontPage Server Extensions nie są zainstalowane.
 Upewnij się, że składnik Web Authoring Microsoft Visual Studio jest zainstalowany na komputerze, na którym jest publikowany. W przypadku użytkowników programu Express ten składnik nie jest instalowany domyślnie. Aby uzyskać więcej informacji, zobacz [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Komunikat o błędzie: nie można odnaleźć pliku "Microsoft. Windows. Common-Controls, Version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , Type = Win32"
 Ten komunikat o błędzie pojawia się podczas próby opublikowania aplikacji WPF z włączonymi stylami wizualizacji. Aby rozwiązać ten problem, zobacz [jak: publikowanie aplikacji WPF przy użyciu stylów wizualnych](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>Korzystanie z programu Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Podjęto próbę zalogowania się za pomocą certyfikatu w magazynie certyfikatów i odebranym pustym komunikatem
 W oknie dialogowym **podpisywania** należy:

- Wybierz pozycję **Podpisz z przechowywanym certyfikatem** i

- Wybierz certyfikat z listy. pierwszy certyfikat nie jest wybór domyślny.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Kliknięcie przycisku "nie Podpisz" powoduje wystąpienie wyjątku
 Ten problem jest znanym błędem. Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty muszą być podpisane. Po prostu wybierz jedną z opcji podpisywania, a następnie kliknij przycisk **OK**.

## <a name="additional-errors"></a>Dodatkowe błędy
 W poniższej tabeli przedstawiono niektóre typowe komunikaty o błędach, które użytkownik komputera klienckiego może otrzymać, gdy użytkownik zainstaluje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację. Każdy komunikat o błędzie jest wyświetlany obok opisu najbardziej prawdopodobnej przyczyny błędu.

| Komunikat o błędzie | Opis |
| - | - |
| Nie można uruchomić aplikacji. Skontaktuj się z wydawcą aplikacji.<br /><br /> Nie można uruchomić aplikacji. Skontaktuj się z dostawcą aplikacji w celu uzyskania pomocy. | Są to ogólne komunikaty o błędach występujące, gdy aplikacja nie może zostać uruchomiona i nie można znaleźć żadnych innych przyczyn. Często oznacza to, że aplikacja jest w jakiś sposób uszkodzona lub że [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Magazyn jest uszkodzony. |
| Nie można kontynuować. Aplikacja jest nieprawidłowo sformatowana. Skontaktuj się z wydawcą aplikacji w celu uzyskania pomocy.<br /><br /> Weryfikacja aplikacji nie powiodła się. Nie można kontynuować.<br /><br /> Nie można pobrać plików aplikacji. Pliki są uszkodzone we wdrożeniu. | Jeden z plików manifestu we wdrożeniu jest syntaktycznie nieprawidłowy lub zawiera skrót, którego nie można uzgodnić z odpowiednim plikiem. Ten błąd może również wskazywać na uszkodzenie manifestu osadzonego wewnątrz zestawu. Ponownie Utwórz wdrożenie i skompiluj swoją aplikację lub ręcznie Znajdź i napraw błędy w manifestach. |
| Nie można pobrać aplikacji. Błąd uwierzytelniania.<br /><br /> Instalacja aplikacji nie powiodła się. Nie można zlokalizować plików aplikacji na serwerze. Skontaktuj się z wydawcą aplikacji lub administratorem w celu uzyskania pomocy. | Nie można pobrać co najmniej jednego pliku we wdrożeniu, ponieważ nie masz uprawnień dostępu do nich. Może to być spowodowane błędem zakazanym przez 403 błąd, który może wystąpić, jeśli jeden z plików w danym wdrożeniu zostanie zakończony rozszerzeniem, który sprawia, że serwer sieci Web traktuje go jako plik chroniony. Ponadto katalog zawierający co najmniej jeden plik aplikacji może wymagać nazwy użytkownika i hasła w celu uzyskania dostępu. |
| Nie można pobrać aplikacji. W aplikacji brakuje wymaganych plików. Skontaktuj się z dostawcą aplikacji lub administratorem systemu, aby uzyskać pomoc. | Na serwerze nie można odnaleźć co najmniej jednego pliku wymienionego w manifeście aplikacji. Sprawdź, czy wszystkie pliki zależne od wdrożenia zostały przekazane, i spróbuj ponownie. |
| Pobieranie aplikacji nie powiodło się. Sprawdź połączenie sieciowe lub skontaktuj się z administratorem systemu lub dostawcą usług sieciowych. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie można nawiązać połączenia sieciowego z serwerem. Sprawdź dostępność serwera i stan sieci. |
| URLDownloadToCacheFile nie powiodła się. wynik HRESULT to " \<number> ". Wystąpił błąd podczas próby pobrania " \<file> ". | Jeśli Użytkownik ustawił opcję zaawansowanego zabezpieczeń programu Internet Explorer "Ostrzegaj w przypadku zmiany między trybem bezpiecznym i niezabezpieczonym" na komputerze docelowym wdrożenia, a jeśli adres URL instalacji instalowanej aplikacji ClickOnce zostanie przekierowany z niezabezpieczonej do zabezpieczonej lokacji (lub odwrotnie), instalacja zakończy się niepowodzeniem, ponieważ ostrzeżenie programu Internet Explorer przerwie ją.<br /><br /> Aby rozwiązać ten problem, można wykonać jedną z następujących czynności:<br /><br /> -Wyczyść opcję Zabezpieczenia.<br />-Upewnij się, że adres URL instalacji nie jest przekierowywany w taki sposób, że zmienia tryby zabezpieczeń.<br />-Usuń Przekierowanie całkowicie i wskaż rzeczywisty adres URL instalacji. |
| Wystąpił błąd podczas zapisywania na dysku twardym. Na dysku może być za mało dostępnego miejsca. Skontaktuj się z dostawcą aplikacji lub administratorem systemu, aby uzyskać pomoc. | Może to wskazywać na niewystarczającą ilość miejsca na dysku do przechowywania aplikacji, ale może także wskazywać bardziej ogólny błąd we/wy podczas próby zapisania plików aplikacji na dysku. |
| Nie można uruchomić aplikacji. Za mało dostępnego miejsca na dysku. | Dysk twardy jest pełny. Wyczyść wolne miejsce i spróbuj ponownie uruchomić aplikację. |
| Podjęto próbę załadowania zbyt wielu wdrożonych aktywacji jednocześnie. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ogranicza liczbę różnych aplikacji, które mogą być uruchamiane w tym samym czasie. Jest to bardzo duże bezpieczeństwo przed złośliwymi próbami zaewidencjonowania ataków typu "odmowa usługi" [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] w usłudze lokalnej; Użytkownicy, którzy próbują wielokrotnie uruchomić tę samą aplikację, w krótkim sukcesie będą kończyć się tylko jednym wystąpieniem aplikacji. |
| Skrótów nie można aktywować za pośrednictwem sieci. | Skróty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji można uruchamiać tylko na lokalnym dysku twardym. Nie można ich uruchomić, otwierając adres URL wskazujący na plik skrótu na serwerze zdalnym. |
| Aplikacja jest zbyt duża, aby można było uruchomić ją w trybie online w częściowej relacji zaufania. Skontaktuj się z dostawcą aplikacji lub administratorem systemu, aby uzyskać pomoc. | Aplikacja działająca w częściowej relacji zaufania nie może być większa niż połowa rozmiaru limitu przydziału aplikacji online, która domyślnie wynosi 250 MB. |

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Rozwiązywanie problemów z programem Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)