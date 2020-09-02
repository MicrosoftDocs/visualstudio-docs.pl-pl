---
title: Odwołanie do schematu pliku projektu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158857"
---
# <a name="msbuild-project-file-schema-reference"></a>Odwołanie do schematu pliku projektu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera tabelę wszystkich [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] elementów schematu XML z ich dostępnymi atrybutami i elementami podrzędnymi.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używa plików projektu do nakazuje aparatowi kompilacji, co należy skompilować i jak go skompilować. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliki projektu są plikami XML, które są zgodne ze [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] schematem XML. Ta sekcja dokumentuje plik definicji schematu XML (XSD) dla [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="msbuild-xml-schema-elements"></a>Elementy schematu XML programu MSBuild  
 W poniższej tabeli wymieniono wszystkie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] elementy schematu XML wraz z ich elementami i atrybutami podrzędnymi.  
  
|Element|Elementy podrzędne|Atrybuty|  
|-------------|--------------------|----------------|  
|[Choose, element (MSBuild)](../msbuild/choose-element-msbuild.md)|Przypadku<br /><br /> Kiedy|--|  
|[Import — Element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> Projekt|  
|[Zaimportuj element](../msbuild/importgroup-element.md)|Importuj|Warunek|  
|[Item — Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata —*|Warunek<br /><br /> Exclude<br /><br /> Uwzględnij<br /><br /> Usuń|  
|[ItemDefinitionGroup — Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|  
|[ItemGroup, element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|  
|[ItemMetadata — Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|  
|[OnError — Element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> ExecuteTargets|  
|[Otherwise — Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz ikonę<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output — Element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> Nazwa_produktu<br /><br /> PropertyName<br /><br /> Parametr zadania|  
|[Element parametru](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> ParameterType<br /><br /> Wymagane|  
|[Element DataParameter](../msbuild/parametergroup-element.md)|*Parametr*|--|  
|[Project — Element (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz ikonę<br /><br /> Importuj<br /><br /> ItemGroup<br /><br /> ProjectExtensions —<br /><br /> PropertyGroup<br /><br /> Cel<br /><br /> UsingTask|DefaultTargets —<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> 'xmlns|  
|[ProjectExtensions, element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property — Element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|  
|[PropertyGroup, element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Właściwość*|Warunek|  
|[Target, element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Zadanie*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Warunek<br /><br /> DependsOnTargets<br /><br /> Dane wejściowe<br /><br /> KeepDuplicateOutputs<br /><br /> Nazwa<br /><br /> Dane wyjściowe<br /><br /> Zwraca|  
|[Task — Element (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> ContinueOnError<br /><br /> *Parametr*|  
|[TaskBody, element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Evaluate|  
|[UsingTask — Element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup —<br /><br /> TaskBody —|AssemblyFile<br /><br /> AssemblyName<br /><br /> Warunek<br /><br /> TaskFactory<br /><br /> TaskName|  
|[When, element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz ikonę<br /><br /> ItemGroup<br /><br /> PropertyGroup|Warunek|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Przyczyn](../msbuild/msbuild-conditions.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
