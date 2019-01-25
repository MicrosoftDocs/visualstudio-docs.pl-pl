---
title: Assignculture — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c161dcd18a46928c9e180608a122f106ecd6554e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780905"
---
# <a name="assignculture-task"></a>AssignCulture — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
To zadanie akceptuje listę elementów, które mogą zawierać prawidłowy ciąg identyfikatora kultury .NET jako część nazwy pliku i tworzy elementy, które mają metadanych o nazwie `Culture` zawierającego odpowiednie kulturze identyfikatora. Na przykład, nazwa pliku Form1.fr-fr.resx ma osadzony kultury identyfikator "fr-fr", dlatego to zadanie powoduje wygenerowanie elementu, który ma taką samą nazwę z metadanymi `Culture` równa `fr-fr`. Zadanie tworzy także listę nazw plików z kulturą usunięte z nazwy pliku.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AssignCulture` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssignedFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów trafiła `Files` parametru za pomocą `Culture` wpis metadanych dodany do każdego elementu.<br /><br /> Jeśli przychodzący element z `Files` zawiera już parametr `Culture` wpis metadanych, oryginalnym wpis metadanych jest używany.<br /><br /> Przypisuje tylko zadania `Culture` wpis metadanych, jeśli nazwa pliku zawiera identyfikator prawidłową kulturą. Identyfikator kultury musi wynosić od ostatnie dwie kropki w nazwie pliku.|  
|`AssignedFilesWithCulture`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera podzestaw elementów z `AssignedFiles` parametr, który ma `Culture` wpis metadanych.|  
|`AssignedFilesWithNoCulture`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera podzestaw elementów z `AssignedFiles` parametrów, które nie mają `Culture` wpis metadanych.|  
|`CultureNeutralAssignedFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę tych samych elementów, które są generowane w `AssignedFiles` parametru, z wyjątkiem z kulturą usunięte z nazwy pliku.<br /><br /> Zadanie powoduje usunięcie tylko kultury na podstawie nazwy pliku, gdy jest to identyfikator prawidłową kulturą.|  
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę plików z osadzonych kultury nazwy kultury, aby przypisać.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `AssignCulture` zadań za pomocą `ResourceFiles` elementu kolekcji.  
  
```  
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
  
 W poniższej tabeli opisano wartości elementów danych wyjściowych po wykonaniu zadania. Metadane elementu jest wyświetlany w nawiasie po elemencie.  
  
|Kolekcja elementów|Spis treści|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (Brak dodatkowych metadanych)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (Brak dodatkowych metadanych)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`nie dodatkowe metadane)|  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
