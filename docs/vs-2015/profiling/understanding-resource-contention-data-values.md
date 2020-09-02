---
title: Informacje o wartościach danych rywalizacji o zasoby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5983396924f38c31b6dafcd42b762042e1880e8d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145433"
---
# <a name="understanding-resource-contention-data-values"></a>Zapoznanie z wartościami danych kontencji zasobów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie rywalizacji o zasoby zbiera szczegółowe informacje o stosie wywołań za każdym razem, gdy konkurujące wątki w aplikacji są zmuszeni do oczekiwania na dostęp do zasobu udostępnionego.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Raporty z rywalizacji o zasoby pokazują łączną liczbę zdarzeń rywalizacji oraz całkowity czas spędzony przez moduły, funkcje, wiersze kodu źródłowego i instrukcje w oczekiwaniu na zasoby.  
  
- Wartości włączne przedstawiają łączną liczbę rywalizacji, która wymusić, że funkcja oczekuje na zaczekanie zasobów i łączny czas oczekiwania funkcji.  Rywalizacje, które były spowodowane przez funkcje podrzędne, które zostały wywołane przez funkcję, są uwzględniane w wartościach włącznie.  
  
- Wartości wyłączne wyświetlają tylko liczbę rywalizacji, które wymuszą oczekiwanie, i które zostały spowodowane przez kod w treści funkcji. Rywalizacje związane z funkcjami podrzędnymi nie są uwzględniane. Czas wyłączny dla funkcji obejmuje również czas oczekiwania, który został spowodowany przez instrukcje w treści funkcji.  
  
  Widoki raportów rywalizacji o zasoby obejmują także wykresy osi czasu, które pokazują poszczególne zdarzenia rywalizacji w czasie i pokazują stosy wywołań, które utworzyły określone zdarzenie. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:  
  
- [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)  
  
- [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md)  
  
  Aby uzyskać więcej informacji o drugim trybie profilowania współbieżności, zobacz [Concurrency Visualizer](../profiling/concurrency-visualizer.md).
