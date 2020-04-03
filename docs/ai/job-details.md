---
title: Wyświetlanie ostatnich ofert pracy
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 55865e4907175664e8a8bfb8a813ff8d02c85b69
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638429"
---
# <a name="view-recent-job-performance-and-details"></a>Wyświetlanie najnowszych wyników i szczegółów zadania

Po przesłaniu zadań można wyświetlić listę zadań, aby wyświetlić ich stan, czas trwania i inne.

1. W **Eksploratorze serwerów**rozwiń określony kontekst obliczeniowy.
2. Kliknij dwukrotnie pozycję **Zadania**.
3. Zostanie wyświetlona lista zadań przesłanych do tego kontekstu obliczeniowego.
4. Wybierz określone **zadanie** na liście, aby wyświetlić szczegóły.

![monitorowanie zadań](media/job-details/monitor-jobs.png)

> Historia zadań przesłana do maszyn wirtualnych z systemem Linux jest przechowywana na maszynie wirtualnej w katalogu /tmp. W związku z tym po ponownym uruchomieniu historia zadań jest czyszczona. Aby uzyskać stały rekord historii zadań, należy skonfigurować maszynę wirtualną jako kontekst obliczeniowy w usłudze Azure Machine Learning, a następnie prześlij zadanie do usługi Azure Machine Learning (wybierając maszynę wirtualną jako kontekst obliczeniowy).
