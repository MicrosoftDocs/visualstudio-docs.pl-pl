---
title: Pusty segment osi czasu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62970112"
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
W wizualizatorze współbieżności powód, dla którego sekcja osi czasu jest pusta (ma białe tło) zależy od rodzaju kanału.

- W przypadku kanału wątku procesora CPU oznacza to, że wątek nie istniał w tej części osi czasu. Jeśli interesuje Cię wątek, możesz znaleźć jego sekcję wykonywania przy użyciu kontrolki powiększenia lub przewijania w poziomie.

- W przypadku kanału we/wy oznacza to, że w tym momencie nie wystąpił dostęp do dysku w imieniu procesu docelowego.

- W przypadku kanału DirectX oznacza to, że nie wykonano żadnych zadań procesora GPU w imieniu procesu docelowego w tej części osi czasu.

- W przypadku kanału znacznika oznacza to, że nie Wygenerowano żadnych znaczników.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)
- [Kontrolka powiększenia (Widok wątków)](../profiling/zoom-control-threads-view.md)