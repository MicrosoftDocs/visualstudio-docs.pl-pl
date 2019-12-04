---
title: Informacje o wartościach danych rywalizacji o zasoby | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f522d1854cae86d9dc6e757ef0c9a62f4511800
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779990"
---
# <a name="understand-resource-contention-data-values"></a>Opis wartości danych rywalizacji o zasoby

Profilowanie rywalizacji o zasoby zbiera szczegółowe informacje o stosie wywołań za każdym razem, gdy konkurujące wątki w aplikacji są zmuszeni do oczekiwania na dostęp do zasobu udostępnionego.

Raporty z rywalizacji o zasoby pokazują łączną liczbę zdarzeń rywalizacji oraz całkowity czas spędzony przez moduły, funkcje, wiersze kodu źródłowego i instrukcje w oczekiwaniu na zasoby.

- Wartości włączne przedstawiają łączną liczbę rywalizacji, która wymusić, że funkcja oczekuje na zaczekanie zasobów i łączny czas oczekiwania funkcji.  Rywalizacje, które były spowodowane przez funkcje podrzędne, które zostały wywołane przez funkcję, są uwzględniane w wartościach włącznie.

- Wartości wyłączne wyświetlają tylko liczbę rywalizacji, które wymuszą oczekiwanie, i które zostały spowodowane przez kod w treści funkcji. Rywalizacje związane z funkcjami podrzędnymi nie są uwzględniane. Czas wyłączny dla funkcji obejmuje również czas oczekiwania, który został spowodowany przez instrukcje w treści funkcji.

Widoki raportów rywalizacji o zasoby obejmują także wykresy osi czasu, które pokazują poszczególne zdarzenia rywalizacji w czasie i pokazują stosy wywołań, które utworzyły określone zdarzenie. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

- [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)

- [Widok szczegółów zasobu](../profiling/resource-details-view-contention-data.md)

Aby uzyskać więcej informacji o drugim trybie profilowania współbieżności, zobacz [Concurrency Visualizer](../profiling/concurrency-visualizer.md).
