---
title: QueryCounters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 501818d000b2db69b0744649d8e4a472cb87a55b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627717"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** opcji Wyświetla liczniki wydajności procesora CPU (sprzęt), które są dostępne na komputerze.

 **QueryCounters** musi być jedyną opcją, w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="remarks"></a>Uwagi
 Korzystając z metody instrumentacji, program profilujący może zbierać wartości co najmniej jeden liczniki wydajności procesora CPU w poszczególnych zdarzeń zbierania danych. Gdy używana jest metoda profilowania próbkowanie, można określić jedno zdarzenie licznika i liczbę wystąpień zdarzeń ma być używany jako interwał próbkowania.

 Różnych procesorów ujawnić różne liczniki wydajności procesora CPU. Program profilujący definiuje zestaw ogólnych liczniki, które mogą być używane na prawie wszystkie procesory w systemie. **QueryCounters** opcja list zarówno nazwy liczników ogólny i nazwy liczników, które są specyficzne dla procesora.

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)