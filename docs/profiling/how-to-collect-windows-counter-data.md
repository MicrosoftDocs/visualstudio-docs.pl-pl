---
title: 'Instrukcje: Zbieranie danych licznika Windows | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 730345edb42ff3d14608bdcce91bc7b97c4bb478
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973854"
---
# <a name="how-to-collect-windows-counter-data"></a>Instrukcje: Zbieranie danych licznika Windows

Liczniki Windows są liczniki wydajności systemu, które mogą być zbierane podczas profilowania w ustalonych odstępach czasu. W widoku znaczniki raportu narzędzi profilowania z wiersza jest oznaczona etykietą **AutoMark** dla każdego interwału zbierania. Wiersz zawiera kolumny, które opisują wartości licznika wydajności, w tym odstępach czasu. Aby ograniczyć analizę do okresu czasu między dwoma określonymi znacznikami, zaznacz znaki, kliknij prawym przyciskiem myszy, a następnie wybierz **Filtruj wg** > **znaczniki** z menu skrótów.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Aby zebrać dane Windows

1. W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki Windows, a następnie wybierz pozycję **właściwości**.

2. W **stron właściwości**, kliknij przycisk **liczniki Windows**.

3. Wybierz **zbierania liczników Windows** pole wyboru.

4. W **interwał zbierania (MS)** tekstu wpisz przedział czasu.

5. Wybierz kategorię z **kategorii licznika** listy rozwijanej.

6. Wybierz domyślne wystąpienie z **wystąpienia** listy rozwijanej.

7. Wybierz liczniki, które chcesz użyć podczas profilowania aplikacji.

8. Kliknij przycisk **zastosowania.**

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
[właściwości sesji wydajności](../profiling/performance-session-properties.md)
[liczniki procesora CPU i Windows](../profiling/cpu-and-windows-counters.md)