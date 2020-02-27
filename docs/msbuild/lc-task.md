---
title: LC — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cea0ca4e6562ccc626bf52ad74dfa75b4f118f9
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633606"
---
# <a name="lc-task"></a>LC — Zadanie

Zawija program *LC. exe*, który generuje plik *licencji* z pliku *. licx* . Aby uzyskać więcej informacji na temat *LC. exe*, zobacz [LC. exe (kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania `LC`.

|Parametr|Opis|
|---------------|-----------------|
|`LicenseTarget`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa plik wykonywalny, dla którego są generowane pliki *licencji* .|
|`NoLogo`|Opcjonalny parametr `Boolean`.<br /><br /> Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|`OutputDirectory`|Opcjonalny parametr `String`.<br /><br /> Określa katalog, w którym mają zostać umieszczone pliki *. licenses* .|
|`OutputLicense`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku *. licenses* . Jeśli nazwa nie zostanie określona, zostanie użyta nazwa pliku *. licx* , a plik *. licenses* zostanie umieszczony w katalogu, który zawiera plik *. licx* .|
|`ReferencedAssemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa składniki, do których istnieją odwołania do załadowania podczas generowania pliku *licencji* .|
|`SdkToolsPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *Resgen. exe*.|
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy zawierające licencjonowane składniki do uwzględnienia w pliku *. licenses* . Aby uzyskać więcej informacji, zapoznaj się z dokumentacją przełącznika `/complist` w pliku [LC. exe (kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).|

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa zadania `LC` do kompilowania licencji.

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

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
