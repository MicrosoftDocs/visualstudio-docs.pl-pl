---
title: 'Instrukcje: kompilowanie określonych obiektów docelowych w rozwiązaniach za pomocą MSBuild.exe | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156664"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Porady: kompilacja określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą MSBuild.exe można tworzyć określone cele konkretnych projektów w rozwiązaniu.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Aby utworzyć konkretny obiekt docelowy określonego projektu w rozwiązaniu  
  
1. W wierszu polecenia wpisz `MSBuild.exe <SolutionName>.sln` , gdzie `<SolutionName>` odpowiada nazwie pliku rozwiązania zawierającego obiekt docelowy, który chcesz wykonać.  
  
2. Określ element docelowy po przełączniku **/t** w formacie *ProjectName*:*TargetName*.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wykonywana jest wartość `Rebuild` docelowa `NotInSlnFolder` projektu, a następnie wykonywana `Clean` jest wartość docelowa `InSolutionFolder` projektu, który znajduje się w `NewFolder` folderze rozwiązania.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
