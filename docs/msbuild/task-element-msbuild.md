---
title: Task — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37a843c6e282ca664ed3d2cc87d58aa50e6b5a74
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935426"
---
# <a name="task-element-msbuild"></a>Task — element (MSBuild)
Tworzy i uruchamia wystąpienie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania. Nazwa elementu jest określana przez nazwę zadania, tworzona.  

 \<Project>  
 \<Docelowy >  

## <a name="syntax"></a>Składnia  

```xml  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny. Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Atrybut opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` elementu i kompilacja nie są wykonywane i całą `Target` elementu i kompilacja jest uważany za nie powiodło się.<br /><br /> Wersje programu .NET Framework przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Wymagane, jeśli klasa zadania zawiera jeden lub więcej właściwości z etykietą `[Required]` atrybutu.<br /><br /> Parametr zadania zdefiniowane przez użytkownika, który zawiera wartość parametru jako jego wartość. Może to być dowolna liczba parametrów w `Task` elementu z każdy jest mapowany na właściwość platformy .NET w klasie zadania.|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Magazyny danych wyjściowych z zadania w pliku projektu. Może wynosić zero lub więcej `Output` elementów w zadaniu.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

| Element | Opis |
| - | - |
| [Docelowy](../msbuild/target-element-msbuild.md) | Element kontenera służy do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania. |

## <a name="remarks"></a>Uwagi  
 A `Task` element [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu tworzy wystąpienie zadania, ustawia właściwości i uruchamia go. `Output` Element parametry wyjściowe są przechowywane we właściwościach lub elementy, które ma być używany w innym miejscu w pliku projektu.  

 Czy istnieją jakieś [OnError](../msbuild/onerror-element-msbuild.md) elementów w obiekcie nadrzędnym `Target` element zadania, są nadal będą brane w razie niepowodzenia zadania i `ContinueOnError` ma wartość `false`. Aby uzyskać więcej informacji na temat zadań, zobacz [zadania](../msbuild/msbuild-tasks.md).  

## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy wystąpienie [CSC — zadanie](../msbuild/csc-task.md) klasy, ustawia sześć właściwości, a następnie wykonuje zadanie. Po wykonaniu wartość `OutputAssembly` właściwość obiektu, jest umieszczana w listę elementów o nazwie `FinalAssemblyName`.  

```xml  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
