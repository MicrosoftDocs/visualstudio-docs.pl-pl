---
title: Element GuidSymbol | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711128"
---
# <a name="guidsymbol-element"></a>Element GuidSymbol
Element `GuidSymbol` zawiera identyfikator GUID:ID par, który reprezentuje menu, grupy lub polecenia. Identyfikator pochodzi z `IDSymbol` elementu w `GuidSymbol` elemencie. Element `GuidSymbol` ma `name` atrybut, który zapewnia przyjazną nazwę dla identyfikatora GUID, który jest zawarty w `value` atrybucie.

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
|[IDSymbol element](../extensibility/idsymbol-element.md)|Zawiera identyfikator pary GUID:ID reprezentującej menu, grupę lub polecenie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Symbole, element](../extensibility/symbols-element.md)|Grupuje `GuidSymbol` elementy w pliku *vsct.*|

## <a name="remarks"></a>Uwagi
 Zazwyczaj plik *.vsct* zawiera `GuidSymbol` trzy elementy `Symbols` w swojej sekcji, jeden dla samego pakietu, jeden dla zestawu poleceń (zbiór menu, grup i poleceń, które pakiet udostępnia) i jeden dla map bitowych, które zapewniają ikony dla przycisków i innych składników wizualnych. Każdy `IDSymbol` element w `GuidSymbol` danym elemencie musi mieć unikatowy `value`element. Jednak `IDSymbol` elementy, które mają identyczne wartości mogą istnieć w pakiecie, tak długo, jak mają różne elementy podstawowe.

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
