---
title: Oznacz jako automarkę | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aaa1e7f39a9dcaedec51eb6a40ed3a2d06bcfb0e
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330604"
---
# <a name="automark"></a>AutoMark
Opcja automatycznego **oznaczania** określa liczbę milisekund między kolekcją zdarzeń licznika wydajności oprogramowania systemu Windows. Liczniki wydajności systemu Windows są określone w opcji **WinCounter** .

 W wierszu polecenia można określić tylko jedną opcję **Autooznaczania** . Należy zauważyć, że interwał próbkowania **WinCounter** określony przez **automarkę** jest niezależny od głównego interwału próbkowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parametry
 `Milliseconds`Określa liczbę milisekund między kolekcjami zdarzeń licznika wydajności systemu Windows.

## <a name="required-options"></a>Wymagane opcje
 **WinCounter:** `Path` Określa licznik wydajności systemu Windows do zebrania. W przypadku korzystania z metody instrumentacji można określić wiele liczników systemu Windows. W przypadku korzystania z metody próbkowania można określić tylko jeden licznik oprogramowania. Opcja **WinCounter** musi być określona w wierszu polecenia zawierającym opcję **Start** .

## <a name="example"></a>Przykład
 W tym przykładzie interwał próbkowania 1000 milisekund jest ustawiany dla dwóch liczników wydajności systemu Windows.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
