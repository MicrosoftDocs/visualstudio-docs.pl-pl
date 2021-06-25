---
title: ButtonText, element | Microsoft Docs
description: Element ButtonText umożliwia określenie tekstu, który jest wyświetlany w różnych menu. Element ButtonText nie może być pusty, nawet jeśli określono inne pola tekstowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf20a6876dd7ba52413a11f30a3d0130b32e535d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900721"
---
# <a name="buttontext-element"></a>ButtonText, element
To pole umożliwia określenie tekstu, który będzie wyświetlany w różnych menu. Domyślnie element jest `ButtonText` wyświetlany w kontrolerach menu. Element `ButtonText` staje się również wartością domyślną, jeśli inne pola tekstowe są puste. Element `ButtonText` nie może być pusty, nawet jeśli określono inne pola tekstowe.

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
|[Strings, element](../extensibility/strings-element.md)|Grupuje elementy tekstowe, takie `ButtonText` jak i `CommandName` .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa elementu zawiera tekst, który jest wyświetlany dla elementów menu, kombinacji i innych elementów interfejsu użytkownika, które `ButtonText` mają widoczny tekst.

## <a name="see-also"></a>Zobacz też
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
