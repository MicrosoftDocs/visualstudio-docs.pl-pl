---
title: Element zestawu SDK (MSBuild) | Microsoft Docs
description: Dowiedz się więcej na temat składni, atrybutów i elementów dla elementu zestawu MSBuild SDK, który odwołuje się do zestawu SDK projektu MSBuild.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd5f66cc6500a3320e0da962985f5b7fff1e86dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937904"
---
# <a name="sdk-element-msbuild"></a>Element zestawu SDK (MSBuild)

Odwołuje się do zestawu SDK projektu programu MSBuild.

 \<Project> \<Sdk>

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
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="see-also"></a>Zobacz też

- [Instrukcje: odwoływanie się do zestawu SDK projektu programu MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
