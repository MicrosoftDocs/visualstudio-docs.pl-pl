---
title: Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fe9e8d3dbd1e7395287cd7241f1e6145dffca7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145398"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wybrane [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania narzędzia i opcje wiersza polecenia są zależne od czynników, takich jak typ aplikacji, która jest profilowania, Metoda profilowania, która ma być używana, oraz czy aplikacja docelowa jest zapisywana w kodzie macierzystym czy w języku [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Ten temat organizuje Tematy proceduralne wiersza polecenia zgodnie z wybraną metodą profilowania.  
  
## <a name="in-this-topic"></a>W tym temacie:  
 [Korzystanie z metody próbkowania w celu zbierania statystyk wydajności](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody instrumentacji](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Wykorzystanie metod pamięci .NET do zbierania danych alokacji pamięci i okresu istnienia obiektów](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Używanie metody współbieżności do zbierania danych rywalizacji o zasoby i aktywność wątków](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Dodawanie danych interakcji między warstwami do przebiegu profilowania](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
## <a name="using-the-sampling-method-to-collect-performance-statistics"></a><a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Korzystanie z metody próbkowania w celu zbierania statystyk wydajności  
 Metoda próbkowania narzędzia profilowania zbiera dane dotyczące wydajności w określonych odstępach czasu w przebiegu profilowania. Dane próbkowania mogą zapewniać wgląd w problemy z wydajnością powiązane z PROCESORem i być dobrym sposobem na rozpoczęcie eksplorowania wydajności aplikacji.  
  
 Program Profiler i aplikację można uruchomić w tym samym czasie lub można dołączyć Profiler do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacje autonomiczne](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołącz do uruchomionego procesu**|-   [.NET Framework aplikacji autonomicznych](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Natywne aplikacje autonomiczne](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [ASP.NET aplikacje sieci Web](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi platformy .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi natywne](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="using-the-instrumentation-method-to-collect-detailed-timing-data"></a><a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Zbieranie szczegółowych danych o chronometrażu przy użyciu metody instrumentacji  
 Metoda narzędzia profilowania Instrumentation gromadzi dane wydajności z kopii plików binarnych aplikacji, które zawierają sondy oprogramowania umożliwiające rejestrowanie informacji o wydajności. Dane instrumentacji są zbierane na początku i na końcu każdej funkcji z instrumentacją oraz w każdym wywołaniu funkcji z Instrumentacji. Metoda Instrumentacji jest przydatna do wykrywania problemów z wydajnością w przypadku problemów z operacji we/wy, takich jak użycie dysku.  
  
 Tworzysz plik binarny Instrumentacji za pomocą narzędzia [VInstr.exe](../profiling/vsinstr.md) . Po zainicjowaniu profilera dane są automatycznie zbierane z Instrumentacji plików binarnych po uruchomieniu aplikacji docelowej.  
  
 **Typ aplikacji docelowej**  
  
- [.NET Framework autonomiczne składniki](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Natywne składniki autonomiczne](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Statycznie skompilowane aplikacje sieci Web ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [Dynamicznie kompilowane aplikacje sieci Web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [Usługi platformy .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
- [Usługi natywne](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="using-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a><a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Wykorzystanie metod pamięci .NET do zbierania danych alokacji pamięci i okresu istnienia obiektów  
 Metoda narzędzia profilowania pamięci .NET umożliwia zbieranie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] danych alokacji pamięci oraz informacji o okresie istnienia obiektów w programie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Aplikację docelową można uruchomić za pomocą profilera; Możesz dołączyć Profiler do uruchomionego wystąpienia aplikacji; można również utworzyć instrumentację wersji aplikacji do zbierania szczegółowych informacji o chronometrażu wraz z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] danymi pamięci.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Autonomiczne aplikacje .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Dołącz do uruchomionego procesu**|-   [.NET Framework aplikacji autonomicznych](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET aplikacje sieci Web](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Usługi platformy .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Moduły Instrumentacji**|-   [.NET Framework autonomiczne składniki](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Statycznie skompilowane aplikacje sieci Web ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Dynamicznie kompilowane aplikacje sieci Web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Usługi platformy .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="using-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a><a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Używanie metody współbieżności do zbierania danych rywalizacji o zasoby i aktywność wątków  
 Metoda współbieżności narzędzia profilowania pozwala zbierać dane dotyczące rywalizacji zasobów i wątku oraz przetwarzania danych z aplikacji wielowątkowych.  
  
 Aplikację można uruchomić za pomocą profilera lub można dołączyć Profiler do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Autonomiczna aplikacja .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Autonomiczna aplikacja natywna](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dołącz do uruchomionego procesu**|-   [.NET Framework aplikacji autonomicznej](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Natywna aplikacja autonomiczna](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [Aplikacja sieci Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa natywna](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="adding-tier-interaction-data-to-a-profiling-run"></a><a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Dodawanie danych interakcji między warstwami do przebiegu profilowania  
 Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
