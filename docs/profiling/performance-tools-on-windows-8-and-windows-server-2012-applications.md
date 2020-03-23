---
title: Narzędzia wydajności w systemach Windows 8 & aplikacje systemu Windows Server 2012
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3938e7dc1b3ec33c8a4cf74b6957067bbdfd6185
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778430"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Narzędzia do oceny wydajności w aplikacjach Windows 8 i Windows Server 2012

Ulepszone funkcje zabezpieczeń, począwszy od systemów Windows 8 i Windows Server 2012, wymagały znaczących zmian w sposobie, w jaki narzędzia wydajności programu Visual Studio zbierają dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. W tym temacie opisano zmiany dotyczące narzędzi wydajności rozpoczynających się na platformach Windows 8 i Windows Server 2012.

> [!NOTE]
> Narzędzia wydajności dla innych obsługiwanych wersji systemu Windows (Windows 7, Windows Server 2008 R2) nie uległy zmianie.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Zbieranie danych dotyczących aplikacji platformy uniwersalnej systemu Windows z środowiska IDE programu Visual Studio

Podczas profilowania aplikacji platformy uniwersalnej systemu Uniwersalnego, która jest napisana w językach JavaScript i HTML 5, zbierasz dane instrumentacji dla kodu JavaScript. Podczas profilowania aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu wizowego, który jest napisany w języku Visual C++, Visual C#, lub Visual Basic, zbierasz dane próbkowania dla kodu macierzystego i zarządzanego. Aplikację można profilować lokalnie lub na komputerze zdalnym.

Te funkcje profilowania i opcje nie są obsługiwane podczas profilowania aplikacji platformy uniwersalnej systemu Windows:

- Profilowanie aplikacji JavaScript przy użyciu metody próbkowania.
- Profilowanie zarządzane i kod macierzysty przy użyciu metody instrumentacji.
- Profilowanie współbieżności
- Profilowanie pamięci .NET
- Profilowanie interakcji warstwy (TIP)
- Opcje próbkowania, takie jak ustawianie zdarzenia próbkowania i przedziału czasu lub zbieranie dodatkowych danych licznika wydajności.
- Opcje instrumentacji, takie jak zbieranie danych wydajności i licznika systemu Windows lub określanie dodatkowych opcji wiersza polecenia.

Aby uzyskać więcej informacji na temat profilowania aplikacji platformy uniwersalnej systemu Windows, zobacz następujące artykuły:

