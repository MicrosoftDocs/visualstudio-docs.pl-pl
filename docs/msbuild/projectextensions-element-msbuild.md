---
title: ProjectExtensions — — element (MSBuild) | Microsoft Docs
description: Dowiedz się więcej na temat elementu MSBuildProjectExtensions, który umożliwia plikom projektu MSBuild zawiera informacje inne niż MSBuild.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7b186fa1d7a5ecb8297045d4b0bbb111d136d1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905290"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions —, element (MSBuild)

Zezwala na pliki projektu MSBuild zawierające informacje inne niż MSBuild. Wszystkie elementy wewnątrz `ProjectExtensions` elementu zostaną zignorowane przez MSBuild.

 \<Project> \<ProjectExtensions>

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
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="remarks"></a>Uwagi

 `ProjectExtensions`W projekcie MSBuild może być użyty tylko jeden element.

## <a name="example"></a>Przykład

 Poniższy przykład kodu przedstawia informacje z zintegrowanego środowiska programistycznego, które są przechowywane w `ProjectExtensions` elemencie.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
