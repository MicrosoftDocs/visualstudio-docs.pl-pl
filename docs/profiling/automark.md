---
title: AutoMark | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f7c4a47910d15da0a93a937622ce47843124d82
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040544"
---
# <a name="automark"></a>AutoMark
**AutoMark** opcja określa liczbę milisekund między zbierania zdarzeń liczników wydajności oprogramowania Windows. Liczniki wydajności Windows są określone w **WinCounter** opcji.  
  
 Tylko jeden **AutoMark** opcja może być określona w wierszu polecenia. Należy pamiętać, że **WinCounter** interwał próbkowania określony przez **AutoMark** jest niezależna od interwału próbkowania głównego.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parametry  
 `Milliseconds`  
 Określa liczbę milisekund między kolekcji zdarzeń licznika wydajności Windows.  
  
## <a name="required-options"></a>Wymagane opcje  
 **WinCounter:** `Path`  
 Określa Windows licznika wydajności do zbierania. Korzystając z metody instrumentacji, można określić wiele liczników Windows. Korzystając z metody pobierania próbek, można określić tylko jeden licznik oprogramowania. **WinCounter** opcja musi być określona w wierszu polecenia, który zawiera **Start** opcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dla dwóch liczników wydajności Windows ustawiono interwał próbkowania 1000 milisekund.  
  
```cmd  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)