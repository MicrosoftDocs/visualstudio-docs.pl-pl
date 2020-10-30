---
title: Odwołanie do schematu pliku projektu MSBuild | Microsoft Docs
description: Zobacz tabelę zawierającą listę wszystkich elementów schematu XML programu MSBuild z ich dostępnymi atrybutami i elementami podrzędnymi.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 549e78309ef5fc5e9baf4237f9eca8c7484bc198
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046166"
---
# <a name="msbuild-project-file-schema-reference"></a>Dokumentacja schematu pliku projektu MSBuild

Zawiera tabelę zawierającą wszystkie elementy schematu XML programu MSBuild z ich dostępnymi atrybutami i elementami podrzędnymi.

 MSBuild używa plików projektu, aby poinstruować aparat kompilacji, co należy skompilować i jak go skompilować. Pliki projektów programu MSBuild są plikami XML, które są zgodne ze schematem XML programu MSBuild. Ta sekcja dokumentuje plik definicji schematu XML ( *XSD* ) dla programu MSBuild.

W programie Visual Studio 2017 i nowszych nie jest wymagany link do schematu w pliku projektu programu MSBuild. Jeśli jest obecny, powinna być ` http://schemas.microsoft.com/developer/msbuild/2003` bez względu na wersję programu Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementy schematu XML programu MSBuild

 W poniższej tabeli wymieniono wszystkie elementy schematu XML programu MSBuild wraz z ich elementami i atrybutami podrzędnymi.

|Element|Elementy podrzędne|Atrybuty|
|-------------|--------------------|----------------|
|[Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)|Przypadku<br /><br /> Kiedy|--|
|[Import — element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> Project|
|[ImportGroup, element](../msbuild/importgroup-element.md)|Importuj|Warunek|
|[Item — element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata —*|Warunek<br /><br /> Exclude<br /><br /> Uwzględnij<br /><br /> Usuń|
|[ItemDefinitionGroup, element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|
|[Item, element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|
|[ItemMetadata —, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|
|[OnError — element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> ExecuteTargets|
|[Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz ikonę<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output — element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> Nazwa_produktu<br /><br /> PropertyName<br /><br /> Parametr zadania|
|[Parameter, element](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> ParameterType<br /><br /> Wymagane|
|[ParameterGroup, element](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Project — element (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz ikonę<br /><br /> Importuj<br /><br /> ItemGroup<br /><br /> ProjectExtensions —<br /><br /> PropertyGroup<br /><br /> Cel<br /><br /> UsingTask|DefaultTargets —<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> 'xmlns|
|[ProjectExtensions —, element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property — element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|
|[Property — element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Właściwość*|Warunek|
|[Element zestawu SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nazwa<br /><br /> Wersja|
|[Target — element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Zadanie*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Warunek<br /><br /> DependsOnTargets<br /><br /> Dane wejściowe<br /><br /> KeepDuplicateOutputs<br /><br /> Nazwa<br /><br /> Dane wyjściowe<br /><br /> Zwraca|
|[Element Task elementu docelowego (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> ContinueOnError<br /><br /> *Parametr*|
|[Element Task elementu UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Evaluate|
|[UsingTask, element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup —<br /><br /> Zadanie|AssemblyFile<br /><br /> AssemblyName<br /><br /> Warunek<br /><br /> TaskFactory<br /><br /> TaskName|
|[When, element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz ikonę<br /><br /> ItemGroup<br /><br /> PropertyGroup|Warunek|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Warunki](../msbuild/msbuild-conditions.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
