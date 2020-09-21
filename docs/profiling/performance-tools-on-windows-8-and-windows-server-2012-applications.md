---
title: Narzędzia do oceny wydajności w systemie Windows 8 & WS 2012
ms.custom: SEO-VS-2020
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cc44eddc2af2e2d85f7c4bb9c876d336ccd1b546
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90807836"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Narzędzia do oceny wydajności w aplikacjach Windows 8 i Windows Server 2012

Ulepszone funkcje zabezpieczeń, począwszy od systemu Windows 8 i Windows Server 2012, wymagały znaczących zmian w sposobie, w jaki narzędzia do oceny wydajności programu Visual Studio zbierają dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. W tym temacie opisano zmiany dotyczące narzędzi wydajności, które są uruchamiane na platformach Windows 8 i Windows Server 2012.

> [!NOTE]
> Narzędzia do oceny wydajności dla innych obsługiwanych wersji systemu Windows (Windows 7, Windows Server 2008 R2) nie zostały zmienione.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Zbieranie danych z aplikacji platformy UWP z poziomu środowiska IDE programu Visual Studio

W przypadku profilowania aplikacji platformy UWP, która jest zapisywana w języku JavaScript i HTML 5, zbierane są dane Instrumentacji dla kodu JavaScript. W przypadku profilowania aplikacji platformy UWP lub składnika, który jest pisany w Visual C++, Visual C# lub Visual Basic, zbierane są dane próbkowania dla kodu natywnego i zarządzanego. Aplikację można profilować lokalnie lub na komputerze zdalnym.

Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji platformy UWP:

- Profilowania aplikacji JavaScript przy użyciu metody próbkowania.
- Profilowanie kodu zarządzanego i natywnego za pomocą metody instrumentacji.
- Profilowanie współbieżności
- Profilowanie pamięci platformy .NET
- Profilowanie interakcji między warstwami (TIP)
- Opcje próbkowania, takie jak ustawienie zdarzenia próbkowania i interwał czasowy lub gromadzenie dodatkowych danych licznika wydajności.
- Opcje instrumentacji, takie jak zbieranie danych wydajności i liczników systemu Windows lub określanie dodatkowych opcji wiersza polecenia.

Aby uzyskać więcej informacji na temat profilowania aplikacji platformy UWP, zobacz następujące artykuły:

