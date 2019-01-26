---
title: Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012 | Dokumentacja firmy Microsoft
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e510705dc8aebad7cee6c8eea4e91c2522e4306
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959713"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Narzędzia do oceny wydajności w aplikacjach Windows 8 i Windows Server 2012

Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane istotne zmiany w Visual Studio tools wydajności sposób zbierania danych na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. W tym temacie opisano zmiany dotyczące narzędzia do oceny wydajności uruchamiania na platformach systemu Windows 8 i Windows Server 2012.

> [!NOTE]
> Narzędzia do oceny wydajności dla innych obsługiwanych wersji systemu Windows (Windows 7, Windows Server 2008 R2) nie uległy zmianie.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Zbieranie danych w aplikacjach platformy uniwersalnej systemu Windows z programu Visual Studio IDE

Podczas profilowania aplikacji platformy uniwersalnej systemu Windows, które napisano w języku JavaScript i HTML 5, możesz zbierać dane instrumentacji dla kodu JavaScript. Podczas profilowania aplikacji platformy uniwersalnej systemu Windows lub składnik, który został napisany w języku Visual C++, Visual C# lub Visual Basic, można zbierać dane z próbkowania dla kodu natywnego i zarządzanego. Można profilować aplikację, lokalnie lub na komputerze zdalnym.

Tych funkcji i opcji profilowania nie są obsługiwane, gdy profilowanie aplikacji platformy uniwersalnej systemu Windows:

- Profilowanie aplikacji JavaScript przy użyciu metody próbkowania.
- Profilowania kodu zarządzanego i natywnego przy użyciu metody instrumentacji.
- Metoda profilowania współbieżność
- Profilowanie pamięci .NET
- (TIP) profilowanie interakcji między warstwami
- Opcje próbkowania, takie jak ustawienie zdarzenie próbkowania i interwał czasu lub zbieranie danych licznika wydajności.
- Opcje instrumentacji, takie jak zbieranie danych liczników systemu windows i wydajności lub określanie dodatkowych opcji wiersza polecenia.

Aby uzyskać więcej informacji na temat profilowanie aplikacji platformy uniwersalnej systemu Windows zobacz następujące artykuły:

