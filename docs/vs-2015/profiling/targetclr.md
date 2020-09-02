---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145619"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **TargetCLR** określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska CLR jest załadowana w aplikacji.  
  
 Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania jest celem pierwszej wersji środowiska CLR, która jest ładowana przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametry  
 `ClrVersion`  
 Numer wersji środowiska CLR. Użyj formatu wersji **vn. nnnnn**.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcji **TargetCLR** można użyć tylko z opcjami **uruchamiania** lub **dołączania** .  
  
 **Uruchom:**`AppName`  
 Uruchamia określoną aplikację i uruchamia profilowanie.  
  
 **Dołącz:**`PID`  
 Zaczyna profilować określony proces.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie opcja TargetCLR jest używana w celu upewnienia się, że środowisko CLR w wersji 4.0.11003 jest profilowane.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
