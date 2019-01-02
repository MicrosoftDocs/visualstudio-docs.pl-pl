---
title: Profilowanie wiersza polecenia aplikacji sieci Web programu ASP.NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 2b2f4602e56a89452635ebe0ad94dbc1664c2fb3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835347"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilowanie wiersza polecenia aplikacji sieci web ASP.NET
W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania z wiersza polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Wspólne zadania
  
| Zadanie | Powiązana zawartość |
| - | - |
| **Zbierz ASP.NET podstawowych danych profilowania w prosty sposób:** Użyj **VSPerfASPNETCmd** narzędzia do zbierania próbkowanie, instrumentację, pamięć .NET rywalizacji o zasoby i warstwy danych o interakcji między bez ponownego uruchomienia usług Internet Information Services (IIS), które są potrzebne i wymagania dotyczące konfiguracji Aby uzyskać **VSPerfCmd**. **Polecenie VSPerfASPNETCmd** nie pozwala zbierać dodatkowe dane lub kontrolować zbieranie danych. **Uwaga:**  **Polecenie VSPerfASPNETCmd** jest preferowanym narzędziem do użycia, możesz użyć programu profilującego autonomicznej do profilu usługi witryny sieci Web platformy ASP.NET. | -   [Szybkie profilowanie za pomocą polecenia VSPerfASPNETCmd witryny sieci web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Zbieranie statystyk aplikacji:** W celu zbierania statystyk wydajności, należy użyć metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemów użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Aby zbierać szczegółowe informacje o czasie, należy użyć metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Zbieranie danych pamięci .NET:** Aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiar i liczba przydzielonych obiektów, należy użyć próbkowania i instrumentacji. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania. | -   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Zbieranie danych współbieżności:** Metoda współbieżności służy do zbierania danych kontencji zasobów. **Uwaga:**  Zbieranie danych o aktywności i wizualizacji wątku nie jest obsługiwana dla aplikacji sieci Web. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Dodaj dane interakcji między warstwami:** Możesz dodać dane wydajności dotyczące synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] wywołuje się, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web wysyła do firmy Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych. | -   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Zadania powiązane

  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klienta)**|-   [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|