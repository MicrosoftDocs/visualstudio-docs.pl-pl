---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcd48f421dcae74e82b0d9249a958f2a834f0a45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831684"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
W tej sekcji opisano procedury składowane i opcji zbierania danych wydajności dla aplikacji autonomicznej (klienta) przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania z wiersza polecenia.

## <a name="common-tasks"></a>Wspólne zadania

| Zadanie | Zawartość pokrewna |
| - | - |
| **Zbieranie statystyk aplikacji:** W celu zbierania statystyk wydajności, należy użyć metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i zrozumienia charakterystyki ogólnej wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Aby zbierać szczegółowe informacje o czasie, należy użyć metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów z operacji We/Wy i szczegółową analizę scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Zbieranie danych pamięci .NET:** Aby zbierać dane alokacji pamięci .NET, który pokazuje, rozmiar i liczba przydzielonych obiektów, należy użyć próbkowania i instrumentacji. Może również zbierać danych o okresie istnienia obiektu, który pokazuje, rozmiaru i liczby obiektów, które są odzyskiwane w wszystkich generacjach wyrzucania. | -   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Zbieranie danych współbieżności:** Aby zbierać dane kontencji zasobów i dane o aktywności wątku, który pokazuje CPU wykorzystania, rywalizacji wątków, migracji wątków, opóźnień synchronizacji, obszarów nakładania się wejść / i inne zdarzenia systemowe, należy użyć metody współbieżności. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Dodawanie danych interakcji między warstwami:** Możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania aplikacji do firmy Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych. Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. | -   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Wypróbuj to:** Użyj procedury krok po kroku do profilowania Przykładowa aplikacja kliencka, za pomocą metody próbkowania i instrumentacji. | -   [Wskazówki: Wiersza polecenia, profilowania przy użyciu metody próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Wskazówki: Wiersza polecenia, profilowania przy użyciu metody Instrumentacji](/visualstudio/profiling/command-line-profiling-of-stand-alone-applications) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profil aplikacji ASP.NET**|-   [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|