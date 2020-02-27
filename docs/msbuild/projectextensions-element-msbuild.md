---
title: ProjectExtensions — — element (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94f2d88aa19bf01ebe6f25c7d80772c812abcc59
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632969"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions —, element (MSBuild)

Zezwala na pliki projektu MSBuild zawierające informacje inne niż MSBuild. Wszystkie elementy wewnątrz elementu `ProjectExtensions` zostaną zignorowane przez MSBuild.

 \<Project > \<ProjectExtensions — >

## <a name="syntax"></a>Składnia

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

 None

### <a name="child-elements"></a>Elementy podrzędne

 None

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="remarks"></a>Uwagi

 Tylko jeden element `ProjectExtensions` może być używany w projekcie programu MSBuild.

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
