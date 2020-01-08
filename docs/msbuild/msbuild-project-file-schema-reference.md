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
ms.openlocfilehash: def9edb232a37bc58a56ffd1ec9a16bcb1b75092
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590322"
---
# <a name="msbuild-project-file-schema-reference"></a>Odwołanie do schematu pliku projektu MSBuild
Zawiera tabelę zawierającą wszystkie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementy schematu XML z ich dostępnymi atrybutami i elementami podrzędnymi.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa plików projektu do nakazuje aparatowi kompilacji, co należy skompilować, i jak go skompilować. pliki projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] są plikami XML, które są zgodne ze schematem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML. Ta sekcja dokumentuje plik definicji schematu XML (*XSD*) dla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="msbuild-xml-schema-elements"></a>Elementy schematu XML programu MSBuild
 W poniższej tabeli wymieniono wszystkie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementy schematu XML wraz z ich elementami i atrybutami podrzędnymi.

|Element|Elementy podrzędne|{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}|
|-------------|--------------------|----------------|
|[Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)|Przypadku<br /><br /> Po|--|
|[Import — element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> {1&gt;Projekt&lt;1}|
|[Zaimportuj element](../msbuild/importgroup-element.md)|Importuj|Warunek|
|[Item — element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Warunek<br /><br /> Wyklucz<br /><br /> Uwzględnij<br /><br /> Usuwanie|
|[ItemDefinitionGroup, element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|
|[Item, element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|
|[ItemMetadata —, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|
|[OnError — element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> ExecuteTargets|
|[Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz pozycję<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output — element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> Nazwa_produktu<br /><br /> PropertyName<br /><br /> Parametr zadania|
|[Element parametru](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> ParameterType<br /><br /> Wymagane|
|[Element DataParameter](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Project — element (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz pozycję<br /><br /> Importuj<br /><br /> ItemGroup<br /><br /> ProjectExtensions —<br /><br /> PropertyGroup<br /><br /> Docelowy<br /><br /> UsingTask|DefaultTargets —<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions —, element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property — element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|
|[Property — element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Warunek|
|[Element zestawu SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nazwa<br /><br /> Wersja|
|[Target — element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Zadanie*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Warunek<br /><br /> DependsOnTargets<br /><br /> Wejścia<br /><br /> KeepDuplicateOutputs<br /><br /> Nazwa<br /><br /> Wyjścia<br /><br /> Zwraca|
|[Task — element (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> ContinueOnError<br /><br /> *Parametr*|
|[TaskBody —, element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Ocena programu|
|[UsingTask, element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody —|AssemblyFile<br /><br /> AssemblyName<br /><br /> Warunek<br /><br /> TaskFactory<br /><br /> TaskName|
|[When, element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz pozycję<br /><br /> ItemGroup<br /><br /> PropertyGroup|Warunek|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Warunki](../msbuild/msbuild-conditions.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
