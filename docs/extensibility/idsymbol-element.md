---
title: Element IDSymbol | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710376"
---
# <a name="idsymbol-element"></a>IDSymbol element
Element `IDSymbol` zawiera identyfikator pary GUID:ID, która reprezentuje menu, grupę lub polecenie. Identyfikator GUID pochodzi `GuidSymbol` z elementu nadrzędnego. Element `IDSymbol` ma `name` atrybut, który zapewnia przyjazną nazwę dla identyfikatora, `value` który jest zawarty w atrybucie.

## <a name="syntax"></a>Składnia

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|name|Wymagany. Nazwa symbolu identyfikatora.|
|value|Wymagany. Wartość identyfikatora numerycznego symbolu identyfikatora.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element GuidSymbol](../extensibility/guidsymbol-element.md)|Zawiera identyfikator GUID:ID, który reprezentuje menu, grupę lub polecenie. Grupuje `IDSymbol` elementy.|

## <a name="remarks"></a>Uwagi
 Każdy `IDSymbol` element w `GuidSymbol` danym elemencie musi mieć unikatowy `value`element. Jednak `IDSymbol` elementy, które mają identyczne wartości mogą istnieć w pakiecie, tak długo, jak mają różne elementy podstawowe.

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
