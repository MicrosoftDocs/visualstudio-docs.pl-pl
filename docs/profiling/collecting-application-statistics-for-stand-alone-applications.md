---
title: Zbieranie statystyk aplikacji autonomicznych przy użyciu wiersza polecenia profilera
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de399bf493e328e583bdd2765822ca3a66144698
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779639"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla aplikacji klienckiej (autonomicznej) za pomocą metody próbkowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Uruchamianie aplikacji przy użyciu profilowania**|-   [: uruchamianie aplikacji autonomicznej i zbieranie statystyk aplikacji](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Dołącz profiler do uruchomionej aplikacji .NET Framework**|-   [instrukcje: dołączanie profilera do aplikacji .NET Framework i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Dołącz profiler do uruchomionej aplikacji C/C++**|-   [instrukcje: dołączanie profilera do natywnej aplikacji i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Dodawanie danych interakcji warstwy**|-   [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-stand-alone-applications"></a>Profile aplikacji autonomicznych

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Instrumentacja aplikacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Zbierz dane alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieraj dane .NET Framework pamięci](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Zbieranie danych rywalizacji o zasoby i wykonywanie wątków**|-   [zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody próbkowania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profilowanie aplikacji sieci Web ASP.NET**|-   [zbierać dane statystyczne aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Usługi profilu**|-   [zbierać dane statystyczne aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Opisuje sposób zbierania statystyk wydajności z usług systemu Windows przy użyciu metody próbkowania.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
