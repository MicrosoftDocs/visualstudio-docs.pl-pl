---
title: 'Błąd: Serwer sieci web nie jest poprawnie skonfigurowany. | Dokumentacja firmy Microsoft'
ms.date: 09/20/2017
ms.topic: troubleshooting
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
ms.openlocfilehash: fd59211da9228f2940c675f889d0536fbea9045d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019195"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Błąd: Serwer internetowy nie został poprawnie skonfigurowany

Po wykonaniu czynności przedstawione w tym miejscu w celu rozwiązania problemu i przed podjęciem ponownej próby debugowania konieczne może być Zresetuj usługi IIS. Możesz to zrobić, otwierając wiersza polecenia z uprawnieniami administratora i wpisując `iisreset`.

Wykonaj następujące czynności, aby rozwiązać ten problem:

1. Jeśli aplikacja sieci web hostowanych na serwerze jest skonfigurowany jako kompilację wydania ponownie opublikować jako kompilację debugowania i sprawdź, czy plik web.config zawiera `debug=true` w elemencie kompilacji. Zresetuj usługi IIS, a następnie spróbuj ponownie.

    Na przykład jeśli używasz profilu publikacji dla kompilacji oficjalnej, zmień ją na debugowania i ponownie opublikuj. W przeciwnym razie zostanie ustawiony atrybut debugowania `false` po opublikowaniu.

2. (IIS) Sprawdź poprawność ścieżki fizycznej. W usługach IIS, możesz znaleźć tego ustawienia w **podstawowe ustawienia > Ścieżka fizyczna** (lub **Zaawansowane ustawienia** w starszych wersjach usług IIS).

    Jeśli aplikacja sieci web został skopiowany do innej maszyny, ręcznie przeniesiony lub może być nieprawidłowa ścieżka fizyczna. Zresetuj usługi IIS, a następnie spróbuj ponownie.

3. Jeśli debugujesz lokalnie w programie Visual Studio, sprawdź, czy właściwym serwerem jest zaznaczone w oknie właściwości. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** w zależności od typu projektu. Projekt formularzy sieci Web otwórz **strony właściwości > opcje Start > serwer**).

    Jeśli używasz zewnętrznego serwera (niestandardowy), takich jak usługi IIS, adres URL musi być prawidłowy. W przeciwnym razie wybierz usług IIS Express, a następnie spróbuj ponownie.

4. (IIS) Upewnij się, że na serwerze zainstalowano poprawną wersję platformy ASP.NET.

    Niezgodność wersji platformy ASP.NET w usługach IIS i w projekcie programu Visual Studio może być przyczyną tego problemu. Może być konieczne ustawienie wersji framework w pliku web.config. Aby zainstalować program ASP.NET w usługach IIS, należy użyć [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Zobacz też [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub dla platformy ASP.NET Core [hosta w Windows z programem IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Jeśli `maxConnection` limit w usługach IIS jest zbyt niska i masz zbyt wiele połączeń, konieczne może być [zwiększyć limit połączeń](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)