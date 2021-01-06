---
title: Wizualizuj liczniki dotnet | Microsoft Docs
description: Dowiedz się, jak używać narzędzia .NET Counters w profilerze wydajności programu Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905041"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Wizualizowanie liczników dotnet przy użyciu profilera programu Visual Studio


Narzędzie liczniki platformy .NET umożliwia wizualizację [liczników dotnet](/dotnet/core/diagnostics/dotnet-counters) w miarę upływu czasu bezpośrednio z poziomu profilera programu Visual Studio.


> [!NOTE]
> Narzędzie liczniki platformy .NET wymaga programu Visual Studio 2019 w wersji 16,7 lub nowszej, który jest przeznaczony dla programu .NET Core 3.0 +.

## <a name="setup"></a>Konfigurowanie

1. Otwórz narzędzie Performance Profiler (**ALT + F2** lub **Debug-> Performance Profiler**) w programie Visual Studio.

2. Zaznacz pole wyboru **liczniki platformy .NET** .

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Wybrane narzędzie Counters.":::

3. Kliknij przycisk **Uruchom** , aby uruchomić narzędzie.

Aby uzyskać więcej informacji na temat optymalizowania wydajności narzędzi, zobacz [Optymalizacja ustawień profilera](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Zrozumienie danych

Gdy narzędzie początkowo zbiera dane, można zobaczyć wartości na żywo [liczników dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Trwa zbieranie narzędzi licznika platformy .NET.":::

Możesz również wyświetlić wykresy liczników, zaznaczając pole wyboru obok nazw liczników. Można wyświetlić wykresy z wieloma licznikami jednocześnie.


Po zakończeniu wykonywania aplikacji i zbieraniu danych możesz zatrzymać zbieranie dla jeszcze bardziej szczegółowego raportu. Aby to zrobić, naciśnij przycisk **Zatrzymaj zbieranie** .


Po załadowaniu raportu powinien zostać wyświetlony raport końcowy podobny do przedstawionego poniżej.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Raport narzędzia licznika platformy .NET.":::

Raport przedstawia następujące wartości:

- Min — wartość minimalna dla tego licznika w wybranym zakresie czasu.
- Max — maksymalna wartość tego licznika w wybranym zakresie czasu.
- Średnia — wartość średnia dla tego licznika w wybranym zakresie czasu.

Możesz filtrować lub dodawać kolumny w tabeli, klikając prawym przyciskiem myszy nagłówki kolumn i wybierając nagłówek.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Kolumny narzędzi licznika .NET.":::

Możesz również wyświetlić wykresy w szczegółowym raporcie, zaznaczając pola wyboru obok pozycji liczniki. Dane w tabelach przedstawiają domyślnie wartości całego czasu trwania zebranego śledzenia. Aby odfiltrować dane do określonego zakresu czasu, kliknij i przeciągnij na wykresach.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtrowanie czasu narzędzia liczników platformy .NET.":::

Tabela aktualizuje odpowiednie wartości w czasie wybranym na wykresach. Użyj przycisku **wyczyść zaznaczenie** , aby zresetować wybrany zakres czasu do całego śledzenia.


## <a name="see-also"></a>Zobacz też

- [Optymalizowanie ustawień profilera](../profiling/optimize-profiler-settings.md)
- [Liczniki dotnet](/dotnet/core/diagnostics/dotnet-counters)
