---
title: Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2fa9581d94b3b70ca427c292c147562a11d55a4
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847998"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Narzędzia do oceny wydajności w aplikacjach systemów Windows 8 i Windows Server 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie zbierania danych na tych platformach przez narzędzia do oceny wydajności programu Visual Studio. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. W tym temacie opisano zmiany dotyczące narzędzi wydajności na platformach z systemami Windows 8 i Windows Server 2012.  
  
> [!NOTE]
> Narzędzia do oceny wydajności dla innych obsługiwanych wersji systemu Windows (Windows 7, Windows Server 2008 R2) nie zostały zmienione.  
  
## <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Zbieranie danych w aplikacjach ze sklepu Windows z programu Visual Studio IDE](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Zbieranie danych w aplikacjach uruchamianych na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 z programu Visual Studio IDE](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Zbieranie danych w aplikacjach uruchamianych na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 przy użyciu próbkowania z programu Visual Studio IDE](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Profilowanie z wiersza polecenia](#BKMK_Profiling_from_the_command_line)  
  
  [Zbieranie danych o interakcji warstwy (TIP)](#BKMK_Collecting_tier_interaction__TIP__data)  
  
## <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a>Zbieranie danych w aplikacjach ze sklepu Windows z programu Visual Studio IDE  
 W przypadku profilowania aplikacji ze sklepu Windows, która jest zapisywana w języku JavaScript i HTML 5, zbierane są dane Instrumentacji dla kodu JavaScript. W przypadku profilowania aplikacji ze sklepu Windows lub składnika, który jest pisany w C++wizualizacji C#, wizualizacji lub Visual Basic, zbierane są dane próbkowania dla kodu natywnego i zarządzanego. Aplikację można profilować lokalnie lub na komputerze zdalnym.  
  
 Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji ze sklepu Windows:  
  
- Profilowania aplikacji JavaScript przy użyciu metody próbkowania.  
  
- Profilowanie kodu zarządzanego i natywnego za pomocą metody instrumentacji.  
  
- Profilowanie współbieżności  
  
- Profilowanie pamięci platformy .NET  
  
- Profilowanie interakcji między warstwami (TIP)  
  
- Opcje próbkowania, takie jak ustawienie zdarzenia próbkowania i interwał czasowy lub gromadzenie dodatkowych danych licznika wydajności.  
  
- Opcje instrumentacji, takie jak zbieranie danych wydajności i liczników systemu Windows lub określanie dodatkowych opcji wiersza polecenia.  
  
  Aby uzyskać więcej informacji na temat profilowania aplikacji ze sklepu Windows, zobacz następujące tematy w centrum deweloperów systemu Windows:  
  
  [Uruchamianie aplikacji ze Sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Uruchamianie aplikacji ze Sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Analizowanie wydajności aplikacji](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [Chronometraż funkcji JavaScript](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Chronometraż funkcji języka JavaScript na urządzeniu zdalnym](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [Analizuj dane chronometrażu funkcji JavaScript](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Profilowanie C++wizualizacji C#, wizualizacji i Visual Basic w aplikacjach do sklepu Windows na komputerze lokalnym](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Profilowanie C++wizualizacji C#, wizualizacji i Visual Basic w aplikacjach ze sklepu Windows na urządzeniu zdalnym](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Analizowanie danych wydajności dla wizualizacji C++, C#wizualizacji i Visual Basic kodu w aplikacjach ze sklepu Windows](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a>Zbieranie danych w aplikacjach uruchamianych na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 z programu Visual Studio IDE  
 Profilowanie przy użyciu metody instrumentacji nie zostało zmienione dla systemu Windows 8.  
  
 Profilowanie interakcji między warstwami (TIP) nie jest obsługiwane przy użyciu metody próbkowania.  
  
### <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a>Zbieranie danych w aplikacjach uruchamianych na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 przy użyciu próbkowania z programu Visual Studio IDE  
 Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji klasycznych systemu Windows 8 lub systemu Windows Server 2012 przy użyciu metody próbkowania:  
  
- Profilowanie interakcji między warstwami (TIP). Zbieranie danych TIP jest obsługiwane przy użyciu instrumentacji.  
  
- Opcje próbkowania, takie jak ustawienie zdarzenia próbkowania i interwał czasowy lub gromadzenie dodatkowych danych licznika wydajności.  
  
## <a name="BKMK_Profiling_from_the_command_line"></a>Profilowanie z wiersza polecenia  
 Za pomocą dwóch narzędzi wiersza polecenia można zbierać dane profilowania na urządzeniach z systemami Windows 8 i Windows Server 2012, w tym urządzeń, które nie mają instalacji programu Visual Studio:  
  
|Nazwa narzędzia|Opis|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Zbiera dane profilowania z aplikacji ze sklepu Windows i zbiera przykładowe dane profilowania z aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Zbiera dane profilowania instrumentacji, współbieżności i warstwy z aplikacji, które są uruchomione na theWindows 8 Desktop lub Windows Server 2012. Zbiera wszystkie typy danych profilowania z poprzednich wersji systemu Windows.|  
  
 Oba narzędzia są instalowane z programem Visual Studio do użytku na komputerze lokalnym.  
  
 Aby profilować aplikacje na urządzeniach, na których nie zainstalowano programu Visual Studio, wykonaj jedną z następujących czynności:  
  
- Pobierz narzędzia jako część Remote Tools for Visual Studio z [witryny MSDN w sieci Web](https://www.microsoft.com/visualstudio/eng#downloads+d-additional-software).  
  
- Skopiuj i uruchom program instalacyjny autonomicznych narzędzi profilera z komputera programu Visual Studio. Programy instalacyjne znajdują się w folderze *% VSInstallDir%* **\Team Tools\Performance Tools\Setups** . Wybierz program instalacyjny systemu operacyjnego (x86/x64) komputera zdalnego.  
  
> [!NOTE]
> Aby zebrać dane profilowania TIP, należy zainstalować autonomiczny profiler z maszyny programu Visual Studio na komputerze zdalnym.  
  
 Te funkcje i opcje profilowania nie są obsługiwane w przypadku profilowania aplikacji systemu Windows 8 i Windows Server 2012 z wiersza polecenia:  
  
- Zbieranie danych z aplikacji sieci Web systemu Windows 8 i Windows Server 2012 przy użyciu trybu próbkowania z [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md).  
  
- Zbieranie danych próbkowania przy użyciu programu VsPerfCmd. exe.  
  
- Opcje próbkowania, takie jak ustawienie zdarzenia próbkowania i interwał czasowy lub gromadzenie dodatkowych danych licznika wydajności.  
  
## <a name="BKMK_Collecting_tier_interaction__TIP__data"></a>Zbieranie danych o interakcji warstwy (TIP)  
 Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pomocą usług ADO.NET Services. Dane są zbierane tylko dla wywołań funkcji synchronicznych.  
  
 **Visual Studio editions**  
  
 Dane profilowania interakcji między warstwami można zbierać przy użyciu [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]lub [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Windows 8 i Windows Server 2012**  
  
1. Aby zbierać dane interakcji warstwy z aplikacji, które są uruchomione na komputerze z systemem Windows 8 lub Windows Server 2012, należy użyć metody instrumentacji.  
  
2. Nie można zbierać danych o interakcji między warstwami dla aplikacji ze sklepu Windows.  
  
3. Możesz uwzględnić dane interakcji warstwy we wszystkich metodach profilowania w innej obsługiwanej wersji systemu Windows.  
  
   **Kreator wydajności i Eksplorator wydajności**  
  
   Należy dodać opcję zbierania danych interakcja warstwy do przebiegu profilowania z Eksplorator wydajności. Należy również dodać projekt, plik wykonywalny lub witrynę sieci Web do węzła docelowego Eksplorator wydajności. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md).  
  
   **Zbieranie danych TIP na komputerze zdalnym**  
  
   Aby zbierać dane interakcji warstwy na komputerze zdalnym, należy skopiować program **vs\_profiler\_** _\<Platform >_ **\_** _\<Language >_ **. exe** z folderu _% VSInstallDir%_ **\Team Tools\Performance Tools\Setups** na komputerze zdalnym i zainstalować go. Nie można używać narzędzi profilowania w pakiecie pobierania [narzędzi zdalnych programu Visual Studio](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
   Aby zebrać dane profilowania, można użyć [VSPerfCmd](../profiling/vsperfcmd.md) lub [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) .  
  
   **Raporty TIP**  
  
   Dane interakcji warstwy można wyświetlać tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] lub [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE. Raporty interakcji z warstwą opartą na plikach za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) są niedostępne.  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
