---
title: 'Błąd: Nie można rozpocząć debugowania na serwerze sieci Web | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048765"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Błąd: Nie można rozpocząć debugowania na serwerze sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas debugowania aplikacji ASP.NET uruchomionych na serwerze sieci Web, może pojawić się ten komunikat o błędzie: Nie można rozpocząć debugowania na serwerze sieci Web.
  
W wielu przypadkach ten błąd występuje, ponieważ usługi IIS nie jest poprawnie skonfigurowany.

## <a name="vxtbshttpservererrorsthingstocheck"></a> Sprawdź konfigurację usług IIS

Po wykonaniu czynności, aby rozwiązać problem szczegółowe, w tym miejscu. Ponadto przed podjęciem ponownej próby debugowania, może być również konieczne Zresetuj usługi IIS. Możesz to zrobić, otwierając wiersza polecenia z uprawnieniami administratora i wpisując `iisreset`, lub można to zrobić w Menedżerze usług IIS. 

* Zatrzymywanie i ponowne uruchomienie puli aplikacji, a następnie spróbuj ponownie.

    Pula aplikacji może mieć została zatrzymana lub innej konfiguracji wprowadzone zmiany będą mogą wymagać zatrzymanie i ponowne uruchomienie puli aplikacji.
    
    > [!NOTE]
    > Przechowuje Zatrzymywanie puli aplikacji, konieczne może odinstalować moduł ponowne zapisywanie adresów URL z Panelu sterowania, a następnie zainstaluj go przy użyciu Instalatora platformy sieci Web (usługi). Być może wystąpił problem po uaktualnieniu systemu znaczące.

* Sprawdź konfigurację puli aplikacji, popraw go w razie potrzeby, a następnie ponów próbę wykonania.

    Poświadczenia hasła zostały zmienione, konieczne może zaktualizować je w puli aplikacji. Ponadto jeśli niedawno zainstalowano program ASP.NET, puli aplikacji może być skonfigurowany do niewłaściwej wersji programu ASP.NET. Rozwiąż problem i ponownie uruchom pulę aplikacji.
    
* Sprawdź, czy folder aplikacji sieci Web ma odpowiednie uprawnienia.

    Upewnij się, nadaj IIS_IUSRS lub IUSR (lub określonego użytkownika, które są skojarzone z pulą aplikacji) Odczyt i wykonywanie praw do folderu aplikacji sieci Web. Rozwiąż problem i ponowne uruchomienie puli aplikacji.

* Jeśli używasz pliku HOSTS przy użyciu adresów lokalnych, spróbuj użyć adresu sprzężenia zwrotnego zamiast adresu IP komputera.

* Wyświetlenie strony hosta lokalnego, w przeglądarce.

     Jeśli usługi IIS nie jest zainstalowany poprawnie, powinny występują błędy podczas wpisywania tekstu `http://localhost` w przeglądarce.
     
     Aby dowiedzieć się, jak wdrażanie w usługach IIS, zobacz [zdalnego debugowania ASP.NET, na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) lub dla platformy ASP.NET Core [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Upewnij się, że zainstalowano poprawną wersję platformy ASP.NET, w usługach IIS.  Zobacz [wdrożyć aplikację ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) lub dla platformy ASP.NET Core [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Tworzenie podstawowej aplikacji ASP.NET na serwerze.

     Jeśli nie można pobrać aplikację do pracy z debugerem, spróbuj utworzyć podstawową aplikację ASP.NET lokalnie na serwerze i spróbuj debugować podstawową aplikację. Jeśli debugujesz podstawowej aplikacji, które pomogą Ci określenie, jakie są różnice między dwie konfiguracje.
  
* Rozwiązywanie błędów uwierzytelniania, jeśli używasz tylko adres IP

     Domyślnie adresy IP są uważane za część Internet, a uwierzytelnianie NTLM nie odbywa się za pośrednictwem Internetu. Jeśli witryna sieci web jest skonfigurowana w usługach IIS, aby wymagać uwierzytelniania, to uwierzytelnianie nie powiedzie się. Aby rozwiązać ten problem, można określić nazwę komputera zdalnego zamiast adresu IP.
     
## <a name="other-causes"></a>Inne przyczyny

Jeśli używasz starszej wersji programu Visual Studio:

- Uruchom program Visual Studio z podwyższonym poziomem uprawnień i spróbuj ponownie.

    Usterkę w starszych wersjach (stałe później) wymagane podniesione uprawnienia w programie ASP.NET: niektóre debugowania scenariuszy.
    
- Jeśli korzystasz z wielu wystąpień programu Visual Studio, ponownie otwórz projekt w jednym wystąpieniu programu Visual Studio i spróbuj ponownie.

## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
