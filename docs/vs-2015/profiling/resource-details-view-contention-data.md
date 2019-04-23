---
title: Widok — dane rywalizacji o zasoby szczegółów zasobów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aac43a88a62182a33ea3b340c5520e921d681cd7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089578"
---
# <a name="resource-details-view---contention-data"></a>Widok szczegółów zasobów — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok szczegółów zasobów przedstawia wykres osi czasu blokowania zdarzeń, które były spowodowane przez rywalizacji za pośrednictwem wybranego zasobu. Blokowanie zdarzenie występuje, gdy wątek jest zmuszony do zawieszenia wykonania, ponieważ inny wątek został zablokowany dostęp do zasobu.  
  
 Ten widok przedstawia oś czasu wykonywania każdego wątku jako poziomy pasek i reprezentuje każde zdarzenie blokowania jako pionowy pasek na osi czasu w wątku. Gdy jest to konieczne, można powiększyć części osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżki wykonywania (stosu wywołań) funkcje, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje są wyświetlane w **stos wywołań** okna. Po udostępnieniu kodu źródłowego dla funkcji kliknąć nazwę funkcji, aby edytować plik źródłowy w interfejsie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-magnify-a-timeline-segment"></a>Aby powiększyć segment osi czasu  
  
- Przeciągnij kursor nad obszarem osi czasu.  
  
     Po zwolnieniu przycisku myszy widok powiększa do segmentu wybrana wartość czasu. Możesz powtórzyć proces dalsze powiększanie segmentu. Pole przewijania na pasku przewijania czas reprezentuje rozmiar względny, segmentu czas, który pojawia się w widoku.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć na osi czasu  
  
- Wykonaj jedną z następujących czynności:  
  
    - Kliknij przycisk **Pomniejsz** aby powrócić do poprzedniego poziomu powiększenia.  
  
    - Kliknij przycisk **resetowania powiększenia** do wyświetlenia wszystkich osi czasu w widoku.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzenia  
  
- Na wykresie osi czasu kliknij pasek zdarzeń.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kod źródłowy funkcji w stosie wywołań  
  
- W **stos wywołań** okna, kliknij nazwę funkcji.  
  
  Kod źródłowy funkcji musi być częścią bieżącego projektu.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Aby wyświetlić drzewo wywołań rywalizacji zdarzeń dla zasobu  
  
- Wykres osi czasu, kliknij **całkowita**.  
  
     Widok Kontencji pojawia się dla zasobu. Aby uzyskać więcej informacji, zobacz [widok Kontencji zasobów](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Aby wyświetlić wszystkie zdarzenia rywalizacji wątków  
  
- Na wykresie osi czasu kliknij nazwę lub identyfikator wątku.  
  
     Widok szczegółów wątku są wyświetlane dla zaznaczonych wątków. Aby uzyskać więcej informacji, zobacz [widok szczegółów wątku](../profiling/thread-details-view-contention-data.md).
