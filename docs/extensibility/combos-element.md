---
title: Elementy kombi | Microsoft Docs
description: Element kombi Grupuje elementy kombi, które definiują polecenia, które pojawiają się w polu kombi. Ten artykuł zawiera przykład.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38383882005e3a19b1a31709fb5656caf2a7d788
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938372"
---
# <a name="combos-element"></a>Elementy kombi
Grupuje elementy [elementu kombi](../extensibility/combo-element.md) .

## <a name="syntax"></a>Składnia

```
<Combos>
  <Combo>... </Combo>
  <Combo>... </Combo>
</Combos>
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
|[Elementy kombi](../extensibility/combos-element.md)|Grupuje elementy kombi.|
|[Element kombi](../extensibility/combo-element.md)|Definiuje polecenia, które pojawiają się w polu kombi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Commands, element](../extensibility/commands-element.md)|Reprezentuje kolekcję poleceń na pasku narzędzi pakietu VSPackage.|

## <a name="example"></a>Przykład

```
<Combos>
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
    defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
    <CommandFlag>DynamicVisibility</CommandFlag>
    <Strings>
      <ButtonText>Select Insert Options</ButtonText>
    </Strings>
  </Combo>

  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0500" type="DropDownCombo" defaultWidth="100"
    idCommandList="cmdidGetInsertOptionsList">
    <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>DynamicVisibility</CommandFlag>
    <Strings>
      <ButtonText>Select Insert Options</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

## <a name="see-also"></a>Zobacz także
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
