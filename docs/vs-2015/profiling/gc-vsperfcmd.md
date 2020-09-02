---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bdb28f74dd305dc497521e95d38e00192c21c54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193600"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **GC** umożliwia zbieranie danych .NET Framework alokacji pamięci i okresu istnienia obiektu. Opcji **GC** można używać tylko z metodą profilowania próbkowania i tylko z opcją **uruchomienia** .  
  
 W przypadku korzystania z opcji **GC** polecenie VSPerfCLREnv **/sampleon** nie jest wymagane.  
  
 Jeśli nie określono parametrów lub jeśli określono parametr **alokacji** , zbierane są tylko .NET Framework dane alokacji pamięci. Jeśli określono parametr **okresu istnienia** , zostaną zebrane dane dotyczące alokacji pamięci .NET Framework i .NET Framework okresu istnienia obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Dział**  
 Domyślne. Zbiera .NET Framework dane alokacji pamięci.  
  
 **Okres istnienia**  
 Zbiera .NET Framework dane alokacji pamięci i .NET Framework dane okresu istnienia obiektu.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcji **GC** można używać tylko z opcją **uruchamiania** .  
  
 **Uruchom:**`AppName`  
 Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uruchamia aplikację i zbiera .NET Framework dane alokacji pamięci.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
