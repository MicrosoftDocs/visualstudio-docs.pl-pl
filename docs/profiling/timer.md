---
title: Zegar | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1bed2715421948385a5b7eb1ddbbac064f3288b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778118"
---
# <a name="timer"></a>Czasomierz
Opcja **czasomierza** *programu VSPerfCmd.exe* ustawia zdarzenie profilowania, które jest próbkowany do cykli zegara procesora i opcjonalnie zmienia liczbę cykli w interwale próbkowania z domyślnego 10,000,000. Na procesorze 1GH (jeden gigaherc) 10,000,000 zegar cykle jest około 100 próbek na sekundę. Minimalna liczba cykli, które można określić jest 50,000.

 **Czasomierz** może być używany tylko wtedy, gdy używasz metody profilowania próbkowania i może być używany tylko w wierszu polecenia, który zawiera również **launch** lub **dołącz** opcję.

 Domyślnie zdarzenie próbkowania profilera jest ustawione na cykle zegara procesora, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF,** **Sys**i **Counter** umożliwiają ustawienie zdarzenia próbkowania i interwału próbkowania. Opcja **GC** zbiera dane pamięci .NET przy każdym zdarzeniu alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.

 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, który zawiera opcję **Uruchom** lub **Dołącz.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametry
 `Cycles`Wartość całkowita określająca liczbę cykli zegara procesora w interwale próbkowania. Jeśli `Cycles` nie zostanie określony, interwał jest ustawiony na 10 000 000. Określ wartość bez przecinków.

## <a name="required-options"></a>Wymagane opcje
 **Czasomierz** można określić tylko w wierszu polecenia, który zawiera jedną z następujących opcji.

 **Uruchom:** `AppName` Uruchamia profiler i aplikację `AppName`określoną przez .

 **Dołącz:** `PID` Dołącza profiler do procesu określonego przez identyfikator`PID`procesu ( ).

## <a name="invalid-options"></a>Nieprawidłowe opcje
 W tym samym wierszu polecenia nie można określić następujących opcji co **timer**.

 **PF**[**:**`Events`] Ustawia zdarzenie próbkowania na błędy `Events`strony i opcjonalnie ustawia interwał próbkowania na . Domyślny interwał PF wynosi 10.

 **Sys**[**:**`Events`] Ustawia zdarzenie próbkowania na wywołania `Events`systemu operacyjnego i opcjonalnie ustawia interwał próbkowania na . Domyślny interwał Sys wynosi 10.

 **Licznik**[**:**`Name,Reload,FriendlyName`] Ustawia zdarzenie próbkowania `Name` na licznik wydajności `Reload`procesora określony przez i ustawia interwał próbkowania na .

 **GC**[**:**{ Okres **istnienia****alokacji**&#124;}] Zbiera dane pamięci .NET. Domyślnie **(Alokacja**) dane są zbierane przy każdym zdarzeniu alokacji pamięci. Po określeniu **parametru Lifetime** dane są również zbierane w każdym przypadku wyrzucania elementów bezużytecznych.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak ustawić interwał próbkowania profilera na 1 000 000 cykli procesora.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
