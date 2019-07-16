---
title: 'Instrukcje: Kompilacja określonych obiektów docelowych, w przypadku rozwiązań przy użyciu MSBuild.exe | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bfef86b8ea82077ba7fe3f753f9835c06c3380a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156664"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Instrukcje: Kompilacja określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć MSBuild.exe, aby kompilacja określonych obiektów docelowych określonych projektów w rozwiązaniu.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Tworzenie konkretnego celu określonego projektu w rozwiązaniu  
  
1. W wierszu polecenia wpisz polecenie `MSBuild.exe <SolutionName>.sln`, gdzie `<SolutionName>` odnosi się do nazwy pliku rozwiązania, który zawiera element docelowy, który chcesz wykonać.  
  
2. Określ element docelowy po **/t** przełącznika w formacie *ProjectName*:*TargetName*.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `Rebuild` celem `NotInSlnFolder` projektu, a następnie wykonuje `Clean` celem `InSolutionFolder` projektu, który znajduje się w `NewFolder` folderu rozwiązania.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
