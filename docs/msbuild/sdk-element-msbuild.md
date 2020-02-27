---
title: Element zestawu SDK (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a704744032c5dea70246463a816ba8e1f5c84e8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632475"
---
# <a name="sdk-element-msbuild"></a>Element zestawu SDK (MSBuild)

Odwołuje się do zestawu SDK projektu programu MSBuild.

 \<Project > \<SDK >

## <a name="syntax"></a>Składnia

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Atrybut wymagany.<br /><br /> Nazwa zestawu SDK projektu.|
|`Version`|Atrybut opcjonalny.<br /><br /> Wersja zestawu SDK projektu|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="see-also"></a>Zobacz też

- [Instrukcje: odwoływanie się do zestawu SDK projektu programu MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
