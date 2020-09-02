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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583174"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie profiler zbiera numer wiersza kodu źródłowego i dane przesunięcia numerów wierszy przy użyciu metody profilowania próbkowania. Opcja VSPerfCmd **LineOff** wyłącza zbieranie danych o numerach wierszy, gdy do uruchomienia aplikacji jest używany VSPerfCmd. Dane profilowania są zbierane do poziomu funkcji po określeniu **LineOff** .  
  
 Opcji **LineOff** można użyć tylko w przypadku opcji **uruchamiania** i tylko wtedy, gdy profiler został zainicjowany do próbkowania przy użyciu polecenia **Start**:**Sample** .  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcji **LineOff** można użyć tylko w wierszu polecenia zawierającym opcję **uruchamiania** .  
  
 **Uruchom:**`AppName`  
 Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.  
  
## <a name="example"></a>Przykład  
 Ten przykład uruchamia aplikację i Profiler i wyłącza próbkowanie na poziomie wiersza.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
