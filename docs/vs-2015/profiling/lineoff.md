---
title: LineOff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93fe4acedfcae36f75ed38bef102ccc35f08f2ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759677"
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
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



