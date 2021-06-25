---
title: Ikona, element | Microsoft Docs
description: Dowiedz się więcej o elemencie Icon, który reprezentuje ikony używane w rozszerzeniach ide Visual Studio, w tym atrybuty używanej mapy bitowej i miejsce w pasku mapy bitowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ad5bfdf000232ef92a9e9a27b12152df36a4335
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900827"
---
# <a name="icon-element"></a>Icon, element
Atrybut guid tagu Icon jest identyfikatorem GUID zdefiniowanej mapy bitowej. Atrybut `id` wybiera miejsce na pasku mapy bitowej. Ten element jest opcjonalny. Jeśli ten element nie zostanie uwzględniony, zostanie **implikowana wartość guidOfficeIcon:msotcidNoIcon.**

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
|[Buttons, element](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Zobacz też
- [Visual Studio tabeli poleceń (pliki vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
