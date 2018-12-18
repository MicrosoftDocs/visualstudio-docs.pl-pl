---
title: WinCounter | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a0e13869c46a9e2998252e819442bd61480b4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809300"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**WinCounter** opcja określa Windows lub aplikacji licznika wydajności zbierane w ustalonych odstępach czasu podczas profil Uruchom. Liczniki wydajności aplikacji i Windows są wyświetlane jako znaki w pliku danych profilowania. Można określić wiele liczników wydajności do zebrania w oddzielnych opcji.  
  
 Domyślnie są zbierane liczniki co 500 milisekund. Użyj **AutoMark** opcję, aby określić interwał inną kolekcję.  
  
 Tylko jeden **AutoMark** jest używana opcja. Jeśli wiele **AutoMark** opcje są określone, ostatni z nich jest używany.  
  
 **WinCounter** opcja może być używana tylko z **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



