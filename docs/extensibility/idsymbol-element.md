---
title: IDSymbol, element | Microsoft Docs
description: IdSymbol element zawiera identyfikator pary IDENTYFIKATOR GUID:ID, który reprezentuje menu, grupy lub polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5158b16fb2d12a7d1a93c0296126e915a138269
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904945"
---
# <a name="idsymbol-element"></a>IDSymbol, element
Element `IDSymbol` zawiera identyfikator pary GUID:ID reprezentujący menu, grupę lub polecenie. Identyfikator GUID pochodzi z elementu `GuidSymbol` nadrzędnego. Element `IDSymbol` ma `name` atrybut, który zapewnia przyjazną nazwę identyfikatora, który jest zawarty w `value` atrybut.

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
|wartość|Wymagane. Wartość identyfikatora liczbowego symbolu id.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[GuidSymbol, element](../extensibility/guidsymbol-element.md)|Zawiera identyfikator GUID pary GUID:ID reprezentującej menu, grupę lub polecenie. Grupuje `IDSymbol` elementy.|

## <a name="remarks"></a>Uwagi
 Każdy `IDSymbol` element w danym `GuidSymbol` elemencie musi mieć unikatowy element `value` . Jednak `IDSymbol` elementy, które mają identyczne wartości, mogą istnieć w pakiecie, o ile mają różne elementy główne.

## <a name="see-also"></a>Zobacz też
- [Visual Studio tabeli poleceń (pliki vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
