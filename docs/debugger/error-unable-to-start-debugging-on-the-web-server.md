---
title: 'Błąd: Nie można rozpocząć debugowania na serwerze sieci Web | Dokumentacja firmy Microsoft'
ms.date: 05/23/2018
ms.topic: troubleshooting
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
ms.openlocfilehash: 53ffc893b63447ab75a439ea1e093ddaf4b75645
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067134"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Błąd: Nie można rozpocząć debugowania na serwerze sieci Web

Podczas debugowania aplikacji ASP.NET uruchomionych na serwerze sieci Web, może wystąpić ten komunikat o błędzie: `Unable to start debugging on the Web server`.

Często ten błąd występuje, ponieważ wystąpił błąd podczas zmiany lub konfiguracji, wymagającego aktualizacji pul aplikacji i/lub resetowanie usług IIS. Możesz zresetować usług IIS, otwierając wiersz polecenia i wpisując `iisreset`.

## <a name="specificerrors"></a>Co to jest komunikat szczegółowy komunikat o błędzie?

`Unable to start debugging on the Web server` Jest ogólny komunikat. Zazwyczaj bardziej szczegółowy komunikat o błędzie, w której znajduje się w ciąg błędu i zidentyfikować przyczynę problemu lub Wyszukaj, aby dokładniej poprawki, może pomóc. Poniżej przedstawiono niektóre typowe komunikaty o błędach, które są dołączane do komunikatu o błędzie główne:

