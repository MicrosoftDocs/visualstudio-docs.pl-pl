---
title: LineOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4de8aa278adab0127f3a39d9adcf105f906e152
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625247"
---
# <a name="lineoff"></a>LineOff
Domyślnie profiler zbiera kodu wiersza numer i wierszu numer przesunięcia dane źródłowe, gdy używana jest metoda profilowania próbkowanie. Narzędzia VSPerfCmd **LineOff** opcji wyłącza kolekcję danych numeru linii, gdy narzędzie VSPerfCmd są używane do uruchamiania aplikacji. Danych profilowania zbieranych funkcji poziomie podczas **LineOff** jest określony.

 Możesz użyć **LineOff** tylko w przypadku **Uruchom** opcji i tylko gdy program profilujący został zainicjowany do próbkowania przy użyciu **Start**:**przykładowe** opcji.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 **LineOff** opcja może być używana tylko w wierszu polecenia, który zawiera **Uruchom** opcji.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.

## <a name="example"></a>Przykład
 W tym przykładzie uruchamia aplikację i profiler i wyłączenie próbkowania na poziomie wiersza.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)