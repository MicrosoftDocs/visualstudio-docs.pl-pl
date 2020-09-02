---
title: AssignCulture — — zadanie | Microsoft Docs
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
ms.openlocfilehash: 23b991efaa32e2c1886e6e0cd64bb9d6181190d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187041"
---
# <a name="assignculture-task"></a>AssignCulture — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To zadanie akceptuje listę elementów, które mogą zawierać prawidłowy ciąg identyfikatora kultury .NET jako część nazwy pliku i tworzy elementy o metadanych o nazwie `Culture` zawierającej odpowiedni identyfikator kultury. Na przykład nazwa pliku Form1.fr-fr. resx ma osadzony identyfikator kultury "fr-fr", więc to zadanie spowoduje utworzenie elementu o tej samej nazwie pliku z metadanymi `Culture` równymi `fr-fr` . Zadanie tworzy również listę nazw plików z kulturą usuniętą z pliku.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AssignCulture` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssignedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów odebranych w `Files` parametrze z `Culture` wpisem metadanych dodanym do każdego elementu.<br /><br /> Jeśli element przychodzący z `Files` parametru zawiera już `Culture` wpis metadanych, zostanie użyty pierwotny wpis metadanych.<br /><br /> Zadanie przypisuje tylko `Culture` wpis metadanych, jeśli nazwa pliku zawiera prawidłowy identyfikator kultury. Identyfikator kultury musi należeć do przedziału od dwóch ostatnich kropek w nazwie pliku.|  
|`AssignedFilesWithCulture`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera podzestaw elementów z `AssignedFiles` parametru, który ma `Culture` wpis metadanych.|  
|`AssignedFilesWithNoCulture`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera podzestaw elementów z `AssignedFiles` parametru, który nie ma `Culture` wpisu metadanych.|  
|`CultureNeutralAssignedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera tę samą listę elementów, która jest generowana w `AssignedFiles` parametrze, z wyjątkiem kultury usuniętej z nazwy pliku.<br /><br /> Zadanie usuwa tylko kulturę z nazwy pliku, jeśli jest to prawidłowy identyfikator kultury.|  
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę plików z osadzonymi nazwami kultur, do której ma zostać przypisana kultura.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `AssignCulture` zadanie przy użyciu `ResourceFiles` kolekcji elementów.  
  
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
  
 W poniższej tabeli opisano wartości elementów wyjściowych po wykonaniu zadania. Metadane elementu są wyświetlane w nawiasach po elemencie.  
  
|Kolekcja elementów|Zawartość|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (brak dodatkowych metadanych)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (brak dodatkowych metadanych)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`Brak dodatkowych metadanych)|  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
