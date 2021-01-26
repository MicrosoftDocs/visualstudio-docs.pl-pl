---
title: Wprowadzenie do narzędzi wydajności | Microsoft Docs
description: Poznaj różne sposoby, które program Visual Studio oferuje do zbierania, wyświetlania i analizowania danych dotyczących wydajności kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4f168c4c88ba12ff1f1c9bd0543e9d2b74ae095c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801507"
---
# <a name="getting-started-with-performance-tools"></a>Wprowadzenie do narzędzi wydajności

Program Visual Studio oferuje kilka metod zbierania, wyświetlania i analizowania danych wydajności kodu. W wielu przypadkach najlepszym sposobem na rozpoczęcie pracy z narzędziami wydajności jest użycie ustawień domyślnych **Kreatora wydajności**. Kreator zbiera dane statystyczne aplikacji, które mogą wskazywać na problemy z wydajnością w kodzie.

- Ostrzeżenia o wydajności, które powiadamiają o typowych problemach z kodowaniem, są wyświetlane w oknie **Lista błędów** programu Visual Studio. Możesz nawigować od ostrzeżeń do kodu źródłowego i szczegółowe tematy pomocy ułatwiające pisanie bardziej wydajnego kodu.

- Raporty wydajności zapewniają widoki na różnych poziomach struktury aplikacji, wierszach kodu źródłowego i procesach. Raporty wydajności zawierają dane dotyczące wykonywania aplikacji, od wywołujących i wywoływanych funkcji określonej funkcji, do drzewa wywołań całej aplikacji.

Aby szybko profilować witrynę sieci Web, aplikację lub ASP.NET, wybierz kolejno opcje **Debuguj**  >  **wydajność Profiler** i **Kreator wydajności**. Aby uzyskać szczegółowe instrukcje, zobacz [początkując Przewodnik dotyczący profilowania wydajności](../profiling/beginners-guide-to-cpu-sampling.md) i instrukcje [: gromadzenie danych wydajności dla witryny sieci Web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Aby ręcznie określić i skonfigurować sesję profilowania wydajności, wybierz pozycję **Debuguj**  >  **Profiler**  >  **Eksplorator wydajności**. Użyj folderu **targets** i stron **Właściwości** w **Eksplorator wydajności** , aby skonfigurować sesje. Aby uzyskać instrukcje, zobacz [How to: ręczne tworzenie sesji wydajności](../profiling/how-to-manually-create-performance-sessions.md).

**Zobacz również:**

- [Przeglądy narzędzi wydajności](../profiling/overviews-performance-tools.md)
- [Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)
- [Korzystanie z reguł wydajności do analizowania danych](../profiling/using-performance-rules-to-analyze-data.md)
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
