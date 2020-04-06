---
title: Symbole Element | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699348"
---
# <a name="symbols-element"></a>Symbols, element
Definiuje identyfikatory GUID i identyfikatory, które są używane przez inne elementy VSCT. W przypadku kodu niezarządzanego te informacje zazwyczaj pochodzą z plików nagłówkowych określonych przez [element Extern](../extensibility/extern-element.md). Kod zarządzany używa elementów podrzędnych symboli elementu do zdefiniowania tych informacji.

 Jeśli utworzysz plik vsct z istniejącego pliku .cto, symbole zostaną wygenerowane jako elementy podrzędne elementu Symbols. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie pliku . Plik vsct z istniejącego pliku . Plik Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Symbols element nie należy mylić z [Define Element](../extensibility/define-element.md), który definiuje pary nazwa-wartość do użycia przez preprocesora.

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
|Guidsymbol|Definiuje symbol GUID. GuidSymbol ma dwa wymagane atrybuty: nazwa i wartość. Nazwa jest nazwą symbolu, a wartość jest wartością identyfikatora GUID jako ciągu.<br /><br /> Na przykład:\<GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|Idsymbol|Definiuje symbol. IDSymbol ma dwa wymagane atrybuty: nazwa i wartość. Nazwa jest nazwą symbolu, a wartość jest wartością symbolu jako ciągu.<br /><br /> Na przykład:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

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

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
