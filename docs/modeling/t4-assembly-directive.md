---
title: Dyrektywa T4 dotycząca zestawu
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f605748d4bda13567713b646f0232d684ec46fe1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748186"
---
# <a name="t4-assembly-directive"></a>Dyrektywa T4 dotycząca zestawu

W szablonie tekstu czasu projektowania programu Visual Studio dyrektywa `assembly` ładuje zestaw, aby kod szablonu mógł używać jego typów. Efekt jest podobny do dodawania odwołania do zestawu w projekcie programu Visual Studio.

 Ogólne omówienie pisania szablonów tekstowych można znaleźć w artykule [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Dyrektywa `assembly` nie jest potrzebna w szablonie tekstowym czasu wykonywania (wstępnie przetworzonym). Zamiast tego należy dodać niezbędne zestawy do **odwołań** projektu programu Visual Studio.

## <a name="using-the-assembly-directive"></a>Używanie dyrektywy Assembly
 Składnia tej dyrektywy jest następująca:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Nazwa zestawu powinna być jedną z następujących:

- Silna nazwa zestawu w GAC, taka jak `System.Xml.dll`. Możesz również użyć długiej formy, takiej jak `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName>.

- Bezwzględna ścieżka zestawu

  Składni `$(variableName)` można użyć do odwoływania się do zmiennych środowiskowych programu Visual Studio, takich jak `$(SolutionDir)`, i `%VariableName%` do referencyjnych zmiennych środowiska. Na przykład:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Dyrektywa zestawu nie ma wpływu na przetworzony wstępnie szablon tekstowy. Zamiast tego należy uwzględnić wymagane odwołania w sekcji **odwołania** projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

## <a name="msbuild"></a>Korzystanie z właściwości projektu w MSBuild i Visual Studio
 Makra programu Visual Studio, takie jak $ (SolutionDir), nie działają w programie MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. Ten przykład definiuje właściwość o nazwie `myLibFolder`:

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

## <a name="see-also"></a>Zobacz także

- [Dyrektywa T4 dotycząca dołączania](../modeling/t4-include-directive.md)