---
title: Profilowanie wiersza polecenia aplikacji sieci Web ASP.NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c93cb4774953f1425ff0330d7f588cbbf0f0b823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827448"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilowanie wiersza polecenia aplikacji internetowych ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury i opcje zbierania danych wydajności dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania z wiersza polecenia.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Łatwo Zbieraj podstawowe dane profilowania ASP.NET:** Za pomocą narzędzia **VSPerfASPNETCmd** Zbieraj dane interakcji z próbką, Instrumentacją, pamięcią .NET, rywalizacją lub warstwą bez konieczności konfiguracji i ponownego uruchamiania Internet Information Services (IIS), które są niezbędne do **VSPerfCmd**. **VSPerfASPNETCmd** nie pozwala zbierać dodatkowych danych ani kontrolować zbierania danych. **Uwaga:**  **VSPerfASPNETCmd** jest preferowanym narzędziem do korzystania z autonomicznego profilera do profilowania witryn sieci Web ASP.NET.|-   [Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Zbieranie statystyk aplikacji:** Użyj metody próbkowania, aby zebrać dane statystyczne wydajności. Dane próbkowania są przydatne do analizowania problemów z użyciem procesora CPU oraz do poznania ogólnych cech wydajności aplikacji.|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** Użyj metody instrumentacji, aby zbierać szczegółowe informacje o chronometrażu. Dane instrumentacji są przydatne do analizowania problemów we/wy i dla szczegółowych analiz scenariuszy aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Zbierz dane pamięci .NET:** Użyj próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET pokazujące rozmiar i liczbę przydzielonych obiektów. Możesz również zbierać dane o okresie istnienia obiektu, pokazujące rozmiar i liczbę obiektów, które są odzyskiwane w każdej generacji wyrzucania elementów bezużytecznych.|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Zbierz dane współbieżności:** Użyj metody współbieżności, aby zebrać dane rywalizacji o zasoby. **Uwaga:**  Zbieranie danych dotyczących aktywności wątku i wizualizacji nie jest obsługiwane w przypadku aplikacji sieci Web.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Dodaj dane interakcji warstwy:** Można dodać dane wydajności dotyczące wywołań synchronicznych [!INCLUDE[vstecado](../includes/vstecado-md.md)] , które [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacja sieci Web tworzy w [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazie danych firmy Microsoft.|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Powiązane zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Usługi profilu**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|
