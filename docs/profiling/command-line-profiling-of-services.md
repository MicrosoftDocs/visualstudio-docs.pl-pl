---
title: Profilowanie wiersza polecenia usług | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec59cde780a1d6b05ea6a5d42d458ec50c48e385
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990204"
---
# <a name="command-line-profiling-of-services"></a>Profilowanie wiersza polecenia usług
W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla usług Windows za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania z wiersza polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Wspólne zadania

  
| Zadanie | Powiązana zawartość |
| - | - |
| **Zbieranie statystyk aplikacji:** W celu zbierania statystyk wydajności, należy użyć metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Aby zbierać szczegółowe informacje o czasie, należy użyć metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Zbieranie danych pamięci .NET:** Aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiar i liczba przydzielonych obiektów, należy użyć próbkowania i instrumentacji. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania. | -   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Zbieranie danych współbieżności:** Aby zbierać dane kontencji zasobów i dane o aktywności wątku, który pokazuje CPU wykorzystania, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszary nachodzące We/Wy i inne zdarzenia systemowe, należy użyć metody współbieżności. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Dodaj dane interakcji między warstwami:** Możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania usługi do firmy Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych. | -   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Zadania powiązane  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klienta)**|-   [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil aplikacji ASP.NET**|-   [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)|