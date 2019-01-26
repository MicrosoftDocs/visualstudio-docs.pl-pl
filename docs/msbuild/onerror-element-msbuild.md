---
title: OnError — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5a7ecc4c91dcb39d090c00b7b2ed37bd6bb906c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011900"
---
# <a name="onerror-element-msbuild"></a>OnError — element (MSBuild)
Powoduje, że jeden lub więcej celów do wykonania, jeśli `ContinueOnError` atrybut jest `false` dla zadania nie powiodło się.  

 \<Project>  
 \<Docelowy >  
 \<OnError — >  

## <a name="syntax"></a>Składnia  

```xml  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Cele do wykonania, jeśli zadanie nie powiedzie się. Wiele elementów docelowych należy oddzielić średnikami. Wiele elementów docelowych są wykonywane w określonej kolejności.|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  

### <a name="parent-elements"></a>Elementy nadrzędne  

| Element | Opis |
| - | - |
| [Docelowy](../msbuild/target-element-msbuild.md) | Element kontenera służy do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania. |

## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wykonuje `OnError` elementu, jeśli jest to jeden z `Target` elementu zadań kończy się niepowodzeniem z `ContinueOnError` ustawioną wartość atrybutu `ErrorAndStop` (lub `false`). Jeśli zadanie nie powiedzie się, obiektów docelowych określonych w `ExecuteTargets` atrybutu jest wykonywany. Jeśli istnieje więcej niż jedna `OnError` elementu w miejscu docelowym, `OnError` elementy są wykonywane sekwencyjnie, gdy zadanie nie powiodło się.  

 Aby uzyskać informacje o `ContinueOnError` atrybutów, zobacz [Task — element (MSBuild)](../msbuild/task-element-msbuild.md). Aby uzyskać informacje o środowiskach docelowych, zobacz [cele](../msbuild/msbuild-targets.md).  

## <a name="example"></a>Przykład  
 Poniższy kod wykonuje `TaskOne` i `TaskTwo` zadania. Jeśli `TaskOne` zakończy się niepowodzeniem, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ocenia `OnError` elementu i wykonuje `OtherTarget` docelowej.  

```xml  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  

## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)
