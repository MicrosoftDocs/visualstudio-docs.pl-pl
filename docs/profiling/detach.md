---
title: Odłączyć | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b151e3ede34d0c8fa3a863d7a4e7474431ae6f4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777393"
---
# <a name="detach"></a>Detach
VsPerfCmd.exe **Detach** Opcja odłącza profiler z określonych procesów lub wszystkich procesów, jeśli nie są określone. Profilowanie musi zostać zainicjowane przy użyciu metody pobierania próbek.

 Profilowanie rozpoczęte z opcjami **Uruchom** lub **Dołącz** można odłączyć za pomocą **programu Detach**. Profiler można ponownie sattched za pomocą kolejnych **polecenia Dołącz.**

 **Odłączanie** nie zamyka pliku danych profilowania. Użyj opcji **Zamykanie,** aby zakończyć profilowanie i zamknąć plik danych.

> [!NOTE]
> Jeśli opcja **Start** została określona za pomocą opcji **Crosssession,** wszystkie wywołania **vsperfcmd /Attach** lub **VSPerfCmd /Detach** muszą również określać **crosssession**.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametry
 `PIDs|ProcessNames``PID` - System numeryczny identifer jednego lub więcej procesów.

 `ProcessNames`- nazwę procesu. Jeśli wiele wystąpień nazwanego procesu są uruchomione, wyniki są nieprzewidywalne.

 Oddziel wiele procesów przecinkami.

 Jeśli nie określono procesu, profiler jest odłączony od wszystkich profilowanych procesów.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje **VSPerfCmd** można łączyć z opcją **Dołącz** w jednym wierszu polecenia.

 **Crosssession (krzyżyk)** Umożliwia profilowanie aplikacji w sesjach innych niż sesja logowania. Wymagane, jeśli opcja **Start** została określona za pomocą opcji **Crosssession.**

## <a name="example"></a>Przykład
 W tym przykładzie polecenie **Odłącz** zawiesza profilowanie, a polecenie **Shutdown** zamyka plik danych profilera.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
