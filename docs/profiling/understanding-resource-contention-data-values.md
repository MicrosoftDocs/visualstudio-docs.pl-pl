---
title: Zapoznanie z wartościami danych Kontencji zasobów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ed72fe023e849d68dc8c417fc237bdd9e3d8c0f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622504"
---
# <a name="understand-resource-contention-data-values"></a>Zrozumienie wartościami danych kontencji zasobów

Profilowanie rywalizacji zasobów zbiera szczegółowe informacje stosu wywołań każdorazowo że konkurencyjne wątki w aplikacji są zmuszone czekać na dostęp do zasobu udostępnionego.

Raporty z rywalizacji o zasoby pokazują łączną liczbę zdarzeń rywalizacji oraz całkowity czas spędzony przez moduły, funkcje, wiersze kodu źródłowego i instrukcje w oczekiwaniu na zasoby.

- Alternatywne wartości wyświetlane całkowita liczba rywalizacji, których wymuszone funkcja oczekiwania przez rywalizacje o zasoby i łączny czas oczekiwania funkcji.  Rywalizacji, które były spowodowane przez funkcje podrzędne, które zostały wywołane przez funkcję znajdują się w wartości włącznie.

- Wyłączne wartości są wyświetlane tylko liczbę rywalizacji, wymuszone funkcja oczekiwania i że zostały spowodowane przez kod w treści funkcji. Rywalizacji spowodowane przez funkcje podrzędne nie są uwzględniane. Własny czas funkcji obejmuje także czasy oczekiwania, które były spowodowane przez instrukcje w treści funkcji.

Widoki raportu rywalizacji zasobów również uwzględnić wykresy z osią czasu, które pokazują zdarzenia rywalizacji indywidualnych wraz z upływem czasu i Pokaż stosy wywołań, które tworzone określonego zdarzenia. Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:

- [Widok szczegółów wątku](../profiling/thread-details-view-contention-data.md)

- [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md)

Aby uzyskać więcej informacji na temat tryb drugiego profilowania współbieżności zobacz [Concurrency Visualizer](../profiling/concurrency-visualizer.md).