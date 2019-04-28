---
title: Odwołanie do schematu pliku projektu MSBuild | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c49c2198a4ecc40a40e3f5f6414bfd4af47279b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842295"
---
# <a name="msbuild-project-file-schema-reference"></a>Odwołanie do schematu pliku projektu MSBuild
Zawiera spis wszystkich [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementów schematu XML z ich dostępne atrybuty i elementy podrzędne.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa plików projektu, aby nakazać aparat kompilacji, co do kompilacji i jak ją skompilować. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu są plikami XML, które będą zgodne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] schematu XML. W tej sekcji omówiono definicji schematu XML (*XSD*) plik [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="msbuild-xml-schema-elements"></a>Elementy schematu MSBuild XML
 Poniższa tabela zawiera listę wszystkich [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementy schematu XML wraz z ich elementów podrzędnych i atrybutów.

|Element|Elementy podrzędne|Atrybuty|
|-------------|--------------------|----------------|
|[Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)|W przeciwnym razie<br /><br /> Kiedy|--|
|[Import — element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> Projekt|
|[Importgroup — element](../msbuild/importgroup-element.md)|Import|Warunek|
|[Item — element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Warunek<br /><br /> Wyklucz<br /><br /> Uwzględnij<br /><br /> Usuń|
|[ItemDefinitionGroup — element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|
|[Itemgroup — element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|
|[Itemmetadata — element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|
|[OnError — element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> ExecuteTargets|
|[Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[OUTPUT — element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Parameter — element](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> Zgodność<br /><br /> Wymagane|
|[Parametergroup — element](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Project — element (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz<br /><br /> Import<br /><br /> ItemGroup<br /><br /> Projectextensions —<br /><br /> PropertyGroup<br /><br /> Cel<br /><br /> UsingTask|Defaulttargets —<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Projectextensions — element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property — element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|
|[PropertyGroup — element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Warunek|
|[Zestaw SDK, element (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nazwa<br /><br /> Wersja|
|[TARGET — element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Zadanie*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Warunek<br /><br /> DependsOnTargets<br /><br /> Dane wejściowe<br /><br /> KeepDuplicateOutputs<br /><br /> Nazwa<br /><br /> Dane wyjściowe<br /><br /> Zwraca|
|[Task — element (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> ContinueOnError<br /><br /> *Parametr*|
|[Taskbody — element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Oceń|
|[Usingtask — element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Taskbody —|AssemblyFile<br /><br /> AssemblyName<br /><br /> Warunek<br /><br /> TaskFactory<br /><br /> TaskName|
|[Gdy element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz<br /><br /> ItemGroup<br /><br /> PropertyGroup|Warunek|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Warunki](../msbuild/msbuild-conditions.md)
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
