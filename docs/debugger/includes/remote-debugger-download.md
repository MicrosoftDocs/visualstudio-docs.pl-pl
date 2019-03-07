---
title: Pobieranie zdalnego debugera
description: Łącza pobierania dla zdalnego debugera
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 01ec01ad642333d9ee46296cbcb4a02526152e94
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526876"
---
Na urządzeniu zdalnym lub serwerze, na którym chcesz debugować na, zamiast maszyny programu Visual Studio Pobierz i zainstaluj poprawną wersję narzędzi zdalnych z łączy w poniższej tabeli.

- Pobierz najnowsze narzędzia zdalne dla używanej wersji programu Visual Studio. Najnowsza wersja narzędzi zdalnych jest zgodna z wcześniejszymi wersjami programu Visual Studio, ale wcześniejszych wersji narzędzi zdalnych nie są zgodne z nowszej wersji programu Visual Studio.
- Pobierz narzędzia zdalnej z taką samą architekturę co maszyna instalujesz je na. Na przykład jeśli chcesz debugować aplikację 32-bitowego na komputerze zdalnym z systemem 64-bitowym systemie operacyjnym, należy zainstalować narzędzia zdalne 64-bitowych.

::: moniker range=">=vs-2019"

> [!NOTE]
> Do momentu autonomiczny Remote tools for Visual Studio 2019 r są dostępne, jeśli potrzebujesz zdalnego debugera za pomocą programu Visual Studio 2019 r, [znaleźć zdalny debuger](https://docs.microsoft.com/visualstudio/debugger/remote-debugging?view=vs-2017#fileshare_msvsmon) w instalacji programu Visual Studio 2019 r, a następnie skopiuj i uruchomienie go na zdalnych maszyny lub uruchamiać jej z udziałem plików.

::: moniker-end

|Wersja|Łącze|Uwagi|
|-|-|-|
|Visual Studio 2017 (Najnowsza wersja)|[Zdalne narzędzia](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Zgodny ze wszystkimi wersjami programu Visual Studio 2017. Pobierz wersję dopasowania system operacyjny urządzenia (x 86, x64 lub ARM64). W systemie Windows Server, zobacz [odblokować pobierania pliku](../../debugger/remote-debugging-unblock-file-download.md) pomocy pobieranie narzędzi zdalnych.|
|Visual Studio 2015|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Zdalne narzędzia dla programu Visual Studio 2015 są dostępne z My.VisualStudio.com. Jeśli zostanie wyświetlony monit, weź udział w bezpłatnych [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) program lub zaloguj się przy użyciu identyfikatora subskrypcji programu Visual Studio. W systemie Windows Server, zobacz [odblokować pobierania pliku](../../debugger/remote-debugging-unblock-file-download.md) pomocy pobieranie narzędzi zdalnych.|
|Visual Studio 2013|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2013|
|Visual Studio 2012|[Zdalne narzędzia](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2012|

Można uruchomić zdalnego debugera, kopiując *msvsmon.exe* na komputerze zdalnym, zamiast Instalowanie narzędzi zdalnych. Jednak Kreator konfiguracji debugera zdalnego (*rdbgwiz.exe*) jest dostępna tylko po zainstalowaniu narzędzi zdalnych. Może być konieczne użycie Kreatora konfiguracji, aby uruchomić zdalny debuger jako usługę. Aby uzyskać więcej informacji, zobacz [(opcjonalnie) Konfigurowanie debugera zdalnego jako usługę](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Aby debugować aplikacje systemu Windows 10 na urządzeniach ARM, należy użyć ARM64, który jest dostępny z najnowszą wersję narzędzi remote tools.
>- Aby debugować aplikacje systemu Windows 10 na urządzeniach z systemem Windows RT, należy użyć ARM, który jest dostępny tylko w programie Visual Studio 2015, Pobierz narzędzia zdalne.
