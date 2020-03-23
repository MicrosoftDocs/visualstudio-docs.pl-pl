---
title: Zbieranie statystyk aplikacji przy użyciu metody próbkowania profilera
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17217a51c58e1d30b6e6854ee9dbb0c1fb662a3a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779691"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Zbieranie statystyk aplikacji dla usług przy użyciu metody próbkowania profilera
W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla usług systemu Windows przy użyciu metody próbkowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołączanie profilera do usługi .NET**|-   [Jak: Dołącz profiler do usługi .NET, aby zbierać statystyki aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Dołączanie profilera do usługi C/C++**|-   [Jak: Dołącz profiler do usługi macierzystej, aby zbierać statystyki aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-windows-services"></a>Usługi systemu Windows profil

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody oprzyrządowania**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Alokacja pamięci .NET i wyrzucanie elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Rywalizacja o zasoby profilu i działanie wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profil przy użyciu metody pobierania próbek

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profile ASP.NET aplikacji sieci Web**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
