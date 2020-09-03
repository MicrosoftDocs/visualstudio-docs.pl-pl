---
title: Pobieranie zdalnego debugera
description: Pobierz linki dla zdalnego debugera
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89327147"
---
Na urządzeniu zdalnym lub serwerze, który ma być debugowany, a nie z maszyną programu Visual Studio, Pobierz i zainstaluj poprawną wersję narzędzi zdalnych z linków w poniższej tabeli.

- Pobierz najnowsze narzędzia zdalne dla używanej wersji programu Visual Studio. Najnowsza wersja narzędzi zdalnych jest zgodna ze starszymi wersjami programu Visual Studio, ale wcześniejsze wersje narzędzi zdalnych nie są zgodne z nowszymi wersjami programu Visual Studio. (Na przykład jeśli używasz programu Visual Studio 2017, Pobierz najnowszą aktualizację narzędzi Remote Tools for Visual Studio 2017. W tym scenariuszu nie należy pobierać narzędzi Remote Tools for Visual Studio 2019.
- Pobierz narzędzia zdalne z tą samą architekturą, w której są instalowane maszyny. Na przykład jeśli chcesz debugować aplikację 32-bitową na komputerze zdalnym z systemem operacyjnym 64-bitowym, zainstaluj narzędzia zdalnego 64-bit.

::: moniker range=">=vs-2019"

|Wersja|Link|Uwagi|
|-|-|-|
|Visual Studio 2019|[Zdalne narzędzia](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Zgodne ze wszystkimi wersjami programu Visual Studio 2019. Pobierz wersję zgodną z systemem operacyjnym urządzenia (x86, x64 lub ARM64). W systemie Windows Server zapoznaj się z tematem [Odblokuj pobieranie pliku](../../debugger/remote-debugging-unblock-file-download.md) , aby uzyskać pomoc dotyczącą pobierania narzędzi zdalnych.|
|Visual Studio 2017|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Zgodne ze wszystkimi wersjami programu Visual Studio 2017. Pobierz wersję zgodną z systemem operacyjnym urządzenia (x86, x64 lub ARM64). W systemie Windows Server zapoznaj się z tematem [Odblokuj pobieranie pliku](../../debugger/remote-debugging-unblock-file-download.md) , aby uzyskać pomoc dotyczącą pobierania narzędzi zdalnych.|
|Visual Studio 2015|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Narzędzia Remote Tools for Visual Studio 2015 są dostępne z My.VisualStudio.com. Jeśli zostanie wyświetlony monit, Dołącz do bezpłatnego programu [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) lub Zaloguj się przy użyciu identyfikatora subskrypcji programu Visual Studio. W systemie Windows Server zapoznaj się z tematem [Odblokuj pobieranie pliku](../../debugger/remote-debugging-unblock-file-download.md) , aby uzyskać pomoc dotyczącą pobierania narzędzi zdalnych.|
|Visual Studio 2013|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Strona pobierania w dokumentacji Visual Studio 2013|
|Visual Studio 2012|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Strona pobierania w dokumentacji programu Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Wersja|Link|Uwagi|
|-|-|-|
|Visual Studio 2017|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Zgodne ze wszystkimi wersjami programu Visual Studio 2017. Pobierz wersję zgodną z systemem operacyjnym urządzenia (x86, x64 lub ARM64). W systemie Windows Server zapoznaj się z tematem [Odblokuj pobieranie pliku](../../debugger/remote-debugging-unblock-file-download.md) , aby uzyskać pomoc dotyczącą pobierania narzędzi zdalnych. Aby uzyskać najnowszą wersję narzędzi zdalnych, Otwórz [dokument Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Narzędzia Remote Tools for Visual Studio 2015 są dostępne z My.VisualStudio.com. Jeśli zostanie wyświetlony monit, Dołącz do bezpłatnego programu [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) lub Zaloguj się przy użyciu identyfikatora subskrypcji programu Visual Studio. W systemie Windows Server zapoznaj się z tematem [Odblokuj pobieranie pliku](../../debugger/remote-debugging-unblock-file-download.md) , aby uzyskać pomoc dotyczącą pobierania narzędzi zdalnych.|
|Visual Studio 2013|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Strona pobierania w dokumentacji Visual Studio 2013|
|Visual Studio 2012|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Strona pobierania w dokumentacji programu Visual Studio 2012|

::: moniker-end

Zdalny debuger można uruchomić, kopiując *msvsmon.exe* na komputer zdalny, zamiast instalować narzędzia zdalne. Jednak Kreator konfiguracji debugera zdalnego (*rdbgwiz.exe*) jest dostępny tylko po zainstalowaniu narzędzi zdalnych. Może być konieczne użycie Kreatora konfiguracji, jeśli chcesz uruchomić zdalny debuger jako usługę. Aby uzyskać więcej informacji, zobacz [(opcjonalnie). Skonfiguruj zdalny debuger jako usługę](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Aby debugować aplikacje systemu Windows 10 na urządzeniach ARM, użyj ARM64, który jest dostępny w najnowszej wersji narzędzi zdalnych.
>- Aby debugować aplikacje systemu Windows 10 na urządzeniach z systemem Windows RT, użyj ARM, który jest dostępny tylko w pobieraniu narzędzi zdalnych programu Visual Studio 2015.
