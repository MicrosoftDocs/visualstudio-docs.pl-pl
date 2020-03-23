---
title: 'Jak: Zbieranie danych licznika systemu Windows | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c85187fd54d61fdf40956c8aee3c0a222d95a313
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776322"
---
# <a name="how-to-collect-windows-counter-data"></a>Jak: Zbieranie danych licznika systemu Windows

Liczniki systemu Windows to liczniki wydajności systemu, które mogą być zbierane w ustalonych odstępach czasu podczas profilowania. W widoku Znaczniki raportu Narzędzia profilowania wiersz jest oznaczony jako **AutoMark** dla każdego interwału zbierania. Wiersz zawiera kolumny opisujące wartości licznika wydajności w tym przedziale. Aby ograniczyć analizę do okresu między dwoma określonymi znacznikami, zaznacz znaczniki, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Filtruj według** > **znaczników** z menu skrótów.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Aby zebrać dane licznika systemu Windows

1. W Eksploratorze wydajności kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki systemu Windows i wybierz polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij pozycję **Liczniki systemu Windows**.

3. Zaznacz pole wyboru **Zbieranie liczników systemu Windows.**

4. W polu **tekstowym Interwał kolekcji (ms)** wpisz przedział czasu.

5. Wybierz kategorię z listy rozwijanej **Kategoria licznika.**

6. Wybierz wystąpienie z listy rozwijanej **Wystąpienie.**

7. Wybierz liczniki, których chcesz użyć podczas profilowania aplikacji.

8. Kliknij przycisk **Zastosuj.**

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[Właściwości](../profiling/performance-session-properties.md)
sesji[procesora CPU i liczniki systemu Windows](../profiling/cpu-and-windows-counters.md)
