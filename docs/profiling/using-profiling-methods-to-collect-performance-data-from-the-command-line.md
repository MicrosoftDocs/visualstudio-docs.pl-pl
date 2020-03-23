---
title: Aby uzyskać dane dotyczące wydajności, za pomocą metod profilowania wiersza polecenia
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779977"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
Wybór narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia i opcji narzędzi wiersza polecenia Narzędzia profilowania zależy od czynników, takich jak typ aplikacji, które są profilowane, metoda profilowania, który chcesz użyć i czy aplikacja docelowa jest napisana w kodzie macierzystym lub .NET Framework.

 W tym temacie organizuje tematy proceduralne wiersza polecenia zgodnie z wybraną metodą profilowania.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Metoda pobierania próbek służy do zbierania statystyk wydajności
 Metoda próbkowania narzędzi profilowania zbiera dane dotyczące wydajności w określonych odstępach czasu w przebiegu profilowania. Próbkowanie danych może zapewnić wgląd w problemy z wydajnością związane z procesorem CPU i może być dobrym sposobem, aby rozpocząć eksplorowanie wydajności aplikacji.

 Profiler i aplikację można uruchomić w tym samym czasie lub można dołączyć profiler do uruchomionego wystąpienia aplikacji.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchamianie aplikacji**|-   [Aplikacje autonomiczne](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Dołączanie do uruchomionego procesu**|-   [Aplikacje autonomiczne programu .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Natywne aplikacje autonomiczne](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET aplikacje internetowe](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi natywne](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Metoda oprzyrządowania służy do zbierania szczegółowych danych dotyczących chronometrażu
 Metoda instrumentacji narzędzia profilowania zbiera dane dotyczące wydajności z kopii plików binarnych aplikacji, które zawierają sondy oprogramowania do rejestrowania informacji o wydajności. Dane oprzyrządowania są zbierane na początku i na końcu każdej funkcji instrumentacji oraz przy każdym wywołaniu innych funkcji z funkcji instrumentowanego. Metoda instrumentacji jest przydatna do wykrywania problemów z wydajnością problemów we/wy, takich jak użycie dysku.

 Instrumentowany plik binarny można utworzyć za pomocą narzędzia [VInstr.exe.](../profiling/vsinstr.md) Po zainicjowaniu profilera dane są automatycznie zbierane z instrumentowanych plików binarnych po uruchomieniu aplikacji docelowej.

 **Typ aplikacji docelowej**

- [Składniki autonomiczne programu .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Natywne komponenty autonomiczne](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Statycznie skompilowane ASP.NET aplikacje internetowe](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dynamicznie kompilowane ASP.NET aplikacje internetowe](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Usługi .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Usługi natywne](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Metody pamięci .NET używają do zbierania alokacji pamięci i danych okresu istnienia obiektów
 Metoda pamięci Narzędzia profilowania .NET umożliwia zbieranie danych alokacji pamięci programu .NET Framework i informacji o okresie istnienia obiektów w programie .NET Framework.

 Aplikację docelową można uruchomić przy użyciu profilera; można dołączyć profiler do uruchomionego wystąpienia aplikacji; i można utworzyć instrumentowane wersje aplikacji, aby zbierać szczegółowe informacje o chronometrażu wraz z danymi pamięci .NET Framework.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchamianie aplikacji**|-   [Autonomiczne aplikacje .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Dołączanie do uruchomionego procesu**|-   [Aplikacje autonomiczne programu .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET aplikacje internetowe](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Usługi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Moduły przyrządów**|-   [Składniki autonomiczne programu .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Statycznie skompilowane ASP.NET aplikacje internetowe](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dynamicznie kompilowane ASP.NET aplikacje internetowe](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Usługi .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Metoda współbieżności służy do zbierania danych rywalizacji o zasoby i aktywności wątków
 Metoda współbieżności narzędzi profilowania umożliwia zbieranie rywalizacji o zasoby oraz danych aktywności wątków i procesów z aplikacji wielowątkowych.

 Aplikację można uruchomić za pomocą profilera lub można dołączyć profiler do uruchomionego wystąpienia aplikacji.

|Zadanie|Typ aplikacji docelowej|
|----------|-----------------------------|
|**Uruchamianie aplikacji**|-   [Autonomiczna aplikacja .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Autonomiczna aplikacja natywna](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Dołączanie do uruchomionego procesu**|-   [Aplikacja autonomiczna programu .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Natywna aplikacja autonomiczna](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET aplikacja internetowa](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa natywna](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Dodawanie danych interakcji warstwy do uruchomienia profilowania
 Dodawanie danych interakcji warstwy do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi do profilowania wiersza polecenia. Zobacz [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Zobacz też
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
