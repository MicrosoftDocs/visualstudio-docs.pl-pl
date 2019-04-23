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
ms.openlocfilehash: ee221f0c1da32694e869177399981cc16ce901f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099471"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **VsPerf** narzędzie wiersza polecenia do:  
  
1. Profil aplikacji Windows Store z poziomu wiersza polecenia, gdy program Visual Studio nie jest zainstalowany na urządzeniu.  
  
2. Profile, aplikacje klasyczne systemu Windows 8 i aplikacji systemu Windows Server 2012 za pomocą metoda profilowania próbkowanie.  
  
   Aby uzyskać więcej informacji na temat opcji profilowania, zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="BKMK_In_this_topic"></a> W tym temacie  
 W tym temacie opisano opcje używane z `vsperf.exe` narzędzia wiersza polecenia. Temat zawiera następujące sekcje:  
  
 [Tylko aplikacje Windows Store](#BKMK_windows_store_apps_only)  
  
 [Aplikacje klasyczne systemu Windows 8 i tylko w aplikacji systemu Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Wszystkie aplikacje](#BKMK_All_applications)  
  
## <a name="BKMK_windows_store_apps_only"></a> Tylko aplikacje Windows Store  
 Te opcje są stosowane tylko do aplikacji Windows Store.  
  
|||  
|-|-|  
|**App: {AppName}**|Uruchamia program profilujący i czeka, aż do określonej aplikacji, które mają zostać uruchomione z Start menu.<br /><br /> Uruchom `vsperf /listapps` Aby wyświetlić nazwę aplikacji i Pełna_nazwa_pakietu zainstalowanych aplikacji.|  
|**/package:{PackageFullName}**|Uruchamia program profilujący i czeka, aż do określonej aplikacji, które mają zostać uruchomione z Start menu.<br /><br /> Uruchom `vsperf /listapps` Aby wyświetlić nazwę aplikacji i Pełna_nazwa_pakietu zainstalowanych aplikacji.|  
|**/js**|Wymagane na potrzeby profilowania aplikacji JavaScript.<br /><br /> Zbieranie danych wydajności z aplikacji JavaScript.<br /><br /> Użyj tylko przy użyciu przełącznika/Package lub / dołączyć.|  
|**/noclr**|Opcjonalna. Nie zbieraj danych CLR.<br /><br /> Użyj tylko przy użyciu przełącznika/Package lub / dołączyć.<br /><br /> Optymalizacja, symboli zarządzanych, nie zostanie rozwiązany.|  
|**/listapps**|Lista zainstalowanych aplikacji, nazwy i PackageFullNames.|  
  
## <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Aplikacje klasyczne systemu Windows 8 i tylko w aplikacji systemu Windows Server 2012  
 Te opcje nie działają w aplikacjach Windows Store.  
  
|||  
|-|-|  
|**/ uruchomienia: {pliku wykonywalnego}**|Rozpoczyna się i rozpoczyna się profilowanie określony plik wykonywalny.|  
|**przełącznika/args: {ExecutableArguments}**|Określa argumenty wiersza polecenia do przekazania **/uruchamianie** docelowej.|  
|**/ Console**|Przebiegi **/uruchamianie** elementu docelowego w nowym oknie polecenia.|  
  
## <a name="BKMK_All_applications"></a> Wszystkie aplikacje  
 Te opcje stosowania się do aplikacji systemu Windows 8 lub Windows Server 2012.  
  
|||  
|-|-|  
|**/ Dołącz: {identyfikator PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Zbiera dane z określonych procesów.<br /><br /> Użyj Menedżera zadań, aby wyświetlić identyfikator procesu (PID) i nazwy działających aplikacji procesu.|  
|**/file:{ReportName}**|Opcjonalna. Określa plik wyjściowy (zastąpi istniejący plik).<br /><br /> Użyj tylko przy użyciu przełącznika/Package lub / dołączyć.|  
|**/ pause**|Wstrzymaj zbieranie danych.|  
|**/Resume**|Wznów zbieranie danych.|  
|**/ stop**|Zatrzymaj zbieranie danych, a następnie Zakończ działanie procesów docelowych.|  
|**/ Odłącz**|Zatrzymaj zbieranie danych, ale pozwól procesów docelowych, które będą nadal działać.|  
|**status**|Pokaż stan profilera.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
