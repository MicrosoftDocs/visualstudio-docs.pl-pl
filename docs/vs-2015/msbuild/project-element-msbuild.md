---
title: Project — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b11449626050c4da75b09f2d348a4b1b0190ec4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476934"
---
# <a name="project-element-msbuild"></a>Project — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wymagany element główny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
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
  
|       Atrybut        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Opis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 Atrybut opcjonalny.<br /><br /> Domyślny element docelowy lub docelowy jako punkt wejścia kompilacji, jeśli nie określono elementu docelowego. Wiele obiektów docelowych jest średnikami (;) Lista.<br /><br /> Jeśli nie określono domyślnego obiektu docelowego w `DefaultTargets` atrybucie lub [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wierszu polecenia, aparat wykonuje pierwszy element docelowy w pliku projektu po ocenie elementów [importu](../msbuild/import-element-msbuild.md) .                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             Atrybut opcjonalny.<br /><br /> Początkowe miejsce docelowe lub obiekty docelowe do uruchomienia przed obiektami docelowymi określonymi w `DefaultTargets` atrybucie lub w wierszu polecenia. Wiele obiektów docelowych jest średnikami (;) Lista.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Atrybut opcjonalny.<br /><br /> Wersja zestawu narzędzi MSBuild używa do określenia wartości dla $ (MSBuildBinPath) i $ (MSBuildToolsPath).                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | Atrybut opcjonalny.<br /><br /> Nazwy właściwości, które nie będą uznawane za globalne. Ten atrybut uniemożliwia określone właściwości wiersza polecenia przed zastępowaniem wartości właściwości, które są ustawiane w pliku projektu lub obiektów docelowych oraz wszystkich kolejnych importach. Wiele właściwości jest średnikiem (;) Lista.<br /><br /> Zwykle właściwości globalne przesłaniają wartości właściwości, które są ustawiane w pliku projektu lub obiektów docelowych. Jeśli właściwość jest wymieniona w `TreatAsLocalProperty` wartości, wartość właściwości globalnej nie przesłania wartości właściwości, które są ustawione w tym pliku oraz wszelkich kolejnych importów. Aby uzyskać więcej informacji, zobacz [How to: build te same pliki źródłowe z innymi opcjami](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Uwaga:**  Właściwości globalne są ustawiane w wierszu polecenia za pomocą przełącznika **/Property** (lub **/p**). Można również ustawić lub zmodyfikować właściwości globalne dla projektów podrzędnych w kompilacji wieloprojektowej przy użyciu `Properties` atrybutu zadania programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadanie MSBuild](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Wymagany atrybut (w MSBuild 15. x i wcześniejszych).<br /><br /> `xmlns`Atrybut musi mieć wartość `http://schemas.microsoft.com/developer/msbuild/2003` .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Wybierz ikonę](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne w celu wybrania jednego zestawu `ItemGroup` elementów i/lub `PropertyGroup` elementów do obliczenia.|  
|[Importuj](../msbuild/import-element-msbuild.md)|Element opcjonalny.<br /><br /> Umożliwia plikowi projektu Importowanie innego pliku projektu. W projekcie może istnieć zero lub więcej `Import` elementów.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Element grupujący dla poszczególnych elementów. Elementy są określone za pomocą elementu [Item](../msbuild/item-element-msbuild.md) . W projekcie może istnieć zero lub więcej `ItemGroup` elementów.|  
|[ProjectExtensions —](../msbuild/projectextensions-element-msbuild.md)|Element opcjonalny.<br /><br /> Zapewnia sposób utrwalania nie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tylko informacji w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu. W projekcie może istnieć zero lub jeden `ProjectExtensions` element.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Element grupujący dla poszczególnych właściwości. Właściwości są określone za pomocą elementu [Właściwości](../msbuild/property-element-msbuild.md) . W projekcie może istnieć zero lub więcej `PropertyGroup` elementów.|  
|[Obiektów](../msbuild/target-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zadań [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do wykonania sekwencyjnie. Zadania są określone za pomocą elementu [Task](../msbuild/task-element-msbuild.md) . W projekcie może istnieć zero lub więcej `Target` elementów.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Element opcjonalny.<br /><br /> Zapewnia sposób rejestrowania zadań w programie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . W projekcie może istnieć zero lub więcej `UsingTask` elementów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)
