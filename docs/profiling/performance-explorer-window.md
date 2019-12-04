---
title: Okno Eksplorator wydajności | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772442"
---
# <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

Okno **Eksplorator wydajności** w środowisku IDE programu Visual Studio umożliwia konfigurowanie i uruchamianie sesji wydajności przy użyciu narzędzia profilowania programu Visual Studio. Jeśli musisz otworzyć okno, postępuj zgodnie z instrukcjami w [przewodniku początkujących, aby przeprowadzić profilowanie wydajności](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Eksplorator wydajności pasek narzędzi

Na pasku narzędzi **Eksplorator wydajności** są dostępne następujące opcje:

- **Uruchom Kreatora wydajności** — wyświetla Kreatora wydajności, aby dodać nową sesję wydajności do okna Eksplorator wydajności.

- **Nowa sesja wydajności** — dodaje pustą sesję wydajności do okna Eksplorator wydajności.

- **Uruchom** — lista przycisków poleceń **uruchamiania** umożliwia uruchomienie aplikacji docelowej, która ma natychmiastowe włączenie profilowania (**Uruchom z profilowania**) lub profilowanie zawieszone (**Uruchom z wstrzymanym profilem**).

- **Metoda** — określa, czy metoda profilowania sesji jest próbką lub Instrumentacją.

- **Zatrzymaj** — natychmiast zamyka aplikację docelową i Profiler.

- **Dołącz/Odłącz** — wyświetla okno dialogowe **Dołącz profiler do procesu** , aby wybrać uruchomiony proces, do którego ma zostać dołączony Profiler.

## <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

Okno **Eksplorator wydajności** zawiera kontrolkę drzewa, która wyświetla pliki binarne i dane raportów z co najmniej jednej sesji wydajności.

- **Nazwa sesji** — katalog główny kontrolki drzewa zawiera nazwę sesji. Kliknij prawym przyciskiem myszy nazwę sesji, aby ustawić właściwości sesji lub uruchomić aplikację docelową oraz Profiler.

- **Elementy docelowe** — wyświetla nazwy plików binarnych, które mają być profilowane w sesji. Kliknij prawym przyciskiem myszy element **docelowy** , aby dodać lub usunąć dane binarne, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt lub witrynę sieci Web. Kliknij prawym przyciskiem myszy nazwę docelową, aby ustawić właściwości dla poszczególnych plików binarnych.

- **Raporty** — wyświetla nazwy plików danych profilera, które są generowane dla danej sesji. Kliknij prawym przyciskiem myszy pozycję **raporty** , aby dodać istniejący raport lub porównać dwa pliki danych profilera. Kliknij prawym przyciskiem myszy nazwę raportu, aby otworzyć, usunąć lub wyeksportować plik danych profilera.

## <a name="see-also"></a>Zobacz także

[Przeglądy](../profiling/overviews-performance-tools.md)
[konfigurowania sesji wydajności](../profiling/configuring-performance-sessions.md)
[kontrolowania zbierania danych](../profiling/controlling-data-collection.md)
