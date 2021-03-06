---
title: WinCounter | Microsoft Docs
description: Dowiedz się więcej na temat opcji WinCounter, w której określono licznik wydajności systemu Windows lub aplikacji, który ma być zbierany w ustalonych odstępach czasu podczas przebiegu profilu.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eaa5482ba1bad297fd1cfdf20810ad985b050c25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915934"
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
 `Path` Licznik wydajności systemu Windows w formacie ścieżki licznika PDH.

## <a name="required-options"></a>Wymagane opcje
 Opcji **WinCounter** można użyć tylko z opcją **Start** .

 **Rozpocznij:** `Method` Opcja **Start** inicjuje profiler do określonej metody profilowania.

## <a name="exclusive-options"></a>Opcje wyłączności
 Opcji **AutoMark** można używać tylko z opcją **WinCounter** .

 **Oznacz jako:** `Milliseconds` Określa liczbę milisekund między zbieraniem danych licznika wydajności systemu Windows.

## <a name="example"></a>Przykład
 W poniższym przykładzie określono dwa liczniki wydajności systemu Windows, które mają być zbierane w interwale 1000 milisekund.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
