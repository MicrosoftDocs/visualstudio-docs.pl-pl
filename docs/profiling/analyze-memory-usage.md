---
title: Analizowanie użycia pamięci
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73fc70231e9756bf20f90f5873a0241c5f29bdd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315566"
---
# <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci
Użyj zintegrowane z debugerem **użycie pamięci** narzędzie do diagnostyki do umożliwia znajdowanie przecieków pamięci i wykorzystania pamięci nieefektywne. Narzędzie umożliwia wykorzystanie pamięci, zapoznasz się z co najmniej jeden *migawek* sterty pamięci zarządzanego i natywnego. Można zbierać migawki aplikacji platformy .NET, ASP.NET, Tryb natywny lub mieszany (.NET i natywny).

-   Możesz analizować pojedynczej migawki zrozumieć konsekwencje typów obiektów na wykorzystanie pamięci i znaleźć kod w swojej aplikacji, która używa pamięci nieefektywne.

-   Można również porównać (różnica) dwiema migawkami znajdowanie obszarów w kodzie aplikacji, które powodują wykorzystanie pamięci zwiększyć wraz z upływem czasu.

Aby uzyskać szczegółowe instrukcje, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md) samouczka.  Obecnie do mierzenia użycia pamięci dla aplikacji platformy .NET Core, należy użyć narzędzia w debugerze. W przypadku innych aplikacji zarządzanych i natywnych można użyć narzędzia, z lub bez w debugerze.

Można użyć narzędzi profilowania bez debugera, system Windows 7 lub nowszy. Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno).

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizowanie użycia Procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blogu Visual C++: Profilowanie pamięci w programie Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)