---
title: WinCounter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9455d596e27526f6075ad3b667ac441b12511d58
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779847"
---
# <a name="wincounter"></a>WinCounter
Opcja **WinCounter** Określa licznik wydajności systemu Windows lub aplikacji do zebrania w ustalonych odstępach czasu podczas przebiegu profilu. Liczniki wydajności systemu Windows i aplikacji są wyświetlane jako znaczniki w pliku danych profilowania. Można określić wiele liczników wydajności do zebrania w osobnych opcjach.

 Domyślnie liczniki są zbierane co 500 milisekund. Użyj opcji **AutoMark** , aby określić inny interwał kolekcji.

 Używana jest tylko jedna opcja automatycznego **oznaczania** . Jeśli określono wiele opcji **Autooznaczania** , zostanie użyta Ostatnia z nich.

 Opcji **WinCounter** można użyć tylko z opcją **Start** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametry
 `Path` licznik wydajności systemu Windows w formacie ścieżki licznika PDH.

## <a name="required-options"></a>Wymagane opcje
 Opcji **WinCounter** można użyć tylko z opcją **Start** .

 **Rozpoczęcie:** `Method` opcja **Start** inicjuje profiler do określonej metody profilowania.

## <a name="exclusive-options"></a>Opcje wyłączności
 Opcji **AutoMark** można używać tylko z opcją **WinCounter** .

 **Autoznacznik:** `Milliseconds` określa liczbę milisekund między zbieraniem danych licznika wydajności systemu Windows.

## <a name="example"></a>Przykład
 W poniższym przykładzie określono dwa liczniki wydajności systemu Windows, które mają być zbierane w interwale 1000 milisekund.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
