---
title: ButtonText — element | Microsoft Docs
description: Element ButtonText umożliwia określenie tekstu, który pojawia się w różnych menu. Element ButtonText nie może być pusty, nawet jeśli określono inne pola tekstowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2db20bb3298a7b849e8bc4a261987c5314a29841
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974469"
---
# <a name="buttontext-element"></a>ButtonText, element
To pole umożliwia określenie tekstu wyświetlanego w różnych menu. Domyślnie `ButtonText` element pojawia się na liście Kontrolery menu. `ButtonText`Element jest również domyślnym ustawieniem, jeśli inne pola tekstowe są puste. `ButtonText`Element nie może być pusty, nawet jeśli określono inne pola tekstowe.

## <a name="syntax"></a>Składnia

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Strings, element](../extensibility/strings-element.md)|Grupuje elementy tekstowe, takie jak `ButtonText` i `CommandName` .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa `ButtonText` elementu zawiera tekst wyświetlany dla elementów menu, kombi i innych elementów interfejsu użytkownika, które mają widoczny tekst.

## <a name="see-also"></a>Zobacz także
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
