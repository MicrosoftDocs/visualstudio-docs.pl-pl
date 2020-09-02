---
title: Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7d56f0d8540da90925ebe2f5fc4ab8f6372bc3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785648"
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metoda współbieżności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania pozwala zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację wątków, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy i inne zdarzenia systemowe.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Dołącz do uruchomionej usługi platformy .NET**|-   [Instrukcje: dołączanie profilera do usługi .NET w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Dołącz do uruchomionej usługi C/C++**|-   [Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Powiązane zadania  
  
### <a name="profiling-windows-services"></a>Profilowanie usług systemu Windows  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profile.NET alokacji pamięci i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-concurrency-data"></a>Profilowanie danych współbieżności  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profile aplikacji autonomicznych**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilowanie aplikacji sieci Web ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analizowanie widoków danych współbieżności i raportów  
 [Widok danych kontencji zasobów](../profiling/resource-contention-data-views.md)  
  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Informacje narzędzia profilowania wiersza polecenia](../profiling/command-line-profiling-tools-reference.md)
