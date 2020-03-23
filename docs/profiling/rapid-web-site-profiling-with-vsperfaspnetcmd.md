---
title: Szybkie profilowanie witryny sieci Web za pomocą vsperfASPNETCmd | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fff2486c4197cbbe28c3b5deb0099e264805e12b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771695"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie witryny sieci Web za pomocą vsperfAspnetcmd

Narzędzie wiersza polecenia **VSPerfASPNETCmd** umożliwia [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] łatwe profilowanie aplikacji internetowych. W porównaniu do narzędzia wiersza polecenia [VSPerfCmd,](../profiling/vsperfcmd.md) opcje są zmniejszone, nie ma zmiennych środowiskowych muszą być ustawione, a ponowne uruchomienie komputera nie jest wymagane. Za pomocą **VSPerfASPNETCmd** jest preferowaną metodą profilowania za pomocą autonomicznego profilera. Aby uzyskać więcej informacji, zobacz [Jak: Instalowanie autonomicznego profilera](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, przy użyciu **VSPerfCmd** jest preferowaną metodą profilowania.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

## <a name="profile-an-aspnet-application"></a>Profiluj aplikację ASP.NET

Aby profilować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci web, wpisz jedno z poleceń opisanych w poniższych sekcjach. Witryna sieci Web jest uruchomiona, a profiler rozpoczyna zbieranie danych. Ćwicz aplikację, a następnie zamknij przeglądarkę. Aby zatrzymać profilowanie, naciśnij klawisz **Enter** w oknie wiersza polecenia.

> [!NOTE]
> Domyślnie wiersz polecenia nie zwraca się po poleceniu **vsperfaspnetcmd.** Można użyć opcji **/nowait,** aby wymusić powrót wiersza polecenia. Zobacz [Użyj opcji /NoWait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Aby zebrać statystyki aplikacji przy użyciu metody pobierania próbek
 Próbkowanie jest domyślną metodą profilowania narzędzia **VSPerfASPNETCmd** i nie musi być określona w wierszu polecenia. Następujący wiersz polecenia zbiera statystyki aplikacji z określonej aplikacji sieci web:

 **vsperfaspnetcmd**  *strona internetowaUrl*

 Przykładem lokalnej witryny sieci Web hosted *http://localhost/MySite/default.aspx* *serverUrl* może być . Przykładem lokacji zewnętrznej *http://www.contoso.com*jest . Aby uzyskać więcej informacji, zobacz przykładowe adresy URL w [do profilu witryny sieci Web bez otwierania projektu w programie Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Aby zebrać szczegółowe dane dotyczące chronometrażu przy użyciu metody instrumentacji

Użyj następującego wiersza polecenia, aby zebrać [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] szczegółowe dane chronometrażu z dynamicznie skompilowaną aplikacją sieci web:

**vsperfaspnetcmd /śledź**  *stronę internetowąUrl*

Jeśli chcesz profil statycznie skompilowany . *dll* plików w aplikacji sieci web, należy instrumentować pliki za pomocą narzędzia wiersza polecenia [VSInstr.](../profiling/vsinstr.md) Polecenie vsperfaspnetcmd /trace będzie zawierać dane z instrumentowanych plików.

## <a name="to-collect-net-memory-data"></a>Aby zebrać dane pamięci .NET

Opcja **/Memory** zbiera dane dotyczące alokacji obiektów w pamięci platformy .NET i może zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji jest domyślnym trybem opcji **/Memory** data i nie musi być określone w wierszu polecenia.

 **vsperfaspnetcmd /memory websiteUrl vsperfaspnetcmd /memory websiteUrl vsperfaspnetcmd /memory** *websiteUrl vsper*

 Parametr **Lifetime** służy do zbierania danych dotyczących okresu istnienia obiektu oprócz danych alokacji:

 **vsperfaspnetcmd /memory:lifetime websiteUrl vsperfaspnetcmd /memory:lifetime websiteUrl vsperfaspnetcmd /memory:lifetime** *websiteUrl vsper*

 Można również użyć **/Trace** opcji, aby dołączyć szczegółowe informacje o chronometrażu z danymi pamięci .NET:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Aby zbierać dane interakcji warstwy

> [!WARNING]
> Dane profilowania interakcji warstwy (TIP) mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise.
>
> Aby zbierać dane TIP w systemie Windows 8 lub Windows Server 2012, należy użyć opcji instrumentacji (**/trace).**

Aby zbierać dane interakcji warstwy z danymi próbkowania:

**vsperfaspnetcmd /końcówka**`websiteUrl`

Aby zbierać dane dotyczące interakcji warstwy z danymi instrumentacji:

**vsperfaspnetcmd /trace /tip websiteUrl vsperfaspnetcmd /trace /tip websiteUrl vsperfaspnetcmd /trace /tip** *websiteUrl vsper*

Aby zbierać dane interakcji warstwy za pomocą danych pamięci .NET:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Użyj opcji /NoWait

Domyślnie wiersz polecenia nie zwraca się po poleceniu **vsperfaspnetcmd.** Można użyć następującej opcji składni, aby wymusić powrót wiersza polecenia. Następnie można wykonać inne operacje w oknie wiersza polecenia. Aby zakończyć profilowanie, należy użyć opcji **/shutdown** w osobnym poleceniu **vsperfaspnetcmd.**

Aby rozpocząć profilowanie:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

Aby zakończyć profilowanie:

**vsperfaspnetcmd /shutdown** *strona internetowaUrl*

## <a name="additional-options"></a>Opcje dodatkowe

Do poleceń wymienionych wcześniej w tej sekcji można dodać dowolną z następujących opcji, z wyjątkiem polecenia **vsperfaspnetcmd /shutdown.**

|Opcja|Opis|
|------------|-----------------|
|**/Wyjście:**`VspFile`|Domyślnie dane profilowania (.* vsp)* tworzony jest w bieżącym katalogu o nazwie pliku **PerformanceReport.vsp**. Użyj opcji /output, aby określić inną lokalizację, nazwę pliku lub obie te lokalizacje.|
|**/PackSymbols:Wył.**|Domyślnie vsperfASPNETCmd osadza symbole (nazwy funkcji i parametrów itd.) w pliku . *vsp.* Osadzanie symboli może sprawić, że plik danych profilowania będzie bardzo duży. Jeśli będziesz mieć dostęp do pliku . *pliki pdb,* które zawierają symbole podczas analizowania danych, użyj opcji /packsymbols:off, aby wyłączyć osadzanie symboli.|
