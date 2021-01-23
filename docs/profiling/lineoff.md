---
title: LineOff | Microsoft Docs
description: Dowiedz się, jak opcja VSPerfCmd LineOff wyłącza zbieranie danych o numerach wierszy, gdy do uruchomienia aplikacji jest używany VSPerfCmd.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45ec3592049e00d6a492c489e8fb60254003ac6d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721414"
---
# <a name="lineoff"></a>LineOff
Domyślnie profiler zbiera numer wiersza kodu źródłowego i dane przesunięcia numerów wierszy przy użyciu metody profilowania próbkowania. Opcja VSPerfCmd **LineOff** wyłącza zbieranie danych o numerach wierszy, gdy do uruchomienia aplikacji jest używany VSPerfCmd. Dane profilowania są zbierane do poziomu funkcji po określeniu **LineOff** .

 Opcji **LineOff** można użyć tylko w przypadku opcji **uruchamiania** i tylko wtedy, gdy profiler został zainicjowany do próbkowania przy użyciu polecenia **Start**:**Sample** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 Opcji **LineOff** można użyć tylko w wierszu polecenia zawierającym opcję **uruchamiania** .

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.

## <a name="example"></a>Przykład
 Ten przykład uruchamia aplikację i Profiler i wyłącza próbkowanie na poziomie wiersza.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
