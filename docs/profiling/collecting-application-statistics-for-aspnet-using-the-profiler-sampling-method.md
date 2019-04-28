---
title: Zbieranie statystyk dla platformy ASP.NET, aplikacje sieci web | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 6ff7f1596d9b3336cb7fdbc02de7d1bc10172f94
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405753"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Zbieranie statystyk aplikacji sieci web ASP.NET

W tej sekcji opisano procedury składowane i zbieranie statystyk wydajności dla aplikacji sieci Web platformy ASP.NET przy użyciu opcji **VSPerfASPNETCmd** i **VSPerfCmd** narzędzie wiersza polecenia i Metoda profilowania próbkowanie.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Mimo że **VSPerfCmd** narzędzie zapewnia pełny dostęp do funkcje Profiling Tools, w tym wstrzymywanie i wznawianie profilowania i zbieranie dodatkowych danych z procesora i liczniki wydajności Windows, należy użyć **VSPerfASPNETCmd** narzędzia wiersza polecenia, jeśli nie potrzebujesz tej funkcji. **VSPerfASPNETCmd** narzędzia wiersza polecenia jest to preferowana metoda gdy jesteś profilowania witryn sieci Web platformy ASP.NET przy użyciu autonomicznego profilera. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, żadne zmienne środowiskowe, które należy skonfigurować i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [profilowania szybkie witryn sieci web za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Dołącz profiler do aplikacji ASP.NET**|-   [Jak: Dołącz profiler do aplikacji sieci web ASP.NET w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Aplikacje sieci web ASP.NET profilu

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profil kolekcji alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profil działanie zasobu rywalizacji o zasoby i wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Przykładowa metoda

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil aplikacji autonomicznej (klienta)**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Usługi profilowania**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie próbkowanie danych widoków i raportów
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)