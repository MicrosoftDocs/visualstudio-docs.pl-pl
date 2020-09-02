---
title: OnError — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46f6907bea5954cffae92b41398717a8247350e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195659"
---
# <a name="onerror-element-msbuild"></a>OnError — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Powoduje, że co najmniej jeden obiekt docelowy jest wykonywany, jeśli `ContinueOnError` atrybut dotyczy `false` zadania zakończonego niepowodzeniem.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>Składnia  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Elementy docelowe do wykonania, jeśli zadanie zakończy się niepowodzeniem. Rozdziel wiele obiektów docelowych średnikami. Wiele obiektów docelowych jest wykonywanych w określonej kolejności.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Obiektów](../msbuild/target-element-msbuild.md)|Element kontenera [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadań.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wykonuje `OnError` element, jeśli jeden z `Target` zadań elementu kończy się niepowodzeniem z `ContinueOnError` atrybutem ustawionym na `ErrorAndStop` (lub `false` ). Gdy zadanie nie powiedzie się, obiekty docelowe określone w `ExecuteTargets` atrybucie są wykonywane. Jeśli obiekt docelowy zawiera więcej niż jeden `OnError` element, `OnError` elementy są wykonywane sekwencyjnie, gdy zadanie zakończy się niepowodzeniem.  
  
 Aby uzyskać informacje na temat `ContinueOnError` atrybutu, zobacz [element Task (MSBuild)](../msbuild/task-element-msbuild.md). Aby uzyskać informacje o celach, zobacz [targets](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje `TaskOne` `TaskTwo` zadania i. W przypadku `TaskOne` niepowodzenia program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] oblicza `OnError` element i wykonuje element `OtherTarget` docelowy.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
