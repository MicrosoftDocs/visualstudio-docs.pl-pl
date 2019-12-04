---
title: Korzystanie z metod profilowania wiersza polecenia w celu uzyskania danych wydajności
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b30aa723ea3014aec2bd05d4bd204b9427b3c218
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779977"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
Wybór [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania narzędzia i opcje wiersza polecenia zależą od takich czynników, jak typ profilowania aplikacji, Metoda profilowania, która ma być używana, oraz czy aplikacja docelowa jest zapisywana w kodzie natywnym czy .NET Framework.

 Ten temat organizuje Tematy proceduralne wiersza polecenia zgodnie z wybraną metodą profilowania.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Użycie metody próbkowania w celu zbierania danych statystycznych wydajności
 Metoda próbkowania narzędzia profilowania zbiera dane dotyczące wydajności w określonych odstępach czasu w przebiegu profilowania. Dane próbkowania mogą zapewniać wgląd w problemy z wydajnością powiązane z PROCESORem i być dobrym sposobem na rozpoczęcie eksplorowania wydajności aplikacji.

 Program Profiler i aplikację można uruchomić w tym samym czasie lub można dołączyć Profiler do uruchomionego wystąpienia aplikacji.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchom aplikację**|-   [aplikacji autonomicznych](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Dołącz do uruchomionego procesu**|-   [.NET Framework Aplikacje autonomiczne](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [natywnych aplikacji autonomicznych](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [aplikacje sieci web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [usługi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [usługi natywne](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu metody instrumentacji
 Metoda narzędzia profilowania Instrumentation gromadzi dane wydajności z kopii plików binarnych aplikacji, które zawierają sondy oprogramowania umożliwiające rejestrowanie informacji o wydajności. Dane instrumentacji są zbierane na początku i na końcu każdej funkcji z instrumentacją oraz w każdym wywołaniu funkcji z Instrumentacji. Metoda Instrumentacji jest przydatna do wykrywania problemów z wydajnością w przypadku problemów z operacji we/wy, takich jak użycie dysku.

 Tworzysz plik binarny Instrumentacji za pomocą narzędzia [VInstr. exe](../profiling/vsinstr.md) . Po zainicjowaniu profilera dane są automatycznie zbierane z Instrumentacji plików binarnych po uruchomieniu aplikacji docelowej.

 **Typ aplikacji docelowej**

- [.NET Framework autonomiczne składniki](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Natywne składniki autonomiczne](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Statycznie skompilowane aplikacje sieci Web ASP.NET](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dynamicznie kompilowane aplikacje sieci Web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Usługi platformy .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Usługi natywne](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Użyj metod pamięci platformy .NET do zbierania danych alokacji pamięci i okresu istnienia obiektów
 Metoda narzędzia profilowania pamięci .NET umożliwia zbieranie danych alokacji pamięci .NET Framework i informacji o okresie istnienia obiektów w .NET Framework.

 Aplikację docelową można uruchomić za pomocą profilera; Możesz dołączyć Profiler do uruchomionego wystąpienia aplikacji; Możesz również utworzyć instrumentację wersji aplikacji, aby zbierać szczegółowe informacje o chronometrażu wraz z danymi pamięci .NET Framework.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchom aplikację**|-   autonomiczne [aplikacje .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Dołącz do uruchomionego procesu**|-   [.NET Framework Aplikacje autonomiczne](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [aplikacje sieci web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [usługi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Moduły Instrumentacji**|-   [.NET Framework składników autonomicznych](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [skompilowane statycznie aplikacje sieci web ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [dynamicznie kompilowane aplikacje sieci web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [usługi .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Użyj metody współbieżności, aby zebrać dane rywalizacji o zasoby i aktywność wątku
 Metoda współbieżności narzędzia profilowania pozwala zbierać dane dotyczące rywalizacji zasobów i wątku oraz przetwarzania danych z aplikacji wielowątkowych.

 Aplikację można uruchomić za pomocą profilera lub można dołączyć Profiler do uruchomionego wystąpienia aplikacji.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchom aplikację**|-   autonomiczną [aplikację .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   autonomiczną [aplikację natywną](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Dołącz do uruchomionego procesu**|-   [.NET Framework aplikacji autonomicznej](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [natywnej aplikacji autonomicznej](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />[aplikacja sieci web -   ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [usługi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />[usługa -   Native](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Dodawanie danych interakcji warstwy do przebiegu profilowania
 Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Zobacz także
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
