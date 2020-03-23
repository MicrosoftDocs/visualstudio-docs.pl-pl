---
title: Licznik | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779483"
---
# <a name="counter"></a>Licznik
**Opcja Licznik** zbiera dane z liczników wydajności procesora (sprzętu).

- Podczas korzystania z metody profilowania próbkowania **Counter** określa licznik wydajności na chipie i liczbę zdarzeń licznika do użycia jako interwał próbkowania. Można określić tylko jeden licznik podczas korzystania z próbkowania.

- Podczas korzystania z metody profilowania instrumentacji liczba zdarzeń licznika, które wystąpiły w interwale między poprzednimi i bieżącymi zdarzeniami zbierania są wyświetlane jako oddzielne pola w raportach profilera. Wiele opcji **licznika** można określić podczas korzystania z instrumentacji.

  Każdy typ procesora ma swój własny zestaw liczników wydajności sprzętu. Profiler definiuje zestaw ogólnych liczników wydajności, które są wspólne dla prawie wszystkich procesorów. Aby wyświetlić listę liczników ogólnych i specyficznych dla procesora na komputerze, należy użyć polecenia VSPerfCmd **QueryCounters.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametry
 `Name`Nazwa licznika. Użyj opcji VSPerfCmd.exe **/QueryCounters,** aby wyświetlić listę nazw dostępnych liczników na komputerze.

 `Reload`Liczba zdarzeń licznika w interwale próbkowania. Nie stosować z metodą oprzyrządowania.

 `FriendlyName`(Opcjonalnie) Ciąg do użycia zamiast `Name` nagłówków kolumn raportów i widoków profilera.

## <a name="required-options"></a>Wymagane opcje
 Opcji Licznik można używać tylko z jedną z następujących opcji:

 **Start:** `Trace` Inicjuje profiler, aby użyć metody instrumentacji.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i profiler. Profiler musi być zainicjowany, aby użyć metody pobierania próbek.

 **Dołącz:** `PID` Uruchamia profiler i dołącza go do procesu określonego przez identyfikator procesu. Profiler musi być zainicjowany, aby użyć metody pobierania próbek.

## <a name="example"></a>Przykład
 Przykład metody próbkowania pokazuje, jak próbkować aplikację co 1000 wystąpień ogólnego licznika profilera NonHaltedCycles.

 Przykład metody instrumentacji pokazuje, jak zainicjować profiler do zbierania L2InstructionFetches zdarzeń licznika. Nazwa licznika L2InstructionFetches jest specyficzna dla procesora.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
