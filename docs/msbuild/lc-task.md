---
title: Zadanie LC | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633606"
---
# <a name="lc-task"></a>LC — Zadanie

Zawija *plik LC.exe*, który generuje plik *.license* z pliku *.licx.* Aby uzyskać więcej informacji na temat *LC.exe*, zobacz [Lc.exe (Kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametry

W poniższej tabeli `LC` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`LicenseTarget`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik wykonywalny, dla którego są generowane pliki *.licenses.*|
|`NoLogo`|Parametr `Boolean` opcjonalny.<br /><br /> Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|`OutputDirectory`|Parametr `String` opcjonalny.<br /><br /> Określa katalog, w którym mają być umieszczane wyjściowe pliki *.licenses.*|
|`OutputLicense`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa nazwę pliku *.licenses.* Jeśli nazwa nie zostanie określona, zostanie użyta nazwa pliku *.licx,* a plik *.licenses* zostanie umieszczony w katalogu zawierającym plik *.licx.*|
|`ReferencedAssemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa składniki, do których ma się odwołować, które mają być ładowane podczas generowania pliku *licencji.*|
|`SdkToolsPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*.|
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy zawierające składniki licencjonowane do uwzględnienia w pliku *.licenses.* Aby uzyskać więcej informacji, `/complist` zobacz dokumentację przełącznika w [Lc.exe (Kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).|

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, <xref:Microsoft.Build.Utilities.ToolTask> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `LC` użyto zadania do skompilowania licencji.

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
