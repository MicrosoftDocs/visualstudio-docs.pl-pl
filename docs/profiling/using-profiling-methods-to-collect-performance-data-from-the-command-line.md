---
title: Korzystanie z metod profilowania do zbierania danych wydajności z wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a6350c16da79bc102f85a382ce57aa6924bb2c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831446"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
Wybór [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opcje i narzędzi wiersza poleceń Profiling Tools jest zależna od czynników, takich jak typ aplikacji, profilowany, metody profilowania, którego chcesz użyć, i czy aplikacji docelowej jest zapisywany w natywnym, czy [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]kodu.

 W tym temacie organizuje wiersza polecenia tematów proceduralnych zgodnie z wybranej metody profilowania.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Zbieranie statystyk wydajności przy użyciu metody pobierania próbek
 Metoda pobierania próbek Profiling Tools zbiera dane dotyczące wydajności w określonych odstępach czasu do uruchomienia profilowania. Próbkowanie danych może zapewnić wgląd w problemy z wydajnością Procesora CPU i może być dobrym sposobem na rozpoczęcie eksplorowania wydajność aplikacji.

 Można uruchomić profiler jak i aplikacji, w tym samym czasie, lub należy dołączyć profiler do uruchomionego wystąpienia aplikacji.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchom aplikację**|-   [Aplikacje autonomiczne](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Natywne aplikacje autonomiczne](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [Aplikacje sieci web platformy ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi platformy .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Natywnych usług](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji
 Metoda Instrumentacja Profiling Tools zbiera dane wydajności z kopiuje pliki binarne aplikacji, które zawierają oprogramowanie sondy do informacji o wydajności rekordów. Na początku i końcu każdego instrumentowanych funkcji i w każdym wywołaniu do innych funkcji z instrumentowanych funkcji, zbierane są dane instrumentacji. Metoda Instrumentacja jest przydatna do wykrywania problemów z wydajnością za pomocą operacji We/Wy problemy, takie jak użycie dysku.

 Utwórz instrumentowanego pliku binarnego z [VInstr.exe](../profiling/vsinstr.md) narzędzia. Po użytkownik zainicjowania programu profilującego, dane są automatycznie zbierane z instrumentowanych danych binarnych, po uruchomieniu aplikacji docelowej.

 **Typ aplikacji docelowej**

- [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Składnikami macierzystymi autonomiczny](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Statycznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dynamicznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Usługi platformy .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Natywnych usług](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Umożliwia zbieranie danych pamięci alokacji i obiekt okresu istnienia metod pamięci .NET
 Metoda pamięci Profiling Tools .NET umożliwia zbieranie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dane alokacji pamięci oraz informacje o okresie istnienia obiektów w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

 Można uruchomić aplikacji docelowej za pomocą profilera; należy dołączyć profiler do uruchomionego wystąpienia aplikacji; można także tworzyć instrumentowanej wersji aplikacji, zbierać szczegółowe informacje o czasach wraz z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dane pamięci.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchom aplikację**|-   [Autonomicznej aplikacji .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [Aplikacje sieci web platformy ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Usługi platformy .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Moduły Instrumentacji**|-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Statycznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dynamicznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Usługi platformy .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Zbierania danych zasobów rywalizacji o zasoby i wątku działania przy użyciu metody współbieżności
 Metody współbieżności Profiling Tools umożliwia zbieranie rywalizacji o zasoby i dane o aktywności procesu i wątku z poziomu aplikacji wielowątkowych.

 Możesz uruchomić aplikację za pomocą profilera, lub należy dołączyć profiler do uruchomionego wystąpienia aplikacji.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Natywnej aplikacji autonomicznej](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Autonomicznej aplikacji natywnej](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [Aplikacja sieci web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Macierzystej usługi](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Dodawanie danych interakcji do profilowania uruchomi
 Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Zobacz także
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)