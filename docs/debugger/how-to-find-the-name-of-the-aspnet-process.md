---
title: Znajdź uruchomiony proces ASP.NET | Microsoft Docs
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
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187656"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Znajdowanie nazwy procesu ASP.NET

Aby debugować działającą aplikację [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debuger programu Visual Studio musi dołączyć do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu według nazwy.

**Aby dowiedzieć się, który proces ma uruchomioną aplikację ASP.NET:**

1. Po uruchomieniu aplikacji w programie Visual Studio wybierz kolejno opcje **debuguj** > **Dołącz do procesu**.

1. W oknie dialogowym **Dołącz do procesu** wpisz pierwsze litery nazw procesów z poniższej listy lub wprowadź je w polu wyszukiwania. Uruchomiona aplikacja ASP.NET jest uruchomiona. Dołącz do tego procesu, aby debugować aplikację.

    - *w3wp. exe* to IIS 6,0 i nowsze.
    - *Proces aspnet_wp. exe* jest wcześniejszą wersją usług IIS.
    - *iisexpress. exe* to iisexpress.
    - ASP.NET Core.
    - *Inetinfo. exe* to starsze aplikacje ASP działające w procesie.

>[!NOTE]
>Program Visual Studio 2012 i jego wcześniejszy kod [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mogą znajdować się w systemie plików i działać na serwerze testowym *webdev. WebServer. exe* lub *webdev. WebServer40. exe*. W tym przypadku do lokalnego debugowania należy dołączyć do *webdev. WebServer. exe* lub *webdev. WebServer40. exe* zamiast procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**Zobacz również:**

- [Dołącz do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Wymagania wstępne dotyczące zdalnego debugowania aplikacji sieci Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)
- [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)