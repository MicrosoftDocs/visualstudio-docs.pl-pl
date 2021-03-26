---
title: Ikona — element | Microsoft Docs
description: Zapoznaj się z ikoną elementu, który reprezentuje ikony używane w rozszerzeniach środowiska IDE programu Visual Studio, w tym atrybuty używanej mapy bitowej i miejsca na pasku mapy bitowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52ccb8093b61e0458f7c3caefea6f826609aa51d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082143"
---
# <a name="icon-element"></a>Icon — element
Atrybut GUID tagu Icon jest identyfikatorem GUID zdefiniowanej mapy bitowej. Ten `id` atrybut wybiera miejsce na pasku mapy bitowej. Ten element jest opcjonalny. Jeśli ten element nie jest uwzględniony w wartości **guidOfficeIcon: msotcidNoIcon** zostanie implikowany.

## <a name="syntax"></a>Składnia

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID zdefiniowanej mapy bitowej.|
|identyfikator|Wymagane. Wybiera miejsce na pasku mapy bitowej.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
