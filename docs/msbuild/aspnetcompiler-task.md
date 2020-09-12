---
title: Użyj zadania AspNetCompiler — do prekompilowania ASP.NET
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 43b7ccc11e8d265c0b1490e7e8de0bd33d903904
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036187"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler — zadanie

`AspNetCompiler`Zadanie zapakuje *aspnet_compiler.exe*, narzędzie do prekompilowania aplikacji ASP.NET.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry `AspNetCompiler` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma wartość `true` , zestaw o silnej nazwie zezwoli częściowo zaufanym wywołującym.|
|`Clean`|`Boolean`Parametr opcjonalny<br /><br /> Jeśli ten parametr ma wartość `true` , prekompilowana aplikacja zostanie skompilowana jako oczyszczona. Wszystkie poprzednio skompilowane składniki zostaną ponownie skompilowane. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-c** w *aspnet_compiler.exe*.|
|`Debug`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr to `true` , informacje debugowania (. Plik PDB jest emitowany podczas kompilacji. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-d** na *aspnet_compiler.exe*.|
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma wartość `true` , zestaw nie jest w pełni podpisany podczas tworzenia.|
|`FixedNames`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma wartość `true` , skompilowane zestawy będą mieć stałe nazwy..|
|`Force`|`Boolean`Parametr opcjonalny<br /><br /> Jeśli ten parametr ma wartość `true` , zadanie zastąpi katalog docelowy, jeśli już istnieje. Istniejąca zawartość zostanie utracona. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-f** na *aspnet_compiler.exe*.|
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa kontener klucza o silnej nazwie.|
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę fizyczną do pliku klucza o silnej nazwie.|
|`MetabasePath`|Opcjonalny `String` parametr.<br /><br /> Określa pełną ścieżkę metabazy usług IIS aplikacji. Ten parametr nie może być połączony z `VirtualPath` `PhysicalPath` parametrami lub. Ten parametr odnosi się do przełącznika **-m** na *aspnet_compiler.exe*.|
|`PhysicalPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę fizyczną aplikacji do skompilowania. Jeśli brakuje tego parametru, metabaza IIS jest używana do lokalizowania aplikacji. Ten parametr odnosi się do przełącznika **-p** na *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Opcjonalny `String` parametr.<br /><br /> Określa TargetFrameworkMoniker wskazujący, która .NET Framework wersja *aspnet_compiler.exe* powinna być używana. Akceptuje tylko monikery .NET Framework.|
|`TargetPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę fizyczną, do której aplikacja jest kompilowana. Jeśli nie zostanie określony, aplikacja jest wstępnie skompilowana w miejscu.|
|`Updateable`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma wartość `true` , prekompilowana aplikacja zostanie zaktualizowana.  Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika **-u** na *aspnet_compiler.exe*.|
|`VirtualPath`|Opcjonalny `String` parametr.<br /><br /> Ścieżka wirtualna aplikacji do skompilowania. Jeśli `PhysicalPath` Ta wartość jest określona, ścieżka fizyczna jest używana do lokalizowania aplikacji. W przeciwnym razie zostanie użyta metabaza IIS, a aplikacja zostanie przyjęta jako witryna domyślna. Ten parametr odnosi się do przełącznika **-v** na *aspnet_compiler.exe*.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Przykład

Poniższy przykład kodu używa `AspNetCompiler` zadania do prekompilowania aplikacji ASP.NET.

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
* [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
