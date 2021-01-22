---
title: Odłącz | Microsoft Docs
description: Użyj opcji Odłącz VSPerfCmd.exe, aby odłączyć Profiler od określonego procesu lub ze wszystkich procesów, jeśli żaden z nich nie zostanie określony.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45225e4478b0a1a3cddc7f74ae223c437bf4226e
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686600"
---
# <a name="detach"></a>Odłącz
Opcja **Odłączania** VSPerfCmd.exe rozłącza Profiler od określonych procesów lub wszystkich procesów, jeśli nie zostały określone. Profilowanie musi zostać zainicjowane przy użyciu metody próbkowania.

 Profilowanie uruchomione przy użyciu opcji **Uruchom** lub **dołączania** można rozłączyć z **odłączeniem**. Można ponownie dołączyć Profiler przy użyciu kolejnych poleceń **Attach** .

 **Odłącz** nie zamyka pliku danych profilowania. Użyj opcji **zamykania** , aby zakończyć profilowanie i zamknąć plik danych.

> [!NOTE]
> Jeśli opcja **Start** została określona przy użyciu opcji **CrossSession** , wszystkie wywołania **VSPerfCmd/Attach** lub **VSPerfCmd/detach** muszą również określać **CrossSession**.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametry
 `PIDs|ProcessNames``PID`-Identyfikator systemowy z co najmniej jednym procesem.

 `ProcessNames` -Nazwa procesu. Jeśli jest uruchomionych wiele wystąpień nazwanego procesu, wyniki są nieprzewidywalne.

 Rozdziel wiele procesów przecinkami.

 Jeśli żaden proces nie zostanie określony, profiler zostanie odłączony ze wszystkich profilowanych procesów.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje **VSPerfCmd** można łączyć z opcją **Attach** w pojedynczym wierszu polecenia.

 **CrossSession** Włącza Profilowanie aplikacji w sesjach innych niż sesja logowania. Wymagane, jeśli opcja **Start** została określona z opcją **CrossSession** .

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
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
