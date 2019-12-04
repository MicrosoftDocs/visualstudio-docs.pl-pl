---
title: Zamknij | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 89a08808387067b934bfd826feb2dcfbcf949aab
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778287"
---
# <a name="shutdown"></a>Zamykanie
Opcja **zamykania** czeka na zakończenie lub odłączenie aktualnie profilowanego procesu, a następnie wyłącza Profiler i zamyka plik danych profilowania. Opcja **Shutdown** musi być ostatnim poleceniem przebiegu profilowania.

 Jeśli parametr limitu czasu nie zostanie określony, opcja **zamykania** czeka na czas nieokreślony. Jeśli określono parametr limitu czasu, opcja wraca po określonej liczbie sekund bez wyłączania profilera lub zamykania pliku danych.

 Opcja **Shutdown** musi być jedyną opcją określoną w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametry
`Timeout`
- Obowiązkowe Jeśli ta opcja jest określona, funkcja wraca po określonej liczbie sekund bez wyłączania profilera lub zamykania pliku danych profilowania.

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
