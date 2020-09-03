---
title: Zamknij | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64bad66491588178dc7d80655a8e517d6daed053
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330996"
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

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
