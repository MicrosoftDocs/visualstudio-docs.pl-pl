---
title: Licznik | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e2f1684257ed39560fa0ea049d3296a6e45cdd7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779483"
---
# <a name="counter"></a>Licznik
Opcja **licznik** zbiera dane z liczników wydajności procesora (sprzętu).

- W przypadku korzystania z metody profilowania próbkowania **licznik** Określa licznik wydajności on-Chip i liczbę zdarzeń licznika, które mają być używane jako interwał próbkowania. Przy użyciu próbkowania można określić tylko jeden licznik.

- W przypadku korzystania z metody profilowania Instrumentacji liczba zdarzeń licznika, które wystąpiły w interwale między poprzednimi a bieżącymi zdarzeniami kolekcji, jest wyświetlana jako osobne pola w raportach profilera. W przypadku korzystania z Instrumentacji można określić wiele opcji **licznika** .

  Każdy typ procesora ma swój własny zestaw liczników wydajności sprzętu. Profiler definiuje zestaw ogólnych liczników wydajności, które są wspólne dla niemal wszystkich procesorów. Aby wyświetlić listę liczników ogólnych i specyficznych dla procesora na komputerze, użyj polecenia VSPerfCmd **QueryCounters** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametry
 `Name` nazwę licznika. Użyj opcji **/QueryCounters** VSPerfCmd. exe, aby wyświetlić listę nazw dostępnych liczników na komputerze.

 `Reload` liczbę zdarzeń licznika w interwale próbkowania. Nie należy używać z metodą Instrumentacji.

 `FriendlyName` (opcjonalnie) ciąg, który ma zostać użyty zamiast `Name` w nagłówkach kolumn w raportach i widokach profilera.

## <a name="required-options"></a>Wymagane opcje
 Opcji Counter można używać tylko z jedną z następujących opcji:

 **Uruchom:** `Trace` inicjuje profiler, aby użyć metody instrumentacji.

 **Uruchom:** `AppName` uruchamia określoną aplikację i Profiler. Profiler musi być zainicjowany, aby można było używać metody próbkowania.

 **Dołącz:** `PID` uruchamia Profiler i dołącza go do procesu określonego przez identyfikator procesu. Profiler musi być zainicjowany, aby można było używać metody próbkowania.

## <a name="example"></a>Przykład
 Przykładowa Metoda próbkowania demonstruje sposób próbkowania aplikacji w każdym 1000 wystąpieniach ogólnego licznika profilera NonHaltedCycles.

 W przykładzie metody instrumentacji pokazano, jak zainicjować profiler, aby zbierać zdarzenia licznika L2InstructionFetches. Nazwa licznika L2InstructionFetches jest specyficzna dla procesora.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
