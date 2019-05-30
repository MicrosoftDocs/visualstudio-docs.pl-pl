---
title: Zbieranie statystyk aplikacji przy użyciu metody próbkowania profilera
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9b2de87e77abc701f14211cb49e82220c4c935d
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263005"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Zbieranie statystyk aplikacji dla usług przy użyciu metody próbkowania profilera
W tej sekcji opisano procedury składowane i opcji zbierania statystyk wydajności dla usług Windows przy użyciu metody próbkowania w wierszu polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołącz profiler do usługi .NET**|-   [Jak: Dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Dodawanie danych interakcji między warstwami**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Dołączanie profilera do usługi języka C/C++**|-   [Jak: Dołączanie profilera do usługi natywnej i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-windows-services"></a>Profil usługi Windows

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profilowanie pamięci .NET alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profil działanie zasobu rywalizacji o zasoby i wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profil przy użyciu metody próbkowania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil aplikacji autonomicznej (klienta)**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profil aplikacji sieci Web ASP.NET**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie próbkowanie danych widoków i raportów
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