- [Uruchamianie aplikacji platformy UWP na komputerze lokalnym](/visualstudio/debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml)
- [Uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Pierwsze spojrzenie na narzędziach profilowania](profiling-feature-tour.md)
- [Pamięć języka JavaScript](../profiling/javascript-memory.md)
- [Kod profilu Visual C++, Visual C# i Visual Basic w aplikacjach platformy UWP na komputerze lokalnym](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Kod profilu Visual C++, Visual C# i Visual Basic w aplikacjach platformy UWP na urządzeniu zdalnym](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analizowanie danych dotyczących wydajności dla kodu języka Visual C++, Visual C# i Visual Basic w aplikacjach platformy UWP](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Zbieranie danych w aplikacje działające na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 ze środowiska IDE programu Visual Studio

Profilowanie przy użyciu metody Instrumentacji nie zmienił się w systemie Windows 8.

Funkcję Tier interaction profiling (TIP) nie jest obsługiwana przy użyciu metody próbkowania.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Zbieranie danych w aplikacje działające na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 za pomocą próbkowania ze środowiska IDE programu Visual Studio

Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji klasycznych systemu Windows 8 lub aplikacji systemu Windows Server 2012 za pomocą metody pobierania próbek:

- (TIP) profilowanie interakcji między warstwami. Zbieranie danych Porada jest obsługiwana przy użyciu metody instrumentacji.

- Opcje próbkowania, takie jak ustawienie zdarzenie próbkowania i interwał czasu, lub zbieranie danych licznika wydajności.

## <a name="profile-from-the-command-line"></a>Profilowanie z wiersza polecenia

Dwa narzędzia wiersza polecenia służy do zbierania danych profilowania na urządzeniach systemu Windows 8 i Windows Server 2012, w tym urządzenia, które nie mają instalacji programu Visual Studio:

|Nazwa narzędzia|Opis|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Zbiera dane profilowania aplikacji platformy UWP i zbiera dane profilowania próbki z aplikacji pulpitu systemu Windows 8 i Windows Server 2012 aplikacji...|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Zbiera dane instrumentacji, współbieżność i obejrzeć takie dane z aplikacji, które są uruchomione na pulpicie theWindows 8 lub Windows Server 2012. Zbiera wszystkie typy danych profilowania z poprzednich wersji systemu Windows.|

Oba narzędzia są instalowane z programem Visual Studio do użytku na komputerze lokalnym.

Do profilu aplikacji na urządzeniach, które nie zainstalowano program Visual Studio, wykonaj jedną z następujących czynności:

- Pobierz narzędzia jako część pakietu Remote Tools for Visual Studio z [witryny sieci web MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).

- Kopiowanie i uruchom program instalacyjny narzędzia autonomicznego profilera z komputera programu Visual Studio. Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Wybierz Instalatora systemu operacyjnego — x86/x64 64 komputera zdalnego.

> [!NOTE]
> Aby zbierać Porada danych profilowania, należy zainstalować autonomicznego profilera z poziomu Twojej maszyny programu Visual Studio na komputerze zdalnym.

Te profilowania funkcji i opcji nie są obsługiwane, gdy profilowanie aplikacji Windows 8 i Windows Server 2012 w wierszu polecenia:

- Zbieranie danych z aplikacji sieci web systemu Windows 8 i Windows Server 2012 przy użyciu trybu próbkowania przy użyciu [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Zbieranie danych próbkowania przy użyciu VsPerfCmd.exe.

- Opcje próbkowania, takie jak ustawienie zdarzenie próbkowania i interwał czasu, lub zbieranie danych licznika wydajności.

## <a name="collect-tier-interaction-tip-data"></a>Zbieranie danych interakcji (TIP)

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat czasu wykonania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.

**Visual Studio editions**

Obejrzeć takie dane mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Natomiast obejrzeć takie dane można wyświetlać tylko w programie Visual Studio Enterprise.

**System Windows 8 i Windows Server 2012**

1. Aby zebrać dane interakcji między warstwami aplikacji, które są uruchomione na pulpicie systemu Windows 8 lub Windows Server 2012, należy użyć metody instrumentacji.

2. Nie można zebrać dane interakcji między warstwami aplikacji platformy uniwersalnej systemu Windows.

3. Dane interakcji między warstwami można uwzględnić w wszystkich metod profilowania w innych obsługiwanych wersji systemu Windows.

**Kreator wydajności i Eksploratora wydajności**

Należy dodać opcji zbierania danych interakcji warstwy do uruchomienia profilowania z poziomu Eksploratora wydajności. Do węzła docelowego Eksploratora wydajności, należy dodać projekt, plik wykonywalny lub witryny sieci Web. Zobacz [zbierania danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md).

**Zbieranie danych Porada na komputerze zdalnym**

Aby zebrać dane interakcji między warstwami na komputerze zdalnym, należy skopiować **vs\_profiler\_**_\<platformy >_ **\_**  _\<Języka >_**.exe** plik wchodzącej w skład *%VSInstallDir%\Team Tools\Setups narzędzia* folderu maszynie z systemem Visual Studio komputer zdalny i zainstaluj go. Nie można użyć narzędzi profilowania w [zdalne debugowanie](../debugger/remote-debugging.md) Pobieranie pakietu.

Możesz użyć [VSPerfCmd](../profiling/vsperfcmd.md) lub [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) do zbierania danych profilowania.

**Porada raportów**

Dane interakcji między warstwami można wyświetlić tylko w Visual Studio Enterprise. Interakcje między warstwami plikowym raportów za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.

## <a name="see-also"></a>Zobacz także

[Eksplorator wydajności](../profiling/performance-explorer.md)
[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
[profilu z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)