---
title: Command-Line profilowania aplikacji Stand-Alone | Microsoft Docs
description: Dowiedz się, jak zbierać dane wydajności dla aplikacji klienckich (autonomicznych) za pomocą narzędzia profilowania z wiersza polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 876c2a72f0929cffa3613026fa56a17d82786854
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533644"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
W tej sekcji opisano procedury i opcje zbierania danych wydajności dla autonomicznych aplikacji (klienta) przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania z wiersza polecenia.

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Zawartość pokrewna |
| - | - |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania, aby zebrać dane statystyczne wydajności. Dane próbkowania są przydatne do analizowania problemów z użyciem procesora CPU oraz do poznania ogólnych cech wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Użyj metody instrumentacji, aby zbierać szczegółowe informacje o chronometrażu. Dane instrumentacji są przydatne do analizowania problemów we/wy i szczegółowych analiz scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Zbierz dane pamięci .NET:** Użyj próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET pokazujące rozmiar i liczbę przydzielonych obiektów. Możesz również zbierać dane o okresie istnienia obiektu, pokazujące rozmiar i liczbę obiektów, które są odzyskiwane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Zbierz dane współbieżności:** Użyj metody współbieżności, aby zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację o wątki, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy oraz inne zdarzenia systemowe. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Dodaj dane interakcji warstwy:** Można dodać dane dotyczące wydajności dotyczące synchronicznych wywołań ADO.NET, które aplikacja wykonał w [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazie danych firmy Microsoft. Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. | -   [Zbierz dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Usługi profilu**|-   [Usługi profilu](../profiling/command-line-profiling-of-services.md)|
