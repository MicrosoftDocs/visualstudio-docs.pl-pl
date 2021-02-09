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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c4e68889ae6ea8396795137243cf732a9b028931
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883275"
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
