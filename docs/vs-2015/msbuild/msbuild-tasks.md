---
title: Zadania programu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 756c19da1aeb8878c2d045f4ee471d8449d2a954
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154815"
---
# <a name="msbuild-tasks"></a>Zadania programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platforma kompilacji musi mieć możliwość wykonywania dowolnej liczby akcji w procesie kompilacji. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używa *zadań* do wykonania tych działań. Zadanie jest jednostką kodu wykonywalnego używaną przez program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do wykonywania niepodzielnych operacji kompilacji.  
  
## <a name="task-logic"></a>Logika zadań  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Format pliku projektu XML nie może w pełni wykonywać operacji kompilacji, więc logika zadań musi być implementowana poza plikiem projektu.  
  
 Logika wykonywania zadania jest implementowana jako Klasa platformy .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w <xref:Microsoft.Build.Framework> przestrzeni nazw.  
  
 Klasa Task definiuje również parametry wejściowe i wyjściowe dostępne dla zadania w pliku projektu. Wszystkie publiczne, niestatyczne właściwości nieabstrakcyjne uwidocznione przez klasę zadania mogą być dostępne w pliku projektu przez umieszczenie odpowiedniego atrybutu o tej samej nazwie w elemencie [Task](../msbuild/task-element-msbuild.md) .  
  
 Można napisać własne zadanie, tworząc zarządzaną klasę, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Aby uzyskać więcej informacji, zobacz [Zapisywanie zadań](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Wykonywanie zadania z pliku projektu  
 Przed wykonaniem zadania w pliku projektu należy najpierw zmapować typ w zestawie, który implementuje zadanie do nazwy zadania z elementem [UsingTask](../msbuild/usingtask-element-msbuild.md) . Pozwala to [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] uzyskać informacje o tym, gdzie szukać logiki wykonywania zadania po jego znalezieniu w pliku projektu.  
  
 Aby wykonać zadanie w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu, należy utworzyć element o nazwie zadania jako element podrzędny `Target` elementu. Jeśli zadanie przyjmuje parametry, są one przenoszone jako atrybuty elementu.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] listy elementów i właściwości mogą być używane jako parametry. Na przykład poniższy kod wywołuje `MakeDir` zadanie i ustawia wartość `Directories` właściwości `MakeDir` obiektu równą wartości `BuildDir` Właściwości zadeklarowanej w poprzednim przykładzie.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Zadania mogą także zwracać informacje do pliku projektu, które mogą być przechowywane w elementach lub właściwościach w celu późniejszego użycia. Na przykład poniższy kod wywołuje `Copy` zadanie i zapisuje informacje z `CopiedFiles` Właściwości Output na `SuccessfullyCopiedFiles` liście elementów.  
  
```  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Uwzględnione zadania  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Program jest dostarczany z wieloma zadaniami, takimi jak [Kopiowanie](../msbuild/copy-task.md), które kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), które tworzą katalogi, i [CSC](../msbuild/csc-task.md), które kompilują [!INCLUDE[csprcs](../includes/csprcs-md.md)] pliki kodu źródłowego. Aby uzyskać pełną listę dostępnych zadań i informacji o użyciu, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Zastąpione zadania  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wyszukuje zadania w kilku lokalizacjach. Pierwsza lokalizacja znajduje się w plikach z rozszerzeniem. OverrideTasks przechowywanych w katalogach .NET Framework. Zadania w tych plikach zastępują wszystkie inne zadania o tych samych nazwach, w tym zadania w pliku projektu. Druga lokalizacja znajduje się w plikach z rozszerzeniem. Zadania w katalogach .NET Framework. Jeśli zadanie nie zostanie odnalezione w żadnej z tych lokalizacji, zostanie użyte zadanie w pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md)   
 [Pisanie zadania](../msbuild/task-writing.md)   
 [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)
