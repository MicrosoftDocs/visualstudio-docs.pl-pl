---
title: GuidSymbol, element | Microsoft Docs
description: GuidSymbol element zawiera identyfikator GUID pary IDENTYFIKATOR GUID:ID, który reprezentuje menu, grupy lub polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c30c7a48b03b5deed3267e106e926d3cb5114c1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902764"
---
# <a name="guidsymbol-element"></a>GuidSymbol, element
Element `GuidSymbol` zawiera identyfikator GUID pary GUID:ID reprezentującej menu, grupę lub polecenie. Identyfikator pochodzi z `IDSymbol` elementu w `GuidSymbol` elemencie . Element `GuidSymbol` ma `name` atrybut, który zapewnia przyjazną nazwę identyfikatora GUID, który jest zawarty w `value` atrybutu.

## <a name="syntax"></a>Składnia

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|name|Wymagane. Nazwa symbolu identyfikatora GUID.|
|wartość|Wymagane. Identyfikator GUID symbolu identyfikatora GUID.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[IDSymbol, element](../extensibility/idsymbol-element.md)|Zawiera identyfikator pary GUID:ID reprezentujący menu, grupę lub polecenie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Symbols, element](../extensibility/symbols-element.md)|Grupuje `GuidSymbol` elementy w pliku *vsct.*|

## <a name="remarks"></a>Uwagi
 Zazwyczaj plik *vsct* zawiera trzy elementy w jego sekcji, jeden dla samego pakietu, jeden dla zestawu poleceń (kolekcję menu, grup i poleceń dostępnych w pakiecie) i jeden dla map bitowych, które zapewniają ikony dla przycisków i innych składników `GuidSymbol` wizualnych. `Symbols` Każdy `IDSymbol` element w danym `GuidSymbol` elemencie musi mieć unikatowy element `value` . Jednak elementy `IDSymbol` o identycznych wartościach mogą istnieć w pakiecie, o ile mają różne elementy główne.

## <a name="see-also"></a>Zobacz też
- [Visual Studio tabeli poleceń (pliki vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
