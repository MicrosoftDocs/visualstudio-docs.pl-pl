---
title: AutoMark | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 072f80508f81a7b42ad481048f604cbd4c54af88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779795"
---
# <a name="automark"></a>AutoMark
Opcja **Automark** określa liczbę milisekund między zbieraniem zdarzeń licznika wydajności oprogramowania systemu Windows. Liczniki wydajności systemu Windows są określone w opcji **WinCounter.**

 W wierszu polecenia można określić tylko jedną opcję **Automark.** Należy zauważyć, że interwał próbkowania **WinCounter** określony przez **AutoMark** jest niezależny od głównego interwału próbkowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parametry
 `Milliseconds`Określa liczbę milisekund między kolekcjami zdarzeń licznika wydajności systemu Windows.

## <a name="required-options"></a>Wymagane opcje
 **WinCounter:** `Path` Określa licznik wydajności systemu Windows do zbierania. Podczas korzystania z metody instrumentacji można określić wiele liczników systemu Windows. Podczas korzystania z metody próbkowania można określić tylko jeden licznik oprogramowania. Opcja **WinCounter** musi być określona w wierszu polecenia zawierającym opcję **Start.**

## <a name="example"></a>Przykład
 W tym przykładzie interwał próbkowania 1000 milisekund jest ustawiony dla dwóch liczników wydajności systemu Windows.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
