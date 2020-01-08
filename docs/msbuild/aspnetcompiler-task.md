---
title: Używanie zadania AspNetCompiler — do prekompilowania aplikacji ASP.NET | Microsoft Docs
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
ms.openlocfilehash: a6535dbec7c09f0888d0fb29a2e6b801632da22f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593463"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler — zadanie
Zadanie `AspNetCompiler` zawija *aspnet_compiler. exe*, narzędzie do wstępnego kompilowania aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

## <a name="task-parameters"></a>Parametry zadania
W poniższej tabeli opisano parametry zadania `AspNetCompiler`.

|Parametr|Opis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ten parametr jest `true`, zestaw o silnej nazwie zezwoli częściowo zaufanym wywołującym.|
|`Clean`|Opcjonalny parametr `Boolean`<br /><br /> Jeśli ten parametr jest `true`, prekompilowana aplikacja zostanie skompilowana w sposób przejrzysty. Wszystkie poprzednio skompilowane składniki zostaną ponownie skompilowane. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-c** w *aspnet_compiler. exe*.|
|`Debug`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ten parametr jest `true`, informacje o debugowaniu (. Plik PDB jest emitowany podczas kompilacji. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-d** w pliku *aspnet_compiler. exe*.|
|`DelaySign`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ten parametr jest `true`, zestaw nie jest w pełni podpisany podczas tworzenia.|
|`FixedNames`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ten parametr jest `true`, skompilowane zestawy będą mieć stałe nazwy..|
|`Force`|Opcjonalny parametr `Boolean`<br /><br /> Jeśli ten parametr jest `true`, zadanie zastąpi katalog docelowy, jeśli już istnieje. Istniejąca zawartość zostanie utracona. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-f** w pliku *aspnet_compiler. exe*.|
|`KeyContainer`|Opcjonalny parametr `String`.<br /><br /> Określa kontener klucza o silnej nazwie.|
|`KeyFile`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę fizyczną do pliku klucza o silnej nazwie.|
|`MetabasePath`|Opcjonalny parametr `String`.<br /><br /> Określa pełną ścieżkę metabazy usług IIS aplikacji. Nie można połączyć tego parametru z parametrami `VirtualPath` lub `PhysicalPath`. Ten parametr odnosi się do przełącznika **-m** w *aspnet_compiler. exe*.|
|`PhysicalPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę fizyczną aplikacji do skompilowania. Jeśli brakuje tego parametru, metabaza IIS jest używana do lokalizowania aplikacji. Ten parametr odnosi się do przełącznika **-p** w pliku *aspnet_compiler. exe*.|
|`TargetFrameworkMoniker`|Opcjonalny parametr `String`.<br /><br /> Określa TargetFrameworkMoniker wskazujący, która .NET Framework wersja *aspnet_compiler. exe* powinna być używana. Akceptuje tylko monikery .NET Framework.|
|`TargetPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę fizyczną, do której aplikacja jest kompilowana. Jeśli nie zostanie określony, aplikacja jest wstępnie skompilowana w miejscu.|
|`Updateable`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ten parametr jest `true`, prekompilowana aplikacja zostanie zaktualizowana.  Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-u** w *aspnet_compiler. exe*.|
|`VirtualPath`|Opcjonalny parametr `String`.<br /><br /> Ścieżka wirtualna aplikacji do skompilowania. Jeśli `PhysicalPath` określony, ścieżka fizyczna jest używana do lokalizowania aplikacji. W przeciwnym razie zostanie użyta metabaza IIS, a aplikacja zostanie przyjęta jako witryna domyślna. Ten parametr odnosi się do przełącznika **-v** w *aspnet_compiler. exe*.|

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład kodu używa zadania `AspNetCompiler` do prekompilowania aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

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

## <a name="see-also"></a>Zobacz także
* [Zadania](../msbuild/msbuild-tasks.md)
* [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
