---
title: Wyświetl ostatnie zadania
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 2e404d6a258ebb480b3eb02e615097872714db03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371550"
---
# <a name="view-recent-job-performance-and-details"></a>Wyświetl ostatnią wydajność i szczegóły zadania

Po przesłaniu zadań można wyświetlić listę zadań, aby zobaczyć ich stan, czas trwania i inne.

1. W **Eksplorator serwera**rozwiń określony kontekst obliczeniowy.
2. Kliknij dwukrotnie pozycję **Zadania**.
3. Zostanie wyświetlona lista zadań przesłanych do tego kontekstu obliczeniowego.
4. Wybierz określone **zadanie** na liście, aby wyświetlić szczegóły.

![Monitorowanie zadań](media/job-details/monitor-jobs.png)

> Historia zadań przesłana do maszyn wirtualnych systemu Linux jest przechowywana na maszynie wirtualnej w katalogu/tmp. W związku z tym po każdym ponownym uruchomieniu historia zadania jest czyszczona. W przypadku stałego rekordu historii zadania Skonfiguruj maszynę wirtualną jako kontekst obliczeniowy w usłudze Azure Machine Learning, a następnie Prześlij zadanie do Azure Machine Learning (Wybierz maszynę wirtualną jako kontekst obliczeń).
