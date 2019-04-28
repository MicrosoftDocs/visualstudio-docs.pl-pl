---
title: LineOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbe8a715c5bb179c5293dd666f1879c07068d8b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583174"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie profiler zbiera kodu wiersza numer i wierszu numer przesunięcia dane źródłowe, gdy używana jest metoda profilowania próbkowanie. Narzędzia VSPerfCmd **LineOff** opcji wyłącza kolekcję danych numeru linii, gdy narzędzie VSPerfCmd są używane do uruchamiania aplikacji. Danych profilowania zbieranych funkcji poziomie podczas **LineOff** jest określony.  
  
 Możesz użyć **LineOff** tylko w przypadku **Uruchom** opcji i tylko gdy program profilujący został zainicjowany do próbkowania przy użyciu **Start**:**przykładowe** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **LineOff** opcja może być używana tylko w wierszu polecenia, który zawiera **Uruchom** opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia aplikację i profiler i wyłączenie próbkowania na poziomie wiersza.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
