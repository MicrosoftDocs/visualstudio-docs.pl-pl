---
title: ProjectExtensions — — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0afc4f73ed287f753acf87bd0b112e6f5303e996
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551265"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zezwala [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] na pliki projektu, które nie zawierają [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] informacji. Wszystkie elementy wewnątrz `ProjectExtensions` elementu zostaną zignorowane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
 \<Project>  
 \<ProjectExtensions>  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymagany element główny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
  
## <a name="remarks"></a>Uwagi  
 `ProjectExtensions`W projekcie może być użyty tylko jeden element [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia informacje z zintegrowanego środowiska programistycznego, które są przechowywane w `ProjectExtensions` elemencie.  
  
```  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](msbuild.md)
