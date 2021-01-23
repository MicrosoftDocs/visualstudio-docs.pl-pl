---
title: Sys (VSPerfCmd) | Microsoft Docs
description: Dowiedz się, jak opcja VSPerfCmd.exe sys ustawia zdarzenie profilowania, które jest próbkowane do zdarzeń wywołania systemowego.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5e8090a39426455e0f6d877c26a7f0a50f00f10c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719763"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
Opcja *VSPerfCmd.exe* **sys** ustawia zdarzenie profilowania, które jest próbkowane do zdarzeń wywołania systemowego (wywołania funkcji z profilowanej aplikacji do systemu operacyjnego) i opcjonalnie zmienia liczbę wywołań systemowych w interwale próbkowania z wartości domyślnej 10.

 **Sys** można używać tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** lub **dołączania** .

 Domyślnie zdarzenie próbkowania profilera jest ustawione na cykle zegara procesora, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF**, **sys** i **Counter** umożliwiają ustawienie zdarzenia próbkowania i interwału próbkowania. Opcja **GC** zbiera dane pamięci .NET dla każdego zdarzenia alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.

 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia zawierającym opcję **uruchamiania** lub **dołączania** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events` Wartość całkowita określająca liczbę zdarzeń wywołań systemu w interwale próbkowania. Jeśli `Events` nie jest określony, interwał jest ustawiony na wartość 10.

## <a name="required-options"></a>Wymagane opcje
 **Sys** wymaga jednej z następujących opcji.

 **Uruchom:** `AppName` Uruchamia program profilujący i aplikację określoną przez `AppName` .

 **Dołącz:** `PID` Dołącza Profiler do procesu określonego przez `PID` .

## <a name="invalid-options"></a>Nieprawidłowe opcje
 Nie można określić następujących opcji w tym samym wierszu polecenia co **sys**.

 **PF**[**:** `Events` ] ustawia zdarzenie próbkowania na błędy stron i opcjonalnie ustawia interwał próbkowania na `Events` . Domyślny interwał PF wynosi 10.

 **Czasomierz**[**:** `Cycles` ] ustawia zdarzenie próbkowania na cykle zegara procesora i opcjonalnie ustawia interwał próbkowania na `Cycles` . Domyślny interwał czasomierza to 10 000 000.

 **Licznik:** `Name` [ `,Reload` [ `,FriendlyName` ]] Ustawia zdarzenie próbkowania na licznik wydajności procesora CPU określony przez `Name` i ustawia interwał próbkowania na `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] zbiera dane pamięci platformy .NET. Domyślnie (**alokacja**) dane są zbierane przy każdym zdarzeniu przydziału pamięci. Gdy określono parametr **okresu istnienia** , dane są również zbierane przy każdym zdarzeniu odzyskiwania pamięci.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak ustawić zdarzenie próbkowania profilera na wywołania systemowe i jak ustawić interwał próbkowania na 20 wywołań na próbkę.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
