---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Dokumentacja firmy Microsoft
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
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2879ecfe22722b3a3c2f5fc836ec9874f7acdf2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756452"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla aplikacji autonomicznej (klienta) przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi profilowania z wiersza polecenia.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Zbieranie statystyk aplikacji:** zbierania statystyk wydajności przy użyciu metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** zbierać szczegółowe informacje o czasie przy użyciu metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych pamięci .NET:** Użyj próbkowania i instrumentacji, aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiaru i liczby przydzielonych obiektów. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania.|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** umożliwia zbieranie danych kontencji zasobów i dane o aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszary nachodzące operacji We/Wy i inne metody współbieżności zdarzenia systemowe.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Dodawanie danych interakcji między warstwami:** możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania aplikacji do firmy Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazy danych. Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Wypróbuj:** procedury krok po kroku profilu Przykładowa aplikacja kliencka przy użyciu metody próbkowania i instrumentacji.|-   [Wskazówki: Profilowanie wiersza polecenia przy użyciu metody próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Wskazówki: Profilowanie wiersza polecenia przy użyciu metody Instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|



