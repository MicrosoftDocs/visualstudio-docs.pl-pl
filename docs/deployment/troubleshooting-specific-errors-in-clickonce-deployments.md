---
title: Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 46b7a159fb2d15f817cad47817262202397d3981
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654324"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce
W tym artykule przedstawiono następujące typowe błędy, które mogą wystąpić podczas wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji oraz przedstawiono kroki, aby rozwiązać każdy problem.

## <a name="general-errors"></a>Ogólne błędy

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Podczas lokalizowania pliku aplikacji, nic się nie dzieje, XML, który powoduje wyświetlenie w przeglądarce Internet Explorer lub pojawi się okno dialogowe Run "lub" Zapisz jako
 Typy zawartości (znany także jako typy MIME) nie jest poprawnie zarejestrowany na serwerze lub kliencie prawdopodobnie przyczyną tego błędu.

 Najpierw upewnij się, że serwer jest skonfigurowany do skojarzenia *.application* rozszerzenie o zawartości typu "application/x-ms aplikacji."

 Jeśli serwer jest skonfigurowany prawidłowo, sprawdź, czy [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] jest zainstalowany na tym komputerze. Jeśli [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] jest zainstalowany i nadal widzisz ten problem, spróbuj odinstalowania i ponownego zainstalowania [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] ponownie zarejestrować typ zawartości na komputerze klienckim.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Komunikat o błędzie jest wyświetlany komunikat, "nie można pobrać aplikacji. Pliki Brak we wdrożeniu"lub"pobrania aplikacji zostało przerwane, sprawdź, czy błędy sieciowe i spróbuj ponownie później "
 Ten komunikat oznacza, że jeden lub więcej plików, do którego nastąpiło odwołanie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty nie można pobrać. Najprostszym sposobem, aby debugować ten błąd jest spróbują pobrać adres URL, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mówi, nie można go pobrać. Poniżej przedstawiono niektóre możliwe przyczyny:

