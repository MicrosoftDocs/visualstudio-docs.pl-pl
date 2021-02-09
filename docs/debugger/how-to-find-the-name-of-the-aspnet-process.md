---
title: Znajdź uruchomiony proces ASP.NET | Microsoft Docs
description: Dowiedz się, jak debugować uruchomioną aplikację ASP.NET. Debuger programu Visual Studio jest dołączany do procesu ASP.NET według nazwy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 11526639975924fd9984dce33a08e54c9a5405b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877658"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Znajdowanie nazwy procesu ASP.NET

Aby debugować uruchomioną [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację, debuger programu Visual Studio musi dołączyć do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu według nazwy.

**Aby dowiedzieć się, który proces ma uruchomioną aplikację ASP.NET:**

1. Po uruchomieniu aplikacji w programie Visual Studio wybierz pozycję **Debuguj**  >  **Dołącz do procesu**.

1. W oknie dialogowym **Dołącz do procesu** wpisz pierwsze litery nazw procesów z poniższej listy lub wprowadź je w polu wyszukiwania. Uruchomiona aplikacja ASP.NET jest uruchomiona. Dołącz do tego procesu, aby debugować aplikację.

    - *w3wp.exe* to IIS 6,0 i nowsze.
    - *aspnet_wp.exe* jest wcześniejszymi wersjami usług IIS.
    - *iisexpress.exe* jest IISExpress.
    - *dotnet.exe* jest ASP.NET Core.
    - *inetinfo.exe* to starsze aplikacje ASP działające w procesie.

>[!NOTE]
>Program Visual Studio 2012 i jego starszy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod mogą znajdować się w systemie plików i działać na serwerze testowym *WebDev.WebServer.exe* lub *WebDev.WebServer40.exe*. W tym przypadku do lokalnego debugowania należy dołączyć do *WebDev.WebServer.exe* lub *WebDev.WebServer40.exe* zamiast [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu.

**Zobacz również:**

- [Dołącz do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Wymagania wstępne dotyczące zdalnego debugowania aplikacji sieci Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)
- [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)