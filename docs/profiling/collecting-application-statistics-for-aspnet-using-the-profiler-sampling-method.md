---
title: Zbieranie danych statystycznych dotyczących usługi ASP.NET Web Apps
description: Przejrzyj procedury i opcje, aby zebrać statystyki wydajności dla ASP.NET Web Apps przy użyciu narzędzia VSPerfASPNETCmd i VSPerfCmd oraz metody profilowania próbkowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 190e67b3471162f29273d56f3e1cbeee6d09e557
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952827"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Zbieranie danych statystycznych dotyczących usługi ASP.NET Web Apps

W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla aplikacji sieci Web ASP.NET za pomocą narzędzia wiersza polecenia **VSPerfASPNETCmd** i **VSPerfCmd** oraz metody profilowania próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Mimo że narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzia profilowania, w tym Wstrzymywanie i wznawianie profilowania oraz gromadzenie dodatkowych danych z liczników wydajności procesora i systemu Windows, należy użyć narzędzia wiersza polecenia  **VSPerfASPNETCmd** , jeśli nie są potrzebne. Narzędzie wiersza polecenia **VSPerfASPNETCmd** jest preferowaną metodą profilowania ASP.NET witryn sieci Web przy użyciu autonomicznego profilera. W porównaniu z narzędziem wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych ani ponownie uruchamiać komputera. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołącz profiler do aplikacji ASP.NET**|-   [Instrukcje: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Profilowanie aplikacji sieci Web ASP.NET

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie przy użyciu metody instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Alokacja pamięci profilu i wyrzucanie elementów bezużytecznych**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profilowanie zasobów i aktywność wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Przykładowa Metoda

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Usługi profilu**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
