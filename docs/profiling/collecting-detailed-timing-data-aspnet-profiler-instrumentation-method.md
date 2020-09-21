---
title: Zbieranie danych o chronometrażu dla ASP.NET przy użyciu instrumentacji
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: a73d81eaaef45a9ae97e733a8ae94805106a9ef8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809638"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Zbieranie szczegółowych danych o chronometrażu dla aplikacji sieci Web ASP.NET przy użyciu metody instrumentacji profilera z wiersza polecenia
W tej sekcji opisano procedury i opcje dotyczące zbierania szczegółowych danych dotyczących wydajności [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu narzędzia wiersza polecenia **VSPerfCmd** oraz metody instrumentacji.

> [!NOTE]
> Narzędzie **VSPerfCmd** zapewnia pełny dostęp do funkcji narzędzia profilowania, w tym Wstrzymywanie i wznawianie profilowania oraz gromadzenie dodatkowych danych z liczników wydajności procesora i systemu Windows. Możesz również użyć narzędzia wiersza polecenia  **VSPerfASPNETCmd** , gdy ta funkcja nie jest potrzebna. W porównaniu do narzędzia wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) nie trzeba ustawiać żadnych zmiennych środowiskowych ani ponownie uruchamiać komputera. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie skompilowanych statycznie plików binarnych**|-   [Instrukcje: Instrumentacja statycznie skompilowanej aplikacji ASP.NET i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Dynamicznie skompilowane pliki binarne profilu**|-   [Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-aspnet-web-applications"></a>Profilowanie aplikacji sieci Web ASP.NET

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Alokacja pamięci profilu i wyrzucanie elementów bezużytecznych**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profilowanie zasobów i aktywność wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profilowanie przy użyciu metody instrumentacji

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Usługi profilu**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analizowanie widoków i raportów danych Instrumentacji
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
