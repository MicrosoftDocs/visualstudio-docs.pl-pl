---
title: Szybkie witryny sieci Web profilowanie za pomocą polecenia VSPerfASPNETCmd | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759a1cbf711b4264478c1e7fc44a65b86328ce32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431974"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie za pomocą polecenia VSPerfASPNETCmd witryny sieci web

**VSPerfASPNETCmd** narzędzie wiersza polecenia umożliwia łatwe profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia Opcje są mniejsze, żadne zmienne środowiskowe muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Za pomocą **VSPerfASPNETCmd** jest preferowana metoda profilowania za pomocą Autonomiczny profiler. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie autonomicznego profilera](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, przy użyciu **VSPerfCmd** jest preferowana metoda profilowania.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

## <a name="profile-an-aspnet-application"></a>Profiluj aplikację ASP.NET

Do profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, wpisz jedno z poleceń opisanych w poniższych sekcjach. Witryna sieci Web jest uruchamiana, a program profiler uruchamia zbieranie danych. Wykonywanie aplikacji, a następnie zamknij przeglądarkę. Aby zatrzymać profilowanie, naciśnij klawisz **Enter** klucza w oknie wiersza polecenia.

> [!NOTE]
> Domyślnie, wiersz polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Możesz użyć **flagi/nowait** opcję, aby wymusić wiersza polecenia do zwrócenia. Zobacz [opcja flagi/nowait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>W celu zbierania statystyk aplikacji przy użyciu metody próbkowania
 Próbkowanie to domyślna metoda profilowania **VSPerfASPNETCmd** narzędzie i nie musi być określona w wierszu polecenia. Następujące polecenie w wierszu służy do zbierania statystyk aplikacji z określonej aplikacji sieci web:

 **vsperfaspnetcmd**  *websiteUrl*

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji

Użyj następującego polecenia, aby zebrać szczegółowe dane czasowe z dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web:

**vsperfaspnetcmd /trace**  *websiteUrl*

Jeśli chcesz przeprowadzić profilowanie statycznie skompilowany. *dll* plików w aplikacji sieci web muszą instrumentować plików za pomocą [VSInstr](../profiling/vsinstr.md) narzędzie wiersza polecenia. Polecenie vsperfaspnetcmd/trace będzie zawierać dane z instrumentowanych plików.

## <a name="to-collect-net-memory-data"></a>Do zbierania danych pamięci .NET

**/Memory** opcji zbiera dane dotyczące alokacji obiektów w pamięci platformy .NET i zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji to domyślny tryb **/Memory** danych opcji i nie musi być określona w wierszu polecenia.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Użyj **okres istnienia** parametru dodatkowo do zebrania danych o okresie istnienia obiektu z danymi alokacji:

 **vsperfaspnetcmd /memory:lifetime** *podanym adresem URL*

 Można również użyć **/Trace** opcję, aby uwzględnić szczegółowe informacje o czasie przy użyciu danych pamięci .NET:

 **polecenie vsperfaspnetcmd/Memory**[**: okres istnienia**]   **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Do zbierania danych o interakcji między warstwami

> [!WARNING]
> Interakcje między warstwami (TIP) dane profilowania mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Natomiast obejrzeć takie dane można wyświetlać tylko w programie Visual Studio Enterprise.
>
> Aby zebrać dane Porada w systemie Windows 8 lub Windows Server 2012, należy użyć Instrumentacji (**/trace**) opcji.

Aby zebrać dane interakcji między warstwami przy użyciu dane próbkowania:

**vsperfaspnetcmd /tip** `websiteUrl`

Aby zebrać dane interakcji między warstwami przy użyciu danych Instrumentacji:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Aby zebrać dane interakcji między warstwami przy użyciu danych pamięci .NET:

**polecenie vsperfaspnetcmd/Memory**[**: okres istnienia**] **/Porada**_podanym adresem URL_

## <a name="use-the-nowait-option"></a>Użyj opcji flagi/nowait

Domyślnie, wiersz polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Następująca opcja składni umożliwia wymuszenie wiersza polecenia, aby zwrócić. W oknie wiersza polecenia można wykonywać inne operacje. Aby zakończyć profilowania, należy użyć **/shutdown** opcję w oddzielnym **vsperfaspnetcmd** polecenia.

Aby rozpocząć profilowanie:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

Aby zakończyć profilowania:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Dodatkowe opcje

Można dodać dowolne z następujących opcji na polecenia wymienione wcześniej w tej sekcji, z wyjątkiem **polecenie vsperfaspnetcmd/shutdown** polecenia.

|Opcja|Opis|
|------------|-----------------|
|**/ Dane wyjściowe:** `VspFile`|Domyślnie dane profilowania (. *Vsp*) plik zostanie utworzony w bieżącym katalogu z nazwą pliku **pliku PerformanceReport.vsp**. Użyj opcji/OUTPUT, aby określić inną lokalizację i nazwę pliku.|
|**/PackSymbols:Off**|Domyślnie VsPerfASPNETCmd osadza w symbole (nazwy funkcji i parametrów oraz itp.). *vsp* pliku. Osadzanie symbole można wprowadzać bardzo duży plik danych profilowania. Jeśli masz dostęp do. *pdb* pliki, które zawierają symbole podczas analizowania danych, użyj packsymbols: Wyłącz możliwość wyłączenia osadzania symboli.|
