---
title: Profilowanie wiersza polecenia ASP.NET aplikacji sieci Web | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: aa184667e5d569bc2662052a29b25bfea6e470a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779574"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilowanie wiersza polecenia ASP.NET aplikacji internetowych
W tej sekcji opisano procedury i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] opcje zbierania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] danych o wydajności aplikacji sieci Web przy użyciu narzędzi profilowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Łatwe gromadzenie podstawowych danych ASP.NET profilowania:** Narzędzie **VSPerfASPNETCmd** służy do zbierania próbkowania, instrumentacji, pamięci .NET, rywalizacji lub interakcji warstwy bez wymagań konfiguracyjnych i ponownego uruchamiania internetowych usług informacyjnych (IIS), które są potrzebne dla **programu VSPerfCmd**. **VSPerfASPNETCmd** nie pozwala na zbieranie dodatkowych danych lub kontrolować zbieranie danych. **Uwaga:**  **VSPerfASPNETCmd** jest preferowanym narzędziem do używania autonomicznego profilera do profilowania ASP.NET witryn sieci Web. | -   [Szybkie profilowanie witryny sieci Web za pomocą vsperfAspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania do zbierania statystyk wydajności. Próbkowanie danych jest przydatne do analizowania problemów z użyciem procesora CPU i do zrozumienia ogólnych cech wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Zbieranie szczegółowych danych dotyczących chronometrażu:** Metoda instrumentacji służy do zbierania szczegółowych informacji o czasie. Dane instrumentacji jest przydatne do analizy problemów we/wy i do szczegółowej analizy scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Zbieranie danych pamięci platformy .NET:** Próbkowanie lub instrumentacji służy do zbierania danych alokacji pamięci .NET, które pokazują rozmiar i liczbę przydzielonych obiektów. Można również zbierać dane okresu istnienia obiektu, który pokazuje rozmiar i liczbę obiektów, które są odzyskane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Zbieranie danych współbieżności:** Metoda współbieżności służy do zbierania danych rywalizacji o zasoby. **Uwaga:**  Zbieranie danych aktywności wątku i wizualizacji nie jest obsługiwane dla aplikacji sieci Web. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Dodawanie danych interakcji warstwy:** Do bazy danych firmy Microsoft [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] można dodać dane dotyczące wydajności wywołań synchronicznych, które aplikacja sieci Web wykonuje. | -   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|
