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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9fc551fd84197e936ef0f6069ecbc4beaecdf25a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961377"
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
[Właściwości sesji wydajności](../profiling/performance-session-properties.md)  
[Liczniki procesora CPU i systemu Windows](../profiling/cpu-and-windows-counters.md)