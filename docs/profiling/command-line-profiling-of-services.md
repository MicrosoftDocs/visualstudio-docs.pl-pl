---
title: Profilowanie wiersza polecenia usług | Dokumenty firmy Microsoft
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
ms.openlocfilehash: b20835eaf8b81bd64bd90aa75d2efb32975a7c53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772834"
---
# <a name="command-line-profiling-of-services"></a>Profilowanie wiersza polecenia usług
W tej sekcji opisano procedury i opcje zbierania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] danych o wydajności usług systemu Windows przy użyciu narzędzi profilowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Powiązana zawartość |
| - | - |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania do zbierania statystyk wydajności. Próbkowanie danych jest przydatne do analizowania problemów z wykorzystaniem procesora CPU i do zrozumienia ogólnych cech wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Zbieranie szczegółowych danych dotyczących chronometrażu:** Metoda instrumentacji służy do zbierania szczegółowych informacji o czasie. Dane instrumentacji jest przydatne do analizy problemów we/wy i do szczegółowej analizy scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Zbieranie danych pamięci platformy .NET:** Próbkowanie lub instrumentacji służy do zbierania danych alokacji pamięci .NET, które pokazują rozmiar i liczbę przydzielonych obiektów. Można również zbierać dane okresu istnienia obiektu, który pokazuje rozmiar i liczbę obiektów, które są odzyskane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Zbieranie danych współbieżności:** Użyj metody współbieżności do zbierania danych rywalizacji o zasoby i danych aktywności wątku, który pokazuje wykorzystanie procesora CPU, rywalizacja wątków, migracja wątków, opóźnienia synchronizacji, obszary nakładających się we/wy i inne zdarzenia systemowe. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Dodawanie danych interakcji warstwy:** Można dodać dane dotyczące wydajności synchronii ADO.NET wywołania, które [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] usługa wykonana do bazy danych firmy Microsoft. | -   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje autonomiczne profilu**|-   [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Aplikacje ASP.NET profilowe**|-   [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
