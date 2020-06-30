---
title: VSPerf | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8042b228a481dc3d720d8b422963db41abbddcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533838"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj narzędzia wiersza polecenia **VsPerf** , aby:  
  
1. Profilowanie aplikacji ze sklepu Windows z poziomu wiersza polecenia, gdy program Visual Studio nie jest zainstalowany na urządzeniu.  
  
2. Profilowanie aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012 przy użyciu metody profilowania próbkowania.  
  
   Aby uzyskać więcej informacji na temat opcji profilowania, zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>W tym temacie  
 W tym temacie opisano opcje, których można użyć z `vsperf.exe` narzędziem wiersza polecenia. Temat zawiera następujące sekcje:  
  
 [Tylko aplikacje ze sklepu Windows](#BKMK_windows_store_apps_only)  
  
 [Aplikacje klasyczne systemu Windows 8 i aplikacje systemu Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Wszystkie aplikacje](#BKMK_All_applications)  
  
## <a name="windows-store-apps-only"></a><a name="BKMK_windows_store_apps_only"></a>Tylko aplikacje ze sklepu Windows  
 Te opcje mają zastosowanie tylko do aplikacji ze sklepu Windows.  
  
|Opcja|Opis|  
|-|-|  
|**/App: {nazwa_aplikacji}**|Uruchamia Profiler i czeka na uruchomienie określonej aplikacji z menu Start.<br /><br /> Uruchom, `vsperf /listapps` Aby wyświetlić nazwę aplikacji i PackageFullName zainstalowanych aplikacji.|  
|**/Package: {PackageFullName}**|Uruchamia Profiler i czeka na uruchomienie określonej aplikacji z menu Start.<br /><br /> Uruchom, `vsperf /listapps` Aby wyświetlić nazwę aplikacji i PackageFullName zainstalowanych aplikacji.|  
|**/js**|Wymagane do profilowania aplikacji JavaScript.<br /><br /> Zbieranie danych dotyczących wydajności z aplikacji JavaScript.<br /><br /> Używaj tylko z/Package lub/Attach.|  
|**/noclr**|Opcjonalny. Nie Zbieraj danych CLR.<br /><br /> Używaj tylko z/Package lub/Attach.<br /><br /> Optymalizacja nie zostanie rozpoznana przez żadne zarządzane symbole.|  
|**/listapps**|Wyświetl listę zainstalowanych nazw aplikacji i PackageFullNames.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a><a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a>Aplikacje klasyczne systemu Windows 8 i aplikacje systemu Windows Server 2012  
 Te opcje nie działają w aplikacjach ze sklepu Windows.  
  
|Opcja|Opis|  
|-|-|  
|**Przełącznik/Launch: {plik wykonywalny}**|Rozpoczyna i rozpoczyna profilowanie określonego pliku wykonywalnego.|  
|**/args: {ExecutableArguments}**|Określa argumenty wiersza polecenia do przekazania elementu docelowego **przełącznik/Launch** .|  
|**/Console**|Uruchamia element docelowy **przełącznik/Launch** w nowym oknie poleceń.|  
  
## <a name="all-applications"></a><a name="BKMK_All_applications"></a>Wszystkie aplikacje  
 Ta opcja ma zastosowanie do dowolnej aplikacji systemu Windows 8 lub Windows Server 2012.  
  
|Opcja|Opis|  
|-|-|  
|**/Attach: {PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Zbiera dane z określonych procesów.<br /><br /> Użyj Menedżera zadań, aby wyświetlić identyfikator procesu (PID) i nazwy procesów uruchomionych aplikacji.|  
|**/File: {ReportName}**|Opcjonalny. Określa plik wyjściowy (Zastępuje istniejący plik).<br /><br /> Używaj tylko z/Package lub/Attach.|  
|**/Pause**|Wstrzymywanie zbierania danych.|  
|**/Resume**|Wznów zbieranie danych.|  
|**/Stop**|Zatrzymaj zbieranie danych i kończenie procesów docelowych.|  
|**/detach**|Zatrzymaj zbieranie danych, ale pozwól, aby procesy docelowe nadal działały.|  
|**/status**|Pokaż stan profilera.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
