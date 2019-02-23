---
title: ButtonText, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 519ba206b334ef9c955245c152fb14663366472b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698836"
---
# <a name="buttontext-element"></a>ButtonText, element
To pole pozwala określić tekst, który pojawia się w różnych menu. Domyślnie `ButtonText` element jest wyświetlany w menu kontrolerów. `ButtonText` Element staje się również wartość domyślna Jeśli inne pola tekstowe są puste. `ButtonText` Element nie może być pusta, nawet jeśli inne pola tekstowe są określone.

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
|[Strings, element](../extensibility/strings-element.md)|Grupuje elementy tekstu, takie jak `ButtonText` i `CommandName`.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa elementu `ButtonText` element zawiera tekst, który jest wyświetlany dla elementów menu, combos i inne elementy interfejsu użytkownika, które mają widocznego tekstu.

## <a name="see-also"></a>Zobacz także
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)