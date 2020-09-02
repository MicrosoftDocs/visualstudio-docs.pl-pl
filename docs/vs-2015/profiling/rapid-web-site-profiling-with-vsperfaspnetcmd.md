---
title: Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce5534f5723a3f0e570779939f207018cac71cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835303"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie wiersza polecenia **VSPerfASPNETCmd** umożliwia łatwe profilowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. W porównaniu do narzędzia wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) opcje są skracane, nie trzeba ustawiać żadnych zmiennych środowiskowych ani ponownie uruchamiać komputera. Użycie **VSPerfASPNETCmd** jest preferowaną metodą profilowania przy użyciu autonomicznego profilera. Aby uzyskać więcej informacji, zobacz [How to: Install](../profiling/how-to-install-the-stand-alone-profiler.md)The samodzielne Profiler.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, użycie **VSPerfCmd** jest preferowaną metodą profilowania.  
  
> [!NOTE]
> Narzędzia wiersza polecenia narzędzia profilowania znajdują się w podkatalogu \Team Tools\Performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach z 64 bitowym, użyj narzędzia VSPerfASPNETCmd znajdującego się w katalogu 32 bitowym \Team Tools\Performance Tools. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilowanie aplikacji ASP.NET  
 Aby profilować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikację sieci Web, wpisz jedno z poleceń opisanych w poniższych sekcjach. Witryna sieci Web zostanie uruchomiona, a Profiler zacznie zbierać dane. Ćwiczenie aplikacji, a następnie zamykanie przeglądarki. Aby zatrzymać profilowanie, naciśnij klawisz ENTER w oknie wiersza polecenia.  
  
> [!NOTE]
> Domyślnie wiersz polecenia nie zwraca po **VSPerfASPNETCmd** polecenia. Można użyć opcji **flagi/nowait** , aby wymusić zwrócenie wiersza polecenia. Zobacz [Korzystanie z opcji flagi/nowait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Aby zebrać statystyki aplikacji za pomocą metody próbkowania  
 Próbkowanie jest domyślną metodą profilowania narzędzia **VSPerfASPNETCmd** i nie musi być określona w wierszu polecenia. Poniższy wiersz polecenia zbiera statystyki aplikacji z określonej aplikacji sieci Web:  
  
 **VSPerfASPNETCmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu metody instrumentacji  
 Następujący wiersz polecenia służy do zbierania szczegółowych danych o chronometrażu z dynamicznie skompilowanej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web:  
  
 **VSPerfASPNETCmd/Trace**  *websiteUrl*  
  
 Jeśli chcesz profilować pliki dll skompilowane statycznie w aplikacji sieci Web, musisz Instrumentacja plików przy użyciu narzędzia wiersza polecenia [VSInstr](../profiling/vsinstr.md) . Polecenie VSPerfASPNETCmd/Trace będzie zawierać dane z Instrumentacji plików.  
  
## <a name="to-collect-net-memory-data"></a>Zbieranie danych pamięci .NET  
 Opcja **/Memory** zbiera dane dotyczące alokacji obiektów w pamięci .NET i może zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji jest domyślnym trybem opcji danych **/Memory** i nie musi być określone w wierszu polecenia.  
  
 **VSPerfASPNETCmd/Memory** *websiteUrl*  
  
 Użyj parametru **Lifetime** , aby zebrać dane okresu istnienia obiektu oprócz danych alokacji:  
  
 **VSPerfASPNETCmd/Memory: okres istnienia** *websiteUrl*  
  
 Można również użyć opcji **/Trace** , aby dołączyć szczegółowe informacje o chronometrażu do danych pamięci .NET:  
  
 **VSPerfASPNETCmd/Memory**[**: Lifetime**] **/Trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Aby zbierać dane interakcji warstwy  
  
> [!WARNING]
> Dane profilowania interakcji między warstwami (TIP) można zbierać przy użyciu [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] lub [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] . Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
>   
> Aby zebrać dane TIP w systemie Windows 8 lub Windows Server 2012, należy użyć opcji Instrumentacja (**/Trace**).  
  
 Aby zebrać dane dotyczące interakcji warstwy z danymi próbkowania:  
  
 **VSPerfASPNETCmd/TIP**`websiteUrl`  
  
 Aby zbierać dane dotyczące interakcji warstwy z danymi Instrumentacji:  
  
 **VSPerfASPNETCmd/Trace/TIP** *websiteUrl*  
  
 Aby zbierać dane interakcji warstwy z danymi pamięci platformy .NET:  
  
 **VSPerfASPNETCmd/Memory**[**: Lifetime**] **/TIP**_websiteUrl_  
  
## <a name="using-the-nowait-option"></a><a name="UsingNoWait"></a> Korzystanie z opcji flagi/nowait  
 Domyślnie wiersz polecenia nie zwraca po **VSPerfASPNETCmd** polecenia. Możesz użyć następującej opcji składni, aby wymusić zwrócenie wiersza polecenia. Następnie można wykonywać inne operacje w oknie wiersza polecenia. Aby zakończyć profilowanie, użyj opcji **/Shutdown** w osobnym **VSPerfASPNETCmd** polecenia.  
  
 Aby rozpocząć profilowanie:  
  
 **VSPerfASPNETCmd** [*/Options*] **flagi/nowait**_websiteUrl_  
  
 Aby zakończyć profilowanie:  
  
 **VSPerfASPNETCmd/Shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Opcje dodatkowe  
 Do poleceń wymienionych wcześniej w tej sekcji można dodać dowolną z następujących opcji, z wyjątkiem **VSPerfASPNETCmd/Shutdown** polecenia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Output:**`VspFile`|Domyślnie plik danych profilowania (. vsp) jest tworzony w bieżącym katalogu przy użyciu nazwy pliku **PerformanceReport. vsp**. Użyj opcji/Output, aby określić inną lokalizację, nazwę pliku lub oba te elementy.|  
|**/PackSymbols: wyłączone**|Domyślnie VsPerfASPNETCmd osadza symbole (nazwy funkcji i parametrów itp.) w pliku VSP. Osadzenie symboli może sprawiać, że plik danych profilowania jest bardzo duży. Jeśli będziesz mieć dostęp do plików. pdb, które zawierają symbole podczas analizowania danych, użyj opcji/packsymbols: off, aby wyłączyć osadzanie symboli.|
