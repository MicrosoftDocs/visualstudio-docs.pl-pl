---
title: Reguły użytkowania narzędzi profilowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 51c4f1384a58b19ad9a6a4f46ad0131158cc967c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778352"
---
# <a name="profiling-tools-usage-rules"></a>Reguły korzystania z narzędzi profilowania
Reguły wydajności w kategorii Użycie narzędzi profilowania zawierają wskazówki dotyczące korzystania z profilera do najbardziej efektywnego zbierania danych.

| | |
| - | - |
| [DA0002: brakuje VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Profilowanie wiersza polecenia może zawierać niekompletne dane dla plików binarnych programu .NET Framework. Może to być spowodowane niestawiając poprawnych zmiennych środowiskowych. |
| [DA0003: Wiele przykładów jądra](../profiling/da0003-many-kernel-samples.md) | Zarejestrowano wiele przykładów profilowania, które wystąpiły poza wykonaniem docelowego pliku binarnego. Aby zebrać dokładniejsze dane, należy rozważyć użycie metody instrumentacji. |
| [DA0004: Znaczące wykorzystanie procesora](../profiling/da0004-high-processor-usage.md) | Dane profilowania sugerują, że procesory były stale zajęte podczas przebiegu profilowania. Aby zebrać dokładniejsze dane, należy rozważyć użycie metody próbkowania. |
| [DA0008: Kilka zebranych próbek](../profiling/da0008-few-samples-collected.md) | Liczba próbek zebranych w przebiegu profilowania nie była wystarczająco wysoka, aby była statystycznie istotna. Rozważ profilowanie ponownie i uruchomienie aplikacji przez dłuższy czas. Można również rozważyć użycie metody instrumentacji do zbierania danych. |
| [DA0026: Nadmierne zużycie czasu procesora CPU w trybie jądra](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | W trybie jądra procesora wystąpił znaczna ilość czasu w przebiegu profilowania. Należy wziąć pod uwagę próbkowanie przy użyciu wywołań systemowych jako metryki zamiast przy użyciu czasu jako metryki. |
| [DA0029: Nieobsługiwana wersja środowiska CLR](../profiling/da0029-unsupported-clr-version.md) | Profilowany plik binarny używa wersji programu .NET Framework, która nie jest obsługiwana przez profiler. Raporty profilera nie mogą rozpoznać nazw symboli. |
| [DA0030: Zbieraj pomiary interakcji warstw dla projektów bazy danych](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Zebrano znaczną liczbę <xref:System.Data?displayProperty=fullName> wywołań metod w obszarze nazw. Aby uwzględnić dane dotyczące wywołań bazy danych, należy rozważyć zbieranie danych interakcji warstwy w przebiegach profilu. |
