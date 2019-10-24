---
title: Wyświetl ostatnie zadania
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 79b396946666077dcdedb3ee2a5ab891c2bb4fb8
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777395"
---
# <a name="view-recent-job-performance-and-details"></a>Wyświetl ostatnią wydajność i szczegóły zadania

Po przesłaniu zadań można wyświetlić listę zadań, aby zobaczyć ich stan, czas trwania i inne.

1. W **Eksplorator serwera**rozwiń określony kontekst obliczeniowy.
2. Kliknij dwukrotnie pozycję **zadania**.
3. Zostanie wyświetlona lista zadań przesłanych do tego kontekstu obliczeniowego.
4. Wybierz określone **zadanie** na liście, aby wyświetlić szczegóły.

![Monitorowanie zadań](media/job-details/monitor-jobs.png)

> Historia zadań przesłana do maszyn wirtualnych systemu Linux jest przechowywana na maszynie wirtualnej w katalogu/tmp. W związku z tym po każdym ponownym uruchomieniu historia zadania jest czyszczona. W przypadku stałego rekordu historii zadania Skonfiguruj maszynę wirtualną jako kontekst obliczeniowy w usłudze Azure Machine Learning, a następnie Prześlij zadanie do Azure Machine Learning (Wybierz maszynę wirtualną jako kontekst obliczeń).
