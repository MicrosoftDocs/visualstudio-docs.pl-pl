---
title: Opis wartości danych rywalizacji o zasoby | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779990"
---
# <a name="understand-resource-contention-data-values"></a>Opis wartości danych rywalizacji o zasoby

Profilowanie rywalizacji o zasoby zbiera szczegółowe informacje o stosie wywołań za każdym razem, gdy konkurujące wątki w aplikacji są zmuszane do oczekiwania na dostęp do zasobu udostępnionego.

Raporty z rywalizacji o zasoby pokazują łączną liczbę zdarzeń rywalizacji oraz całkowity czas spędzony przez moduły, funkcje, wiersze kodu źródłowego i instrukcje w oczekiwaniu na zasoby.

- Wartości włącznie wyświetlają całkowitą liczbę rywalizacji, które wymusiły oczekiwanie funkcji przez rywalizacje o zasoby i całkowity czas oczekiwania funkcji.  Rywalizacje, które zostały spowodowane przez funkcje podrzędne, które zostały wywołane przez funkcję są uwzględniane w wartości włącznie.

- Wartości wyłączne wyświetlić tylko liczbę rywalizacji, które wymusiły funkcję czekać i które zostały spowodowane przez kod w treści funkcji. Rywalizacje spowodowane przez funkcje podrzędne nie są uwzględniane. Czas wyłączności dla funkcji obejmuje również tylko czas oczekiwania, które zostały spowodowane przez instrukcje w treści funkcji.

Widoki raportu rywalizacji o zasoby obejmują również wykresy osi czasu, które pokazują poszczególne zdarzenia rywalizacji w czasie i pokazują stosy wywołań, które utworzyły określone zdarzenie. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

- [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)

- [Widok szczegółów zasobu](../profiling/resource-details-view-contention-data.md)

Aby uzyskać więcej informacji na temat drugiego trybu profilowania współbieżności, zobacz [Wizualizator współbieżności](../profiling/concurrency-visualizer.md).
