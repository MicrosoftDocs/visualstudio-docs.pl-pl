---
title: Argumenty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65759da4363891c713f906e6cb10f00443bcbceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197912"
---
# <a name="args"></a>Args
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja VSPerfCmd.exe **args** określa listę argumentów, które są przekazane do aplikacji docelowej podpolecenia **Uruchom** .  
  
 **Argumentów** można używać tylko wtedy, gdy w wierszu polecenia określono również wartość **uruchomienia** . **Argumenty** są opcjonalne w przypadku określenia parametru **Launch** .  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Arguments`  
 Lista argumentów dla aplikacji docelowej polecenia **uruchamiania** .  
  
## <a name="required-options"></a>Wymagane opcje  
 **Uruchom:**`AppName`  
 Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa opcji **args** do przekazywania argumentów do TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
