---
title: Interfejs API grafiki i statystyka pamięci | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa808e76e6655c5d57108c923b19794d0398b80c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735574"
---
# <a name="graphics-api-and-memory-statistics"></a>Interfejs API grafiki i statystyka pamięci
<!-- VERSIONLESS -->
Program Visual Studio 2017 lub nowszy obsługuje narzędzia graficzne API Graphics i statystyka pamięci.  Te dwa narzędzia pozwalają przeglądać różne bity informacji o użyciu interfejsu API Direct3D, a także zużywać pamięć procesora GPU dla różnych zasobów.

## <a name="graphics-api-statistics"></a>Statystyka interfejsu API grafiki
Statystyka interfejsu API grafiki w programie Visual Studio Diagnostyka grafiki pozwala wyświetlić wszystkie wywołania Direct3D, które zostały wykonane, oraz liczbę każdego wywołania.  Aby wyświetlić okno, wybierz element menu **Statystyka interfejsu API >** .

![Statystyka interfejsu API](media/gfx_diag_api_statistics.png)

To narzędzie może być przydatne w odnalezieniu wywołań DirectX, które nie mogą zostać zrealizowane lub wywołania są zbyt często.

Możesz kliknąć prawym przyciskiem myszy w oknie, aby skopiować wszystkie dane jako wolumin CSV, które można wkleić do programu Excel w celu przeprowadzenia dalszej analizy.

## <a name="memory-statistics"></a>Statystyka pamięci
To narzędzie wyświetli ilość pamięci przydzielanej przez sterownik grafiki do zasobów tworzonych w ramce.  Aby wyświetlić to okno, wybierz element menu **Wyświetl statystykę pamięci >** .

![Statystyka pamięci](media/gfx_diag_memory_statistics.png)

W kolumnie **alokacja procesora GPU** wyświetlana jest ilość pamięci używanej w zdarzeniu wyświetlanym w kolumnie **zdarzenie** .  Możesz również wybrać ikonę czujki ![ikonę czujki](media/gfx_watch.png), aby wyświetlić [historię zasobów](graphics-event-list.md#resource-history) dla wybranego zdarzenia.

Podobnie jak w przypadku narzędzia Statystyka interfejsu API można kliknąć prawym przyciskiem myszy w oknie, aby skopiować wszystkie dane jako woluminy CSV, które można wkleić do programu Excel w celu przeprowadzenia dalszej analizy.

## <a name="see-also"></a>Zobacz także
- [Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)
- [Historia zasobów](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->