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
ms.openlocfilehash: 8c65bafd9183c97efa7595c10d7bdb3641c5f75f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595140"
---
# <a name="sdk-element-msbuild"></a>Element zestawu SDK (MSBuild)
Odwołuje się do zestawu SDK projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

 \<Project> \<Sdk>

## <a name="syntax"></a>Składnia

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Atrybut wymagany.<br /><br /> Nazwa zestawu SDK projektu.|
|`Version`|Atrybut opcjonalny.<br /><br /> Wersja zestawu SDK projektu|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="see-also"></a>Zobacz także
- [Instrukcje: odwoływanie się do zestawu SDK projektu programu MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
