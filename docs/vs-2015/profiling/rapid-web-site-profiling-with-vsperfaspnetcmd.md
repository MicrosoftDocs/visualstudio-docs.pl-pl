---
title: Szybkie witryny sieci Web profilowanie za pomocą polecenia VSPerfASPNETCmd | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438902"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfASPNETCmd** narzędzia wiersza polecenia umożliwia łatwe profilu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia Opcje są mniejsze, żadne zmienne środowiskowe muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Za pomocą **VSPerfASPNETCmd** jest preferowana metoda profilowania za pomocą Autonomiczny profiler. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie autonomiczny Profiler](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, przy użyciu **VSPerfCmd** jest preferowana metoda profilowania.  
  
> [!NOTE]
> Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowy narzędzie VSPerfASPNETCmd znajduje się w katalogu narzędzi tools\performance 32-bitowych. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilowanie aplikacji ASP.NET  
 Do profilu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, wpisz jedno z poleceń opisanych w poniższych sekcjach. Witryna sieci Web jest uruchamiana, a program profiler uruchamia zbieranie danych. Wykonywanie aplikacji, a następnie zamknij przeglądarkę. Aby zatrzymać profilowanie, naciśnij klawisz Enter w oknie wiersza polecenia.  
  
> [!NOTE]
> Domyślnie, wiersz polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Możesz użyć **flagi/nowait** opcję, aby wymusić wiersza polecenia do zwrócenia. Zobacz [przy użyciu opcji flagi/nowait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>W celu zbierania statystyk aplikacji przy użyciu metody próbkowania  
 Próbkowanie to domyślna metoda profilowania **VSPerfASPNETCmd** narzędzie i nie musi być określona w wierszu polecenia. Następujące polecenie w wierszu służy do zbierania statystyk aplikacji z określonej aplikacji sieci Web:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji  
 Użyj następującego polecenia, aby zebrać szczegółowe dane czasowe z dynamicznie skompilowanej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web:  
  
 **vsperfaspnetcmd /trace**  *websiteUrl*  
  
 Jeśli chcesz przeprowadzić profilowanie plików dll statycznie skompilowanej w aplikacji sieci Web, muszą instrumentować plików za pomocą [VSInstr](../profiling/vsinstr.md) narzędzie wiersza polecenia. Polecenie vsperfaspnetcmd/trace będzie zawierać dane z instrumentowanych plików.  
  
## <a name="to-collect-net-memory-data"></a>Do zbierania danych pamięci .NET  
 **/Memory** opcji zbiera dane dotyczące alokacji obiektów w pamięci platformy .NET i zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji to domyślny tryb **/Memory** danych opcji i nie musi być określona w wierszu polecenia.  
  
 **vsperfaspnetcmd /memory** *websiteUrl*  
  
 Użyj **okres istnienia** parametru dodatkowo do zebrania danych o okresie istnienia obiektu z danymi alokacji:  
  
 **vsperfaspnetcmd /memory:lifetime** *podanym adresem URL*  
  
 Można również użyć **/Trace** opcję, aby uwzględnić szczegółowe informacje o czasie przy użyciu danych pamięci .NET:  
  
 **polecenie vsperfaspnetcmd/Memory**[**: okres istnienia**]   **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Do zbierania danych o interakcji między warstwami  
  
> [!WARNING]
> Interakcje między warstwami (TIP) danych profilowania można zbierać w programach [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], lub [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Natomiast obejrzeć takie dane można wyświetlić tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
>   
> Aby zebrać dane Porada w systemie Windows 8 lub Windows Server 2012, należy użyć Instrumentacji (**/trace**) opcji.  
  
 Aby zebrać dane interakcji między warstwami przy użyciu dane próbkowania:  
  
 **vsperfaspnetcmd /tip** `websiteUrl`  
  
 Aby zebrać dane interakcji między warstwami przy użyciu danych Instrumentacji:  
  
 **vsperfaspnetcmd /trace /tip** *websiteUrl*  
  
 Aby zebrać dane interakcji między warstwami przy użyciu danych pamięci .NET:  
  
 **polecenie vsperfaspnetcmd/Memory**[**: okres istnienia**] **/Porada**_podanym adresem URL_  
  
## <a name="UsingNoWait"></a> Przy użyciu opcji flagi/nowait  
 Domyślnie, wiersz polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Następująca opcja składni umożliwia wymuszenie wiersza polecenia, aby zwrócić. W oknie wiersza polecenia można wykonywać inne operacje. Aby zakończyć profilowania, należy użyć **/shutdown** opcję w oddzielnym **vsperfaspnetcmd** polecenia.  
  
 Aby rozpocząć profilowanie:  
  
 **vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_  
  
 Aby zakończyć profilowania:  
  
 **vsperfaspnetcmd /shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Dodatkowe opcje  
 Można dodać dowolne z następujących opcji na polecenia wymienione wcześniej w tej sekcji, z wyjątkiem **polecenie vsperfaspnetcmd/shutdown** polecenia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ Dane wyjściowe:** `VspFile`|Domyślnie plik profilowania (.vsp) danych jest tworzony w bieżącym katalogu z nazwą pliku **pliku PerformanceReport.vsp**. Użyj opcji/OUTPUT, aby określić inną lokalizację i nazwę pliku.|  
|**/PackSymbols:Off**|Domyślnie VsPerfASPNETCmd osadza symbole (funkcja i nazwy parametrów itp.) w pliku Vsp. Osadzanie symbole można wprowadzać bardzo duży plik danych profilowania. Jeśli masz dostęp do plików .pdb, które zawierają symbole podczas analizowania danych, użyj packsymbols: Wyłącz możliwość wyłączenia osadzania symboli.|
