---
title: Pusty segment osi czasu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970112"
---
# <a name="empty-timeline-segment"></a>Opróżnianie segmentu osi czasu
W wizualizatorze współbieżności przyczyna, że sekcja osi czasu jest pusta (ma białe tło) zależy od rodzaju kanału.

- Dla kanału wątku procesora CPU oznacza to, że wątek nie istnieje podczas tej części osi czasu. Jeśli jesteś zainteresowany wątku, można znaleźć jego sekcji wykonywania za pomocą kontroli powiększenia lub przewijanie w poziomie.

- W przypadku kanału We/Wy oznacza to, że w tym momencie nie wystąpił żaden dostęp do dysku w imieniu procesu docelowego.

- W przypadku kanału DirectX oznacza to, że podczas tej części osi czasu nie wykonano żadnej pracy gpu w imieniu procesu docelowego.

- Oznacza to, że w przypadku kanału znaczników nie zostały wygenerowane żadne znaczniki.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)
- [Kontrolka powiększenia (widok wątków)](../profiling/zoom-control-threads-view.md)