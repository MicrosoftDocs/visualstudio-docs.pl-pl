---
title: Task — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6683aac3c5a4314df6fde3d72dd9085b6608d8a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202268"
---
# <a name="task-element-msbuild"></a>Task — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzy i uruchamia wystąpienie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadania. Nazwa elementu jest określana przez nazwę zadania, tworzona.  
  
 \<Project>  
 \<Docelowy >  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
|Element|Opis|  
|-------------|-----------------|  
|[Docelowy](../msbuild/target-element-msbuild.md)|Element kontenera służy do [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadania.|  
  
## <a name="remarks"></a>Uwagi  
 A `Task` element [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu tworzy wystąpienie zadania, ustawia właściwości i uruchamia go. `Output` Element parametry wyjściowe są przechowywane we właściwościach lub elementy, które ma być używany w innym miejscu w pliku projektu.  
  
 Czy istnieją jakieś [OnError](../msbuild/onerror-element-msbuild.md) elementów w obiekcie nadrzędnym `Target` element zadania, są nadal będą brane w razie niepowodzenia zadania i `ContinueOnError` ma wartość `false`. Aby uzyskać więcej informacji na temat zadań, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy wystąpienie [CSC — zadanie](../msbuild/csc-task.md) klasy, ustawia sześć właściwości, a następnie wykonuje zadanie. Po wykonaniu wartość `OutputAssembly` właściwość obiektu, jest umieszczana w listę elementów o nazwie `FinalAssemblyName`.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
