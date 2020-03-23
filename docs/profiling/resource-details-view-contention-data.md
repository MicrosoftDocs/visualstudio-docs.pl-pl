---
title: Widok szczegółów zasobu — dane rywalizacji | Dokumenty firmy Microsoft
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
ms.openlocfilehash: e66432fd2f5d8b1532bece9d76e7dfc2a261e4b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771606"
---
# <a name="resource-details-view---contention-data"></a>Widok szczegółów zasobów — dane rywalizacji
Widok Szczegóły zasobu przedstawia wykres osi czasu zdarzeń blokowania, które zostały spowodowane przez rywalizacje o wybrany zasób. Zdarzenie blokowania występuje, gdy wątek jest zmuszony do zawieszenia wykonywania, ponieważ inny wątek ma zablokowany dostęp do zasobu.

 Ten widok reprezentuje oś czasu wykonywania każdego wątku jako poziomy pasek i reprezentuje każde zdarzenie blokowania jako pionowy pasek na osi czasu wątku. W razie potrzeby można powiększyć część osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżkę wykonywania (stos wywołań) funkcji, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje są wyświetlane w oknie **Stos wywołań.** Gdy kod źródłowy funkcji jest dostępny, można kliknąć nazwę funkcji, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]edytować plik źródłowy w interfejsie dla programu .

## <a name="procedures"></a>Procedury

#### <a name="to-magnify-a-timeline-segment"></a>Aby powiększyć segment osi czasu

- Przeciągnij wskaźnik myszy nad obszar osi czasu.

     Po zwolnieniu przycisku myszy widok zostanie powiększony do wybranego segmentu czasu. Można powtórzyć proces, aby jeszcze bardziej powiększyć segment. Pole przewijania na pasku przewijania czasu reprezentuje względny rozmiar segmentu czasu, który pojawia się w widoku.

#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć oś czasu

- Wykonaj jedną z następujących czynności:

  - Kliknij **pozycję Pomniejsz,** aby powrócić do poprzedniego poziomu powiększenia.

  - Kliknij **pozycję Resetowanie powiększenia,** aby wyświetlić całą oś czasu w widoku.

#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzenia

- Na wykresie osi czasu kliknij pasek zdarzeń.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kod źródłowy funkcji w stosie wywołań

- W oknie **Stos wywołań** kliknij nazwę funkcji.

  Kod źródłowy funkcji musi być częścią bieżącego projektu.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Aby wyświetlić drzewo wywołań zdarzeń rywalizacji dla zasobu

- Na wykresie osi czasu kliknij pozycję **Suma**.

     Widok Rywalizacje jest wyświetlany dla zasobu. Aby uzyskać więcej informacji, zobacz [Widok rywalizacji o zasoby](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Aby wyświetlić wszystkie zdarzenia rywalizacji wątku

- Na wykresie osi czasu kliknij nazwę lub identyfikator wątku.

     Widok szczegółów wątku jest wyświetlany dla wybranego wątku. Aby uzyskać więcej informacji, zobacz [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md).