- [Uruchamianie aplikacji platformy UWP na komputerze lokalnym](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Pierwsze spojrzenie na narzędzia profilowania](profiling-feature-tour.md)
- [Pamięć JavaScript](../profiling/javascript-memory.md)
- [Kod programu Visual Visual++, Visual C#i Visual Basic w aplikacjach platformy uniwersalnej systemu Windows na komputerze lokalnym](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Kod profilu Visual C++, Visual C#i Visual Basic w aplikacjach platformy uniwersalnej systemu Windows na urządzeniu zdalnym](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analizowanie danych o wydajności dla kodu visual c++, visual c#i visual basic w aplikacjach platformy uniwersalnej systemu Windows](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Zbieranie danych dotyczących aplikacji uruchomionych na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 z środowiska IDE programu Visual Studio

Profilowanie przy użyciu metody instrumentacji nie uległo zmianie dla systemu Windows 8.

Profilowanie interakcji warstwy (TIP) nie jest obsługiwane przy użyciu metody próbkowania.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Zbieranie danych dotyczących aplikacji uruchomionych na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 przy użyciu próbkowania z środowiska IDE programu Visual Studio

Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji klasycznych systemu Windows 8 lub aplikacji systemu Windows Server 2012 przy użyciu metody próbkowania:

- Profilowanie interakcji warstwy (TIP). Zbieranie danych TIP jest obsługiwane przy użyciu oprzyrządowania.

- Opcje próbkowania, takie jak ustawianie zdarzenia próbkowania i przedziału czasu lub zbieranie dodatkowych danych licznika wydajności.

## <a name="profile-from-the-command-line"></a>Profil z wiersza polecenia

Do zbierania danych profilowania na urządzeniach z systemem Windows 8 i Windows Server 2012 używane są dwa narzędzia wiersza polecenia, w tym urządzenia, które nie mają instalacji programu Visual Studio:

|Nazwa narzędzia|Opis|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Zbiera dane profilowania z aplikacji platformy uniwersalnej systemu Windows i zbiera przykładowe dane profilowania z aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012.Collects profiling data from UWP apps and collects sample profiling data from Windows 8 desktop applications and Windows Server 2012 applications.Collects profiling data from UWP apps and collects sample profiling data from Windows 8 desktop applications and Windows Server 2012 applications.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Zbiera dane profilowania instrumentacji, współbieżności i interakcji warstwy z aplikacji uruchomionych na pulpicie Systemu Windows 8 lub Windows Server 2012. Zbiera wszystkie typy danych profilowania z poprzednich wersji systemu Windows.|

Oba narzędzia są instalowane w programie Visual Studio do użytku na komputerze lokalnym.

Aby profilować aplikacje na urządzeniach, na których nie zainstalowano programu Visual Studio, wykonaj jedną z następujących czynności:

- Pobierz narzędzia w ramach narzędzia zdalnego programu Visual Studio z [witryny sieci Web MSDN](https://visualstudio.microsoft.com/#downloads+d-additional-software).

- Skopiuj i uruchom autonomiczny program instalacyjny narzędzi profilerów z komputera programu Visual Studio. Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Wybierz program instalacyjny dla systemu operacyjnego (x86/x64) komputera zdalnego.

> [!NOTE]
> Aby zbierać dane profilowania TIP, należy zainstalować autonomiczny profiler z komputera programu Visual Studio na komputerze zdalnym.

Te funkcje profilowania i opcje nie są obsługiwane podczas profilowania aplikacji z systemu Windows 8 i Windows Server 2012 z wiersza polecenia:

- Zbieranie danych z aplikacji sieci Web systemu Windows 8 i Windows Server 2012 przy użyciu trybu próbkowania za pomocą [programu VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Zbieranie danych próbkowania przy użyciu programu VsPerfCmd.exe.

- Opcje próbkowania, takie jak ustawianie zdarzenia próbkowania i przedziału czasu lub zbieranie dodatkowych danych licznika wydajności.

## <a name="collect-tier-interaction-tip-data"></a>Zbieranie danych interakcji warstwy (TIP)

Profilowanie interakcji warstwy zawiera dodatkowe informacje na temat czasów wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Wersje programu Visual Studio**

Dane profilowania interakcji warstwy mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise.

**Windows 8 i Windows Server 2012**

1. Aby zbierać dane interakcji warstwy z aplikacji uruchomionych na pulpicie systemu Windows 8 lub Windows Server 2012, należy użyć metody instrumentacji.

2. Nie można zbierać danych interakcji warstwy dla aplikacji platformy uniwersalnej systemu Windows.

3. Dane interakcji warstwy można uwzględnić we wszystkich metodach profilowania w innej obsługiwanej wersji systemu Windows.

**Kreator wydajności i Eksplorator wydajności**

Należy dodać opcję zbierania danych interakcji warstwy do profilowania uruchomić z Eksploratora wydajności. Należy również dodać projekt, plik wykonywalny lub witrynę sieci Web do węzła docelowego Eksploratora wydajności. Zobacz [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md).

**Zbieranie danych TIP na komputerze zdalnym**

Aby zbierać dane interakcji warstwy na komputerze zdalnym, należy skopiować plik_\< _ _ \<>.exe platformy _vs **.exe** **\_** **\_profiler\_**>language z folderu *%VSInstallDir%\Team Tools\Performance Tools\Setups* komputera programu Visual Studio na komputer zdalny i zainstalować go. Nie można używać narzędzi profilowania w pakiecie pobierania [zdalnego debugowania.](../debugger/remote-debugging.md)

Do zbierania danych profilowania można użyć programu [VSPerfCmd](../profiling/vsperfcmd.md) lub [VSPerfASPNetCmd.](../profiling/vsperfaspnetcmd.md)

**Raporty TIP**

Dane interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise. Raporty interakcji warstwy opartej na plikach za pośrednictwem [programu VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.

## <a name="see-also"></a>Zobacz też

[Eksplorator](../profiling/performance-explorer.md)
wydajności[Konfigurowanie profilu sesji](../profiling/configuring-performance-sessions.md)
wydajności[z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
