---
title: Element projektu (MSBuild) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632982"
---
# <a name="project-element-msbuild"></a>Element projektu (MSBuild)

Wymagany element główny pliku projektu MSBuild.

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

### <a name="attributes"></a>Atrybuty

| Atrybut | Opis |
|------------------------| - |
| `DefaultTargets` | Atrybut opcjonalny.<br /><br /> Domyślny obiekt docelowy lub obiekty docelowe mają być punktem wejścia kompilacji, jeśli nie określono celu. Wiele obiektów docelowych to średnik (;) Rozdzielany.<br /><br /> Jeśli w `DefaultTargets` atrybucie lub wierszu polecenia MSBuild nie określono domyślnego obiektu docelowego, aparat wykonuje pierwszy obiekt docelowy w pliku projektu po ocenie elementów [importu.](../msbuild/import-element-msbuild.md) |
| `InitialTargets` | Atrybut opcjonalny.<br /><br /> Początkowy obiekt docelowy lub obiekty docelowe, `DefaultTargets` które mają być uruchamiane przed obiektami docelowymi określonymi w atrybucie lub w wierszu polecenia. Wiele obiektów docelowych`;`jest rozdzielanych średnikiem ( ). Jeśli wiele importowanych `InitialTargets`plików zdefiniuj , wszystkie wymienione obiekty docelowe zostaną uruchomione w kolejności, w jakiej napotkane zostaną importowane pliki. |
| `Sdk` | Atrybut opcjonalny. <br /><br /> Nazwa SDK i opcjonalna wersja do utworzenia niejawnych instrukcji importu, które są dodawane do pliku proj. Jeśli nie określono żadnej wersji, MSBuild podejmie próbę rozwiązania wersji domyślnej.  Na przykład: `<Project Sdk="Microsoft.NET.Sdk" />` lub `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Atrybut opcjonalny.<br /><br /> Wersja zestawu narzędzi MSBuild używa do określenia wartości dla $(MSBuildBinPath) i $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Atrybut opcjonalny.<br /><br /> Nazwy właściwości, które nie będą uważane za globalne. Ten atrybut uniemożliwia określonym właściwościom wiersza polecenia zastępowanie wartości właściwości, które są ustawione w pliku projektu lub obiektów docelowych i wszystkich kolejnych importach. Wiele właściwości to średnik (;) Rozdzielany.<br /><br /> Zwykle właściwości globalne zastępują wartości właściwości, które są ustawione w pliku projektu lub obiektów docelowych. Jeśli właściwość jest `TreatAsLocalProperty` wymieniona w wartości, wartość właściwości globalnej nie zastępuje wartości właściwości, które są ustawione w tym pliku i wszelkie kolejne importy. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie tych samych plików źródłowych z różnymi opcjami](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Uwaga:**  Właściwości globalne można ustawić w wierszu polecenia za pomocą przełącznika **-property** (lub **-p).** Można również ustawić lub zmodyfikować właściwości globalne dla projektów podrzędnych `Properties` w kompilacji wielu projektów przy użyciu atrybutu zadania MSBuild. Aby uzyskać więcej informacji, zobacz [zadanie MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Atrybut opcjonalny.<br /><br /> Po określeniu `xmlns` atrybut musi mieć `http://schemas.microsoft.com/developer/msbuild/2003`wartość . |

### <a name="child-elements"></a>Elementy podrzędne

| Element | Opis |
| - | - |
| [Wybierz ikonę](../msbuild/choose-element-msbuild.md) | Element opcjonalny.<br /><br /> Ocenia elementy podrzędne, aby `ItemGroup` wybrać jeden `PropertyGroup` zestaw elementów i/lub elementów do oceny. |
| [Import](../msbuild/import-element-msbuild.md) | Element opcjonalny.<br /><br /> Umożliwia plik projektu, aby zaimportować inny plik projektu. Może istnieć zero `Import` lub więcej elementów w projekcie. |
| [Grupa importu](../msbuild/importgroup-element.md) | Element opcjonalny.<br /><br /> Zawiera kolekcję `Import` elementów, które są zgrupowane w warunkach opcjonalnych. |
| [Itemgroup](../msbuild/itemgroup-element-msbuild.md) | Element opcjonalny.<br /><br /> Element grupowania dla poszczególnych elementów. Elementy są określane przy użyciu [elementu Element.](../msbuild/item-element-msbuild.md) Może istnieć zero `ItemGroup` lub więcej elementów w projekcie. |
| [Itemdefinitiongroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Element opcjonalny.<br /><br /> Umożliwia zdefiniowanie zestawu definicji elementów, które są wartościami metadanych, które są domyślnie stosowane do wszystkich elementów w projekcie. ItemDefinitionGroup zastępuje potrzebę użycia `CreateItem` zadania i `CreateProperty` zadania. |
| [Wyeksja projektu](../msbuild/projectextensions-element-msbuild.md) | Element opcjonalny.<br /><br /> Zapewnia sposób utrwalania informacji innych niż MSBuild w pliku projektu MSBuild. Może istnieć zero `ProjectExtensions` lub jeden element w projekcie. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | Element opcjonalny.<br /><br /> Element grupowania dla poszczególnych właściwości. Właściwości są określone przy użyciu [Property](../msbuild/property-element-msbuild.md) elementu. Może istnieć zero `PropertyGroup` lub więcej elementów w projekcie. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Element opcjonalny.<br /><br /> Odwołuje się do sdk projektu MSBuild.  Ten element może służyć jako alternatywa dla atrybutu Sdk. |
| [Obiekt docelowy](../msbuild/target-element-msbuild.md) | Element opcjonalny.<br /><br /> Zawiera zestaw zadań dla MSBuild do wykonania sekwencyjnie. Zadania są określane przy użyciu [Task](../msbuild/task-element-msbuild.md) elementu. Może istnieć zero `Target` lub więcej elementów w projekcie. |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | Element opcjonalny.<br /><br /> Umożliwia rejestrowanie zadań w msbuild. Może istnieć zero `UsingTask` lub więcej elementów w projekcie. |

### <a name="parent-elements"></a>Elementy nadrzędne

 Brak.

## <a name="see-also"></a>Zobacz też

- [Jak: Określ, który cel ma być najpierw zbudowany](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Msbuild](../msbuild/msbuild.md)
