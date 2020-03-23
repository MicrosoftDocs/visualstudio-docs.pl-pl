---
title: Zadanie przypisywania kultury | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9f7bb47efefa3f7a1d4cf52cbfa5891602956f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634568"
---
# <a name="assignculture-task"></a>AssignCulture — zadanie

To zadanie akceptuje listę elementów, które mogą zawierać prawidłowy ciąg identyfikatora kultury .NET jako część nazwy `Culture` pliku i tworzy elementy, które mają metadane o nazwie zawierające odpowiedni identyfikator kultury. Na przykład nazwa pliku *Form1.fr-fr.resx* ma osadzony identyfikator kultury "fr-fr", więc to zadanie spowoduje powstanie elementu o tej `Culture` samej nazwie pliku z metadanymi równymi `fr-fr`. Zadanie tworzy również listę nazwy plików z kultury usunięte z nazwy pliku.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli `AssignCulture` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AssignedFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera listę elementów otrzymanych w `Files` `Culture` parametrze z wpisem metadanych dodanym do każdego elementu.<br /><br /> Jeśli element przychodzący `Files` z parametru zawiera już wpis `Culture` metadanych, używany jest oryginalny wpis metadanych.<br /><br /> Zadanie przypisuje wpis `Culture` metadanych tylko wtedy, gdy nazwa pliku zawiera prawidłowy identyfikator kultury. Identyfikator kultury musi znajdować się między dwoma ostatnimi kropkami w nazwach plików.|
|`AssignedFilesWithCulture`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera podzbiór elementów `AssignedFiles` z parametru, które mają wpis `Culture` metadanych.|
|`AssignedFilesWithNoCulture`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera podzbiór elementów `AssignedFiles` z parametru, `Culture` które nie mają wpisu metadanych.|
|`CultureNeutralAssignedFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera tę samą listę elementów, które są produkowane w parametrze, `AssignedFiles` z wyjątkiem kultury usunięte z nazwy pliku.<br /><br /> Zadanie usuwa kulturę z nazwy pliku tylko wtedy, gdy jest prawidłowym identyfikatorem kultury.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę plików z osadzonymi nazwami kultury, do które mają być przypisywane kultury.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład wykonuje `AssignCulture` zadanie `ResourceFiles` z kolekcji elementów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ResourceFiles Include="MyResource1.fr.resx"/>
        <ResourceFiles Include="MyResource2.XX.resx"/>
    </ItemGroup>

    <Target Name="Culture">
        <AssignCulture
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
            <Output TaskParameter="AssignedFilesWithCulture"
                ItemName="OutAssignedFilesWithCulture"/>
            <Output TaskParameter="AssignedFilesWithNoCulture"
                ItemName="OutAssignedFilesWithNoCulture"/>
            <Output TaskParameter="CultureNeutralAssignedFiles"
                ItemName="OutCultureNeutralAssignedFiles"/>
        </AssignCulture>
    </Target>
</Project>
```

W poniższej tabeli opisano wartość elementów wyjściowych po wykonaniu zadania. Metadane elementu są wyświetlane w nawiasie po elemencie.

|Kolekcja przedmiotów|Spis treści|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx* (Kultura="fr")<br /><br /> *MyResource2.XX.resx* (brak dodatkowych metadanych)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (Kultura="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (brak dodatkowych metadanych)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (Kultura="fr")<br /><br /> *MyResource2.XX.resx* (brak dodatkowych metadanych)|

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
