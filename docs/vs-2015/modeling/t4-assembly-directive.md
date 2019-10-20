---
title: Dyrektywa zestawu T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bc0e6e7e1530abb63beabc6fa4aedd4a0fa985af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672340"
---
# <a name="t4-assembly-directive"></a>Dyrektywa T4 dotycząca zestawu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu tekstu czasu projektowania dyrektywa `assembly` ładuje zestaw, aby kod szablonu mógł używać jego typów. Efekt jest podobny do dodawania odwołania do zestawu w projekcie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Ogólne omówienie pisania szablonów tekstowych można znaleźć w artykule [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Dyrektywa `assembly` nie jest potrzebna w szablonie tekstowym czasu wykonywania (wstępnie przetworzonym). Zamiast tego należy dodać niezbędne zestawy do **odwołań** projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="using-the-assembly-directive"></a>Używanie dyrektywy Assembly
 Składnia tej dyrektywy jest następująca:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Nazwa zestawu powinna być jedną z następujących:

- Silna nazwa zestawu w GAC, taka jak `System.Xml.dll`. Możesz również użyć długiej formy, takiej jak `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName>.

- Bezwzględna ścieżka zestawu

  Składni `$(variableName)` można użyć do odwoływania się do zmiennych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], takich jak `$(SolutionDir)`, i `%VariableName%` do zmiennych środowiskowych odniesienia. Na przykład:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Dyrektywa zestawu nie ma wpływu na przetworzony wstępnie szablon tekstowy. Zamiast tego należy uwzględnić wymagane odwołania w sekcji **References** projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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
 Makra Visual Studio, takie jak $(SolutionDir), nie działają w MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

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

## <a name="see-also"></a>Zobacz też
 [Dyrektywa T4 dotycząca dołączania](../modeling/t4-include-directive.md)
