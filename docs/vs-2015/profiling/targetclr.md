---
title: TargetCLR | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145619"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**TargetCLR** opcji określa wersję wspólnego języka środowiska wykonawczego (języka wspólnego CLR) do profilowania, gdy więcej niż jedna wersja środowiska CLR jest załadowana w aplikacji.  
  
 Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools docelowe pierwszą wersję środowiska CLR, który jest ładowany przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametry  
 `ClrVersion`  
 Numer wersji środowiska CLR. Użyj formatu wersji **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Wymagane opcje  
 **TargetCLR** opcja może być używana tylko z **Uruchom** lub **Dołącz** opcje.  
  
 **Uruchom:** `AppName`  
 Uruchamia określoną aplikację i rozpoczyna się do profilu.  
  
 **Dołącz:** `PID`  
 Uruchamia profilowanie określonego procesu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie opcja TargetCLR służy do upewnij się, że środowisko CLR w wersji 4.0.11003 jest profilowane.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
