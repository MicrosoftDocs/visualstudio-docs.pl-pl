---
title: -ProjectConfig (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b956fb09681f6f4a1f916f4b108028f69f009cd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044203"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa konfigurację kompilacji projektu mają być stosowane podczas kompilacji, czyszczenia, odbudować lub wdrożyć projekt o nazwie w `/project` argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Argumenty  
 /build  
 Tworzy projekt określony przez `/project` `ProjName`.  
  
 / clean  
 Czyści wszystkie pośrednie pliki i katalogi dane wyjściowe utworzone podczas kompilacji.  
  
 /rebuild  
 Czyści, a następnie kompiluje projekt określony przez `/project` `ProjName`.  
  
 /deploy  
 Określa, czy wdrożony po kompilacji lub skompiluj ponownie projekt.  
  
 `SolnConfigName`  
 Wymagana. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w `SolutionName`.  
  
 `SolutionName`  
 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 /project `ProjName`  
 Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.  
  
 / projectconfig `ProjConfigName`  
 Opcjonalna. Nazwa projektu kompilacji konfiguracji, które mają być stosowane do `/project` o nazwie.  
  
## <a name="remarks"></a>Uwagi  
  
- Może być używany z `/project` przełącznika jako część `devenv /build`, /`clean`, `/rebuild`, lub `/deploy` polecenia.  
  
- Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
- Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy projekt `CSharpConsoleApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `Debug` Konfiguracja rozwiązania o `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
