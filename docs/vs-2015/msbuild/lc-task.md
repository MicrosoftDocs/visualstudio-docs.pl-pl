---
title: LC — zadanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ec788e9f0ef80a1543aa15f4ff9bfb21daac6123
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803472"
---
# <a name="lc-task"></a>LC — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
LC.exe zawija generuje plik .license z pliku licx. Aby uzyskać więcej informacji na temat LC.exe, zobacz [Lc.exe (kompilator licencji)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `LC` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`LicenseTarget`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik wykonywalny, dla którego mają być tworzone pliki licenses.|  
|`NoLogo`|Opcjonalnie `Boolean` parametru.<br /><br /> Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`OutputDirectory`|Opcjonalnie `String` parametru.<br /><br /> Określa katalog, w której chcesz umieścić pliki wyjściowe licenses.|  
|`OutputLicense`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku licenses. Jeśli nie określisz nazwy, nazwa pliku licx jest używana, a plik licenses jest umieszczany w katalogu, który zawiera plik licx.|  
|`ReferencedAssemblies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa odwołania składniki można załadować podczas generowania pliku .license.|  
|`SdkToolsPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe.|  
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy, które zawierają licencjonowanych składników, które mają zostać objęte plik licenses. Aby uzyskać więcej informacji, zobacz dokumentację dla `/complist` przełącznika w [Lc.exe (kompilator licencji)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).|  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `LC` zadanie, aby skompilować licencji.  
  
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
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
