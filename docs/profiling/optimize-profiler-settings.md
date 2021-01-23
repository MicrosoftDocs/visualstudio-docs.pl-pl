---
title: Optymalizowanie ustawień profilera | Microsoft Docs
description: Dowiedz się, w jaki sposób Profiler wydajności i okno narzędzia diagnostyczne w programie Visual Studio mają wiele różnych ustawień, które mają wpływ na ogólną wydajność narzędzi.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 482ee640f4b84348e00f2f3da42a4dbe13f73460
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722844"
---
# <a name="optimizing-profiler-settings"></a>Optymalizowanie ustawień profilera

Narzędzie Performance Profiler i okno narzędzia diagnostyczne w programie Visual Studio mają wiele różnych ustawień, które mają wpływ na ogólną wydajność narzędzi. Zmiana niektórych ustawień może spowodować szybkie uruchomienie analizy lub spowodować dodatkowe czasy oczekiwania podczas przetwarzania wyników w narzędziach. Poniżej znajduje się podsumowanie niektórych ustawień i ich wpływ na wydajność.

## <a name="symbol-settings"></a>Ustawienia symboli

Ustawienia symboli Znalezione w opcjach debugera (**opcje > debugowania > symbole** lub **narzędzia > opcje > debugowanie > symbole**) mają znaczny wpływ na to, jak długo trwa generowanie wyników w narzędziach. Włączenie serwerów symboli lub użycie **_NT_SYMBOL_PATH** powoduje, że profiler zażąda symboli dla każdego załadowanego modułu w raporcie. Obecnie Profiler zawsze automatycznie ładuje wszystkie symbole, niezależnie od preferencji automatycznego ładowania symboli.

![Strona ładowania symboli](../profiling/media/symbolloading.png "Ładowanie symboli")

Postęp ładowania symboli można zobaczyć w oknie **danych wyjściowych** pod nagłówkiem **Narzędzia diagnostyczne** .

![Postęp ładowania symboli](../profiling/media/symbolloadingprogress.png "Postęp ładowania symboli")

Po pobraniu symbole są zapisywane w pamięci podręcznej, co spowoduje przyspieszenie przyszłej analizy, ale wymaga załadowania i przeanalizowania plików. Jeśli ładowanie symboli spowalnia analizę, spróbuj wyłączyć serwery symboli i wyczyścić pamięć podręczną symboli. Zamiast tego należy polegać na symbolach utworzonych lokalnie dla projektu.

## <a name="show-external-code"></a>Pokaż kod zewnętrzny

Wiele narzędzi w **profilerze wydajności** i oknie **Narzędzia diagnostyczne** ma koncepcje kodu użytkownika i kodu zewnętrznego. Kod użytkownika to kod, który jest skompilowany przez otwarte rozwiązanie lub otwarty obszar roboczy. Kod zewnętrzny to coś innego. Utrzymując ustawienie **Pokaż zewnętrzny kod** wyłączony lub **Pokaż tylko mój kod** włączony, można zagregować kod zewnętrzny do pojedynczej klatki pierwszego poziomu, znacznie zmniejszając ilość przetwarzania wymaganego do pokazywania wyników. Dzięki temu użytkownicy mogą zobaczyć, co zostało wywołane w zewnętrznym kodzie, który utworzył spowolnienie, przy jednoczesnym przetwarzaniu danych do minimum. Jeśli to możliwe, pozostaw pozycję **Pokaż zewnętrzny kod** wyłączony i upewnij się, że masz otwarte rozwiązanie lub obszar roboczy dla diagsession, które chcesz analizować.

## <a name="trace-duration"></a>Czas trwania śledzenia

Profilowanie krótszych czasów trwania powoduje szybsze analizowanie danych. Zwykle zalecamy, aby próbować ograniczyć ślady do nie więcej niż pięć minut danych wydajności. Niektóre narzędzia, takie jak narzędzie [użycie procesora CPU](../profiling/cpu-usage.md) , umożliwiają wstrzymywanie zbierania danych w trakcie działania narzędzia, dzięki czemu można ograniczyć ilość danych zbieranych do scenariusza, który użytkownik chce analizować.

## <a name="sampling-frequency"></a>Częstotliwość próbkowania

Niektóre narzędzia, takie jak narzędzie [użycie procesora CPU](../profiling/cpu-usage.md) i narzędzie [alokacji obiektów sieciowych](../profiling/dotnet-alloc-tool.md) , umożliwiają dostosowanie częstotliwości próbkowania. Zwiększenie tej częstotliwości próbkowania pozwala na dokładniejsze zmierzenie, ale zwiększa ilość wygenerowanych danych. Zazwyczaj najlepszym rozwiązaniem jest pozostawienie tego ustawienia według stawki domyślnej, chyba że konkretny problem jest badany.

![Strona właściwości centrum diag](../profiling/media/diaghubpropertiespage.png "Strona właściwości centrum diag")

## <a name="see-also"></a>Zobacz także

- [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Jednoczesne używanie wielu narzędzi profilera](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Zapoznanie z metodami zbierania danych wydajności](../profiling/understanding-performance-collection-methods-perf-profiler.md)
