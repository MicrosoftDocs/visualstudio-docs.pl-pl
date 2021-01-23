---
title: Widok szczegółów zasobów — dane rywalizacji | Microsoft Docs
description: Dowiedz się, jak widok Szczegóły zasobu przedstawia wykres osi czasu dla zdarzeń blokowania, które zostały spowodowane przez rywalizacje w ramach wybranego zasobu.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45babe50e794e0831fd0e93048b32feaf18be87a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720361"
---
# <a name="resource-details-view---contention-data"></a>Widok szczegółów zasobów — dane rywalizacji
Widok Szczegóły zasobu przedstawia wykres osi czasu dla zdarzeń blokowania, które były spowodowane przez rywalizacje dla wybranego zasobu. Zdarzenie blokujące występuje, gdy wątek jest zmuszony do wstrzymania wykonywania, ponieważ inny wątek zablokował dostęp do zasobu.

 Ten widok przedstawia oś czasu wykonywania każdego wątku jako poziomy pasek i reprezentuje każde zdarzenie blokujące jako pionowy pasek na osi czasu wątku. W razie potrzeby możesz powiększyć Sekcję osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżkę wykonywania (stos wywołań) funkcji, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje pojawiają się w oknie **stosu wywołań** . Gdy jest dostępny kod źródłowy funkcji, można kliknąć nazwę funkcji, aby edytować plik źródłowy w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="procedures"></a>Procedury

#### <a name="to-magnify-a-timeline-segment"></a>Aby powiększyć segment osi czasu

- Przeciągnij wskaźnik myszy nad obszar osi czasu.

     Po zwolnieniu przycisku myszy widok zostanie powiększony do wybranego segmentu czasu. Można powtórzyć proces, aby rozszerzyć segment. Pole przewijania na pasku przewijania czasu reprezentuje względny rozmiar segmentu czasu, który pojawia się w widoku.

#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć na osi czasu

- Wykonaj jedną z następujących czynności:

  - Kliknij pozycję **Powiększ** , aby powrócić do poprzedniego poziomu powiększenia.

  - Kliknij pozycję **powiększenie Reset** , aby wyświetlić całą oś czasu w widoku.

#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzenia

- Na wykresie osi czasu kliknij pasek zdarzeń.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kod źródłowy funkcji w stosie wywołań

- W oknie **stos wywołań** kliknij nazwę funkcji.

  Kod źródłowy funkcji musi być częścią bieżącego projektu.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Aby wyświetlić drzewo wywołań zdarzeń rywalizacji o zasób

- Na wykresie osi czasu kliknij pozycję **łącznie**.

     Zostanie wyświetlony widok rywalizacje o zasób. Aby uzyskać więcej informacji, zobacz [Widok rywalizacji o zasoby](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Aby wyświetlić wszystkie zdarzenia rywalizacji wątku

- Na wykresie osi czasu kliknij nazwę lub identyfikator wątku.

     Zostanie wyświetlony widok Szczegóły wątku dla wybranego wątku. Aby uzyskać więcej informacji, zobacz [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md).
