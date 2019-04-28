---
title: Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bfd585a3185d83981d24c8dc77e62193c1363d4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442540"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane istotne zmiany w Visual Studio tools wydajności sposób zbierania danych na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. W tym temacie opisano zmiany dotyczące narzędzia do oceny wydajności na platformach systemu Windows 8 i Windows Server 2012.  
  
> [!NOTE]
> Narzędzia do oceny wydajności dla innych obsługiwanych wersji systemu Windows (Windows 7, Windows Server 2008 R2) nie uległy zmianie.  
  
## <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Zbieranie danych w aplikacji Windows Store z poziomu środowiska IDE programu Visual Studio](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Zbieranie danych w aplikacje działające na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 ze środowiska IDE programu Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Zbieranie danych w aplikacje działające na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 za pomocą próbkowania ze środowiska IDE programu Visual Studio](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Profilowanie z wiersza polecenia](#BKMK_Profiling_from_the_command_line)  
  
  [Zbieranie danych (TIP) interakcji między warstwami](#BKMK_Collecting_tier_interaction__TIP__data)  
  
## <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Zbieranie danych w aplikacji Windows Store z poziomu środowiska IDE programu Visual Studio  
 Podczas profilowania aplikacji Windows Store, które napisano w języku JavaScript i HTML 5, możesz zbierać dane instrumentacji dla kodu JavaScript. Podczas profilowania aplikacji Windows Store lub składnika, który został napisany w języku Visual C++, Visual C# lub Visual Basic, można zbierać dane z próbkowania dla kodu natywnego i zarządzanego. Można profilować aplikację, lokalnie lub na komputerze zdalnym.  
  
 Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji Windows Store:  
  
- Profilowanie aplikacji JavaScript przy użyciu metody próbkowania.  
  
- Profilowania kodu zarządzanego i natywnego przy użyciu metody instrumentacji.  
  
- Metoda profilowania współbieżność  
  
- Profilowanie pamięci .NET  
  
- (TIP) profilowanie interakcji między warstwami  
  
- Opcje próbkowania, takie jak ustawienie zdarzenie próbkowania i interwał czasu lub zbieranie danych licznika wydajności.  
  
- Opcje instrumentacji, takie jak zbieranie danych liczników systemu windows i wydajności lub określanie dodatkowych opcji wiersza polecenia.  
  
  Aby uzyskać więcej informacji na temat profilowanie aplikacji Windows Store zobacz następujące tematy w Centrum deweloperów Windows:  
  
  [Uruchamianie aplikacji ze Sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Uruchamianie aplikacji ze Sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Analizowanie wydajności aplikacji](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [Synchronizacja funkcji JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Synchronizacja funkcji JavaScript na urządzeniu zdalnym](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [Analizowanie danych synchronizacja funkcji JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Kod profilu Visual C++, Visual C# i Visual Basic w aplikacjach Windows Store na komputerze lokalnym](http://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Kod profilu Visual C++, Visual C# i Visual Basic w aplikacjach Windows Store na urządzeniu zdalnym](http://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Analizowanie danych dotyczących wydajności dla kodu języka Visual C++, Visual C# i Visual Basic w aplikacjach Windows Store](http://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Zbieranie danych w aplikacje działające na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 ze środowiska IDE programu Visual Studio  
 Profilowanie przy użyciu metody Instrumentacji nie zmienił się w systemie Windows 8.  
  
 Funkcję Tier interaction profiling (TIP) nie jest obsługiwana przy użyciu metody próbkowania.  
  
### <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Zbieranie danych w aplikacje działające na pulpicie systemu Windows 8 lub w systemie Windows Server 2012 za pomocą próbkowania ze środowiska IDE programu Visual Studio  
 Te funkcje i opcje profilowania nie są obsługiwane podczas profilowania aplikacji klasycznych systemu Windows 8 lub aplikacji systemu Windows Server 2012 za pomocą metody pobierania próbek:  
  
- (TIP) profilowanie interakcji między warstwami. Zbieranie danych Porada jest obsługiwana przy użyciu metody instrumentacji.  
  
- Opcje próbkowania, takie jak ustawienie zdarzenie próbkowania i interwał czasu, lub zbieranie danych licznika wydajności.  
  
## <a name="BKMK_Profiling_from_the_command_line"></a> Profilowanie z wiersza polecenia  
 Dwa narzędzia wiersza polecenia służy do zbierania danych profilowania na urządzeniach systemu Windows 8 i Windows Server 2012, w tym urządzenia, które nie mają instalacji programu Visual Studio:  
  
|Nazwa narzędzia|Opis|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Zbiera dane profilowania z aplikacji Windows Store i zbiera dane profilowania próbki z aplikacji pulpitu systemu Windows 8 i Windows Server 2012 aplikacji...|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Zbiera dane instrumentacji, współbieżność i obejrzeć takie dane z aplikacji, które są uruchomione na pulpicie theWindows 8 lub Windows Server 2012. Zbiera wszystkie typy danych profilowania z poprzednich wersji systemu Windows.|  
  
 Oba narzędzia są instalowane z programem Visual Studio do użytku na komputerze lokalnym.  
  
 Do profilu aplikacji na urządzeniach, które nie zainstalowano program Visual Studio, wykonaj jedną z następujących czynności:  
  
- Pobierz narzędzia jako część pakietu Remote Tools for Visual Studio z [witryny sieci web MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
- Kopiowanie i uruchom program instalacyjny narzędzia autonomicznego profilera z komputera programu Visual Studio. Programy instalacyjne znajdują się w *VSInstallDir %* **tools\performance Tools\Setups** folderu. Wybierz Instalatora systemu operacyjnego — x86/x64 64 komputera zdalnego.  
  
> [!NOTE]
> Aby zbierać Porada danych profilowania, należy zainstalować autonomicznego profilera z poziomu Twojej maszyny programu Visual Studio na komputerze zdalnym.  
  
 Te profilowania funkcji i opcji nie są obsługiwane, gdy profilowanie aplikacji Windows 8 i Windows Server 2012 w wierszu polecenia:  
  
- Zbieranie danych z aplikacji sieci web systemu Windows 8 i Windows Server 2012 przy użyciu trybu próbkowania przy użyciu [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
- Zbieranie danych próbkowania przy użyciu VsPerfCmd.exe.  
  
- Opcje próbkowania, takie jak ustawienie zdarzenie próbkowania i interwał czasu, lub zbieranie danych licznika wydajności.  
  
## <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Zbieranie danych (TIP) interakcji między warstwami  
 Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat czasu wykonania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.  
  
 **Visual Studio editions**  
  
 Obejrzeć takie dane można zbierać w programach [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], lub [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Natomiast obejrzeć takie dane można wyświetlić tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **System Windows 8 i Windows Server 2012**  
  
1. Aby zebrać dane interakcji między warstwami aplikacji, które są uruchomione na pulpicie systemu Windows 8 lub Windows Server 2012, należy użyć metody instrumentacji.  
  
2. Nie można zebrać dane interakcji między warstwami aplikacji Windows Store.  
  
3. Dane interakcji między warstwami można uwzględnić w wszystkich metod profilowania w innych obsługiwanych wersji systemu Windows.  
  
   **Kreator wydajności i Eksploratora wydajności**  
  
   Należy dodać opcji zbierania danych interakcji warstwy do uruchomienia profilowania z poziomu Eksploratora wydajności. Do węzła docelowego Eksploratora wydajności, należy dodać projekt, plik wykonywalny lub witryny sieci Web. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md).  
  
   **Zbieranie danych Porada na komputerze zdalnym**  
  
   Aby zebrać dane interakcji między warstwami na komputerze zdalnym, należy skopiować **vs\_profiler\_**_\<platformy >_ **\_**  _\<Języka >_**.exe** plik wchodzącej w skład _VSInstallDir %_**tools\performance Tools\Setups**folder programu Visual Studio komputera na komputerze zdalnym i zainstaluj go. Nie można użyć narzędzi profilowania w [narzędzia zdalne programu Visual Studio](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Pobieranie pakietu.  
  
   Możesz użyć [VSPerfCmd](../profiling/vsperfcmd.md) lub [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) do zbierania danych profilowania.  
  
   **Porada raportów**  
  
   Dane interakcji między warstwami można wyświetlić tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] lub [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE. Interakcje między warstwami plikowym raportów za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
