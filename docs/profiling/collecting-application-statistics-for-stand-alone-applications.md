---
title: Zbieranie statystyk aplikacji autonomicznych za pomocą wiersza polecenia profilera
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de399bf493e328e583bdd2765822ca3a66144698
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779639"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla aplikacji klienta (autonomicznego) przy użyciu metody próbkowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Uruchamianie aplikacji przy użyciu profilowania**|-   [Jak: Uruchamianie aplikacji autonomicznej i zbieranie statystyk aplikacji](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Dołączanie profilera do uruchomionej aplikacji .NET Framework**|-   [Jak: Dołącz profiler do aplikacji .NET Framework i zbieraj statystyki aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Dołączanie profilera do uruchomionej aplikacji C/C++**|-   [Jak: Dołącz profiler do aplikacji natywnej i zbieraj statystyki aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-stand-alone-applications"></a>Aplikacje autonomiczne profilu

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Instrument aplikacji**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Zbieranie danych alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci programu .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Zbieranie danych rywalizacji o zasoby i wykonywania wątków**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profil przy użyciu metody pobierania próbek

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profil ASP.NET aplikacji internetowych**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Usługi profilowania**|-   [Zbieraj statystyki aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). W tym artykule opisano sposób zbierania statystyk wydajności z usług systemu Windows przy użyciu metody próbkowania.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
