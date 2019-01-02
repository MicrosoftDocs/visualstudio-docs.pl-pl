---
title: WinCounter | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51cb5aa0a41f311ea9c24a4ed512d6df4fe2e10f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875222"
---
# <a name="wincounter"></a>WinCounter
**WinCounter** opcja określa Windows lub aplikacji licznika wydajności zbierane w ustalonych odstępach czasu podczas profil Uruchom. Liczniki wydajności aplikacji i Windows są wyświetlane jako znaki w pliku danych profilowania. Można określić wiele liczników wydajności do zebrania w oddzielnych opcji.  
  
 Domyślnie są zbierane liczniki co 500 milisekund. Użyj **AutoMark** opcję, aby określić interwał inną kolekcję.  
  
 Tylko jeden **AutoMark** jest używana opcja. Jeśli wiele **AutoMark** opcje są określone, ostatni z nich jest używany.  
  
 **WinCounter** opcja może być używana tylko z **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Path`  
 Licznik wydajności Windows w formacie ścieżki licznika PDH.  
  
## <a name="required-options"></a>Wymagane opcje  
 **WinCounter** opcja może być używana tylko z **Start** opcji.  
  
 **Początek:** `Method`  
 **Start** opcja inicjuje profiler do określonej metody profilowania.  
  
## <a name="exclusive-options"></a>Wykluczających się opcji  
 **AutoMark** opcja może być używana tylko z **WinCounter** opcji.  
  
 **AutoMark:** `Milliseconds`  
 Określa liczbę milisekund między zbieranie danych licznika wydajności Windows.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie podano dwa liczniki wydajności Windows, mają być zbierane z interwałem 1000 milisekund.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)