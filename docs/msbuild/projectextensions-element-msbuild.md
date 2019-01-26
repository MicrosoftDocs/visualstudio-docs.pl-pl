---
title: Projectextensions — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c600d7756c83fb55a63a91e81b3d826aa9f3d747
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996756"
---
# <a name="projectextensions-element-msbuild"></a>Projectextensions — element (MSBuild)
Umożliwia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki, aby zawierała non - projektu[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] informacji. Wszystko wewnątrz elementu `ProjectExtensions` element zostanie zignorowana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<ProjectExtensions>  

## <a name="syntax"></a>Składnia  

```xml  
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

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Element główny wymagany [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. |

## <a name="remarks"></a>Uwagi  
 Tylko jeden `ProjectExtensions` element może być używany w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.  

## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje informacje z zintegrowanego środowiska programistycznego znajdujących się w `ProjectExtensions` elementu.  

```xml  
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

## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
