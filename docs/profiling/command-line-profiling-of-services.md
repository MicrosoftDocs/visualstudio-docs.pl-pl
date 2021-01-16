---
title: Command-Line profilowania usług | Microsoft Docs
description: Dowiedz się, jak zbierać dane wydajności dla usług systemu Windows przy użyciu narzędzia profilowania z wiersza polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f05ca0a11060e2a9009b38b0caf7ce9172773f36
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533657"
---
# <a name="command-line-profiling-of-services"></a>Profilowanie wiersza polecenia usług
W tej sekcji opisano procedury i opcje zbierania danych wydajności dla usług systemu Windows przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania, aby zebrać dane statystyczne wydajności. Dane próbkowania są przydatne do analizowania problemów z użyciem procesora CPU oraz do poznania ogólnych cech wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Użyj metody instrumentacji, aby zbierać szczegółowe informacje o chronometrażu. Dane instrumentacji są przydatne do analizowania problemów we/wy i dla szczegółowych analiz scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Zbierz dane pamięci .NET:** Użyj próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET pokazujące rozmiar i liczbę przydzielonych obiektów. Możesz również zbierać dane o okresie istnienia obiektu, pokazujące rozmiar i liczbę obiektów, które są odzyskiwane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Zbierz dane współbieżności:** Użyj metody współbieżności, aby zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację o wątki, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy i inne zdarzenia systemowe. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Dodaj dane interakcji warstwy:** Można dodać dane wydajności dotyczące synchronicznych wywołań ADO.NET, które usługa przetworzy do [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych firmy Microsoft. | -   [Zbierz dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profilowanie aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
