---
title: Zbieranie danych pamięci z aplikacji sieci Web ASP.NET przy użyciu wiersza polecenia profilera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f7c759d4c2c4760be6782a518f4cdf209e828d4
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "64838108"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Zbieranie danych pamięci z aplikacji internetowej ASP.NET przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury i opcje zbierania danych alokacji pamięci i okresu istnienia obiektów dla aplikacji sieci Web ASP.NET za pomocą narzędzia wiersza polecenia **VSPerfCmd** .  
  
> [!NOTE]
> Narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzia profilowania, w tym Wstrzymywanie i wznawianie profilowania oraz gromadzenie dodatkowych danych z liczników wydajności procesora i systemu Windows. Możesz również użyć narzędzia wiersza polecenia  **VSPerfASPNETCmd** , gdy ta funkcja nie jest potrzebna. W porównaniu z narzędziem wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych ani ponownie uruchamiać komputera. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Dołącz profiler do uruchomionej aplikacji ASP.NET**|-   [Instrukcje: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych pamięci](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentowo skompilowane pliki binarne w sposób statyczny**|-   [Instrukcje: Instrumentacja statycznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrument dynamicznie skompilowane pliki binarne**|-   [Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Powiązane zadania  
  
### <a name="profiling-aspnet-web-applications"></a>Profilowanie aplikacji internetowej ASP.NET  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Profilowanie zasobów i aktywność wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Profilowanie danych .NET Framework pamięci  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Usługi profilu**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analizowanie widoków i raportów danych pamięci .NET  
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Informacje narzędzia profilowania wiersza polecenia](../profiling/command-line-profiling-tools-reference.md)
