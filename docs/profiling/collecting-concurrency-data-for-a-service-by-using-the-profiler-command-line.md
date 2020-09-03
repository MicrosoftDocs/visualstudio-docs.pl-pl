---
title: Korzystanie z wiersza polecenia profilera w celu uzyskania danych współbieżności dla usługi
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0bd4eb54a5356f7b98846191fb2a9a5f26cc4235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331937"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania pozwala zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację wątków, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy i inne zdarzenia systemowe.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołącz do uruchomionej usługi platformy .NET**|-   [Instrukcje: dołączanie profilera do usługi .NET w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbierz dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Dołącz do uruchomionej usługi C/C++**|-   [Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-windows-services"></a>Profile usług systemu Windows

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET alokacji pamięci i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Dane współbieżności profilu

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profile aplikacji autonomicznych**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Profilowanie aplikacji sieci Web ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie widoków danych współbieżności i raportów
- [Widoki danych rywalizacji o zasoby](../profiling/resource-contention-data-views.md)

- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Dokumentacja
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)
