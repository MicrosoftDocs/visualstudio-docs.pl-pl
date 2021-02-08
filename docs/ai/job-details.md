---
title: Wyświetl ostatnie zadania
description: Informacje o tym, że po przesłaniu zadań można wyświetlić listę zadań, aby zobaczyć ich stan, czas trwania itd.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 13d78913e0d5d708c5e75a80611ae9cc1c2f7366
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841435"
---
# <a name="view-recent-job-performance-and-details"></a>Wyświetl ostatnią wydajność i szczegóły zadania

Po przesłaniu zadań można wyświetlić listę zadań, aby zobaczyć ich stan, czas trwania i inne.

1. W **Eksplorator serwera** rozwiń określony kontekst obliczeniowy.
2. Kliknij dwukrotnie pozycję **Zadania**.
3. Zostanie wyświetlona lista zadań przesłanych do tego kontekstu obliczeniowego.
4. Wybierz określone **zadanie** na liście, aby wyświetlić szczegóły.

![Monitorowanie zadań](media/job-details/monitor-jobs.png)

> Historia zadań przesłana do maszyn wirtualnych systemu Linux jest przechowywana na maszynie wirtualnej w katalogu/tmp. W związku z tym po każdym ponownym uruchomieniu historia zadania jest czyszczona. W przypadku stałego rekordu historii zadania Skonfiguruj maszynę wirtualną jako kontekst obliczeniowy w usłudze Azure Machine Learning, a następnie Prześlij zadanie do Azure Machine Learning (Wybierz maszynę wirtualną jako kontekst obliczeń).
