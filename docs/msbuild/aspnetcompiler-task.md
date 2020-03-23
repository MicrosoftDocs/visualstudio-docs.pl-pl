---
title: Tworzenie wstępnie ASP.NET aplikacji za pomocą zadania AspNetCompiler | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 8707371fac876586d38f12a797aaee7228b5f729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634581"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler — zadanie

Zadanie `AspNetCompiler` jest zawijane *aspnet_compiler.exe*, narzędzie do wstępnej kompilacji aplikacji ASP.NET.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli `AspNetCompiler` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli ten `true`parametr jest ,, zestaw silnej nazwy pozwoli częściowo zaufanych wywołań.|
|`Clean`|Parametr `Boolean` opcjonalny<br /><br /> Jeśli ten `true`parametr jest , wstępnie skompilowana aplikacja zostanie zbudowana w czystości. Wszystkie wcześniej skompilowane składniki zostaną ponownie skompilowane. Wartością domyślną jest `false`. Ten parametr odpowiada przełącznikowi **-c** *na aspnet_compiler.exe*.|
|`Debug`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli ten `true`parametr jest , informacje debugowania (. PDB) jest emitowany podczas kompilacji. Wartością domyślną jest `false`. Ten parametr odpowiada przełącznikowi **-d** *aspnet_compiler.exe*.|
|`DelaySign`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli ten `true`parametr jest , zestaw nie jest w pełni podpisany po utworzeniu.|
|`FixedNames`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli ten `true`parametr jest , skompilowane zestawy otrzymają stałe nazwy..|
|`Force`|Parametr `Boolean` opcjonalny<br /><br /> Jeśli ten `true`parametr jest , zadanie zastąpi katalog docelowy, jeśli już istnieje. Istniejąca zawartość jest tracona. Wartością domyślną jest `false`. Ten parametr odpowiada przełącznikowi **-f** *aspnet_compiler.exe*.|
|`KeyContainer`|Parametr `String` opcjonalny.<br /><br /> Określa kontener klucza silnej nazwy.|
|`KeyFile`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę fizyczną do pliku klucza silnej nazwy..|
|`MetabasePath`|Parametr `String` opcjonalny.<br /><br /> Określa pełną ścieżkę metabazy usług IIS aplikacji. Tego parametru nie `VirtualPath` można `PhysicalPath` łączyć z parametrami. Ten parametr odpowiada przełącznikowi **-m** *aspnet_compiler.exe*.|
|`PhysicalPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę fizyczną aplikacji, która ma zostać skompilowana. Jeśli ten parametr jest brak, metabaza usług IIS jest używana do lokalizowania aplikacji. Ten parametr odpowiada przełącznikowi **-p** *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Parametr `String` opcjonalny.<br /><br /> Określa obiekt TargetFrameworkMoniker wskazujący, która wersja programu .NET Framework *programu aspnet_compiler.exe* powinna być używana. Akceptuje tylko monikery .NET Framework.|
|`TargetPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę fizyczną, do której jest kompilowana aplikacja. Jeśli nie zostanie określony, aplikacja jest wstępnie skompilowana w miejscu.|
|`Updateable`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli ten `true`parametr jest , wstępnie skompilowana aplikacja będzie można zaktualizować.  Wartością domyślną jest `false`. Ten parametr odpowiada przełącznikowi **-u** *aspnet_compiler.exe*.|
|`VirtualPath`|Parametr `String` opcjonalny.<br /><br /> Ścieżka wirtualna aplikacji, która ma zostać skompilowana. Jeśli `PhysicalPath` określono, ścieżka fizyczna jest używana do lokalizowania aplikacji. W przeciwnym razie używana jest metabaza usług IIS, a zakłada się, że aplikacja znajduje się w lokacji domyślnej. Ten parametr odpowiada przełącznikowi **-v** na *aspnet_compiler.exe*.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, <xref:Microsoft.Build.Utilities.ToolTask> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu `AspNetCompiler` używa zadania do wstępnej kompilacji aplikacji ASP.NET.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

* [Zadania](../msbuild/msbuild-tasks.md)
* [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
