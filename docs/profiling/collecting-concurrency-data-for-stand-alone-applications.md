---
title: Wiersz polecenia profilera do pobrania danych współbieżności aplikacji autonomicznych
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15e8be092a8e1e065f2aa1a80be7447a370974b0
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331867"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania pozwala zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację wątków, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy i inne zdarzenia systemowe.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Uruchamianie .NET Framework aplikacji i danych współbieżności profilu**|-   [Instrukcje: uruchamianie aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Uruchamianie aplikacji C/C++ i danych współbieżności profilu**|-   [Instrukcje: uruchamianie aplikacji natywnej w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Dołącz profiler do uruchomionej aplikacji .NET Framework**|-   [Instrukcje: dołączanie profilera do aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Dołącz profiler do uruchomionej aplikacji C/C++**|-   [Instrukcje: dołączanie profilera do aplikacji natywnej i zbieranie danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-stand-alone-applications"></a>Profile aplikacji autonomicznych

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilowanie alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbierz dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Problemy współbieżności profilu

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profilowanie aplikacji ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Usługi profilu**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie widoków danych współbieżności i raportów
- [Widoki danych rywalizacji o zasoby](../profiling/resource-contention-data-views.md)

- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Tematy pomocy
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)
