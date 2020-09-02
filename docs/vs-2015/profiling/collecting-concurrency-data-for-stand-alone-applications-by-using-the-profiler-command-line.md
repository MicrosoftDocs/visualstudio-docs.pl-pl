---
title: Zbieranie danych współbieżności dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fac1c840d93c03b659e7934a82eb53895b60ede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141938"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metoda współbieżności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania pozwala zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację wątków, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy i inne zdarzenia systemowe.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Uruchamianie .NET Framework aplikacji i danych współbieżności profilu**|-   [Instrukcje: uruchamianie aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Uruchamianie aplikacji C/C++ i danych współbieżności profilu**|-   [Instrukcje: uruchamianie aplikacji natywnej w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dołącz profiler do uruchomionej aplikacji .NET Framework**|-   [Instrukcje: dołączanie profilera do aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dołącz profiler do uruchomionej aplikacji C/C++**|-   [Instrukcje: dołączanie profilera do aplikacji natywnej i zbieranie danych współbieżności](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)|  
  
## <a name="related-tasks"></a>Powiązane zadania  
  
### <a name="profiling-stand-alone-applications"></a>Profilowanie aplikacji autonomicznych  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profilowanie alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Dodawanie danych interakcji między warstwami**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilowania problemów współbieżności  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profilowanie aplikacji ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Usługi profilu**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analizowanie widoków danych współbieżności i raportów  
 [Widok danych kontencji zasobów](../profiling/resource-contention-data-views.md)  
  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Dokumentacja  
 [Informacje narzędzia profilowania wiersza polecenia](../profiling/command-line-profiling-tools-reference.md)
