---
title: QueryCounters | Microsoft Docs
description: Dowiedz się, jak opcja QueryCounters wyświetla listę liczników wydajności procesora CPU (sprzętu), które są dostępne na komputerze.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d33b6fe42f786218bf78825a356a25edff2b31ae
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720439"
---
# <a name="querycounters"></a>QueryCounters
Opcja **QueryCounters** wyświetla listę liczników wydajności procesora CPU (sprzętu), które są dostępne na komputerze.

 **QueryCounters** musi być jedyną opcją w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="remarks"></a>Uwagi
 Gdy korzystasz z metody instrumentacji, profiler może zbierać wartości z co najmniej jednego licznika wydajności procesora CPU podczas każdego zdarzenia zbierania danych. W przypadku korzystania z metody profilowania próbkowania można określić jedno zdarzenie licznika oraz liczbę wystąpień zdarzeń, które mają być używane jako interwał próbkowania.

 Różne procesory uwidaczniają różne liczniki wydajności procesora CPU. Profiler definiuje zestaw liczników ogólnych, które mogą być używane na prawie wszystkich procesorach. Opcja **QueryCounters** wyświetla nazwy ogólnych liczników i nazwy liczników, które są specyficzne dla procesora.

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
