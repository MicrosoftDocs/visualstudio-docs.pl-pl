---
title: Okno Eksploratora wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a365892f606da90c608e43b7ccce73b902ec0e98
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772442"
---
# <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

Okno **Eksplorator wydajności** w programie Visual Studio IDE umożliwia konfigurowanie i uruchamianie sesji wydajności przy użyciu narzędzi do profilowania programu Visual Studio. Jeśli chcesz otworzyć okno, postępuj zgodnie z instrukcjami w [Przewodnik dla początkujących do profilowania wydajności](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Pasek narzędzi Eksploratora wydajności

Na pasku narzędzi **Eksploratora wydajności** dostępne są następujące opcje:

- **Uruchom Kreatora wydajności** — wyświetla Kreatora wydajności w celu dodania nowej sesji wydajności do okna Eksploratora wydajności.

- **Nowa sesja wydajności** — dodaje pustą sesję wydajności do okna Eksploratora wydajności.

- **Uruchom** - **Uruchom** listę przycisków polecenia umożliwia uruchomienie aplikacji docelowej, która ma profilowanie natychmiast włączone **(Uruchom z profilowania)** lub profilowania zawieszone **(Uruchom z profilowania wstrzymane).**

- **Metoda** — określa, czy metoda profilowania sesji jest próbkowanie lub instrumentacji.

- **Zatrzymaj** — natychmiast kończy działanie aplikacji docelowej i profilera.

- **Dołącz/Odłącz** — wyświetla okno dialogowe **Dołączanie profilera do procesu,** aby wybrać uruchomiony proces, do którego ma być dołączany profiler.

## <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

Okno **Eksplorator wydajności** zawiera formant drzewa, który wyświetla pliki binarne i pliki danych raportu jednej lub więcej sesji wydajności.

- **Nazwa sesji** — katalog główny formantu drzewa zawiera nazwę sesji. Kliknij prawym przyciskiem myszy nazwę sesji, aby ustawić właściwości sesji lub uruchomić aplikację docelową i profiler.

- **Obiekty docelowe** — wyświetla nazwy plików binarnych, które mają być profilowane w sesji. Kliknij prawym przyciskiem myszy pozycję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Obiekty docelowe,** aby dodać lub usunąć plik binarny, projekt lub witrynę sieci Web. Kliknij prawym przyciskiem myszy nazwę obiektu docelowego, aby ustawić właściwości dla poszczególnych plików binarnych.

- **Raporty** — wyświetla nazwy plików danych profilera, które są generowane dla sesji. Kliknij prawym przyciskiem myszy **raporty,** aby dodać istniejący raport lub porównać dwa pliki danych profilera. Kliknij prawym przyciskiem myszy nazwę raportu, aby otworzyć, usunąć lub wyeksportować plik danych profilera.

## <a name="see-also"></a>Zobacz też

[Przeglądy](../profiling/overviews-performance-tools.md)
[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[kontrolujących zbieranie danych](../profiling/controlling-data-collection.md)
