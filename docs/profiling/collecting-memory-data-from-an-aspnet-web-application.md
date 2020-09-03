---
title: Pobieranie danych pamięci aplikacji sieci Web ASP.NET przy użyciu wiersza polecenia profilera
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 646445613aa9d03d2134094ebf0f694cef2f91ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331698"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Zbieranie danych pamięci z aplikacji sieci Web ASP.NET przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcje zbierania danych alokacji pamięci i okresu istnienia obiektów dla aplikacji sieci Web ASP.NET za pomocą narzędzia wiersza polecenia **VSPerfCmd** .

> [!NOTE]
> Narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzia profilowania, w tym Wstrzymywanie i wznawianie profilowania oraz gromadzenie dodatkowych danych z liczników wydajności procesora i systemu Windows. Możesz również użyć narzędzia wiersza polecenia  **VSPerfASPNETCmd** , gdy ta funkcja nie jest potrzebna. W porównaniu z narzędziem wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych ani ponownie uruchamiać komputera. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołącz profiler do uruchomionej aplikacji ASP.NET**|-   [Instrukcje: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych pamięci](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentowo skompilowane pliki binarne w sposób statyczny**|-   [Instrukcje: Instrumentacja statycznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrument dynamicznie skompilowane pliki binarne**|-   [Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Profilowanie aplikacji sieci Web ASP.NET

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profilowanie zasobów i aktywność wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Profilowanie danych pamięci .NET Framework

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Usługi profilu**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analizowanie widoków i raportów danych pamięci .NET
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Tematy pomocy
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)