- [Uruchamianie aplikacji platformy UWP na komputerze lokalnym](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Pierwsze spojrzenie na narzędzia profilowania](profiling-feature-tour.md)
- [Pamięć JavaScript](../profiling/javascript-memory.md)
- [Profile Visual C++, Visual C# i Visual Basic Code w aplikacjach platformy UWP na komputerze lokalnym](/previous-versions/hh696631(v=vs.140))
- [Profile Visual C++, Visual C# i Visual Basic kod w aplikacjach platformy UWP na urządzeniu zdalnym](/previous-versions/hh972878(v=vs.140))
- [Analizowanie danych wydajności dla Visual C++, Visual C# i kodu Visual Basic w aplikacjach platformy UWP](/previous-versions/hh780914(v=vs.140))

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Zbierz dane dotyczące aplikacji uruchomionych na komputerze stacjonarnym z systemem Windows 8 lub Windows Server 2012 z programu Visual Studio IDE

Profilowanie przy użyciu metody instrumentacji nie zostało zmienione dla systemu Windows 8.

Profilowanie interakcji między warstwami (TIP) nie jest obsługiwane przy użyciu metody próbkowania.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Zbieranie danych w aplikacjach działających na komputerze stacjonarnym z systemem Windows 8 lub w systemie Windows Server 2012 przy użyciu próbkowania z programu Visual Studio IDE

Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji klasycznych systemu Windows 8 lub systemu Windows Server 2012 przy użyciu metody próbkowania:

- Profilowanie interakcji między warstwami (TIP). Zbieranie danych TIP jest obsługiwane przy użyciu instrumentacji.

- Opcje próbkowania, takie jak ustawienie zdarzenia próbkowania i interwał czasowy lub gromadzenie dodatkowych danych licznika wydajności.

## <a name="profile-from-the-command-line"></a>Profil z wiersza polecenia

Za pomocą dwóch narzędzi wiersza polecenia można zbierać dane profilowania na urządzeniach z systemami Windows 8 i Windows Server 2012, w tym urządzeń, które nie mają instalacji programu Visual Studio:

|Nazwa narzędzia|Opis|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Zbiera dane profilowania z aplikacji platformy UWP i zbiera przykładowe dane profilowania z aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Zbiera dane profilowania instrumentacji, współbieżności i warstwy z aplikacji, które są uruchomione na theWindows 8 Desktop lub Windows Server 2012. Zbiera wszystkie typy danych profilowania z poprzednich wersji systemu Windows.|

Oba narzędzia są instalowane z programem Visual Studio do użytku na komputerze lokalnym.

Aby profilować aplikacje na urządzeniach, na których nie zainstalowano programu Visual Studio, wykonaj jedną z następujących czynności:

- Pobierz narzędzia jako część Remote Tools for Visual Studio z [witryny MSDN w sieci Web](https://visualstudio.microsoft.com/#downloads+d-additional-software).

- Skopiuj i uruchom program instalacyjny autonomicznych narzędzi profilera z komputera programu Visual Studio. Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Wybierz program instalacyjny systemu operacyjnego (x86/x64) komputera zdalnego.

> [!NOTE]
> Aby zebrać dane profilowania TIP, należy zainstalować autonomiczny profiler z maszyny programu Visual Studio na komputerze zdalnym.

Te funkcje i opcje profilowania nie są obsługiwane w przypadku profilowania aplikacji systemu Windows 8 i Windows Server 2012 z wiersza polecenia:

- Zbieranie danych z aplikacji sieci Web systemu Windows 8 i Windows Server 2012 przy użyciu trybu próbkowania z [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md).

- Zbieranie danych próbkowania przy użyciu VsPerfCmd.exe.

- Opcje próbkowania, takie jak ustawienie zdarzenia próbkowania i interwał czasowy lub gromadzenie dodatkowych danych licznika wydajności.

## <a name="collect-tier-interaction-tip-data"></a>Zbierz dane interakcji warstwy (TIP)

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pomocą usług ADO.NET Services. Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Wersje programu Visual Studio**

Dane profilowania interakcji między warstwami można zbierać przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w Visual Studio Enterprise.

**Windows 8 i Windows Server 2012**

1. Aby zbierać dane interakcji warstwy z aplikacji, które są uruchomione na komputerze z systemem Windows 8 lub Windows Server 2012, należy użyć metody instrumentacji.

2. Nie można zbierać danych interakcji warstwy dla aplikacji platformy UWP.

3. Możesz uwzględnić dane interakcji warstwy we wszystkich metodach profilowania w innej obsługiwanej wersji systemu Windows.

**Kreator wydajności i Eksplorator wydajności**

Należy dodać opcję zbierania danych interakcja warstwy do przebiegu profilowania z Eksplorator wydajności. Należy również dodać projekt, plik wykonywalny lub witrynę sieci Web do węzła docelowego Eksplorator wydajności. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md).

**Zbieranie danych TIP na komputerze zdalnym**

Aby zbierać dane interakcji warstwy na komputerze zdalnym, należy skopiować plik programu **vs \_ \_ Profiler** _\<Platform>_ **\_** _\<Language>_ **. exe** z folderu *%VSInstallDir%\Team Tools\Performance Tools\Setups* maszyny programu Visual Studio na komputerze zdalnym i zainstalować go. Nie można używać narzędzi profilowania w pakiecie pobierania [debugowania zdalnego](../debugger/remote-debugging.md) .

Aby zebrać dane profilowania, można użyć [VSPerfCmd](../profiling/vsperfcmd.md) lub [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) .

**Raporty TIP**

Dane interakcji warstwy można wyświetlać tylko w Visual Studio Enterprise. Raporty interakcji z warstwą opartą na plikach za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) są niedostępne.

## <a name="see-also"></a>Zobacz też

[Eksplorator wydajności](../profiling/performance-explorer.md) 
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)