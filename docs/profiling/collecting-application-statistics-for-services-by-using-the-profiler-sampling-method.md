---
title: Zbieranie statystyk dla usług systemu Windows — Metoda próbkowania profilera
description: Przejrzyj procedury i opcje w celu zbierania statystyk wydajności dla usług systemu Windows przy użyciu metody próbkowania profilowania z wiersza polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ffbc26cb10d80aedb36d33826f9eab675957c8ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868403"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Zbieranie statystyk aplikacji dla usług przy użyciu metody próbkowania profilera
W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla usług systemu Windows przy użyciu metody próbkowania w wierszu polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołączanie profilera do usługi .NET**|-   [Instrukcje: dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbierz dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Dołącz profiler do usługi C/C++**|-   [Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-windows-services"></a>Profile usług systemu Windows

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profilowanie alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profilowanie zasobów i aktywność wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody próbkowania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilowanie aplikacji sieci Web ASP.NET**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
