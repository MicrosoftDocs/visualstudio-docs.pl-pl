---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f4b2b78f7187b7a49b78312a1105a2af884fda3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186640"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla aplikacji autonomicznej (klienta) przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi profilowania z wiersza polecenia.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Zbieranie statystyk aplikacji:** W celu zbierania statystyk wydajności, należy użyć metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** Aby zbierać szczegółowe informacje o czasie, należy użyć metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych pamięci .NET:** Aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiar i liczba przydzielonych obiektów, należy użyć próbkowania i instrumentacji. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania.|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** Aby zbierać dane kontencji zasobów i dane o aktywności wątku, który pokazuje CPU wykorzystania, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszarów nakładania się wejść / i inne zdarzenia systemowe, należy użyć metody współbieżności.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Dodawanie danych interakcji między warstwami:** Możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania aplikacji do firmy Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazy danych. Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Wypróbuj to:** Użyj procedury krok po kroku do profilowania Przykładowa aplikacja kliencka, za pomocą metody próbkowania i instrumentacji.|-   [Wskazówki: Profilowanie wiersza polecenia przy użyciu próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Wskazówki: Profilowanie wiersza polecenia przy użyciu instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|
