---
title: 'VSPerfCmd: Pobierz dane chronometrażu dla ASP.NET aplikacji internetowej za pomocą instrumentacji'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: d764ef32cdcb061992817d433dabb6ae61b64fd9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779652"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Zbieranie szczegółowych danych chronometrażu dla aplikacji sieci web ASP.NET przy użyciu metody instrumentacji profilera z wiersza polecenia
W tej sekcji opisano procedury i opcje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zbierania szczegółowych danych o wydajności aplikacji sieci Web przy użyciu narzędzia wiersza polecenia **VSPerfCmd** i metody instrumentacji.

> [!NOTE]
> Narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzi profilowania, w tym wstrzymywania i wznawiania profilowania oraz zbierania dodatkowych danych z liczników wydajności procesora i systemu Windows. Narzędzia wiersza polecenia **VSPerfASPNETCMD** można również użyć, gdy nie jest to potrzebne. W porównaniu do narzędzia wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych, a ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [Szybkie profilowanie witryny sieci Web za pomocą programu VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profile skompilowane statycznie pliki binarne**|-   [Jak: Przyrządzowanie statycznie skompilowanego ASP.NET aplikacji i zbieranie szczegółowych danych dotyczących chronometrażu](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profil dynamicznie skompilowane pliki binarne**|-   [Jak: Instrumentowanie dynamicznie skompilowanego ASP.NET aplikacji i zbieranie szczegółowych danych dotyczących chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET aplikacji internetowych

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Alokacja pamięci profilu i wyrzucanie elementów bezużytecznych**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Rywalizacja o zasoby profilu i działanie wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profil przy użyciu metody oprzyrządowania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Usługi profilowania**|-   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analizowanie widoków i raportów danych o instrumentacji
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
