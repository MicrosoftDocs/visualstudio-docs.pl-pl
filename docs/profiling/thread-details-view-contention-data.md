---
title: Widok szczegółów wątku — dane rywalizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 679fd9fd039fa903f5df5a479fa4f0e119bb7a9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778170"
---
# <a name="thread-details-view---contention-data"></a>Widok Szczegóły wątku — dane rywalizacji
Widok Szczegóły wątku przedstawia wykres osi czasu zdarzeń blokowania w wybranym wątku przebiegu profilowania, które zostały spowodowane przez rywalizacje o zasoby. Zdarzenie blokowania występuje, gdy wątek jest zmuszony do zawieszenia wykonywania, ponieważ inny wątek ma zablokowany dostęp do zasobu.

 Ten widok reprezentuje oś czasu wykonania wątku jako poziomy pasek i zdarzenia blokowania jako pionowy pasek na poziomej osi czasu wątku. W razie potrzeby można powiększyć część osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżkę wykonywania funkcji, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje są wyświetlane w oknie **Stos wywołań.** Gdy kod źródłowy funkcji jest dostępny, można kliknąć nazwę funkcji, aby edytować plik źródłowy w programie Visual Studio IDE.

## <a name="navigate-the-timeline"></a>Poruszanie się po osi czasu

#### <a name="to-zoom-in-on-a-timeline-segment"></a>Aby powiększyć segment osi czasu

- Kliknij i przeciągnij wskaźnik myszy, aby zaznaczyć obszar osi czasu.

     Po zwolnieniu myszy widok zostanie powiększony do wybranego segmentu czasu. Proces ten można powtórzyć, aby powiększyć więcej szczegółów. Pole przewijania na pasku przewijania czasu reprezentuje względny rozmiar segmentu czasu, który jest wyświetlany w widoku.

#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć oś czasu

- Kliknij **pozycję Pomniejsz,** aby powrócić do poprzedniego poziomu powiększenia.

- Kliknij **przycisk Resetowanie powiększenia,** aby wyświetlić całą oś czasu w widoku.

#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzenia

- Na wykresie osi czasu kliknij pionowy pasek reprezentujący zdarzenie.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kod źródłowy funkcji w stosie wywołań

- W oknie **Stos wywołań** kliknij nazwę funkcji.

  Kod źródłowy funkcji musi być częścią bieżącego projektu.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Aby wyświetlić zdarzenia rywalizacji zasobu we wszystkich wątkach w przebiegu profilowania

- Na wykresie osi czasu kliknij nazwę lub identyfikator zasobu.

     Dla wybranego zasobu zostanie wyświetlony [widok Szczegółów zasobu.](../profiling/resource-details-view-contention-data.md)

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Aby wyświetlić dane rywalizacji wątków w oknie Procesy

- Na wykresie osi czasu kliknij pozycję **Suma**.

     Zostanie wyświetlony [widok procesu](../profiling/process-view-contention-data.md) z zaznaczonym wątkiem.
