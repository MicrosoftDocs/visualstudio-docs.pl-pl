---
title: WinCounter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9424eb099516761866ec459888ff830fcf56a28b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154744"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **WinCounter** Określa licznik wydajności systemu Windows lub aplikacji do zebrania w ustalonych odstępach czasu podczas przebiegu profilu. Liczniki wydajności systemu Windows i aplikacji są wyświetlane jako znaczniki w pliku danych profilowania. Można określić wiele liczników wydajności do zebrania w osobnych opcjach.  
  
 Domyślnie liczniki są zbierane co 500 milisekund. Użyj opcji **AutoMark** , aby określić inny interwał kolekcji.  
  
 Używana jest tylko jedna opcja automatycznego **oznaczania** . Jeśli określono wiele opcji **Autooznaczania** , zostanie użyta Ostatnia z nich.  
  
 Opcji **WinCounter** można użyć tylko z opcją **Start** .  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Path`  
 Licznik wydajności systemu Windows w formacie ścieżki licznika PDH.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcji **WinCounter** można użyć tylko z opcją **Start** .  
  
 **Rozpocznij:**`Method`  
 Opcja **Start** inicjuje profiler do określonej metody profilowania.  
  
## <a name="exclusive-options"></a>Opcje wyłączności  
 Opcji **AutoMark** można używać tylko z opcją **WinCounter** .  
  
 **Oznacz jako:**`Milliseconds`  
 Określa liczbę milisekund między zbieraniem danych licznika wydajności systemu Windows.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono dwa liczniki wydajności systemu Windows, które mają być zbierane w interwale 1000 milisekund.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
