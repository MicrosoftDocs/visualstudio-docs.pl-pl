---
title: Widok szczegółów wątku — dane rywalizacji | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778170"
---
# <a name="thread-details-view---contention-data"></a>Widok szczegółów wątku — dane rywalizacji
Widok Szczegóły wątku przedstawia wykres osi czasu dla zdarzeń blokowania w wybranym wątku przebiegu profilowania, który został spowodowany przez rywalizację o zasoby. Zdarzenie blokujące występuje, gdy wątek jest zmuszony do wstrzymania wykonywania, ponieważ inny wątek zablokował dostęp do zasobu.

 Ten widok przedstawia oś czasu wykonywania wątku jako poziomy pasek i zdarzenia blokowania jako pionowy pasek na poziomej osi czasu wątku. W razie potrzeby możesz powiększyć Sekcję osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżkę wykonywania funkcji, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje pojawiają się w oknie **stosu wywołań** . Gdy jest dostępny kod źródłowy funkcji, można kliknąć nazwę funkcji, aby edytować plik źródłowy w środowisku IDE programu Visual Studio.

## <a name="navigate-the-timeline"></a>Nawigowanie po osi czasu

#### <a name="to-zoom-in-on-a-timeline-segment"></a>Aby powiększyć segment osi czasu

- Kliknij i przeciągnij wskaźnik myszy, aby wybrać obszar osi czasu.

     Po zwolnieniu przycisku myszy widok zostanie powiększony do wybranego segmentu czasu. Możesz powtórzyć proces, aby powiększyć szczegóły. Pole przewijania na pasku przewijania czasu reprezentuje względny rozmiar segmentu czasu, który jest wyświetlany w widoku.

#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć na osi czasu

- Kliknij pozycję **Powiększ** , aby powrócić do poprzedniego poziomu powiększenia.

- Kliknij pozycję **powiększenie Reset** , aby wyświetlić całą oś czasu w widoku.

#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzenia

- Na wykresie osi czasu kliknij pionowy pasek, który reprezentuje zdarzenie.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kod źródłowy funkcji w stosie wywołań

- W oknie **stos wywołań** kliknij nazwę funkcji.

  Kod źródłowy funkcji musi być częścią bieżącego projektu.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Aby wyświetlić zdarzenia rywalizacji o zasób we wszystkich wątkach w przebiegu profilowania

- Na wykresie osi czasu kliknij nazwę lub identyfikator zasobu.

     Zostanie wyświetlony [Widok szczegóły zasobu](../profiling/resource-details-view-contention-data.md) dla wybranego zasobu.

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Aby wyświetlić dane rywalizacji wątku w oknie procesy

- Na wykresie osi czasu kliknij pozycję **łącznie**.

     Zostanie wyświetlony [Widok procesu](../profiling/process-view-contention-data.md) z wybranym wątkiem.
