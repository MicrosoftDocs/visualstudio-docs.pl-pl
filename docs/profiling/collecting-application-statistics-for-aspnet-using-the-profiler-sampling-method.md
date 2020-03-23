---
title: Zbieranie statystyk dla aplikacji internetowych ASP.NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: a2cae807a8d833cf2653ea23616eeb819673229e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773247"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Zbieranie statystyk dla ASP.NET aplikacji internetowych

W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla ASP.NET aplikacji sieci Web przy użyciu narzędzia wiersza polecenia **VSPerfASPNETCmd** i **VSPerfCmd** oraz metody profilowania próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Mimo że narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzi profilowania, w tym wstrzymywania i wznawiania profilowania oraz zbierania dodatkowych danych z liczników wydajności procesora i systemu Windows, należy użyć narzędzia wiersza polecenia **VSPerfASPNETCmd,** gdy nie jest to potrzebne. Narzędzie wiersza polecenia **VSPerfASPNETCmd** jest preferowaną metodą, gdy profilowanie witryn sieci Web ASP.NET przy użyciu autonomicznego profilera. W porównaniu z narzędziem wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych, a ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [Szybkie profilowanie witryny sieci Web za pomocą programu VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołączanie profilera do aplikacji ASP.NET**|-   [Jak: Dołącz profiler do ASP.NET aplikacji internetowej do zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET aplikacji internetowych

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody oprzyrządowania**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Alokacja pamięci profilu i wyrzucanie elementów bezużytecznych**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Rywalizacja o zasoby profilu i działanie wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Metoda przykładowa

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Usługi profilowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
