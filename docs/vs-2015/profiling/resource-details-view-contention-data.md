---
title: Widok szczegółów zasobów — dane rywalizacji | Microsoft Docs
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
ms.openlocfilehash: 922edcd45dd42c8da5a9ec4dc8d3e8f450ceea09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823599"
---
# <a name="resource-details-view---contention-data"></a>Widok szczegółów zasobów — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok Szczegóły zasobu przedstawia wykres osi czasu dla zdarzeń blokowania, które były spowodowane przez rywalizacje dla wybranego zasobu. Zdarzenie blokujące występuje, gdy wątek jest zmuszony do wstrzymania wykonywania, ponieważ inny wątek zablokował dostęp do zasobu.  
  
 Ten widok przedstawia oś czasu wykonywania każdego wątku jako poziomy pasek i reprezentuje każde zdarzenie blokujące jako pionowy pasek na osi czasu wątku. W razie potrzeby możesz powiększyć Sekcję osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżkę wykonywania (stos wywołań) funkcji, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje pojawiają się w oknie **stosu wywołań** . Gdy jest dostępny kod źródłowy funkcji, można kliknąć nazwę funkcji, aby edytować plik źródłowy w interfejsie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
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
  
     Zostanie wyświetlony widok rywalizacje o zasób. Aby uzyskać więcej informacji, zobacz [Widok rywalizacji o zasoby](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Aby wyświetlić wszystkie zdarzenia rywalizacji wątku  
  
- Na wykresie osi czasu kliknij nazwę lub identyfikator wątku.  
  
     Zostanie wyświetlony widok Szczegóły wątku dla wybranego wątku. Aby uzyskać więcej informacji, zobacz [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md).
