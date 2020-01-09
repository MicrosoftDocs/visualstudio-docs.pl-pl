---
title: Project — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1bb7c49e4f3dc86594c8a3211bacb538d3f10c4f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597441"
---
# <a name="project-element-msbuild"></a>Project — element (MSBuild)
Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="syntax"></a>Składnia

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

| Atrybut | Opis |
|------------------------| - |
| `DefaultTargets` | Atrybut opcjonalny.<br /><br /> Domyślny element docelowy lub docelowy jako punkt wejścia kompilacji, jeśli nie określono elementu docelowego. Wiele obiektów docelowych jest średnikami (;) Lista.<br /><br /> Jeśli nie określono domyślnego obiektu docelowego w atrybucie `DefaultTargets` lub [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wierszu polecenia, aparat wykonuje pierwszy element docelowy w pliku projektu po ocenie elementów [importu](../msbuild/import-element-msbuild.md) . |
| `InitialTargets` | Atrybut opcjonalny.<br /><br /> Początkowe miejsce docelowe lub obiekty docelowe do uruchomienia przed obiektami docelowymi określonymi w atrybucie `DefaultTargets` lub w wierszu polecenia. Wiele obiektów docelowych jest rozdzielanych średnikami (`;`). W przypadku zdefiniowania wielu zaimportowanych plików `InitialTargets`wszystkie wymienione obiekty docelowe zostaną uruchomione w kolejności, w której napotkane są Importy. |
| `Sdk` | Atrybut opcjonalny. <br /><br /> Nazwa zestawu SDK i wersja opcjonalna do użycia w celu utworzenia niejawnych instrukcji importu, które są dodawane do pliku. proj. Jeśli żadna wersja nie zostanie określona, program MSBuild podejmie próbę rozpoznania wersji domyślnej.  Na przykład `<Project Sdk="Microsoft.NET.Sdk" />` lub `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Atrybut opcjonalny.<br /><br /> Wersja zestawu narzędzi MSBuild używa do określenia wartości dla $ (MSBuildBinPath) i $ (MSBuildToolsPath). |
| `TreatAsLocalProperty` | Atrybut opcjonalny.<br /><br /> Nazwy właściwości, które nie będą uznawane za globalne. Ten atrybut uniemożliwia określone właściwości wiersza polecenia przed zastępowaniem wartości właściwości, które są ustawiane w pliku projektu lub obiektów docelowych oraz wszystkich kolejnych importach. Wiele właściwości jest średnikiem (;) Lista.<br /><br /> Zwykle właściwości globalne przesłaniają wartości właściwości, które są ustawiane w pliku projektu lub obiektów docelowych. Jeśli właściwość jest wymieniona w wartości `TreatAsLocalProperty`, wartość właściwości globalnej nie przesłania wartości właściwości, które są ustawione w tym pliku oraz wszelkich kolejnych importów. Aby uzyskać więcej informacji, zobacz [How to: build te same pliki źródłowe z innymi opcjami](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Uwaga:**  Właściwości globalne są ustawiane w wierszu polecenia za pomocą przełącznika **-Property** (lub **-p**). Można również ustawić lub zmodyfikować właściwości globalne dla projektów podrzędnych w kompilacji wieloprojektowej przy użyciu atrybutu `Properties` zadania programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadanie MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Atrybut opcjonalny.<br /><br /> Gdy jest określony, atrybut `xmlns` musi mieć wartość `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Elementy podrzędne

| Element | Opis |
| - | - |
| [Następnie](../msbuild/choose-element-msbuild.md) | Element opcjonalny.<br /><br /> Oblicza elementy podrzędne w celu wybrania jednego zestawu `ItemGroup` elementów i/lub `PropertyGroup` elementów do obliczenia. |
| [Importujuj](../msbuild/import-element-msbuild.md) | Element opcjonalny.<br /><br /> Umożliwia plikowi projektu Importowanie innego pliku projektu. W projekcie może istnieć co najmniej zero elementów `Import`. |
| [Element importgroup](../msbuild/importgroup-element.md) | Element opcjonalny.<br /><br /> Zawiera kolekcję elementów `Import`, które są zgrupowane w warunku opcjonalnym. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Element opcjonalny.<br /><br /> Element grupujący dla poszczególnych elementów. Elementy są określone za pomocą elementu [Item](../msbuild/item-element-msbuild.md) . W projekcie może istnieć co najmniej zero elementów `ItemGroup`. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Element opcjonalny.<br /><br /> Umożliwia zdefiniowanie zestawu definicji elementów, które są wartościami metadanych, które są stosowane do wszystkich elementów w projekcie, domyślnie. ItemDefinitionGroup zastępuje potrzebę korzystania z zadania `CreateItem` i zadania `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Element opcjonalny.<br /><br /> Zapewnia sposób utrwalania[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] informacji w pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. W projekcie może istnieć zero lub jeden `ProjectExtensions` elementów. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Element opcjonalny.<br /><br /> Element grupujący dla poszczególnych właściwości. Właściwości są określone za pomocą elementu [Właściwości](../msbuild/property-element-msbuild.md) . W projekcie może istnieć co najmniej zero elementów `PropertyGroup`. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Element opcjonalny.<br /><br /> Odwołuje się do zestawu SDK projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Ten element może być używany jako alternatywa dla atrybutu SDK. |
| [Cel](../msbuild/target-element-msbuild.md) | Element opcjonalny.<br /><br /> Zawiera zestaw zadań do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wykonywania sekwencyjnie. Zadania są określone za pomocą elementu [Task](../msbuild/task-element-msbuild.md) . W projekcie może istnieć co najmniej zero elementów `Target`. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Element opcjonalny.<br /><br /> Zapewnia sposób rejestrowania zadań w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. W projekcie może istnieć co najmniej zero elementów `UsingTask`. |

### <a name="parent-elements"></a>Elementy nadrzędne
 Brak.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
