---
title: LC — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2fee34977f790589194ec120ea88515bcf884a9e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921776"
---
# <a name="lc-task"></a>LC — Zadanie
Opakowuje *LC.exe*, która generuje *.license* plik wchodzącej w skład *licx* pliku. Aby uzyskać więcej informacji na temat *LC.exe*, zobacz [Lc.exe (kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `LC` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`LicenseTarget`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik wykonywalny, dla którego *licenses* pliki są generowane.|  
|`NoLogo`|Opcjonalnie `Boolean` parametru.<br /><br /> Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`OutputDirectory`|Opcjonalnie `String` parametru.<br /><br /> Określa katalog, w której chcesz umieścić dane wyjściowe *licenses* plików.|  
|`OutputLicense`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę *licenses* pliku. Jeśli nie określisz nazwy, nazwa *licx* plik jest używany i *licenses* plik zostanie umieszczony w katalogu, który zawiera *licx* pliku.|  
|`ReferencedAssemblies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa odwołania składniki można załadować podczas generowania *.license* pliku.|  
|`SdkToolsPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*.|  
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy, które zawierają licencjonowanych składników, które mają zostać objęte *licenses* pliku. Aby uzyskać więcej informacji, zobacz dokumentację dla `/complist` przełącznika w [Lc.exe (kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).|  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `LC` zadanie, aby skompilować licencji.  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)