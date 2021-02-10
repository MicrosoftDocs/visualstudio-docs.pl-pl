---
title: QueryCounters | Microsoft Docs
description: Dowiedz się, jak opcja QueryCounters wyświetla listę liczników wydajności procesora CPU (sprzętu), które są dostępne na komputerze.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e93546c97b2ddec0e944314c51c87da05a725db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950172"
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

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
