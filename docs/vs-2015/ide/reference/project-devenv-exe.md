---
title: -Projekt (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 398d92065b1ff1b5447017c7a21fc0def1e0da52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200888"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Umożliwia określenie jednego projektu w ramach konfiguracji określonego rozwiązania do kompilacji, czyszczenia, odbudować lub wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## <a name="arguments"></a>Argumenty  
 / Build  
 Tworzy projekt określony przez `/project` `ProjName`.  
  
 / clean  
 Czyści wszystkie pośrednie pliki i katalogi dane wyjściowe utworzone podczas kompilacji.  
  
 /rebuild  
 Czyści, a następnie kompiluje projekt określony przez `/project` `ProjName`.  
  
 / deploy  
 Określa, czy wdrożony po kompilacji lub skompiluj ponownie projekt.  
  
 `SolnConfigName`  
 Wymagana. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w `SolutionName`.  
  
 `SolutionName`  
 Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 / Project `ProjName`  
 Opcjonalny. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.  
  
 / projectconfig `ProjConfigName`  
 Opcjonalny. Nazwa projektu kompilacji konfiguracji, które mają być stosowane do `/project` o nazwie.  
  
## <a name="remarks"></a>Uwagi  
  
- Należy użyć wchodzi w skład `devenv /build`, /`clean`, `/rebuild`, lub `/deploy` polecenia.  
  
- Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
- Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy projekt `CSharpConsoleApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `Debug` Konfiguracja rozwiązania o `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)   
 [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
