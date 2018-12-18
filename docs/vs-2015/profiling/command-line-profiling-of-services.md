---
title: Profilowanie wiersza polecenia usług | Dokumentacja firmy Microsoft
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
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bffbaa2cf16c81d1d726043590c1b632560e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729866"
---
# <a name="command-line-profiling-of-services"></a>Profilowanie wiersza polecenia usług
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla usług Windows za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi profilowania z wiersza polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Zbieranie statystyk aplikacji:** zbierania statystyk wydajności przy użyciu metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** zbierać szczegółowe informacje o czasie przy użyciu metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Zbieranie danych pamięci .NET:** Użyj próbkowania i instrumentacji, aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiaru i liczby przydzielonych obiektów. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania.|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** umożliwia zbieranie danych kontencji zasobów i dane o aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszary nachodzące We/Wy i inne metody współbieżności zdarzenia systemowe.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Dodawanie danych o interakcji między warstwami:** możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania usługi do firmy Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazy danych.|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klienta)**|-   [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|



