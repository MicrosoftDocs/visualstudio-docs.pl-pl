---
title: z o.o. | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778417"
---
# <a name="pf"></a>PF
Opcja *VSPerfCmd.exe* **PF** ustawia zdarzenie profilowania, które jest próbkowany do błędów strony i opcjonalnie zmienia liczbę błędów strony w interwale próbkowania z domyślnego 10.

> [!NOTE]
> **PF** nie może być używany w systemach 64-bitowych.

**PF** może być używany tylko w wierszu polecenia, który zawiera również **uruchom** lub **Dołącz** opcji.

 Domyślnie zdarzenie próbkowania jest ustawione na cykle zegara procesora niezatrzymowane, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF,** **Sys**i **Counter** umożliwiają ustawienie zdarzenia próbkowania i interwału próbkowania. Opcja **GC** zbiera dane pamięci .NET przy każdym zdarzeniu alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.

 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, który zawiera opcję **Uruchom** lub **Dołącz.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events`Wartość całkowita określająca liczbę zdarzeń błędów strony w interwale próbkowania. Jeśli `Events` nie zostanie określony, interwał jest ustawiony na 10.

## <a name="required-options"></a>Wymagane opcje
 **Pf** można określić tylko w wierszu polecenia, który zawiera jedną z następujących opcji.

 **Uruchom:** `AppName` Uruchamia profiler i aplikacji określonych przez AppName.

 **Dołącz:** `PID` Dołącza profiler do procesu określonego przez AppName.

## <a name="invalid-options"></a>Nieprawidłowe opcje
 W tym samym wierszu polecenia co **PF**nie można określić następujących opcji.

 **Timer**[**:**`Cycles`] Ustawia zdarzenie próbkowania na cykle `Cycles`zegara procesora i opcjonalnie ustawia interwał próbkowania na . Domyślny interwał czasomierza wynosi 10 000 000.

 **Sys**[**:**`Events`] Ustawia zdarzenie próbkowania na wywołania z profilowanego aplikacji na jądro systemu operacyjnego (syscalls) i opcjonalnie ustawia interwał próbkowania na `Events`. Domyślny interwał Sys wynosi 10.

 **Licznik:** `Name``,Reload`[`,FriendlyName`[ ]] Ustawia zdarzenie próbkowania `Name` na licznik wydajności `Reload`procesora określony przez i ustawia interwał próbkowania na .

 **GC**[**:**{ Okres **istnienia****alokacji**&#124;}] Zbiera dane pamięci .NET. Domyślnie **(Alokacja**) dane są zbierane przy każdym zdarzeniu alokacji pamięci. Po określeniu **parametru Lifetime** dane są również zbierane w każdym przypadku wyrzucania elementów bezużytecznych.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak ustawić profilowanie przykładowe zdarzenie do błędów strony i ustawić interwał próbkowania do 20 błędów strony.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
