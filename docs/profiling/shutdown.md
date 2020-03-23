---
title: Zamykanie systemu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778287"
---
# <a name="shutdown"></a>Shutdown
**Shutdown** Opcja czeka na każdy aktualnie profilowany proces do końca lub odłączyć, a następnie wyłącza profiler i zamyka plik danych profilowania. **Shutdown** Opcja musi być ostatnim poleceniem przebiegu profilowania.

 Jeśli parametr limit czasu nie jest określony, **shutdown** opcja czeka przez czas nieokreślony. Jeśli określono parametr limit czasu, opcja zwraca po określonej liczbie sekund bez wyłączania profilera lub zamykania pliku danych.

 Opcja **Zamykanie** musi być jedyną opcją określoną w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametry
`Timeout`
- (Opcjonalnie) Jeśli jest określony, opcja zwraca po określonej liczbie sekund bez wyłączania profilera lub zamykania pliku danych profilowania.

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
