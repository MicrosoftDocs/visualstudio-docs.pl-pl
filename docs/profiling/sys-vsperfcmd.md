---
title: Sys (VSPerfCmd) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 435393ac536eb70f2f3f6d38b16eaab645848704
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778183"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
Opcja *VSPerfCmd.exe* **Sys** ustawia zdarzenie profilowania, które jest próbkowane do zdarzeń wywołań systemowych (wywołania funkcji z profilowanego aplikacji do systemu operacyjnego) i opcjonalnie zmienia liczbę wywołań systemowych w interwale próbkowania z domyślnego 10.

 **Sys** może być używany tylko w wierszu polecenia, który zawiera również **uruchom** lub **Dołącz** opcji.

 Domyślnie zdarzenie próbkowania profilera jest ustawione na cykle zegara procesora, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF,** **Sys**i **Counter** umożliwiają ustawienie zdarzenia próbkowania i interwału próbkowania. Opcja **GC** zbiera dane pamięci .NET przy każdym zdarzeniu alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.

 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, który zawiera opcję **Uruchom** lub **Dołącz.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events`Wartość całkowita określająca liczbę zdarzeń wywołań systemowych w interwale próbkowania. Jeśli `Events` nie zostanie określony, interwał jest ustawiony na 10.

## <a name="required-options"></a>Wymagane opcje
 **Sys** wymaga jednej z następujących opcji.

 **Uruchom:** `AppName` Uruchamia profiler i aplikację `AppName`określoną przez .

 **Dołącz:** `PID` Dołącza profiler do procesu `PID`określonego przez .

## <a name="invalid-options"></a>Nieprawidłowe opcje
 W tym samym wierszu polecenia co **Sys**nie można określić następujących opcji.

 **PF**[**:**`Events`] Ustawia zdarzenie próbkowania na błędy `Events`strony i opcjonalnie ustawia interwał próbkowania na . Domyślny interwał PF wynosi 10.

 **Timer**[**:**`Cycles`] Ustawia zdarzenie próbkowania na cykle `Cycles`zegara procesora i opcjonalnie ustawia interwał próbkowania na . Domyślny interwał czasomierza wynosi 10 000 000.

 **Licznik:** `Name``,Reload`[`,FriendlyName`[ ]] Ustawia zdarzenie próbkowania `Name` na licznik wydajności `Reload`procesora określony przez i ustawia interwał próbkowania na .

 **GC**[**:**{ Okres **istnienia****alokacji**&#124;}] Zbiera dane pamięci .NET. Domyślnie **(Alokacja**) dane są zbierane przy każdym zdarzeniu alokacji pamięci. Po określeniu **parametru Lifetime** dane są również zbierane w każdym przypadku wyrzucania elementów bezużytecznych.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak ustawić zdarzenie próbkowania profilera do wywołań systemowych i jak ustawić interwał próbkowania do 20 wywołań na próbkę.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
