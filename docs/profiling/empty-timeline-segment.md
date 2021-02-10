---
title: Pusty segment osi czasu | Microsoft Docs
description: W programie Visual Studio Concurrency Visualizer opisz powód, dla którego sekcja osi czasu może być pusta (ma białe tło) dla danego rodzaju kanału.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4a3265c3b31653d94a686fa8fda12f7699596e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955271"
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