---
title: Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ca716b092d8d184313da65bffa6f66839c7254e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615380"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools umożliwia zbieranie danych kontencji zasobów i dane o aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszary nachodzące We/Wy i inne zdarzenia systemowe.

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

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