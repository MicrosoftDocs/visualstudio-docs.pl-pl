---
title: Pobierz ASP.NET danych pamięci aplikacji sieci web przy użyciu wiersza polecenia profilera
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9e8d9fde00a2390793ae8efe05b684e73caca321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773062"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Zbieranie danych pamięci z aplikacji sieci web ASP.NET przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcje zbierania danych alokacji pamięci i okresu istnienia obiektu dla ASP.NET aplikacji sieci Web przy użyciu narzędzia wiersza polecenia **VSPerfCmd.**

> [!NOTE]
> Narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzi profilowania, w tym wstrzymywania i wznawiania profilowania oraz zbierania dodatkowych danych z liczników wydajności procesora i systemu Windows. Narzędzia wiersza polecenia **VSPerfASPNETCMD** można również użyć, gdy nie jest to potrzebne. W porównaniu z narzędziem wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych, a ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [Szybkie profilowanie witryny sieci Web za pomocą programu VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołączanie profilera do uruchomionej aplikacji ASP.NET**|-   [Jak: Dołącz profiler do ASP.NET aplikacji sieci web do zbierania danych pamięci](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrument statycznie skompilowane pliki binarne**|-   [Jak: Instrumentować statycznie skompilowaną ASP.NET aplikacji i zbierać dane pamięci](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumentowanie dynamicznie skompilowanych plików binarnych**|-   [Jak: Instrumentowanie dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET aplikacji internetowych

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profil przy użyciu metody oprzyrządowania**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Rywalizacja o zasoby profilu i działanie wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Dane pamięci programu .NET Framework profil

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Zbieranie danych pamięci programu .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Usługi profilowania**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analizowanie widoków i raportów danych pamięci .NET
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Dokumentacja
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)
