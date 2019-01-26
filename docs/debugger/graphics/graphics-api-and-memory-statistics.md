---
title: Interfejsu API grafiki i statystyki pamięci | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e0c1ed6e2fdd461b0fdf502c01089aeafd9a87cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925633"
---
# <a name="graphics-api-and-memory-statistics"></a>Interfejsu API grafiki i statystyki pamięci
<!-- VERSIONLESS --> Program Visual Studio 2017 i lepsze wsparcie Statystyka interfejsu API grafiki i narzędzia statystyki pamięci.  Te dwa narzędzia umożliwiają wyświetlanie różnych bity informacji na użycie interfejsu API Direct3D, a także użycie pamięci procesora GPU z różnych zasobów.

## <a name="graphics-api-statistics"></a>Statystyka interfejsu API grafiki
Statystyka interfejsu API grafiki w programie Visual Studio Graphics Diagnostics umożliwia wyświetlanie wszystkich połączeń Direct3D, które zostały wprowadzone i liczba każde wywołanie.  Zaznacz, aby wyświetlić okno **Widok > Statystyka interfejsu API** elementu menu.

![Statystyka interfejsu API](media/gfx_diag_api_statistics.png)

To narzędzie może być przydatna w odnajdywania co wywołań programu DirectX, że nie może realizować możesz lub wywołania, które wykonujesz, zbyt często.

Możesz kliknąć prawym przyciskiem myszy w oknie danych Kopiuj wszystko jako plik CSV, który można wkleić do podobny do programu Excel w celu dalszej analizy.

## <a name="memory-statistics"></a>Statystyka pamięci
To narzędzie spowoduje wyświetlenie ilości pamięci, sterownik karty graficznej jest przydzielanie zasobów tworzenie w ramce.  Aby wyświetlić to okno, wybierz **Widok > Statystyki pamięci** elementu menu.

![Statystyka pamięci](media/gfx_diag_memory_statistics.png)

**Przydział procesora GPU** ilość pamięci używanej przez zdarzenia wyświetlane w kolumnie jest wyświetlana **zdarzeń** kolumny.  Możesz również wybrać ikonę Obejrzyj ![ikona monitorowania](media/gfx_watch.png) do wyświetlania [Historia zasobów](graphics-event-list.md#resource-history) dla wybranego zdarzenia.

Podobnie jak w przypadku narzędzia Statystyka interfejsu API, możesz kliknąć prawym przyciskiem myszy w oknie danych Kopiuj wszystko jako plik CSV, który można wkleić do podobny do programu Excel w celu dalszej analizy.

## <a name="see-also"></a>Zobacz też  
[Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)   
[Historia zasobów](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->