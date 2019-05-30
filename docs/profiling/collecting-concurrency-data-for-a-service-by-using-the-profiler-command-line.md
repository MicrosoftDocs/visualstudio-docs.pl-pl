---
title: Użyj wiersza polecenia profilera, aby uzyskać danych współbieżności dla usługi
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fba5c02846fa13cb0929a63e4007acb7db58535
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262977"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools umożliwia zbieranie danych kontencji zasobów i dane o aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszary nachodzące We/Wy i inne zdarzenia systemowe.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołącz do uruchomionej usługi .NET**|-   [Jak: Dołączanie profilera do usługi .NET w celu zbierania danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Dodawanie danych interakcji między warstwami**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Dołącz do uruchomionej usługi w języka C/C++**|-   [Jak: Dołączanie profilera do usługi natywnej i zbieranie danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-windows-services"></a>Profil usługi Windows

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET pamięć alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Profil danych współbieżności

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil aplikacji autonomicznych**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Profil aplikacji sieci Web ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie współbieżność danych widoków i raportów
- [Widok danych kontencji zasobów](../profiling/resource-contention-data-views.md)

- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Tematy pomocy
- [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)