---
title: Zamknięcie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: deeb74e8e8763feb62b0cc21fcfbfbf3c6b220ca
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596701"
---
# <a name="shutdown"></a>Zamykanie
**Zamknięcia** opcji oczekuje żadnego obecnie profilowane procesu, aby zakończyć lub odłączyć, a następnie wyłącza profilera i zamyka plik danych profilowania. **Zamknięcia** opcja musi być ostatnie polecenie uruchomienia profilowania.

 Jeśli nie określono parametr limitu czasu, **zamknięcia** opcji w tym czasie czeka na czas nieokreślony. Jeśli określono parametr limitu czasu, opcja zwraca po określonej liczbie sekund bez konieczności wyłączania program profilujący lub zamykania pliku danych.

 **Zamknięcia** opcja musi być jedyną opcją, określone w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametry
 `Timeout`
 -   (Opcjonalnie) Jeśli zostanie określony, opcja zwraca po określonej liczbie sekund bez konieczności wyłączania program profilujący lub zamykania pliku danych profilowania.

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)