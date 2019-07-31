---
title: Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd | Microsoft Docs
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
ms.openlocfilehash: 5f86ae2e14067a645bb39a1c8fdc0421f415a9e6
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681133"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd

Narzędzie wiersza polecenia **VSPerfASPNETCmd** umożliwia łatwe profilowanie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W porównaniu do narzędzia wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) opcje są skracane, nie trzeba ustawiać żadnych zmiennych środowiskowych ani ponownie uruchamiać komputera. Użycie **VSPerfASPNETCmd** jest preferowaną metodą profilowania przy użyciu autonomicznego profilera. Aby uzyskać więcej informacji, zobacz [jak: Zainstaluj autonomiczny profiler](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, użycie **VSPerfCmd** jest preferowaną metodą profilowania.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

## <a name="profile-an-aspnet-application"></a>Profilowanie aplikacji ASP.NET

Aby profilować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web, wpisz jedno z poleceń opisanych w poniższych sekcjach. Witryna sieci Web zostanie uruchomiona, a Profiler zacznie zbierać dane. Ćwiczenie aplikacji, a następnie zamykanie przeglądarki. Aby zatrzymać profilowanie, naciśnij klawisz **Enter** w oknie wiersza polecenia.

> [!NOTE]
> Domyślnie wiersz polecenia nie zwraca po **VSPerfASPNETCmd** polecenia. Można użyć opcji **flagi/nowait** , aby wymusić zwrócenie wiersza polecenia. Zobacz [Korzystanie z opcji flagi/nowait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Aby zebrać statystyki aplikacji za pomocą metody próbkowania
 Próbkowanie jest domyślną metodą profilowania narzędzia **VSPerfASPNETCmd** i nie musi być określona w wierszu polecenia. Poniższy wiersz polecenia zbiera statystyki aplikacji z określonej aplikacji sieci Web:

 **vsperfaspnetcmd**  *websiteUrl*

 Przykładem *websiteUrl* na serwerze lokalnym może być *http://localhost/MySite/default.aspx* . Przykładem zewnętrznej witryny jest *http://www.contoso.com* . Aby uzyskać więcej informacji, zobacz przykładowe adresy URL w programie w [celu profilowania witryny sieci Web bez otwierania projektu w programie Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu metody instrumentacji

Następujący wiersz polecenia służy do zbierania szczegółowych danych o chronometrażu z dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web:

**VSPerfASPNETCmd/Trace** *websiteUrl*

Jeśli chcesz profilować skompilowanie statycznie. pliki *dll* w aplikacji sieci Web, należy Instrumentacja plików przy użyciu narzędzia wiersza polecenia [VSInstr](../profiling/vsinstr.md) . Polecenie VSPerfASPNETCmd/Trace będzie zawierać dane z Instrumentacji plików.

## <a name="to-collect-net-memory-data"></a>Zbieranie danych pamięci .NET

Opcja **/Memory** zbiera dane dotyczące alokacji obiektów w pamięci .NET i może zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji jest domyślnym trybem opcji danych **/Memory** i nie musi być określone w wierszu polecenia.

 **VSPerfASPNETCmd/Memory** *websiteUrl*

 Użyj parametru **Lifetime** , aby zebrać dane okresu istnienia obiektu oprócz danych alokacji:

 **VSPerfASPNETCmd/Memory: okres istnienia** *websiteUrl*

 Można również użyć opcji **/Trace** , aby dołączyć szczegółowe informacje o chronometrażu do danych pamięci .NET:

 **VSPerfASPNETCmd/Memory** [ **: okres istnienia**] **/Trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Aby zbierać dane interakcji warstwy

> [!WARNING]
> Dane profilowania interakcji między warstwami (TIP) można zbierać przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w Visual Studio Enterprise.
>
> Aby zebrać dane TIP w systemie Windows 8 lub Windows Server 2012, należy użyć opcji Instrumentacja ( **/Trace**).

Aby zebrać dane dotyczące interakcji warstwy z danymi próbkowania:

**VSPerfASPNETCmd/TIP**`websiteUrl`

Aby zbierać dane dotyczące interakcji warstwy z danymi Instrumentacji:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Aby zbierać dane interakcji warstwy z danymi pamięci platformy .NET:

**VSPerfASPNETCmd/Memory** [ **: okres istnienia**] **/TIP** _websiteUrl_

## <a name="use-the-nowait-option"></a>Użyj opcji flagi/nowait

Domyślnie wiersz polecenia nie zwraca po **VSPerfASPNETCmd** polecenia. Możesz użyć następującej opcji składni, aby wymusić zwrócenie wiersza polecenia. Następnie można wykonywać inne operacje w oknie wiersza polecenia. Aby zakończyć profilowanie, użyj opcji **/Shutdown** w osobnym **VSPerfASPNETCmd** polecenia.

Aby rozpocząć profilowanie:

**VSPerfASPNETCmd** [ */Options*] **flagi/nowait** _websiteUrl_

Aby zakończyć profilowanie:

**VSPerfASPNETCmd/Shutdown** *websiteUrl*

## <a name="additional-options"></a>Opcje dodatkowe

Do poleceń wymienionych wcześniej w tej sekcji można dodać dowolną z następujących opcji, z wyjątkiem **VSPerfASPNETCmd/Shutdown** polecenia.

|Opcja|Opis|
|------------|-----------------|
|**/Output:** `VspFile`|Domyślnie dane profilowania (. *VSP*) w bieżącym katalogu zostanie utworzony plik o nazwie **PerformanceReport. vsp**. Użyj opcji/Output, aby określić inną lokalizację, nazwę pliku lub oba te elementy.|
|**/PackSymbols: wyłączone**|Domyślnie VsPerfASPNETCmd osadza symbole (nazwy funkcji i parametrów itd.) w. plik *VSP* . Osadzenie symboli może sprawiać, że plik danych profilowania jest bardzo duży. Jeśli będziesz mieć dostęp do programu. pliki *PDB* , które zawierają symbole podczas analizowania danych, należy użyć opcji/packsymbols: off, aby wyłączyć osadzanie symboli.|
