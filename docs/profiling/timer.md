---
title: Timer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 351b5a8da781d8e60d6a603c1d037f8bf71cd317
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615016"
---
# <a name="timer"></a>Czasomierz
*VSPerfCmd.exe* **czasomierza** opcja umożliwia ustawienie profilowania zdarzenia, które są próbkowane tak, aby cykle zegara procesora i opcjonalnie zmienia liczbę cykli w interwale próbkowania z domyślnego 10 000 000. W przypadku procesora 1GH (jeden gigaherc) cykle zegara 10 000 000 jest około 100 próbek na sekundę. Minimalna liczba cykli, które można określić to 50 000.

 **Czasomierz** można używać tylko gdy używana metoda profilowania próbkowanie i można używać tylko w wierszu polecenia, który zawiera także **Uruchom** lub **Dołącz** opcji.

 Domyślnie ustawiono profiler zdarzenie próbkowania cykli zegara procesora oraz interwał próbkowania jest ustawiony na 10 000 000. **Czasomierza**, **PF**, **Sys**, i **licznika** opcje umożliwiają skonfigurowanie zdarzenie próbkowania i interwał próbkowania. **GC** opcja służy do zbierania danych pamięci .NET na każde zdarzenie kolekcji alokacji i odzyskiwanie. W wierszu polecenia można określić tylko jeden z tych opcji.

 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w przypadku pierwszego wiersza polecenia, który zawiera **Uruchom** lub **Dołącz** opcji.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametry
 `Cycles` Wartość całkowita, która określa liczbę cykli zegara procesora w interwale próbkowania. Jeśli `Cycles` nie zostanie określony, interwał wynosi 10 000 000. Określ wartość bez spacji.

## <a name="required-options"></a>Wymagane opcje
 **Czasomierz** można określić tylko w wierszu polecenia, który zawiera jeden z następujących opcji.

 **Uruchom:** `AppName` Uruchamia program profilujący i aplikacji, określonej przez `AppName`.

 **Dołącz:** `PID` Dołącza profiler do procesu określonego przez identyfikator procesu (`PID`).

## <a name="invalid-options"></a>Nieprawidłowe opcje
 Nie można określić następujące opcje w wierszu polecenia jako **czasomierza**.

 **PF**[**:**`Events`] Ustawia zdarzenie próbkowania błędów strony i opcjonalnie ustawia interwał próbkowania `Events`. Domyślny interwał PF wynosi 10.

 **Sys**[**:**`Events`] zestawy wywołuje zdarzenie próbkowania do systemu operacyjnego i opcjonalnie ustawia interwał próbkowania `Events`. Domyślny interwał Sys wynosi 10.

 **Licznik**[**:**`Name,Reload,FriendlyName`] Ustawia zdarzenie próbkowania wydajności procesorów CPU, licznik określonej przez `Name` i ustawia interwał próbkowania `Reload`.

 **GC**[**:**{**alokacji**&#124;**okres istnienia**}] .NET umożliwia zbieranie danych pamięci. Domyślnie (**alokacji**), dane są zbierane na każde zdarzenie alokacji pamięci. Gdy **okres istnienia** parametr jest określony, dane są również zbierane przy każdym zdarzeniu kolekcji wyrzucania elementów.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak ustawić interwał próbkowania profilera cykli procesora 1 000 000.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)