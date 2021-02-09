---
title: IDSymbol — element | Microsoft Docs
description: 'Element IDSymbol zawiera identyfikator pary GUID: ID, która reprezentuje menu, grupę lub polecenie.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 830324e708ff83fbcbbbdb98d261130e92c7ba00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883197"
---
# <a name="idsymbol-element"></a>IDSymbol, element
`IDSymbol`Element zawiera identyfikator pary GUID: ID, która reprezentuje menu, grupę lub polecenie. Identyfikator GUID pochodzi z elementu nadrzędnego `GuidSymbol` . `IDSymbol`Element ma `name` atrybut, który zawiera przyjazną nazwę dla identyfikatora, który jest zawarty w `value` atrybucie.

## <a name="syntax"></a>Składnia

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|name|Wymagane. Nazwa symbolu identyfikatora.|
|wartość|Wymagane. Wartość identyfikatora numerycznego symbolu identyfikatora.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[GuidSymbol, element](../extensibility/guidsymbol-element.md)|Zawiera identyfikator GUID pary identyfikatora GUID:, która reprezentuje menu, grupę lub polecenie. Grupuje `IDSymbol` elementy.|

## <a name="remarks"></a>Uwagi
 Każdy `IDSymbol` element w danym `GuidSymbol` elemencie musi mieć unikatową wartość `value` . Jednak `IDSymbol` elementy mające identyczne wartości mogą istnieć w pakiecie, o ile mają różne obiekty nadrzędne.

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