- [Usługi IIS nie ma witryny sieci Web, która pasuje do uruchomienia adresu url](#IISlist)
- [Serwer sieci web nie jest poprawnie skonfigurowany.](#web_server_config)
- [Nie można nawiązać połączenia z serwera sieci Web](#unabletoconnect)
- [Serwer sieci web nie odpowiedział w odpowiednim czasie](#webservertimeout)
- [Microsoft visual studio dla zdalnego debugowania monitor(msvsmon.exe) zdaje się nie być uruchomiona na komputerze zdalnym](#msvsmon)
- [Serwer zdalny zwrócił błąd](#server_error)
- [Nie można rozpocząć debugowania ASP.NET](#aspnet)
- [Debuger nie może połączyć się z komputerem zdalnym](#cannot_connect)
- [Zobacz Pomoc dla typowych błędów konfiguracji. Uruchamianie na stronie sieci Web poza debugerem może dostarczyć więcej informacji.](#see_help)

## <a name="IISlist"></a> Usługi IIS nie ma witryny sieci Web, która pasuje do uruchomienia adresu url

- Uruchom program Visual Studio jako Administrator i spróbuj ponownie debugowanie. (Niektóre scenariusze debugowania ASP.NET wymaga podwyższonego poziomu uprawnień).

    Można skonfigurować program Visual Studio można zawsze uruchomić się jako Administrator, klikając prawym przyciskiem myszy ikonę skrótu prowadzącą programu Visual Studio, wybierając **właściwości > Zaawansowane**, a następnie wybierając zawsze Uruchom jako Administrator.

## <a name="web_server_config"></a> Serwer sieci web nie jest poprawnie skonfigurowany.

- Zobacz [błąd: Serwer sieci web nie jest poprawnie skonfigurowany](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Nie można nawiązać połączenia z serwera sieci Web

- Uruchamianie programu Visual Studio i serwera sieci Web na tym samym komputerze i debugowanie przy użyciu **F5** (zamiast **dołączyć do procesu**)? Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany nawiązać połączenie z właściwym serwerem sieci Web i adres URL do uruchomienia. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** w zależności od typu projektu. Projekt formularzy sieci Web otwórz **strony właściwości > opcje Start > serwer**.)

- W przeciwnym razie ponowne uruchomienie puli aplikacji, a następnie Zresetuj usługi IIS. Aby uzyskać więcej informacji, zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Serwer sieci web nie odpowiedział w odpowiednim czasie

- Zresetuj usługi IIS i spróbuj ponownie debugowanie. Wiele wystąpień debugera może zostać dołączony do proces usług IIS; Resetowanie kończy je. Aby uzyskać więcej informacji, zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Microsoft visual studio dla zdalnego debugowania monitor(msvsmon.exe) zdaje się nie być uruchomiona na komputerze zdalnym

- Jeśli debugujesz na komputerze zdalnym, upewnij się, masz [zainstalowane i działają zdalny debuger](../debugger/remote-debugging.md). Jeśli komunikat nazwa zapora, upewnij się, [Popraw porty w zaporze](../debugger/remote-debugger-port-assignments.md) są otwarte, zwłaszcza, jeśli używasz zapory innych firm.
- Jeśli używasz pliku HOSTS, upewnij się, że został on poprawnie skonfigurowany. Na przykład, jeśli debugowanie przy użyciu **F5** (zamiast **dołączyć do procesu**), HOSTY plik musi zawierać ten sam adres URL projektu, tak jak w swojej właściwości projektu **właściwości > sieci Web > serwery**  lub **właściwości > debugowanie**, w zależności od typu projektu.

## <a name="server_error"></a> Serwer zdalny zwrócił błąd

Sprawdź swoje [pliku dziennika usług IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) kody błędów podrzędne i dodatkowe informacje oraz tym IIS 7 [wpis w blogu](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Ponadto poniżej przedstawiono niektóre typowe kody błędów i kilka propozycji.
- (403) zabroniony. Istnieje wiele możliwych przyczyn tego błędu, dlatego należy sprawdzić plik dziennika i ustawienia zabezpieczeń programu IIS dla witryny sieci web. Upewnij się, zawiera web.config serwera `debug=true` w elemencie kompilacji. Upewnij się, że folder aplikacji sieci Web ma odpowiednie uprawnienia i czy konfigurację puli aplikacji jest poprawna, (mógł ulec zmianie hasła). Zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck). Jeśli debugujesz lokalnie te ustawienia są już prawidłowe, również sprawdzić, czy łączysz do poprawnego typu serwera i adres URL (w **właściwości > sieci Web > serwery** lub **właściwości > debugowanie**, w zależności od typu projektu).
- Serwer (503) jest niedostępny. Pula aplikacji może została zatrzymana z powodu błędu lub konfiguracji zmiany. Ponowne uruchomienie puli aplikacji.
- (404) nie można odnaleźć. Upewnij się, że pula aplikacji jest skonfigurowana dla odpowiedniej wersji programu ASP.NET.

## <a name="aspnet"></a> Nie można rozpocząć debugowania ASP.NET

- Ponowne uruchomienie puli aplikacji i Zresetuj usługi IIS. Aby uzyskać więcej informacji, zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).
- Jeśli przeprowadzasz ponownie zapisuje adresu URL, test podstawowy plik web.config z nie ponownego adresu URL. Zobacz **Uwaga** o adresie URL Nadpisz modułu w [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Debuger nie może połączyć się z komputerem zdalnym

Jeśli debugujesz lokalnie, ten błąd może wystąpić, ponieważ program Visual Studio jest 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania 64-bitowych aplikacji. Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany do łączenia się prawidłowy serwer sieci Web i adres URL. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** w zależności od typu projektu.)

Jeśli używasz pliku HOSTS, upewnij się, że został on poprawnie skonfigurowany. Na przykład hostów plik musi zawierać ten sam adres URL projektu, tak jak w swojej właściwości projektu **właściwości > sieci Web > serwery** lub **właściwości > debugowanie**, w zależności od typu projektu.

## <a name="see_help"></a> Zobacz Pomoc dla typowych błędów konfiguracji. Uruchamianie na stronie sieci Web poza debugerem może dostarczyć więcej informacji.

- Czy używasz programu Visual Studio i serwera sieci Web na tym samym komputerze? Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany nawiązać połączenie z właściwym serwerem sieci Web i adres URL do uruchomienia. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** w zależności od typu projektu.)

- Jeśli to nie pomoże, lub debugujesz zdalnie, wykonaj czynności opisane w [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="vxtbshttpservererrorsthingstocheck"></a> Sprawdź konfigurację usług IIS

Po wykonaniu czynności przedstawione w tym miejscu w celu rozwiązania problemu i przed podjęciem ponownej próby debugowania konieczne może być Zresetuj usługi IIS. Możesz to zrobić, otwierając wiersz polecenia i wpisując `iisreset`.

* Zatrzymaj i uruchom ponownie pul aplikacji usług IIS, a następnie spróbuj ponownie.

    Pula aplikacji może mieć została zatrzymana, w wyniku błędu. Lub innej konfiguracji wprowadzone zmiany będą mogą wymagać zatrzymanie i ponowne uruchomienie puli aplikacji.

    > [!NOTE]
    > Przechowuje Zatrzymywanie puli aplikacji, może być konieczne odinstalowanie moduł ponowne zapisywanie adresów URL w Panelu sterowania. Można było go zainstalować za pomocą Instalatora platformy sieci Web (WebPI). Ten problem może wystąpić po uaktualnieniu systemu znaczące.

* Sprawdź konfigurację puli aplikacji, popraw go w razie potrzeby, a następnie ponów próbę wykonania.

    Pula aplikacji może być skonfigurowany dla wersji programu ASP.NET, która jest niezgodna z projektu programu Visual Studio. Zaktualizuj wersję platformy ASP.NET w puli aplikacji, a następnie uruchom go ponownie. Aby uzyskać szczegółowe informacje, zobacz [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ponadto jeśli poświadczeń haseł zostały zmienione, konieczne może być je zaktualizować w puli aplikacji lub witryny sieci Web.  W tej puli aplikacji, należy zaktualizować poświadczenia w **Zaawansowane ustawienia > Model procesu > tożsamości**. Dla witryny sieci Web, należy zaktualizować poświadczenia w **podstawowe ustawienia > Połącz jako...** . Ponowne uruchomienie puli aplikacji.

* Sprawdź, czy folder aplikacji sieci Web ma odpowiednie uprawnienia.

    Upewnij się, że zapewniają IIS_IUSRS, IUSR, lub określonego użytkownika skojarzony z [puli aplikacji](/iis/manage/configuring-security/application-pool-identities) Odczyt i wykonywanie praw do folderu aplikacji sieci Web. Rozwiąż problem i ponowne uruchomienie puli aplikacji.

* Upewnij się, że zainstalowano poprawną wersję platformy ASP.NET, w usługach IIS.

    Niezgodność wersji platformy ASP.NET w usługach IIS i w projekcie programu Visual Studio może być przyczyną tego problemu. Może być konieczne ustawienie wersji framework w pliku web.config. Aby zainstalować program ASP.NET w usługach IIS, należy użyć [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Zobacz też [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub dla platformy ASP.NET Core [hosta w Windows z programem IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Rozwiązywanie błędów uwierzytelniania, jeśli używasz tylko adres IP

     Domyślnie adresy IP są uważane za część Internet, a uwierzytelnianie NTLM nie odbywa się za pośrednictwem Internetu. Jeśli witryna sieci web jest skonfigurowana w usługach IIS, aby wymagać uwierzytelniania, uwierzytelnianie nie powiedzie się. Aby rozwiązać ten problem, można określić nazwę komputera zdalnego zamiast adresu IP.

## <a name="other-causes"></a>Inne przyczyny

Jeśli konfiguracji usług IIS nie jest źródłem problemu, spróbuj wykonać następujące czynności:

- Uruchom program Visual Studio z uprawnieniami administratora i spróbuj ponownie.

    Niektóre scenariusze debugowania ASP.NET, takich jak za pomocą narzędzia Web Deploy wymaga podwyższonego poziomu uprawnień dla programu Visual Studio.

- Jeśli korzystasz z wielu wystąpień programu Visual Studio, otwórz projekt w jednym wystąpieniu programu Visual Studio (z uprawnieniami administratora), a następnie spróbuj ponownie.

- Jeśli używasz pliku HOSTS przy użyciu adresów lokalnych, spróbuj użyć adresu sprzężenia zwrotnego zamiast adresu IP komputera.

    Jeśli nie używasz adresów lokalnych, upewnij się, plik hostów zawiera ten sam adres URL projektu, tak jak w swojej właściwości projektu **właściwości > sieci Web > serwery** lub **właściwości > debugowanie**, w zależności od usługi Typ projektu.

## <a name="more-troubleshooting-steps"></a>Dodatkowe kroki rozwiązywania

* Wyświetlenie strony hosta lokalnego, w przeglądarce na serwerze.

     Jeśli usługi IIS nie jest zainstalowany poprawnie, powinny występują błędy podczas wpisywania tekstu `http://localhost` w przeglądarce.

     Aby uzyskać więcej informacji na temat wdrażania usług IIS, zobacz [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) i dla platformy ASP.NET Core [hosta w Windows z programem IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Tworzenie podstawowej aplikacji ASP.NET na serwerze (lub przy użyciu pliku web.config podstawowych).

    Jeśli nie można pobrać aplikację do pracy z debugerem, spróbuj utworzyć podstawową aplikację ASP.NET lokalnie na serwerze i spróbuj debugować podstawową aplikację. (Można użyć domyślnego szablonu platformy ASP.NET MVC.) Jeśli debugujesz podstawowej aplikacji, które pomogą Ci określenie, jakie są różnice między dwie konfiguracje. Poszukaj różnice w ustawieniach w pliku web.config, takie jak reguły ponownego zapisywania adresów URL.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)