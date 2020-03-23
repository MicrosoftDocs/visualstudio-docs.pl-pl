---
title: Wiersz polecenia profilera w celu uzyskania autonomicznych danych współbieżności aplikacji
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 6180d2f2e3ed655f378900d3d41691daa98a0354
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773260"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania umożliwia zbieranie danych rywalizacji o zasoby i danych aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacja wątków, migracja wątków, opóźnienia synchronizacji, obszary nakładających się we/wy i inne zdarzenia systemowe.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Uruchamianie danych współbieżności aplikacji i profilu .NET Framework**|-   [Jak: Uruchamianie aplikacji .NET Framework w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Uruchamianie danych dotyczących współbieżności aplikacji C/C++ i profilu**|-   [Jak: Uruchamianie aplikacji natywnej w celu zbierania danych współbieżności](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Dołączanie profilera do uruchomionej aplikacji .NET Framework**|-   [Jak: Dołącz profiler do aplikacji .NET Framework do zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Dołączanie profilera do uruchomionej aplikacji C/C++**|-   [Jak: Dołącz profiler do aplikacji natywnej i zbieraj dane współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-stand-alone-applications"></a>Aplikacje autonomiczne profilu

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profil przy użyciu metody oprzyrządowania**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Alokacja pamięci .NET i wyrzucanie elementów bezużytecznych**|-   [Zbieranie danych pamięci programu .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Problemy ze współbieżnością profilu

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Aplikacje ASP.NET profilowe**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Usługi profilowania**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie widoków i raportów danych współbieżności
- [Widoki danych rywalizacji o zasoby](../profiling/resource-contention-data-views.md)

- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Dokumentacja
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)
