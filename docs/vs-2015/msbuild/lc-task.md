---
title: LC — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bbc6463247142ecde20fb2d054d9bd59304c4ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694110"
---
# <a name="lc-task"></a>LC — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija LC.exe, które generuje plik licencji z pliku. licx. Aby uzyskać więcej informacji na LC.exe, zobacz [Lc.exe (kompilator licencji)](https://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `LC` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`LicenseTarget`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik wykonywalny, dla którego są generowane pliki licencji.|  
|`NoLogo`|Opcjonalny `Boolean` parametr.<br /><br /> Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`OutputDirectory`|Opcjonalny `String` parametr.<br /><br /> Określa katalog, w którym mają zostać umieszczone pliki. licenses.|  
|`OutputLicense`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku. licenses. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa pliku. licx, a plik. licenses zostanie umieszczony w katalogu, który zawiera plik. licx.|  
|`ReferencedAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa składniki, do których istnieją odwołania do załadowania podczas generowania pliku licencji.|  
|`SdkToolsPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe.|  
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy zawierające licencjonowane składniki do uwzględnienia w pliku. licenses. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją `/complist` przełącznika w [Lc.exe (kompilator licencji)](https://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).|  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `LC` zadania do kompilowania licencji.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
