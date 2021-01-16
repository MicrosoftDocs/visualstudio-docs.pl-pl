---
title: Command-Line profilowania aplikacji sieci Web ASP.NET | Microsoft Docs
description: Dowiedz się, jak zbierać dane dotyczące wydajności aplikacji sieci Web ASP.NET za pomocą narzędzia profilowania z wiersza polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: c4c95890ae4022b854b76d2e4857fc2a27ce97e5
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533696"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilowanie wiersza polecenia aplikacji sieci Web ASP.NET
W tej sekcji opisano procedury i opcje zbierania danych wydajności dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Łatwo Zbieraj podstawowe dane profilowania ASP.NET:** Za pomocą narzędzia **VSPerfASPNETCmd** Zbieraj dane interakcji z próbką, Instrumentacją, pamięcią .NET, rywalizacją lub warstwą bez konieczności konfiguracji i ponownego uruchamiania Internet Information Services (IIS), które są niezbędne do **VSPerfCmd**. **VSPerfASPNETCmd** nie pozwala zbierać dodatkowych danych ani kontrolować zbierania danych. **Uwaga:**  **VSPerfASPNETCmd** jest preferowanym narzędziem do korzystania z autonomicznego profilera do profilowania witryn sieci Web ASP.NET. | -   [Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania, aby zebrać dane statystyczne wydajności. Dane próbkowania są przydatne do analizowania problemów z użyciem procesora CPU oraz do poznania ogólnych cech wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Użyj metody instrumentacji, aby zbierać szczegółowe informacje o chronometrażu. Dane instrumentacji są przydatne do analizowania problemów we/wy i dla szczegółowych analiz scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Zbierz dane pamięci .NET:** Użyj próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET pokazujące rozmiar i liczbę przydzielonych obiektów. Możesz również zbierać dane o okresie istnienia obiektu, pokazujące rozmiar i liczbę obiektów, które są odzyskiwane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Zbierz dane współbieżności:** Użyj metody współbieżności, aby zebrać dane rywalizacji o zasoby. **Uwaga:**  Zbieranie danych dotyczących aktywności wątku i wizualizacji nie jest obsługiwane w przypadku aplikacji sieci Web. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Dodaj dane interakcji warstwy:** Można dodać dane wydajności dotyczące wywołań synchronicznych [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] , które [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacja sieci Web tworzy w [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazie danych firmy Microsoft. | -   [Zbierz dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Samodzielne Profilowanie aplikacji (klienta)**|-   [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Usługi profilu**|-   [Usługi profilu](../profiling/command-line-profiling-of-services.md)|
