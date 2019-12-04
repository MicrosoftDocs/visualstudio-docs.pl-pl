---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Microsoft Docs
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
ms.openlocfilehash: c5fd11f12f368c266dd19577925db7cec1867e39
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779561"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
W tej sekcji opisano procedury i opcje zbierania danych wydajności dla autonomicznych aplikacji (klienta) za pomocą narzędzia profilowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z wiersza polecenia.

## <a name="common-tasks"></a>Wspólne zadania

| Zadanie | Zawartość pokrewna |
| - | - |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania, aby zebrać dane statystyczne wydajności. Dane próbkowania są przydatne do analizowania problemów z użyciem procesora CPU oraz do poznania ogólnych cech wydajności aplikacji. | -   [zbierać dane statystyczne aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Zbieranie szczegółowych danych o chronometrażu:** Użyj metody instrumentacji, aby zbierać szczegółowe informacje o chronometrażu. Dane instrumentacji są przydatne do analizowania problemów we/wy i szczegółowych analiz scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Zbierz dane pamięci .NET:** Użyj próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET pokazujące rozmiar i liczbę przydzielonych obiektów. Możesz również zbierać dane o okresie istnienia obiektu, pokazujące rozmiar i liczbę obiektów, które są odzyskiwane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieraj dane .NET Framework pamięci](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Zbierz dane współbieżności:** Użyj metody współbieżności, aby zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację o wątki, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy oraz inne zdarzenia systemowe. | -   [zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Dodaj dane interakcji warstwy:** Można dodać dane dotyczące wydajności dotyczące synchronicznych wywołań ADO.NET, które aplikacja wykonał w bazie danych Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. | -   [Zbieraj dane interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Wypróbuj:** Procedury krok po kroku umożliwiają profilowanie przykładowej aplikacji klienckiej przy użyciu metody próbkowania lub Instrumentacji. | [przewodnik -   : Profilowanie wiersza polecenia przy użyciu próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />[przewodnik -   : Profilowanie wiersza polecenia przy użyciu instrumentacji](command-line-profiling-of-stand-alone-applications.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Profilowanie aplikacji ASP.NET**|-   [aplikacji sieci web ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Usługi profilu**|[usługi profilu](../profiling/command-line-profiling-of-services.md) -   |
