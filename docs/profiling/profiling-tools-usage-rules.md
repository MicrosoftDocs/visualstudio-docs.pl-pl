---
title: Reguły użycia narzędzia profilowania | Microsoft Docs
description: Dowiedz się, w jaki sposób reguły wydajności w kategorii użycie narzędzia profilowania zapewniają wskazówki dotyczące najbardziej efektywnego zbierania danych przy użyciu profilera.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2514d6893c205a1c48c76983c859528be6ad938b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861624"
---
# <a name="profiling-tools-usage-rules"></a>Reguły korzystania z narzędzi profilowania
Reguły wydajności w kategorii użycie narzędzia profilowania zawierają wskazówki dotyczące najbardziej efektywnego zbierania danych przy użyciu programu Profiler.

| Reguła | Opis |
| - | - |
| [DA0002: Brak biblioteki VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Profilowanie wiersza polecenia może zawierać niekompletne dane dla .NET Framework plików binarnych. Może to być spowodowane nieustawieniem poprawnych zmiennych środowiskowych. |
| [DA0003: Wiele przykładów jądra](../profiling/da0003-many-kernel-samples.md) | Zarejestrowano wiele przykładów profilowania, które wystąpiły poza wykonywaniem docelowej wartości binarnej. Aby zebrać dokładniejsze dane, rozważ użycie metody instrumentacji. |
| [DA0004: Znaczące użycie procesora](../profiling/da0004-high-processor-usage.md) | Profilowanie danych sugeruje, że procesory były stale zajęte podczas przebiegu profilowania. Aby zebrać dokładniejsze dane, rozważ użycie metody próbkowania. |
| [DA0008: Zebrano kilka próbek](../profiling/da0008-few-samples-collected.md) | Liczba próbek zebranych w przebiegu profilowania była zbyt duża, aby była statystycznie znacząca. Rozważ ponowne utworzenie profilu i uruchomienie aplikacji przez dłuższy czas. Możesz również rozważyć użycie metody instrumentacji do zbierania danych. |
| [DA0026: Nadmierne zużycie czasu procesora w trybie jądra](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | W trybie jądra procesora wystąpił znaczący czas w przebiegu profilowania. Należy rozważyć próbkowanie przy użyciu wywołań systemowych jako metryki zamiast czasu użycia jako metryki. |
| [DA0029: Nieobsługiwana wersja środowiska CLR](../profiling/da0029-unsupported-clr-version.md) | Profilowany plik binarny używa wersji .NET Framework, która nie jest obsługiwana przez profiler. Raporty profilera nie mogą rozpoznać nazw symboli. |
| [DA0030: Zbierz miary interakcji warstw dla projektów bazy danych](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Zebrano znaczną liczbę wywołań metod w <xref:System.Data?displayProperty=fullName> przestrzeni nazw. Aby uwzględnić dane dotyczące wywołań bazy danych, należy rozważyć zbieranie danych o interakcji między warstwami w profilu. |
