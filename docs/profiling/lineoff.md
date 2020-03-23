---
title: LineOff | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac671c3b0ba40c462403b2afa850c3936156d6d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774129"
---
# <a name="lineoff"></a>LineOff
Domyślnie profiler zbiera numer wiersza kodu źródłowego i dane przesunięcia numeru wiersza podczas korzystania z metody profilowania próbkowania. Opcja VSPerfCmd **LineOff** wyłącza zbieranie danych numer wiersza, gdy VSPerfCmd jest używany do uruchamiania aplikacji. Dane profilowania są zbierane do poziomu funkcji, gdy **LineOff** jest określony.

 **Funkcji LineOff** można używać tylko z opcją **Uruchom** i tylko wtedy, gdy profiler został zainicjowany do próbkowania przy użyciu opcji **Start:****Sample.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 Opcji **LineOff** można używać tylko w wierszu polecenia zawierającym opcję **Uruchom.**

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie za pomocą metody próbkowania.

## <a name="example"></a>Przykład
 W tym przykładzie uruchamia aplikację i profiler i wyłącza próbkowanie na poziomie wiersza.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
