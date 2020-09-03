---
title: Błąd — nie można rozpocząć debugowania na serwerze sieci Web | Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00d27dafd5e44b058cff05b3c478322e45242b3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460042"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Błąd: Nie można rozpocząć debugowania na serwerze sieci Web

Podczas próby debugowania aplikacji ASP.NET działającej na serwerze sieci Web może zostać wyświetlony następujący komunikat o błędzie: `Unable to start debugging on the Web server` .

Często ten błąd występuje, ponieważ wystąpił błąd lub zmiana konfiguracji, która wymaga aktualizacji pul aplikacji, resetowania usług IIS lub obu. Możesz zresetować usługi IIS, otwierając wiersz polecenia z podwyższonym poziomem uprawnień i wpisując `iisreset` .

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Co to jest szczegółowy komunikat o błędzie?

`Unable to start debugging on the Web server`Komunikat jest ogólny. Zwykle w ciągu błędu jest zawarty bardziej szczegółowy komunikat, który może pomóc w zidentyfikowaniu przyczyny problemu lub wyszukaniu bardziej dokładnej poprawki. Poniżej przedstawiono kilka typowych komunikatów o błędach, które są dołączane do głównego komunikatu o błędzie:

- [Usługi IIS nie wyświetlają witryny sieci Web zgodnej z adresem URL uruchamiania](#IISlist)
- [Serwer internetowy nie został poprawnie skonfigurowany](#web_server_config)
- [Nie można nawiązać połączenia z serwerem](#unabletoconnect)
- [Serwer sieci Web nie odpowiedział w odpowiednim czasie](#webservertimeout)
- [Monitor zdalnego debugowania programu Microsoft Visual Studio (msvsmon.exe) nie jest uruchomiony na komputerze zdalnym](#msvsmon)
- [Serwer zdalny zwrócił błąd](#server_error)
- [Nie można rozpocząć debugowania ASP.NET](#aspnet)
- [Debuger nie może nawiązać połączenia z komputerem zdalnym](#cannot_connect)
- [Zobacz pomoc dotyczącą typowych błędów konfiguracji. Uruchomienie strony sieci Web poza debugerem może dostarczyć więcej informacji.](#see_help)
- [Operacja nie jest obsługiwana. Nieznany błąd: *ErrorNumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> Usługi IIS nie wyświetlają witryny sieci Web zgodnej z adresem URL uruchamiania

- Uruchom ponownie program Visual Studio jako administrator i ponów próbę debugowania. (Niektóre scenariusze debugowania ASP.NET wymagają podniesionych uprawnień).

    Program Visual Studio można skonfigurować tak, aby zawsze był uruchamiany jako administrator, klikając prawym przyciskiem myszy ikonę skrótu programu Visual Studio, wybierając **właściwości > zaawansowane**, a następnie wybierając opcję Zawsze uruchamiaj jako administrator.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Serwer sieci Web nie jest prawidłowo skonfigurowany

- Zobacz [błąd: serwer sieci Web nie jest prawidłowo skonfigurowany](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Nie można nawiązać połączenia z serwerem

- Czy używasz programu Visual Studio i serwera sieci Web na tym samym komputerze i debugowania przy użyciu klawisza **F5** (zamiast **dołączania do procesu**)? Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany do nawiązywania połączenia z prawidłowym serwerem sieci Web i adresem URL uruchomienia. (Otwórz **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie** w zależności od typu projektu. W przypadku projektu formularzy sieci Web Otwórz **stronę właściwości > opcje uruchamiania > Server**).

- W przeciwnym razie ponownie uruchom pulę aplikacji, a następnie zresetuj usługi IIS. Aby uzyskać więcej informacji, zobacz [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Serwer sieci Web nie odpowiedział w odpowiednim czasie

- Zresetuj usługi IIS i ponów próbę debugowania. Do procesu usług IIS mogą być dołączone wiele wystąpień debugera; Resetowanie kończy się. Aby uzyskać więcej informacji, zobacz [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Monitor zdalnego debugowania programu Microsoft Visual Studio (msvsmon.exe) nie jest uruchomiony na komputerze zdalnym

- W przypadku debugowania na maszynie zdalnej upewnij się, że [zainstalowano i uruchomiono zdalny debuger](../debugger/remote-debugging.md). Jeśli komunikat zawiera informacje o zaporze, upewnij się, że [w zaporze są otwarte odpowiednie porty](../debugger/remote-debugger-port-assignments.md) , zwłaszcza jeśli używasz zapory innej firmy.
- Jeśli używasz pliku HOSTs, upewnij się, że jest prawidłowo skonfigurowany. Na przykład jeśli debugowanie przy użyciu klawisza **F5** (zamiast **dołączania do procesu**), plik hosts musi zawierać ten sam adres URL projektu, co we właściwościach projektu, **Właściwości > serwery > sieci Web** lub **Właściwości > debugowanie**, w zależności od typu projektu.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Serwer zdalny zwrócił błąd

Sprawdź, czy w [pliku dziennika usług IIS zarejestrowano](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) błędy i dodatkowe informacje oraz wpis w [blogu](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)usług IIS 7.

Ponadto poniżej przedstawiono niektóre typowe kody błędów i kilka sugestii.
- (403) Zabronione. Istnieje wiele możliwych przyczyn tego błędu, dlatego sprawdź plik dziennika oraz ustawienia zabezpieczeń usług IIS dla witryny sieci Web. Upewnij się, że web.config serwera zawiera `debug=true` element kompilacja. Upewnij się, że folder aplikacji sieci Web ma odpowiednie uprawnienia i że konfiguracja puli aplikacji jest poprawna (hasło mogło ulec zmianie). Zobacz [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck). Jeśli te ustawienia są już poprawne i debugowanie jest wykonywane lokalnie, należy również sprawdzić, czy łączysz się z prawidłowym typem serwera i adresem URL (w obszarze **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie**, w zależności od typu projektu).
- (503) serwer jest niedostępny. Pula aplikacji mogła zostać zatrzymana z powodu błędu lub zmiany konfiguracji. Ponownie uruchom pulę aplikacji.
- nie znaleziono (404). Upewnij się, że Pula aplikacji została skonfigurowana pod kątem poprawnej wersji ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a> Nie można rozpocząć debugowania ASP.NET

- Ponownie uruchom pulę aplikacji i zresetuj usługi IIS. Aby uzyskać więcej informacji, zobacz [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck).
- Jeśli wykonujesz ponowne zapisywanie adresów URL, przetestuj podstawową web.config bez ponownego zapisywania adresów URL. Zapoznaj **się z informacjami na** temat modułu ponowne zapisywanie adresów URL w temacie [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Debuger nie może nawiązać połączenia z komputerem zdalnym

Jeśli debugujesz lokalnie, Otwórz właściwości projektu w programie Visual Studio i upewnij się, że projekt jest skonfigurowany do nawiązywania połączenia z prawidłowym serwerem sieci Web i adresem URL. (Otwórz **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie** w zależności od typu projektu).

Ten błąd może wystąpić w przypadku debugowania lokalnego, ponieważ program Visual Studio jest aplikacją 32-bitową, więc używa wersji 64-bitowej zdalnego debugera do debugowania aplikacji 64-bitowych. Sprawdź pulę aplikacji w usługach IIS, aby upewnić się, że włączono **aplikacje 32-bitowe** `true` , uruchom ponownie usługi IIS i spróbuj ponownie.

Ponadto, jeśli używasz pliku HOSTs, upewnij się, że jest prawidłowo skonfigurowany. Na przykład plik HOSTs musi zawierać ten sam adres URL projektu, jak we właściwościach projektu, **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie**, w zależności od typu projektu.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Zobacz pomoc dotyczącą typowych błędów konfiguracji. Uruchomienie strony sieci Web poza debugerem może dostarczyć więcej informacji.

- Czy używasz programu Visual Studio i serwera sieci Web na tym samym komputerze? Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany do nawiązywania połączenia z prawidłowym serwerem sieci Web i adresem URL uruchomienia. (Otwórz **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie** w zależności od typu projektu).

- Jeśli to nie zadziała lub debugujesz zdalnie, wykonaj kroki opisane w sekcji [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> Operacja nie jest obsługiwana. Nieznany błąd: *ErrorNumber*

Jeśli wykonujesz ponowne zapisywanie adresów URL, przetestuj podstawową web.config bez ponownego zapisywania adresów URL. Zapoznaj **się z informacjami na** temat modułu ponowne zapisywanie adresów URL w temacie [Sprawdzanie konfiguracji usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Sprawdź konfigurację usług IIS

Po pomyślnym wykonaniu kroków w celu rozwiązania problemu i przed ponowieniem próby debugowania należy zresetować usługi IIS. Możesz to zrobić, otwierając wiersz polecenia z podwyższonym poziomem uprawnień i wpisując `iisreset` .

* Zatrzymaj i uruchom ponownie pule aplikacji IIS, a następnie ponów próbę.

    Pula aplikacji mogła zostać zatrzymana w wyniku błędu. Inna wprowadzona zmiana konfiguracji może wymagać zatrzymania i ponownego uruchomienia puli aplikacji.

    > [!NOTE]
    > Jeśli pula aplikacji pozostaje zatrzymana, może być konieczne odinstalowanie modułu ponowne zapisywanie adresów URL z panelu sterowania. Można zainstalować ją ponownie za pomocą Instalatora platformy sieci Web (Instalatora WebPI). Ten problem może wystąpić po znaczącym uaktualnieniu systemu.

* Sprawdź konfigurację puli aplikacji, w razie konieczności Popraw ją, a następnie ponów próbę.

    Pula aplikacji może być skonfigurowana dla wersji ASP.NET, która nie jest zgodna z projektem programu Visual Studio. Zaktualizuj wersję ASP.NET w puli aplikacji i uruchom ją ponownie. Aby uzyskać szczegółowe informacje, zobacz [IIS 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ponadto jeśli poświadczenia hasła zostały zmienione, może być konieczne ich zaktualizowanie w puli aplikacji lub w witrynie sieci Web.  W puli aplikacji zaktualizuj poświadczenia w **ustawieniach zaawansowanych > model procesu > tożsamość**. W przypadku witryny sieci Web zaktualizuj poświadczenia w **ustawieniach podstawowych > Połącz jako...**. Ponownie uruchom pulę aplikacji.

* Sprawdź, czy folder aplikacji sieci Web ma odpowiednie uprawnienia.

    Upewnij się, że nadajesz IIS_IUSRS, IUSR lub określony użytkownik skojarzony z [pulą aplikacji](/iis/manage/configuring-security/application-pool-identities) uprawnienia do odczytu i wykonywania dla folderu aplikacji sieci Web. Usuń problem i ponownie uruchom pulę aplikacji.

* Upewnij się, że w usługach IIS została zainstalowana poprawna wersja programu ASP.NET.

    Niezgodne wersje programu ASP.NET na serwerze IIS i w projekcie programu Visual Studio mogą spowodować ten problem. Może być konieczne ustawienie wersji platformy w web.config. Aby zainstalować ASP.NET w usługach IIS, użyj [Instalatora platformy sieci Web (Instalatora WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Należy również zapoznać się z artykułem [iis 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub, w przypadku ASP.NET Core, [hosta w systemie Windows z usługami IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Rozwiązywanie problemów z uwierzytelnianiem, jeśli używany jest tylko adres IP

     Domyślnie adresy IP są traktowane jako część Internetu, a uwierzytelnianie NTLM nie odbywa się za pośrednictwem Internetu. Jeśli witryna sieci Web jest skonfigurowana w usługach IIS w celu wymagania uwierzytelniania, to uwierzytelnianie nie powiedzie się. Aby rozwiązać ten problem, można określić nazwę komputera zdalnego zamiast adresu IP.

## <a name="other-causes"></a>Inne przyczyny

Jeśli konfiguracja usług IIS nie powoduje problemu, spróbuj wykonać następujące czynności:

- Uruchom ponownie program Visual Studio z uprawnieniami administratora i spróbuj ponownie.

    Niektóre scenariusze debugowania ASP.NET, takie jak używanie Web Deploy wymagają podniesionych uprawnień dla programu Visual Studio.

- Jeśli działa wiele wystąpień programu Visual Studio, Otwórz ponownie projekt w jednym wystąpieniu programu Visual Studio (z uprawnieniami administratora) i spróbuj ponownie.

- Jeśli używasz pliku HOSTs z adresami lokalnymi, spróbuj użyć adresu sprzężenia zwrotnego zamiast adresu IP maszyny.

    Jeśli nie korzystasz z adresów lokalnych, upewnij się, że plik HOSTs zawiera ten sam adres URL projektu, jak we właściwościach projektu, **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie**, w zależności od typu projektu.

## <a name="more-troubleshooting-steps"></a>Więcej kroków rozwiązywania problemów

* Wywołaj stronę localhost w przeglądarce na serwerze programu.

     Jeśli usługi IIS nie są poprawnie zainstalowane, podczas wpisywania w przeglądarce należy uzyskać błędy `http://localhost` .

     Aby uzyskać więcej informacji na temat wdrażania usług IIS, zobacz [iis 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oraz, w przypadku ASP.NET Core, [host w systemie Windows z usługami IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Utwórz podstawową aplikację ASP.NET na serwerze (lub użyj podstawowego pliku web.config).

    Jeśli nie możesz pobrać aplikacji z debugerem, spróbuj utworzyć podstawową aplikację ASP.NET lokalnie na serwerze, a następnie spróbuj debugować podstawową aplikację. (Możesz chcieć użyć domyślnego szablonu MVC ASP.NET). Jeśli możesz debugować podstawową aplikację, która może pomóc w określeniu, czym się różnią między obiema konfiguracjami. Poszukaj różnic w ustawieniach w pliku web.config, takich jak reguły ponownego zapisywania adresów URL.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)