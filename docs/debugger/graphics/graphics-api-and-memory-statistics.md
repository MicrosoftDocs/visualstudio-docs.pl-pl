---
title: Interfejs API grafiki i statystyka pamięci | Microsoft Docs
description: Zapoznaj się z narzędziami statystyki interfejsu API grafiki i statystyk pamięci, które zawierają informacje na temat użycia interfejsu API Direct3D i wykorzystania pamięci procesora GPU dla różnych zasobów.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08c9f518f6d56f2ec211ef494da3890a56bf1369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882300"
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

W kolumnie **alokacja procesora GPU** wyświetlana jest ilość pamięci używanej w zdarzeniu wyświetlanym w kolumnie **zdarzenie** .  Możesz również wybrać ikonę Obserwuj ikonę ![ czujki, ](media/gfx_watch.png) Aby wyświetlić [historię zasobów](graphics-event-list.md#resource-history) dla wybranego zdarzenia.

Podobnie jak w przypadku narzędzia Statystyka interfejsu API można kliknąć prawym przyciskiem myszy w oknie, aby skopiować wszystkie dane jako woluminy CSV, które można wkleić do programu Excel w celu przeprowadzenia dalszej analizy.

## <a name="see-also"></a>Zobacz też
- [Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)
- [Historia zasobów](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->