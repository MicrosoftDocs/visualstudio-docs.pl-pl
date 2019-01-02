---
title: Wstępna kompilacja aplikacji ASP.NET przy użyciu aspnetcompiler — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 84367bdf99ae7c29f5ecac4d345cd21c8cc17689
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935292"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler — zadanie
`AspNetCompiler` Zawija zadanie *aspnet_compiler.exe*, narzędzie wstępnej kompilacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AspNetCompiler` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ten parametr ma `true`,, zestawu o silnej nazwie umożliwi częściowo zaufanych wywołań.|  
|`Clean`|Opcjonalnie `Boolean` parametru<br /><br /> Jeśli ten parametr jest `true`, zostanie utworzona czyszczenie wstępnie skompilowanej aplikacji. Wszystkie składniki skompilowane wcześniej zostaną ponownie skompilowane. Wartość domyślna to `false`. Ten parametr odnosi się do **- c** Włącz *aspnet_compiler.exe*.|  
|`Debug`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ten parametr jest `true`, informacje o debugowaniu (. Plik PDB) są emitowane podczas kompilacji. Wartość domyślna to `false`. Ten parametr odnosi się do **-d** Włącz *aspnet_compiler.exe*.|  
|`DelaySign`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ten parametr jest `true`, zestaw jest niecałkowicie podpisany podczas tworzenia.|  
|`FixedNames`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ten parametr jest `true`, skompilowanych zestawów będzie mieć stałe nazwy...|  
|`Force`|Opcjonalnie `Boolean` parametru<br /><br /> Jeśli ten parametr jest `true`, zadania spowoduje zastąpienie katalog docelowy, jeśli już istnieje. Istniejąca zawartość zostanie utracona. Wartość domyślna to `false`. Ten parametr odnosi się do **-f** Włącz *aspnet_compiler.exe*.|  
|`KeyContainer`|Opcjonalnie `String` parametru.<br /><br /> Określa kontener klucza silnej nazwy.|  
|`KeyFile`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę fizyczną do pliku klucza silnej nazwy...|  
|`MetabasePath`|Opcjonalnie `String` parametru.<br /><br /> Określa pełną ścieżkę metabazy usług IIS aplikacji. Ten parametr nie może być łączone z `VirtualPath` lub `PhysicalPath` parametrów. Ten parametr odnosi się do **-m** Włącz *aspnet_compiler.exe*.|  
|`PhysicalPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę fizyczną aplikacji do skompilowania. Jeśli ten parametr jest Brak, metabazy usług IIS jest używana do lokalizowania aplikacji. Ten parametr odnosi się do **-p** Włącz *aspnet_compiler.exe*.|  
|`TargetFrameworkMoniker`|Opcjonalnie `String` parametru.<br /><br /> Określa TargetFrameworkMoniker wskazująca, która wersja środowiska .NET Framework *aspnet_compiler.exe* powinny być używane. Akceptuje tylko krótkie nazwy .NET Framework.|  
|`TargetPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę fizyczną, do której aplikacja jest kompilowana. Jeśli nie zostanie określony, aplikacja jest wstępnie skompilowaną w miejscu.|  
|`Updateable`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ten parametr jest `true`, wstępnie skompilowanej aplikacji będzie można aktualizować.  Wartość domyślna to `false`. Ten parametr odnosi się do **-u** Włącz *aspnet_compiler.exe*.|  
|`VirtualPath`|Opcjonalnie `String` parametru.<br /><br /> Ścieżka wirtualna aplikacja jest kompilowana. Jeśli `PhysicalPath` określony, ścieżkę fizyczną jest używana do lokalizowania aplikacji. W przeciwnym razie metabazy usług IIS jest używana, a aplikacja będzie traktowana jako w domyślnej witrynie. Ten parametr odnosi się do **- v** Włącz *aspnet_compiler.exe*.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `AspNetCompiler` zadania wstępnej kompilacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji.  
  
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
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
