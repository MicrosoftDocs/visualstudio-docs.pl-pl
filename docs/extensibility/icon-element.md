---
title: Ikona — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf4f8a69e565620007fba4b9970ce96bb1513995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710518"
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
|guid|Wymagany. Identyfikator GUID zdefiniowanej mapy bitowej.|
|identyfikator|Wymagany. Wybiera miejsce na pasku mapy bitowej.|

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
