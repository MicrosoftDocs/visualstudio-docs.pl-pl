---
title: Profilowanie wiersza polecenia aplikacji sieci Web programu ASP.NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5436da548acaf16169437fdc98b51d182891d2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759156"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilowanie wiersza polecenia aplikacji internetowych ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi profilowania z wiersza polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Zbieranie ASP.NET podstawowe dane profilowania łatwo:** użyj **VSPerfASPNETCmd** narzędzia do zbierania próbkowanie, instrumentację, pamięć .NET rywalizacji o zasoby i warstwy danych o interakcji między bez wymagania dotyczące konfiguracji i Ponowne uruchomienie usług Internet Information Services (IIS), które są wymagane przez **VSPerfCmd**. **Polecenie VSPerfASPNETCmd** nie pozwala zbierać dodatkowe dane lub kontrolować zbieranie danych. **Uwaga:****VSPerfASPNETCmd** jest preferowanym narzędziem do użycia, możesz użyć programu profilującego autonomicznej do profilu usługi witryny sieci Web platformy ASP.NET.|-   [Szybkie profilowanie za pomocą polecenia VSPerfASPNETCmd witryny sieci Web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Zbieranie statystyk aplikacji:** zbierania statystyk wydajności przy użyciu metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemów użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** zbierać szczegółowe informacje o czasie przy użyciu metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Zbieranie danych pamięci .NET:** Użyj próbkowania i instrumentacji, aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiaru i liczby przydzielonych obiektów. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania.|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** zbierania danych kontencji zasobów przy użyciu metody współbieżności. **Uwaga:** zbieranie wątku działania i wizualizacji danych, nie jest obsługiwana dla aplikacji sieci Web.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Dodawanie danych o interakcji między warstwami:** możesz dodać dane wydajności dotyczące synchroniczne [!INCLUDE[vstecado](../includes/vstecado-md.md)] wywołuje się, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web wysyła do firmy Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazy danych.|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klienta)**|-   [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|



