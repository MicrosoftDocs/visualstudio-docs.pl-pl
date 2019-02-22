---
title: Znajdź uruchomionego procesu ASP.NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 27221a4ae47b9fb06130b550ceb6d3cc1f00dce0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680961"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Znajdowanie nazwy procesu ASP.NET

Aby debugować działającego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, należy dołączyć debuger programu Visual Studio do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu według nazwy.

**Aby dowiedzieć się, który proces uruchomiono aplikację ASP.NET:**

1. Za pomocą aplikacji, w programie Visual Studio, wybierz **debugowania** > **dołączyć do procesu**.

1. W **dołączyć do procesu** okno dialogowe, typ pierwsze litery procesu nazwy z poniższej listy lub wprowadź je w polu wyszukiwania. Ta, która jest uruchomiona jest aplikacja ASP.NET działa. Dołącz do procesu debugowania aplikacji.

    - *W3wp.exe* jest IIS 6.0 lub nowszym.
    - *aspnet_wp.exe* is earlier versions of IIS.
    - *iisexpress.exe* is IISExpress.
    - *DotNet.exe* jest platforma ASP.NET Core.
    - *Inetinfo.exe* jest starszych aplikacji ASP, uruchamianych w trakcie.

>[!NOTE]
>Visual Studio 2012 i wcześniejszych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod może być w systemie plików i uruchomić na serwerze testowym *WebDev.WebServer.exe* lub *WebDev.WebServer40.exe*. W takim przypadku dla debugowania lokalnego, Dołącz do *WebDev.WebServer.exe* lub *WebDev.WebServer40.exe* zamiast [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu.

**Zobacz też:**

- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Wymagania wstępne dotyczące zdalnego debugowania aplikacji sieci web](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)
- [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)
- [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)