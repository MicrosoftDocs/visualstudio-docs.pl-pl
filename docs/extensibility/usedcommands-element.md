---
title: UsedCommands — element | Microsoft Docs
description: Element UsedCommands Grupuje elementy UsedCommand i inne grupowania UsedCommands. Element UsedCommands jest opcjonalny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89ecd1d0f7697a38ef7318ddf93a91a4397b5d72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934067"
---
# <a name="usedcommands-element"></a>UsedCommands, element
Element UsedCommands Grupuje elementy UsedCommand i inne grupowania UsedCommands.

 Element UsedCommands jest opcjonalny. Jeśli nie wywołasz poleceń zdefiniowanych poza pakietem, nie musisz uwzględniać tej sekcji w pliku. vsct.

## <a name="syntax"></a>Składnia

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[UsedCommand, element](../extensibility/usedcommand-element.md)|Polecenie, które jest implementowane przez inny kod.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia (na przykład elementy menu, menu, paski narzędzi i pola kombi), które pakietu VSPackage zapewnia zintegrowane środowisko programistyczne (IDE).|

## <a name="example"></a>Przykład

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Zobacz także
- [UsedCommand, element](../extensibility/usedcommand-element.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
