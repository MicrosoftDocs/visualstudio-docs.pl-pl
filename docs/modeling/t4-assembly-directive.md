---
title: Dyrektywa T4 dotycząca zestawu
description: Dowiedz się, Visual Studio szablonie tekstowym czasu projektowania dyrektywa zestawu ładuje zestaw, aby kod szablonu może używać jego typów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38b5a7fe2308884d4837a068770af67435ada70e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386361"
---
# <a name="t4-assembly-directive"></a>Dyrektywa T4 dotycząca zestawu

W Visual Studio tekstowym czasu projektowania dyrektywa ładuje zestaw, aby kod szablonu `assembly` może używać jego typów. Efekt jest podobny do dodawania odwołania do zestawu w Visual Studio projektu.

 Aby uzyskać ogólne omówienie pisania szablonów tekstowych, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> Dyrektywa nie jest potrzebna w szablonie tekstowym czasu uruchomienia `assembly` (wstępnie przetworzonym). Zamiast tego dodaj niezbędne zestawy do **odwołania** do projektu Visual Studio projektu.

## <a name="using-the-assembly-directive"></a>Używanie dyrektywy Assembly
 Składnia tej dyrektywy jest następująca:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Nazwa zestawu powinna być jedną z następujących:

- Silna nazwa zestawu w gace GAC, taka jak `System.Xml.dll` . Można również użyć długiego formularza, takiego jak `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` . Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName>.

- Bezwzględna ścieżka zestawu

  Składnia umożliwia odwołanie się do Visual Studio zmiennych, takich jak , i do zmiennych `$(variableName)` `$(SolutionDir)` `%VariableName%` środowiskowych odwołania. Na przykład:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Dyrektywa zestawu nie ma wpływu na przetworzony wstępnie szablon tekstowy. Zamiast tego uwzględnij niezbędne odwołania w **sekcji Odwołania** w Visual Studio projektu. Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie rzeczywistym za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="standard-assemblies"></a>Standardowe zestawy
 Następujące zestawy są ładowane automatycznie, aby nie trzeba było pisać dla nich dyrektyw zestawu:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Jeśli używasz niestandardowej dyrektywy, procesor dyrektywy może załadować dodatkowe zestawy. Na przykład jeśli piszesz szablony dla języka specyficznego dla domeny (domain-specific language — DSL), nie musisz pisać dyrektyw zestawu dla następujących zestawów:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Zestaw zawierający DSL.

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> Używanie właściwości projektu w programie MSBuild i Visual Studio
 Visual Studio makra, takie jak $(SolutionDir), nie działają w programie MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. W tym przykładzie zdefiniowano właściwość o nazwie `myLibFolder` :

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Teraz można używać właściwości projektu w szablonach tekstowych, które są prawidłowo przekształcane w Visual Studio i MSBuild:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Zobacz też

- [Dyrektywa T4 dotycząca dołączania](../modeling/t4-include-directive.md)
