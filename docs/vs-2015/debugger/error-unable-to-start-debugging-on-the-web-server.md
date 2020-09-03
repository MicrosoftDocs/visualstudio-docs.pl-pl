---
title: 'Błąd: nie można rozpocząć debugowania na serwerze sieci Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
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
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185485"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Błąd: Nie można rozpocząć debugowania na serwerze sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas próby debugowania aplikacji ASP.NET działającej na serwerze sieci Web może zostać wyświetlony następujący komunikat o błędzie: nie można rozpocząć debugowania na serwerze sieci Web.
  
W wielu przypadkach ten błąd występuje, ponieważ usługi IIS nie są poprawnie skonfigurowane.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Sprawdź konfigurację usług IIS

Po wykonaniu kroków, aby rozwiązać problem opisany tutaj i przed ponowną próbą debugowania, może być również konieczne zresetowanie usług IIS. Możesz to zrobić, otwierając wiersz polecenia administratora i wpisując polecenie `iisreset` lub w Menedżerze usług IIS. 

* Zatrzymaj i uruchom ponownie pule aplikacji, a następnie ponów próbę.

    Pula aplikacji mogła zostać zatrzymana lub inna wprowadzona zmiana konfiguracji może wymagać zatrzymania i ponownego uruchomienia puli aplikacji.
    
    > [!NOTE]
    > Jeśli pula aplikacji pozostaje zatrzymana, może być konieczne odinstalowanie modułu ponowne zapisywanie adresów URL z panelu sterowania, a następnie ponowne jego zainstalowanie przy użyciu Instalatora platformy sieci Web (WPI). Może to być problem po znaczącym uaktualnieniu systemu.

* Sprawdź konfigurację puli aplikacji, w razie konieczności Popraw ją, a następnie ponów próbę.

    Jeśli poświadczenia hasła zostały zmienione, może być konieczne zaktualizowanie ich w puli aplikacji. Ponadto, jeśli niedawno zainstalowano ASP.NET, Pula aplikacji może być skonfigurowana dla niewłaściwej wersji programu ASP.NET. Usuń problem i ponownie uruchom pulę aplikacji.
    
* Sprawdź, czy folder aplikacji sieci Web ma odpowiednie uprawnienia.

    Upewnij się, że nadajesz IIS_IUSRS lub IUSR (lub określony użytkownik skojarzony z pulą aplikacji) prawa do odczytu i wykonywania dla folderu aplikacji sieci Web. Usuń problem i ponownie uruchom pulę aplikacji.

* Jeśli używasz pliku HOSTs z adresami lokalnymi, spróbuj użyć adresu sprzężenia zwrotnego zamiast adresu IP maszyny.

* Wywołaj stronę localhost w przeglądarce.

     Jeśli usługi IIS nie są poprawnie zainstalowane, podczas wpisywania w przeglądarce należy uzyskać błędy `http://localhost` .
     
     Aby uzyskać informacje o wdrażaniu w usługach IIS, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) lub, w przypadku ASP.NET Core, [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Upewnij się, że w usługach IIS została zainstalowana poprawna wersja programu ASP.NET.  Zobacz [wdrażanie aplikacji ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) lub, w przypadku ASP.NET Core, [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Utwórz podstawową aplikację ASP.NET na serwerze.

     Jeśli nie możesz pobrać aplikacji z debugerem, spróbuj utworzyć podstawową aplikację ASP.NET lokalnie na serwerze, a następnie spróbuj debugować podstawową aplikację. Jeśli możesz debugować podstawową aplikację, która może pomóc w określeniu, czym się różnią między obiema konfiguracjami.
  
* Rozwiązywanie problemów z uwierzytelnianiem, jeśli używany jest tylko adres IP

     Domyślnie adresy IP są traktowane jako część Internetu, a uwierzytelnianie NTLM nie odbywa się za pośrednictwem Internetu. Jeśli witryna sieci Web jest skonfigurowana w usługach IIS w celu wymagania uwierzytelniania, to uwierzytelnianie nie powiedzie się. Aby rozwiązać ten problem, można określić nazwę komputera zdalnego zamiast adresu IP.
     
## <a name="other-causes"></a>Inne przyczyny

Jeśli używasz starszej wersji programu Visual Studio:

- Uruchom ponownie program Visual Studio z podniesionymi uprawnieniami i spróbuj ponownie.

    Usterka w starszych wersjach (naprawiona później) wymagała podwyższonego poziomu uprawnień w niektórych scenariuszach debugowania ASP.NET.
    
- Jeśli jest uruchomione wiele wystąpień programu Visual Studio, Otwórz ponownie projekt w jednym wystąpieniu programu Visual Studio i spróbuj ponownie.

## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
