---
title: TargetCLR | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed0891715f6c9a0f4f89249a6ca5ac6415bad038
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967125"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** opcji określa wersję wspólnego języka środowiska wykonawczego (języka wspólnego CLR) do profilowania, gdy więcej niż jedna wersja środowiska CLR jest załadowana w aplikacji.  
  
 Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools docelowe pierwszą wersję środowiska CLR, który jest ładowany przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```