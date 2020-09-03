---
title: GuidSymbol — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711128"
---
# <a name="guidsymbol-element"></a>GuidSymbol, element
`GuidSymbol`Element zawiera identyfikator GUID pary GUID: ID, która reprezentuje menu, grupę lub polecenie. Identyfikator pochodzi od `IDSymbol` elementu w `GuidSymbol` elemencie. `GuidSymbol`Element ma `name` atrybut, który zawiera przyjazną nazwę dla identyfikatora GUID, który jest zawarty w `value` atrybucie.

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
|name|Wymagany. Nazwa symbolu GUID.|
|value|Wymagany. Identyfikator GUID symbolu GUID.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[IDSymbol, element](../extensibility/idsymbol-element.md)|Zawiera identyfikator pary GUID: ID, która reprezentuje menu, grupę lub polecenie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Symbol — element](../extensibility/symbols-element.md)|Grupuje `GuidSymbol` elementy w pliku *. vsct* .|

## <a name="remarks"></a>Uwagi
 Zwykle plik *. vsct* zawiera trzy `GuidSymbol` elementy w `Symbols` sekcji, jeden dla samego pakietu, jeden dla zestawu poleceń (Kolekcja menu, grup i poleceń udostępnianych przez pakiet), a drugi dla map bitowych, które udostępniają ikony przycisków i innych elementów wizualnych. Każdy `IDSymbol` element w danym `GuidSymbol` elemencie musi mieć unikatową wartość `value` . Jednak `IDSymbol` elementy mające identyczne wartości mogą istnieć w pakiecie, o ile mają różne obiekty nadrzędne.

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
