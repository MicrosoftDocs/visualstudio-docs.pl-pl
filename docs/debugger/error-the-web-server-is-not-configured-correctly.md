---
title: Błąd — serwer sieci Web nie jest prawidłowo skonfigurowany | Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 711297ef00c064c482ed3a86b896566b6e019534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460328"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Błąd: Serwer sieci Web nie jest prawidłowo skonfigurowany

Po pomyślnym wykonaniu kroków w celu rozwiązania problemu i przed ponowieniem próby debugowania należy zresetować usługi IIS. Możesz to zrobić, otwierając wiersz polecenia administratora i wpisując `iisreset` .

Wykonaj następujące kroki, aby rozwiązać ten problem:

1. Jeśli aplikacja sieci Web hostowana na serwerze jest skonfigurowana jako kompilacja wydania, należy ponownie opublikować ją jako kompilację debugowania i sprawdzić, czy plik web.config zawiera `debug=true` element kompilacja. Zresetuj usługi IIS i ponów próbę.

    Na przykład jeśli używasz profilu publikowania dla kompilacji wydania, Zmień ją na Debuguj i ponownie Opublikuj. W przeciwnym razie atrybut Debug zostanie ustawiony na `false` podczas publikowania.

2. SERWERZE Sprawdź, czy ścieżka fizyczna jest poprawna. W usługach IIS to ustawienie można znaleźć w **ustawieniach podstawowych > ścieżka fizyczna** (lub **Ustawienia zaawansowane** w starszych wersjach usług IIS).

    Ścieżka fizyczna może być niepoprawna, jeśli aplikacja sieci Web została skopiowana na inny komputer, ręcznie zmieniona lub przeniesiona. Zresetuj usługi IIS i ponów próbę.

3. Jeśli debugujesz lokalnie w programie Visual Studio, upewnij się, że we właściwościach wybrano poprawny serwer. (Otwórz **właściwości > serwery > sieci Web** lub **Właściwości > debugowanie** w zależności od typu projektu. W przypadku projektu formularzy sieci Web Otwórz **stronę właściwości > opcje uruchamiania > Server**).

    Jeśli używasz zewnętrznego (niestandardowego) serwera, takiego jak usługi IIS, adres URL musi być prawidłowy. W przeciwnym razie wybierz pozycję IIS Express i ponów próbę.

4. SERWERZE Upewnij się, że na serwerze jest zainstalowana poprawna wersja programu ASP.NET.

    Niezgodne wersje programu ASP.NET na serwerze IIS i w projekcie programu Visual Studio mogą spowodować ten problem. Może być konieczne ustawienie wersji platformy w web.config. Aby zainstalować ASP.NET w usługach IIS, użyj [Instalatora platformy sieci Web (Instalatora WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Należy również zapoznać się z artykułem [iis 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub, w przypadku ASP.NET Core, [hosta w systemie Windows z usługami IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Jeśli `maxConnection` limit w usługach IIS jest zbyt niski i masz zbyt wiele połączeń, może być konieczne [zwiększenie limitu połączeń](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Zobacz też
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)