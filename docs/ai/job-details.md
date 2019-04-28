---
title: Wyświetl ostatnie zadania
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: a2970c0086ec18789347eebdea752487be18ce7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548406"
---
# <a name="view-recent-job-performance-and-details"></a>Wyświetl ostatnią wydajność zadania i szczegóły

Po przesłaniu zadania można wyświetlić listę zadań, aby wyświetlić ich stan, czas trwania i nie tylko.

1. W **Eksploratora serwera**, rozwiń węzeł kontekstu obliczeniowego określone.
2. Kliknij dwukrotnie **zadań**.
3. Zobaczysz listę zadania przesłane do danego kontekstu obliczeniowego.
4. Wybierz konkretną **zadania** na liście, aby wyświetlić szczegóły.

![Monitorowanie zadań](media/job-details/monitor-jobs.png)

> Historia zadania przesłane do maszyn wirtualnych systemu Linux są przechowywane na maszynie Wirtualnej w folderze/tmp katalogu. W związku z tym w każdym przypadku, gdy zostanie ona ponownie uruchomiona w historii zadań jest wyczyszczone. Stałe rekordu historii zadania skonfigurować swoją maszynę Wirtualną jako kontekst obliczeniowy w Azure Machine learning, następnie prześlij zadanie usługi Azure Machine Learning (Wybieranie maszyny Wirtualnej jako kontekst obliczeniowy).