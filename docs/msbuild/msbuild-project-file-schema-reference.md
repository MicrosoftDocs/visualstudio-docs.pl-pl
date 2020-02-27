---
title: Odwołanie do schematu pliku projektu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f8a59349540492cd441f1eb3fa63ed520c0e8cd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633281"
---
# <a name="msbuild-project-file-schema-reference"></a>Odwołanie do schematu pliku projektu MSBuild

Zawiera tabelę zawierającą wszystkie elementy schematu XML programu MSBuild z ich dostępnymi atrybutami i elementami podrzędnymi.

 MSBuild używa plików projektu, aby poinstruować aparat kompilacji, co należy skompilować i jak go skompilować. Pliki projektów programu MSBuild są plikami XML, które są zgodne ze schematem XML programu MSBuild. Ta sekcja dokumentuje plik definicji schematu XML (*XSD*) dla programu MSBuild.

W programie Visual Studio 2017 i nowszych nie jest wymagany link do schematu w pliku projektu programu MSBuild. Jeśli jest obecny, należy ` http://schemas.microsoft.com/developer/msbuild/2003` niezależnie od wersji programu Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementy schematu XML programu MSBuild

 W poniższej tabeli wymieniono wszystkie elementy schematu XML programu MSBuild wraz z ich elementami i atrybutami podrzędnymi.

|Element|Elementy podrzędne|Atrybuty|
|-------------|--------------------|----------------|
|[Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)|Przypadku<br /><br /> Czasie|--|
|[Import — element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> Project|
|[Zaimportuj element](../msbuild/importgroup-element.md)|Import|Warunek|
|[Item — element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata —*|Warunek<br /><br /> Exclude<br /><br /> Uwzględnij<br /><br /> Remove|
|[ItemDefinitionGroup, element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|
|[Item, element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|
|[ItemMetadata —, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|
|[OnError — element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> ExecuteTargets|
|[Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz ikonę<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output — element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> Parametr zadania|
|[Element parametru](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> ParameterType<br /><br /> Wymagany|
|[Element DataParameter](../msbuild/parametergroup-element.md)|*Konstruktora*|--|
|[Project — element (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz ikonę<br /><br /> Import<br /><br /> ItemGroup<br /><br /> ProjectExtensions —<br /><br /> PropertyGroup<br /><br /> Środowisko docelowe<br /><br /> UsingTask|DefaultTargets —<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions —, element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property — element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|
|[Property — element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Właściwość*|Warunek|
|[Element zestawu SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name (Nazwa)<br /><br /> Wersja|
|[Target — element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Zadanie podrzędne*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Warunek<br /><br /> DependsOnTargets<br /><br /> Dane wejściowe<br /><br /> KeepDuplicateOutputs<br /><br /> Name (Nazwa)<br /><br /> Dane wyjściowe<br /><br /> Zwraca|
|[Task — element (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> ContinueOnError<br /><br /> *Konstruktora*|
|[TaskBody —, element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Evaluate|
|[UsingTask, element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody —|AssemblyFile<br /><br /> AssemblyName<br /><br /> Warunek<br /><br /> TaskFactory<br /><br /> TaskName|
|[When, element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz ikonę<br /><br /> ItemGroup<br /><br /> PropertyGroup|Warunek|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Warunki](../msbuild/msbuild-conditions.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
