---
title: Liczniki zapytań | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 24379a720ccaa3405cbe5c127f3b8abaf12e49aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771912"
---
# <a name="querycounters"></a>QueryCounters
Opcja **QueryCounters** zawiera listę liczników wydajności procesora CPU (sprzętu), które są dostępne na komputerze.

 **QueryCounters** musi być jedyną opcją w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="remarks"></a>Uwagi
 Podczas korzystania z metody instrumentacji profiler można zbierać wartości jednego lub więcej liczników wydajności procesora CPU w każdym zdarzeniu zbierania danych. Podczas korzystania z metody profilowania próbkowania można określić jedno zdarzenie licznika i liczbę wystąpień zdarzeń, które mają być używane jako interwał próbkowania.

 Różne procesory ujawniają różne liczniki wydajności procesora. Profiler definiuje zestaw liczników ogólnych, które mogą być używane na prawie wszystkich procesorach. Opcja **QueryCounters** zawiera listę zarówno nazw liczników ogólnych, jak i nazw liczników specyficznych dla procesora.

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
