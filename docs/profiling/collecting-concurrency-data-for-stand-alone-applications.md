---
title: Zbieranie danych współbieżności dla aplikacji autonomicznych przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c02802fa9a32c3ae973108ed2622dc0aa9e0f262
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660635"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools umożliwia zbieranie danych kontencji zasobów i dane o aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszary nachodzące We/Wy i inne zdarzenia systemowe.

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Rozpocznij danych współbieżności aplikacji i profilu .NET Framework**|-   [Jak: Uruchamianie aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Rozpocznij danych współbieżności aplikacji i profilu C/C++**|-   [Jak: Uruchamianie aplikacji natywnej do zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Dołączanie profilera do uruchomionej aplikacji .NET Framework**|-   [Jak: Dołączanie profilera do aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Dołączanie profilera do uruchomionej aplikacji C/C++**|-   [Jak: Dołącz profiler do aplikacji natywnej i zbieranie danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-stand-alone-applications"></a>Profil aplikacji autonomicznych

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profil przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilowanie pamięci .NET alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Dodawanie danych interakcji między warstwami**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Problemy ze współbieżnością profilu

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profil aplikacji ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Usługi profilowania**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie współbieżność danych widoków i raportów
- [Widok danych kontencji zasobów](../profiling/resource-contention-data-views.md)

- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Tematy pomocy
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)