- Jeśli plik dziennika jest wyświetlany komunikat "zabronione (403)" lub "(404) nie znaleziono" Upewnij się, że serwer sieci Web jest skonfigurowany tak, aby pobrać ten plik nie jest blokowany. Aby uzyskać więcej informacji, zobacz [serwera i problemy z konfiguracją klienta we wdrożeniach ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Jeśli *.config* pliku jest blokowane przez serwer, zobacz sekcję "Pobierz błąd podczas próby zainstalowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, która zawiera plik .config" w dalszej części tego artykułu.

- Określić, czy ten błąd wystąpił z powodu `deploymentProvider` wskazuje adres URL w manifeście wdrożenia w innej lokalizacji niż adres URL używany do aktywacji.

- Upewnij się, że wszystkie pliki znajdują się na serwerze; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dziennika powinien poinformować Cię, plik, który nie został znaleziony.

- Czy istnieją problemy z łącznością sieciową; może odbierać wiadomość, jeśli komputer kliencki przeszedł do trybu offline podczas pobierania.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Błąd pobierania, podczas próby zainstalowania aplikacji ClickOnce, który ma pliku config
 Domyślnie aplikacji z systemem Windows w języku Visual Basic zawiera plik App.config. Będą występować problemy po użytkownik podejmuje próbę instalacji z serwera sieci Web, która korzysta z systemu Windows Server 2003, ponieważ ten system operacyjny blokuje instalację programu *.config* pliki ze względów bezpieczeństwa. Aby włączyć *.config* pliku do zainstalowania kliknij **rozszerzenie pliku ".deploy"** w **opcji publikowania** okno dialogowe.

 Należy również ustawić typów zawartości (znany także jako typy MIME) odpowiednio dla .application, manifest i .deploy plików. Aby uzyskać więcej informacji zobacz dokumentację serwera sieci Web.

 Aby uzyskać więcej informacji, zobacz "systemu Windows Server 2003: Blokując typów zawartości" [problemy z konfiguracją serwera i klienta we wdrożeniach ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Komunikat o błędzie: "Aplikacja jest nieprawidłowo sformatowana;" Plik dziennika zawiera "podpis XML jest nieprawidłowy"
 Upewnij się, że zaktualizowany plik manifestu i ponownie podpisana. Ponowne opublikowanie aplikacji przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub zaloguj się ponownie aplikację za pomocą Mage.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Zaktualizowano aplikację na serwerze, ale klient nie pobiera aktualizacji
 Ten problem można rozwiązać, wykonując jedną z następujących czynności:

- Sprawdź `deploymentProvider` adresu URL w manifeście wdrożenia. Upewnij się, że aktualizujesz bitów w tej samej lokalizacji, `deploymentProvider` wskazuje.

- Sprawdź interwał aktualizacji w manifeście wdrożenia. Jeśli tego interwału wynosi okresowych interwałach, takich jak jeden raz co sześć godzin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie będzie skanować aktualizacji, dopóki ten interwał został przekazany. Możesz zmienić manifestu do skanowania w poszukiwaniu aktualizacji każdorazowym uruchomieniu aplikacji. Zmiana interwału aktualizacji jest to wygodny sposób w czasie projektowania, aby sprawdzić aktualizacje są instalowane, ale go spowalnia aktywacji aplikacji.

- Spróbuj ponownie uruchomić aplikację w Start menu. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mógł wykryty aktualizacji w tle, ale spowoduje wyświetlenie monitu do zainstalowania usługi bits na następny aktywacji.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Podczas aktualizacji otrzymasz komunikat o błędzie, który ma następujący wpis dziennika: "Odwołania we wdrożeniu jest niezgodna tożsamości zdefiniowany w manifeście aplikacji"
 Ten błąd może wystąpić, ponieważ ręcznej edycji manifesty wdrażania i aplikacji, a spowodowały opis tożsamość zestawu w jeden manifest zostać zsynchronizowany z innymi. Tożsamość zestawu składa się z nazwy, wersji, kulturę i token klucza publicznego. Sprawdź opisy tożsamości w Twojej manifesty i rozwiązać ewentualne różnice.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Po raz pierwszy aktywacji z dysku CD-ROM lub dysk lokalny zakończy się pomyślnie, ale kolejne Aktywacja w Start Menu nie powiodła się.
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] używa adres URL dostawcy wdrożenia, aby otrzymywać aktualizacje aplikacji. Sprawdź, czy w lokalizacji, która wskazuje adres URL jest poprawny.

#### <a name="error-cannot-start-the-application"></a>Błąd: "Nie można uruchomić aplikacji"
 Ten komunikat o błędzie zwykle wskazuje, że występuje problem z instalację tej aplikacji do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowywania. Aplikacja ma błąd albo magazynu jest uszkodzony. Plik dziennika mogą wskazać, gdzie wystąpił błąd.

 Należy wykonać następujące czynności:

-   Sprawdź, czy tożsamość manifestu wdrażania, tożsamość manifest aplikacji i tożsamość aplikacji głównej EXE są unikatowe.

-   Sprawdź, czy ścieżki do plików nie są dłuższe niż 100 znaków. Jeśli aplikacja zawiera ścieżki plików, które są zbyt długie, może przekroczyć ograniczenia dotyczące maksymalnego ścieżki, które można przechowywać. Spróbuj skrócić ścieżki i ponownie zainstalować.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Ustawienia PrivatePath w pliku konfiguracji aplikacji nie są uznawane.
 Aby użyć PrivatePath (ścieżkach sondowania Fusion), aplikacja musi żądać uprawnienia pełnego zaufania. Spróbuj zmienić manifest aplikacji, aby zażądać pełnego zaufania, a następnie spróbuj ponownie.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Podczas odinstalowania pojawi się komunikat, "Nie można odinstalować aplikację"
 Zazwyczaj ten komunikat oznacza, że aplikacja została już usunięta lub magazynu jest uszkodzony. Po kliknięciu **OK**, **Dodaj/Usuń programy** wpis zostanie usunięty.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Podczas instalacji wyświetlany jest komunikat informujący o tym, że zależności platformy nie są zainstalowane
 Brak wstępnie wymaganego składnika w GAC (globalnej pamięci podręcznej zestawów) aplikację aby można było uruchomić.

## <a name="publishing-with-visual-studio"></a>Publikowanie za pomocą programu Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>Publikowanie w programie Visual Studio kończy się niepowodzeniem.
 Upewnij się, że masz prawo do publikowania na serwerze, przeznaczonych do pracy. Na przykład jeśli użytkownik jest zalogowany na komputerze serwera terminali jako zwykłego użytkownika, nie jako administrator, prawdopodobnie nie będziesz mieć uprawnienia wymagane do publikowania na lokalnym serwerze sieci Web.

 W przypadku publikowania za pomocą adresu URL, upewnij się, że komputer docelowy ma włączone rozszerzenia serwera FrontPage.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Komunikat o błędzie: Nie można utworzyć witryny sieci Web "\<lokacji >'. Składniki komunikacji przy użyciu rozszerzenia serwera FrontPage nie są zainstalowane.
 Upewnij się, że masz programu Microsoft Visual Studio składnika sieci Web autorstwa instalować na komputerze, na którym publikujesz z. Dla użytkowników, Express ten składnik nie jest zainstalowany domyślnie. Aby uzyskać więcej informacji, zobacz [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Komunikat o błędzie: Nie można odnaleźć pliku "Microsoft.Windows.Common — formanty, wersja 6.0.0.0, Culture = = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, typu = win32"
 Ten komunikat o błędzie pojawia się podczas próby publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych. Aby rozwiązać ten problem, zobacz [jak: Publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>Za pomocą Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Próbowano zalogować się przy użyciu certyfikatu w magazynie certyfikatów i odebranego komunikatu puste pola
 W **podpisywanie** okno dialogowe, należy:

-   Wybierz **logowania przechowywanym certyfikatem**, i

-   Wybierz certyfikat z listy; pierwszy certyfikat nie jest ustawieniem domyślnym.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Klikając przycisk "Zaloguj nie" powoduje, że wyjątek
 Ten problem, jest to znana usterka. Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów są wymagane, aby były podpisane. Wystarczy wybrać jedną z opcji podpisywania, a następnie kliknij przycisk **OK**.

## <a name="additional-errors"></a>Dodatkowe błędy
 W poniższej tabeli przedstawiono niektóre typowe komunikaty o błędach, które użytkownik komputera klienckiego może zostać wyświetlony, gdy użytkownik instaluje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Każdy komunikat o błędzie jest wyświetlany obok opis najbardziej prawdopodobna przyczyna błędu.

| Komunikat o błędzie | Opis |
| - | - |
| Nie można uruchomić aplikacji. Skontaktuj się z wydawcą aplikacji.<br /><br /> Nie można uruchomić aplikacji. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji. | Są to ogólne komunikaty o błędach, które występują, gdy nie można uruchomić aplikacji, i można go znaleźć bez określonego powodu. Często oznacza to, że aplikacja jakiś sposób jest uszkodzony lub że [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] magazyn jest uszkodzony. |
| Nie można kontynuować. Aplikacja jest nieprawidłowo sformatowany. Aby uzyskać pomoc, skontaktuj się z wydawcą aplikacji.<br /><br /> Weryfikacja aplikacji nie powiodła się. Nie można kontynuować.<br /><br /> Nie można pobrać plików aplikacji. Pliki uszkodzone we wdrożeniu. | Jeden z plików manifestu we wdrożeniu jest składniowo nieprawidłowy lub zawiera wyznaczania wartości skrótu, których nie można uzgodnić z odpowiednim plikiem. Ten błąd może również wskazywać, że manifestem osadzonym wewnątrz zestawu jest uszkodzony. Ponownie utwórz wdrożenie ponownie skompilować aplikację, lub znaleźć i naprawić błędy ręcznie w manifestach usługi. |
| Nie można pobrać aplikacji. Błąd uwierzytelniania.<br /><br /> Instalacja aplikacji nie powiodła się. Nie można zlokalizować plików aplikacji na serwerze. Aby uzyskać pomoc, skontaktuj się z wydawcą aplikacji lub z administratorem. | Nie można pobrać co najmniej jeden plik we wdrożeniu, ponieważ nie masz uprawnień dostępu do nich. Może to być spowodowane przez błąd 403 Zabroniony zwracanego przez serwer sieci Web, które mogą wystąpić, gdy jeden z plików w danym wdrożeniu kończy się rozszerzeniem, który sprawia, że serwer sieci Web, jej traktowała jako chroniony plik. Ponadto katalog, który zawiera jeden lub więcej plików aplikacji może wymagać nazwy użytkownika i hasła w celu uzyskania dostępu. |
| Nie można pobrać aplikację. Aplikacja nie ma wymaganych plików. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji lub administratorem systemu. | Nie można odnaleźć co najmniej jeden z plików wymienionych w manifeście aplikacji na serwerze. Sprawdź, czy zostały przekazane pliki zależne wszystkie wdrożenia i spróbuj ponownie. |
| Pobieranie aplikacji nie powiodła się. Sprawdź połączenie sieciowe lub skontaktuj się z administratorem systemu lub dostawcy usług sieciowych. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Nie można ustanowić połączenie sieciowe z serwerem. Sprawdź dostępność serwera i stan sieci. |
| URLDownloadToCacheFile nie powiodło się; wynik HRESULT "\<liczba >". Wystąpił błąd podczas próby pobrania "\<pliku >". | Jeśli użytkownik ustawił opcji zaawansowanych zabezpieczeń programu Internet Explorer "Ostrzegaj przy zmianie i nie tryb zabezpieczony" na komputerze docelowym wdrożenia i ustawienia adresu URL aplikacji ClickOnce, instalowana jest przekierowywany z niezabezpieczonego do bezpiecznego witryny (lub odwrotnie), instalacja będzie działać, ponieważ przerywa ostrzeżenie programu Internet Explorer, go.<br /><br /> Aby rozwiązać ten problem, wykonaj jedną z następujących zadań:<br /><br /> -Usuń zaznaczenie opcji zabezpieczeń.<br />-Upewnij się, że adres URL ustawień nie zostanie przekierowana w taki sposób, który zmienia tryby zabezpieczeń.<br />-Przekierowania całkowicie usunąć, a następnie wskaż adresu URL instalacji. |
| Wystąpił błąd podczas zapisywania na dysku twardym. Może być za mało miejsca dostępna na dysku. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji lub administratorem systemu. | Może to wskazywać na Brak miejsca na dysku do przechowywania aplikacji, ale może również oznaczać bardziej ogólny błąd We/Wy podczas próby zapisania plików aplikacji na dysku. |
| Nie można uruchomić aplikacji. Na dysku jest za mało dostępnego miejsca. | Dysk twardy jest pełny. Wyczyść off miejsca i spróbuj ponownie uruchomić aplikację. |
| Zbyt wiele aktywacji wdrożonej próby ładowania jednocześnie. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ogranicza liczbę różnych aplikacji, które można uruchomić w tym samym czasie. Pozwala to głównie pomoże zapewnić ochronę przed złośliwego próbuje podżegały ataków typu "odmowa usługi" na lokalny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usługi; Użytkownicy, którzy próbuje uruchomić ta sama aplikacja regularnie, w krótkim odstępie czasu, zostanie tylko znajdą się przy użyciu jednego wystąpienia aplikacja. |
| Skróty nie można aktywować za pośrednictwem sieci. | Skróty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację można uruchomić tylko na lokalnym dysku twardym. Nie zostały rozpoczęte, otwierając adres URL, który wskazuje plik skrótu, na serwerze zdalnym. |
| Aplikacja jest zbyt duży, aby działać w trybie online w częściowej relacji zaufania. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji lub administratorem systemu. | Aplikację, która działa w trybie częściowego zaufania nie może być większa niż połowy rozmiar przydziału aplikacji w trybie online, której wartością domyślną jest 250 MB. |

## <a name="see-also"></a>Zobacz także
- [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)