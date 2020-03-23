---
title: Odwołanie do schematu pliku projektu MSBuild | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263106"
---
# <a name="msbuild-project-file-schema-reference"></a>Odwołanie do schematu pliku projektu MSBuild

Zawiera tabelę wszystkich elementów schematu XML MSBuild z ich dostępnych atrybutów i elementów podrzędnych.

 MSBuild używa plików projektu, aby poinstruować aparat kompilacji, co do kompilacji i jak go skompilować. Pliki projektu MSBuild są plikami XML, które są zgodne ze schematem XML MSBuild. W tej sekcji dokumentuje plik definicji schematu XML *(xsd)* dla programu MSBuild.

Łącze schematu w pliku projektu MSBuild nie jest wymagane w programie Visual Studio 2017 i nowszych. Jeśli jest obecny, ` http://schemas.microsoft.com/developer/msbuild/2003` powinno być niezależnie od wersji programu Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementy schematu XML msbuild

 W poniższej tabeli wymieniono wszystkie elementy schematu XML MSBuild wraz z ich elementami podrzędnymi i atrybutami.

|Element|Elementy podrzędne|Atrybuty|
|-------------|--------------------|----------------|
|[Wybierz element (MSBuild)](../msbuild/choose-element-msbuild.md)|Inaczej<br /><br /> Kiedy|--|
|[Importuj element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> Project|
|[ImportGroup, element](../msbuild/importgroup-element.md)|Import|Warunek|
|[Element elementu (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData (Dane)*|Warunek<br /><br /> Exclude<br /><br /> Uwzględnij<br /><br /> Remove|
|[Element ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|
|[Element ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|
|[ItemMetadata element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|
|[Element OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> Zestawy celu wykonania|
|[W przeciwnym razie element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz ikonę<br /><br /> Itemgroup<br /><br /> Propertygroup|--|
|[Element wyjściowy (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> Nazwa_produktu<br /><br /> PropertyName<br /><br /> Parametr zadań|
|[Element parametru](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> Parametertype<br /><br /> Wymagany|
|[Element Grupy parametrów](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Element projektu (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz ikonę<br /><br /> Import<br /><br /> Itemgroup<br /><br /> Wyeksja projektu<br /><br /> Propertygroup<br /><br /> Środowisko docelowe<br /><br /> Usingtask|Defaulttargets<br /><br /> Initialtargets<br /><br /> Toolsversion<br /><br /> TreatAsLocalProperty<br /><br /> Xmlns|
|[Element ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Element właściwości (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|
|[PropertyGroup element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Właściwość*|Warunek|
|[Element Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nazwa<br /><br /> Wersja|
|[Element docelowy (MSBuild)](../msbuild/target-element-msbuild.md)|Onerror<br /><br /> *Zadanie*|Zestawy pocelowe<br /><br /> Przedtargety<br /><br /> Warunek<br /><br /> DependsOnTargets (Zestawy celów DependsOn)<br /><br /> Dane wejściowe<br /><br /> KeepDuplicateOutputs<br /><br /> Nazwa<br /><br /> Dane wyjściowe<br /><br /> Zwraca|
|[Element zadania obiektu docelowego (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> Continueonerror<br /><br /> *Parametr*|
|[Element zadania UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Evaluate|
|[UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|Grupa parametrów<br /><br /> Zadanie|Assemblyfile<br /><br /> Assemblyname<br /><br /> Warunek<br /><br /> Taskfactory<br /><br /> Nazwa_zadania|
|[Gdy element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz ikonę<br /><br /> Itemgroup<br /><br /> Propertygroup|Warunek|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Warunki](../msbuild/msbuild-conditions.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
