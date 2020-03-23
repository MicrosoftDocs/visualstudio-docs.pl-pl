---
title: WinCounter | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779847"
---
# <a name="wincounter"></a>WinCounter
**Opcja WinCounter** określa licznik wydajności systemu Windows lub aplikacji do zbierania w ustalonych odstępach czasu podczas uruchamiania profilu. Liczniki wydajności systemu Windows i aplikacji są wyświetlane jako znaczniki w pliku danych profilowania. Można określić wiele liczników wydajności do zbierania w oddzielnych opcjach.

 Domyślnie liczniki są zbierane co 500 milisekund. Użyj opcji **Automark,** aby określić inny interwał zbierania.

 Używana jest tylko jedna opcja **AutoMark.** Jeśli określono wiele opcji **AutoMark,** używana jest ostatnia opcja.

 Opcji **WinCounter** można używać tylko z opcją **Start.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametry
 `Path`Licznik wydajności systemu Windows w formacie ścieżki licznika PDH.

## <a name="required-options"></a>Wymagane opcje
 Opcji **WinCounter** można używać tylko z opcją **Start.**

 **Start:** `Method` Opcja **Start** inicjuje profiler do określonej metody profilowania.

## <a name="exclusive-options"></a>Opcje ekskluzywne
 Opcji **AutoMark** można używać tylko z opcją **WinCounter.**

 **AutoMark:** `Milliseconds` Określa liczbę milisekund między zbieraniem danych licznika wydajności systemu Windows.

## <a name="example"></a>Przykład
 W poniższym przykładzie dwa liczniki wydajności systemu Windows są określone do zbierania w odstępie 1000 milisekund.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
