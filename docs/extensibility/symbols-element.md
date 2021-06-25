---
title: Symbol, | Microsoft Docs
description: Symbol element definiuje identyfikatory GUID i identyfikatory, które są używane przez inne elementy VSCT. Ten artykuł zawiera przykład.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b593f353714f2fbb6f5b726fa2bbc0da449043ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901737"
---
# <a name="symbols-element"></a>Symbols, element
Definiuje identyfikatory GUID i identyfikatory, które są używane przez inne elementy VSCT. W przypadku kodu nieza pomocą kodu te informacje zazwyczaj pochodzą z plików nagłówkowych określonych przez [extern, element](../extensibility/extern-element.md). Kod zarządzany używa elementów podrzędnych elementu Symbols do definiowania tych informacji.

 Jeśli utworzysz plik vsct na podstawie istniejącego pliku cto, symbole zostaną wygenerowane jako elementy children elementu Symbols. Aby uzyskać więcej informacji, [zobacz How to: Create a . Plik Vsct z istniejącego pliku . Plik Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Symbol elementu nie należy mylić z [elementem Define](../extensibility/define-element.md), który definiuje pary nazwa-wartość do użycia przez preprocesor.

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
|Guidsymbol|Definiuje symbol identyfikatora GUID. GuidSymbol ma dwa wymagane atrybuty: nazwa i wartość. Nazwa jest nazwą symbolu, a wartość jest wartością identyfikatora GUID jako ciąg.<br /><br /> Na przykład:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|Idsymbol|Definiuje symbol. IdSymbol ma dwa wymagane atrybuty: nazwa i wartość. Nazwa jest nazwą symbolu, a wartość jest wartością symbolu jako ciąg.<br /><br /> Na przykład:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Element główny pliku vsct.|

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
