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
ms.openlocfilehash: 072d1b94c552b3aca34a1573e5d6545628f6568e
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167335"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler — zadanie

`AspNetCompiler` Zadanie zapakuje *aspnet_compiler. exe*, narzędzie do prekompilowania aplikacji ASP.NET.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry `AspNetCompiler` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma `true`wartość, zestaw o silnej nazwie zezwoli częściowo zaufanym wywołującym.|
|`Clean`|Parametr `Boolean` opcjonalny<br /><br /> Jeśli ten parametr ma `true`wartość, prekompilowana aplikacja zostanie skompilowana jako oczyszczona. Wszystkie poprzednio skompilowane składniki zostaną ponownie skompilowane. Wartością domyślną jest `false`. Ten parametr odnosi się do przełącznika **-c** w *aspnet_compiler. exe*.|
|`Debug`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr to `true`, informacje debugowania (. Plik PDB jest emitowany podczas kompilacji. Wartością domyślną jest `false`. Ten parametr odnosi się do przełącznika **-d** w pliku *aspnet_compiler. exe*.|
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma `true`wartość, zestaw nie jest w pełni podpisany podczas tworzenia.|
|`FixedNames`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma `true`wartość, skompilowane zestawy będą mieć stałe nazwy..|
|`Force`|Parametr `Boolean` opcjonalny<br /><br /> Jeśli ten parametr ma `true`wartość, zadanie zastąpi katalog docelowy, jeśli już istnieje. Istniejąca zawartość zostanie utracona. Wartością domyślną jest `false`. Ten parametr odnosi się do przełącznika **-f** w pliku *aspnet_compiler. exe*.|
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa kontener klucza o silnej nazwie.|
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę fizyczną do pliku klucza o silnej nazwie.|
|`MetabasePath`|Opcjonalny `String` parametr.<br /><br /> Określa pełną ścieżkę metabazy usług IIS aplikacji. Ten parametr nie może być połączony z `VirtualPath` parametrami lub `PhysicalPath` . Ten parametr odnosi się do przełącznika **-m** w *aspnet_compiler. exe*.|
|`PhysicalPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę fizyczną aplikacji do skompilowania. Jeśli brakuje tego parametru, metabaza IIS jest używana do lokalizowania aplikacji. Ten parametr odnosi się do przełącznika **-p** w pliku *aspnet_compiler. exe*.|
|`TargetFrameworkMoniker`|Opcjonalny `String` parametr.<br /><br /> Określa TargetFrameworkMoniker wskazujący, która .NET Framework wersja *aspnet_compiler. exe* powinna być używana. Akceptuje tylko monikery .NET Framework.|
|`TargetPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę fizyczną, do której aplikacja jest kompilowana. Jeśli nie zostanie określony, aplikacja jest wstępnie skompilowana w miejscu.|
|`Updateable`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ten parametr ma `true`wartość, prekompilowana aplikacja zostanie zaktualizowana.  Wartością domyślną jest `false`. Ten parametr odnosi się do przełącznika **-u** w *aspnet_compiler. exe*.|
|`VirtualPath`|Opcjonalny `String` parametr.<br /><br /> Ścieżka wirtualna aplikacji do skompilowania. Jeśli `PhysicalPath` ta wartość jest określona, ścieżka fizyczna jest używana do lokalizowania aplikacji. W przeciwnym razie zostanie użyta metabaza IIS, a aplikacja zostanie przyjęta jako witryna domyślna. Ten parametr odnosi się do przełącznika **-v** w *aspnet_compiler. exe*.|

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
* [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
