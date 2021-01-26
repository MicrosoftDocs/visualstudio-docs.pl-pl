---
title: Zbieranie danych licznika systemu Windows | Microsoft Docs
description: Liczniki systemu Windows są używane w profilowania Instrumentacji. Dowiedz się, jak zbierać dane liczników systemu Windows oraz jak ograniczyć analizę do jednego interwału kolekcji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ccbdf9afb843c8bdac2d904dc22375a4a69e733a
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801046"
---
# <a name="how-to-collect-windows-counter-data"></a>Instrukcje: zbieranie danych licznika systemu Windows

Liczniki systemu Windows są licznikami wydajności systemu, które można zbierać w ustalonych odstępach czasu podczas profilowania. W widoku znaczniki raportu narzędzia profilowania wiersz ma etykietę **autoznaczników** dla każdego interwału kolekcji. Wiersz zawiera kolumny, które opisują wartości licznika wydajności w tym interwale. Aby ograniczyć analizę do okresu między dwoma określonymi znakami, zaznacz znaczniki, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Filtruj według**  >  **znaczników** z menu skrótów.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Aby zebrać dane liczników systemu Windows

1. W Eksplorator wydajności kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki systemu Windows, a następnie wybierz pozycję **Właściwości**.

2. Na **stronie właściwości** kliknij pozycję **liczniki systemu Windows**.

3. Zaznacz pole wyboru **Zbierz liczniki systemu Windows** .

4. W polu tekstowym **Interwał kolekcji (MS)** wpisz przedział czasu.

5. Wybierz kategorię z listy rozwijanej **Kategoria licznika** .

6. Wybierz wystąpienie z listy rozwijanej **wystąpienie** .

7. Wybierz liczniki, które mają być używane podczas profilowania aplikacji.

8. Kliknij przycisk **Zastosuj.**

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [Właściwości](../profiling/performance-session-properties.md) 
 sesji wydajności [Liczniki procesora i systemu Windows](../profiling/cpu-and-windows-counters.md)
