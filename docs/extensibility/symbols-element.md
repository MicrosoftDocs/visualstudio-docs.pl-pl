---
title: Symbols — element | Microsoft Docs
description: Element symboli definiuje identyfikatory GUID i identyfikatory, które są używane przez inne elementy VSCT. Ten artykuł zawiera przykład.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 173da18ca3b38dd64b8a2594c03abd83987f58f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839325"
---
# <a name="symbols-element"></a>Symbols, element
Definiuje identyfikatory GUID i identyfikatorów, które są używane przez inne elementy VSCT. W przypadku kodu niezarządzanego te informacje zazwyczaj pochodzą z plików nagłówkowych, które są określone przez [element extern](../extensibility/extern-element.md). Kod zarządzany używa elementów podrzędnych elementu Symbols do definiowania tych informacji.

 Jeśli utworzysz plik. vsct z istniejącego pliku. Dyrektor ds, symbole zostaną wygenerowane jako elementy podrzędne elementu symboli. Aby uzyskać więcej informacji, zobacz [How to: Create a. Plik vsct z istniejącego. Plik dyrektor ds](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Elementu Symbols nie należy mylić z [elementem define](../extensibility/define-element.md), który definiuje pary nazwa-wartość do użycia przez preprocesor.

## <a name="syntax"></a>Składnia

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Brak||

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|GuidSymbol|Definiuje symbol GUID. GuidSymbol ma dwa wymagane atrybuty: Name i value. Nazwa jest nazwą symbolu, a wartość jest wartością identyfikatora GUID w postaci ciągu.<br /><br /> Na przykład:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Definiuje symbol. IDSymbol ma dwa wymagane atrybuty: Name i value. Nazwa jest nazwą symbolu, a wartość jest wartością symbolu jako ciąg.<br /><br /> Na przykład:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Element główny pliku. vsct.|

## <a name="example"></a>Przykład

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Zobacz także
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
