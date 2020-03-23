---
title: Użyj wiersza polecenia profilera, aby uzyskać dane współbieżności dla usługi
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b7b60ad871f40e06e2a8fbf6782773ce6596f31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779678"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania umożliwia zbieranie danych rywalizacji o zasoby i danych aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacja wątków, migracja wątków, opóźnienia synchronizacji, obszary nakładających się we/wy i inne zdarzenia systemowe.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołączanie do uruchomionej usługi .NET**|-   [Jak: Dołączanie profilera do usługi .NET w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Dołącz do uruchomionej usługi C/C++**|-   [Jak: Dołącz profiler do usługi macierzystej, aby zebrać dane współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-windows-services"></a>Usługi systemu Windows profil

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profil przy użyciu metody oprzyrządowania**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET alokacji pamięci i wyrzucaniu elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Dane współbieżności profilu

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Profile ASP.NET aplikacji sieci Web**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie widoków i raportów danych współbieżności
- [Widoki danych rywalizacji o zasoby](../profiling/resource-contention-data-views.md)

- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Dokumentacja
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)
