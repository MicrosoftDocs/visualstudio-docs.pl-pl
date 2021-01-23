---
title: PF | Microsoft Docs
description: Dowiedz się, jak opcja VSPerfCmd.exe PF ustawia zdarzenie profilowania, które jest próbkowane na błędy stron i zmienia liczbę błędów stron w interwale próbkowania.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b920b641a7bfc4583af7b0ec5a9692a25c19adb5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719555"
---
# <a name="pf"></a>PF
Opcja *VSPerfCmd.exe* **PF** ustawia zdarzenie profilowania, które jest próbkowane do błędów strony i opcjonalnie zmienia liczbę błędów stron w interwale próbkowania z wartości domyślnej 10.

> [!NOTE]
> Nie można używać **PF** w systemach 64-bitowych.

**PF** można użyć tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** lub **dołączania** .

 Domyślnie zdarzenie próbkowania jest ustawione na niezatrzymane cykle zegara procesora, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF**, **sys** i **Counter** umożliwiają ustawienie interwału próbkowania i próbkowania. Opcja **GC** zbiera dane pamięci .NET dla każdego zdarzenia alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.

 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, który zawiera opcję **uruchamiania** lub **dołączania** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events` Wartość całkowita określająca liczbę zdarzeń błędów stron w interwale próbkowania. Jeśli `Events` nie jest określony, interwał jest ustawiony na wartość 10.

## <a name="required-options"></a>Wymagane opcje
 **PF** można określić tylko w wierszu polecenia, który zawiera jedną z następujących opcji.

 **Uruchom:** `AppName` Uruchamia Profiler i aplikację określoną przez nazwa_aplikacji.

 **Dołącz:** `PID` Dołącza Profiler do procesu określonego przez nazwa_aplikacji.

## <a name="invalid-options"></a>Nieprawidłowe opcje
 Nie można określić następujących opcji w tym samym wierszu polecenia co **PF**.

 **Czasomierz**[**:** `Cycles` ] ustawia zdarzenie próbkowania na cykle zegara procesora i opcjonalnie ustawia interwał próbkowania na `Cycles` . Domyślny interwał czasomierza to 10 000 000.

 **Sys**[**:** `Events` ] ustawia zdarzenie próbkowania dla wywołań z profilowanej aplikacji do jądra systemu operacyjnego (systemowe) i opcjonalnie ustawia interwał próbkowania na `Events` . Domyślny interwał sys to 10.

 **Licznik:** `Name` [ `,Reload` [ `,FriendlyName` ]] Ustawia zdarzenie próbkowania na licznik wydajności procesora CPU określony przez `Name` i ustawia interwał próbkowania na `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] zbiera dane pamięci platformy .NET. Domyślnie (**alokacja**) dane są zbierane przy każdym zdarzeniu przydziału pamięci. Gdy określono parametr **okresu istnienia** , dane są również zbierane przy każdym zdarzeniu odzyskiwania pamięci.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak ustawić zdarzenie przykładu profilowania na błędy stron i ustawić interwał próbkowania na 20 błędów stron.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
