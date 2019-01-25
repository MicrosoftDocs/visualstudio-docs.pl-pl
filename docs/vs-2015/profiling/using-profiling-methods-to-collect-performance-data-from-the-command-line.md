---
title: Korzystanie z metod profilowania do zbierania danych wydajności z wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 274508c0152571a36caf18bb481b1a23d9640d99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761383"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wybór [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] opcje i narzędzi wiersza poleceń Profiling Tools jest zależna od czynników, takich jak typ aplikacji, profilowany, metody profilowania, którego chcesz użyć, i czy aplikacji docelowej jest zapisywany w natywnym, czy [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]kodu.  
  
 W tym temacie organizuje wiersza polecenia tematów proceduralnych zgodnie z wybranej metody profilowania.  
  
## <a name="in-this-topic"></a>W tym temacie:  
 [Przy użyciu metody próbkowania w celu zbierania statystyk wydajności](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Przy użyciu metod pamięci .NET w celu zbierania danych pamięci alokacji i obiekt okresu istnienia](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Do zbierania danych działania rywalizacji o zasoby i wątku zasobów za pomocą metody współbieżności](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Dodawanie danych interakcji do profilowania](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Przy użyciu metody próbkowania w celu zbierania statystyk wydajności  
 Metoda pobierania próbek Profiling Tools zbiera dane dotyczące wydajności w określonych odstępach czasu do uruchomienia profilowania. Próbkowanie danych może zapewnić wgląd w problemy z wydajnością Procesora CPU i może być dobrym sposobem na rozpoczęcie eksplorowania wydajność aplikacji.  
  
 Można uruchomić profiler jak i aplikacji, w tym samym czasie, lub należy dołączyć profiler do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacje autonomiczne](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Natywne aplikacje autonomiczne](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Native Services](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji  
 Metoda Instrumentacja Profiling Tools zbiera dane wydajności z kopiuje pliki binarne aplikacji, które zawierają oprogramowanie sondy do informacji o wydajności rekordów. Na początku i końcu każdego instrumentowanych funkcji i w każdym wywołaniu do innych funkcji z instrumentowanych funkcji, zbierane są dane instrumentacji. Metoda Instrumentacja jest przydatna do wykrywania problemów z wydajnością za pomocą operacji We/Wy problemy, takie jak użycie dysku.  
  
 Utwórz instrumentowanego pliku binarnego z [VInstr.exe](../profiling/vsinstr.md) narzędzia. Po użytkownik zainicjowania programu profilującego, dane są automatycznie zbierane z instrumentowanych danych binarnych, po uruchomieniu aplikacji docelowej.  
  
 **Typ aplikacji docelowej**  
  
-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Składnikami macierzystymi autonomiczny](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Aplikacje sieci Web ASP.NET statycznie skompilowanej](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Aplikacje sieci Web ASP.NET dynamicznie skompilowanej](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [.NET Services](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Native Services](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Przy użyciu metod pamięci .NET w celu zbierania danych pamięci alokacji i obiekt okresu istnienia  
 Metoda pamięci Profiling Tools .NET umożliwia zbieranie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dane alokacji pamięci oraz informacje o okresie istnienia obiektów w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Można uruchomić aplikacji docelowej za pomocą profilera; należy dołączyć profiler do uruchomionego wystąpienia aplikacji; można także tworzyć instrumentowanej wersji aplikacji, zbierać szczegółowe informacje o czasach wraz z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dane pamięci.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Moduły Instrumentacji**|-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET statycznie skompilowanej](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET dynamicznie skompilowanej](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET Services](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Do zbierania danych działania rywalizacji o zasoby i wątku zasobów za pomocą metody współbieżności  
 Metody współbieżności Profiling Tools umożliwia zbieranie rywalizacji o zasoby i dane o aktywności procesu i wątku z poziomu aplikacji wielowątkowych.  
  
 Możesz uruchomić aplikację za pomocą profilera, lub należy dołączyć profiler do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Natywnej aplikacji autonomicznej](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Autonomicznej aplikacji natywnej](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [Aplikacja internetowa platformy ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET Service](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Native Service](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Dodawanie danych interakcji do profilowania  
 Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
